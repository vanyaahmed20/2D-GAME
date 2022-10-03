# 2D-GAME
# OVER VIEW
We have designed a 2D game using the concept of object oriented language (OOP) and also by using SFML which is an external language of C++.
We have designed an adventure game where the hero kills the enemy and reach to different levels and gain points.
We have created the characters by using Photoshop (pixel version) and have done the animation. 
# PURPOSE
The purpose of designing this game was to clear our concept about OOP.
To know more about C++ and as this idea was a different one we decided to work on it. 
Getting to know about Photoshop more and other external Languages like SFML and C++. 
This was an interesting topic for those who had an interest in game development.  
# LANGUAGE USED
The concept of object oriented programming was used and the languages we used were the SFML external language of C++ and other language was C++
# CODE
#include<SFML/Graphics.hpp>
#include<SFML/Window.hpp>
#include<SFML/System.hpp>
#include"Enemy.h"
#include"Hero.h"
#include "Time_animation.h"
#include<iostream>
#include<string>

using namespace sf;
using namespace std;

int main()
{
	string y;
	cout << ".................................\"How to play the game\".....................................\n";
	cout << ".....................................\"For movemennt\"........................................\n";
	cout << ".....................................\"W for going Up\".......................................\n";
	cout << ".....................................\"S for going Down\".....................................\n";
	cout << ".....................................\"A for going Left\".....................................\n";
	cout << ".....................................\"D for going Right\"....................................\n";
	cout << "...............................\"Hold J for attacking the enemy\".............................\n";
	cout << "...............................\"For each kill you get 10 points\"............................\n";
	cout << "....................\"If 11 enemies passes you and get to the castle you lose\"................\n";
	cout << "....................\"You have 2 minutes to kill as many enemies as you can\"..................\n";
	cout << "..............................\"Hopefully you will enjoy the game\"...........................\n";
	cout << "\n\nPlease enter \"Your name\" to start the game: ";
	cin >> y;
	
	//Creating window
	RenderWindow window(VideoMode(1920,1080), "THE RISE OF THE HERO", Style::Close|Style::Fullscreen);
	//setting frame reate
	window.setFramerateLimit(60);

	//Creating a texture variable for health
	Texture HEALTH;
	//Smoothing the texture loaded
	HEALTH.setSmooth(true);
	//Loading images from the file 
	HEALTH.loadFromFile("content/Heart.png");
	//Creating a texture variable for enemy
	Texture EMEMY;
	//Smoothing the texture loaded
	EMEMY.setSmooth(true);
	//Loading images from the file 
	EMEMY.loadFromFile("content/Enemy1.png");
	//Creating Enemy class variable and passing the required variable
	Enemy enemy(&EMEMY, Vector2u(4, 1), 0.1, &HEALTH, Vector2u(1, 11), 0.1);

	//Creating a tecture variable for Hero
	Texture HERO;
	//Smoothing the texture
	HERO.setSmooth(true);
	//Loading the images
	HERO.loadFromFile("content/Hero.png");
	//Creating hero class variable
	Hero hero(&HERO, Vector2u(5, 5), 0.1);
	
	//Background
	Texture bg;
	bg.loadFromFile("content/bg01.png");
	//creating a rectangle shape in which the background will print/exisit
	RectangleShape bx;
	bx.setTexture(&bg);
	bg.setSmooth(true);
	//setting size of background
	bx.setSize(Vector2f(1920,1080));
	

	//ANIMATION FOR TIME
	Texture TM;
	TM.loadFromFile("content/TIME1.png");
	TM.setSmooth(true);
	Time_animation time_obj(&TM,Vector2u(120,1),1);

	//variable to store time
	float deltatime;
	//A class that record time
	Clock cll,dll;
	//A class that handle time 
	Time time;
	//variable to decied the speed of enemy
	float speed = 4.0;
	//condition to run the game
	while (window.isOpen())
	{
		//setting an end condition
		if (enemy.end() <= 10 && time.asSeconds() < 120)
		{
			//Storeing time
			deltatime = cll.restart().asSeconds();
			//updating/moving positon of enemy and hero 
			enemy.update(deltatime, &window, speed);
			hero.updatehero(deltatime, &window);
			time_obj.update(deltatime);
			///clearing the frame of window
			window.clear();
			//drawing enemy,hero and background on the window
			window.draw(bx);
			enemy.healthbar(&window);
			enemy.render(&window);
			hero.renderhero(&window);
			time_obj.rendertime(&window);
			//displaying the the things that we had drawn on the window 
			window.display();
			//saving the time elapsed kind of a stop watch
			time = dll.getElapsedTime();
		}
		else
		{
			//closing the  game window when the end condition reach at some point
			window.close();
		}
	
		
	}
	if (enemy.end() >= 10)
	{
		cout << y << "! you have lost the game. \n";
	}
	else
	{
		cout << y << "! you have won the game. \n";
	}
	//displaying the point on the console 
	cout << y << "! you have killed " << enemy.getpoint() / 10 << " enemies. \n";
	cout << y << "! your score is " << enemy.getpoint() << "." << endl;
}

 
#  	OTHER OUTLOOK OF 2D-GAME:
#	The startup:
![image](https://user-images.githubusercontent.com/92653096/193650531-4f6913d7-324f-49ed-a776-187c74ccda50.png)

At first when the program run the console will open with the game controls mentioned on it. When the user will enter his/her name and press enter the game will start.
When the user press enters the game will start and a new window will open with hero and enemy’s animation as well as the animation of health and time animation.

#	INSIDE OF THE GAME:
![image](https://user-images.githubusercontent.com/92653096/193650656-73e03ae6-f79b-4a49-abcc-b8b1267e7465.png)

Hero can move forward, upward, to left side and right side with the help of W, S, A, D keys from the keyboard.
When hero moves near the enemy and the user press “J” key the enemy will get killed.
When the enemy cross the left side of the screen hero will loss a hearts/health
When the time that is shown on the top right of the screen reaches 2:00 the game will end, and the hero will win the game.
In the end of the game hero will either win or loss the game and points will be shown on the screen. 






#	END RESULT:
![image](https://user-images.githubusercontent.com/92653096/193650785-f321cd77-28cc-4b98-9aa4-dd5d98361559.png)


# LEARNING OUTCOME
o	We successfully designed a 2 D game with the help SFML and the core concepts of Object-oriented programming. 
Our project consists of different libraries of SFML that help us to successfully create our game.

