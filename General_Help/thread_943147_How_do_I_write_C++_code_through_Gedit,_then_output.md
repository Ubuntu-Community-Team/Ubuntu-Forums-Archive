---
title: "How do I write C++ code through Gedit, then output to..."
date: 2008-10-09
forum: General Help
---

### Post by johnnyxxxcakes on 2008-10-09
I was looking around in a post about people's favorite IDE's for Ubuntu, and I came across quite a lot of people that just use Gedit, and then output it to the terminal? If I'm not mistaken, that's what they said.

I use Geany right now, and I was looking to try other things because of all the good things I hear about using Gedit, or KDevelop, or Vim, etc.

So how do I compile/view the C++ code I wrote in Gedit?

---

### Post by Pro-reason on 2008-10-10
You sound like someone familiar with programming on Windows.  You may be used to having an IDE that does stuff for you, instead of (much more simply) just doing it yourself on the command line.

I personally don't write C++ code, but I believe that the command that compiles it is “gcc”.  So, if your code is in a file called “hello.c” on your home directory, then you would type “gcc ~/hello.c” to compile it.

---

### Post by loell on 2008-10-10
its g++ instead of gcc. ;)

you might also want to look at **anjuta**, it manages c++ project well.

---

### Post by ubunny on 2008-10-10
go to the edit->preferences and click the plugins tab, you can add your own shortcut commands so you can have g++ compile your c++ code for you etc.  Like all things linux, mix and match to taste.  Experiment and google for examples.

---

### Post by Pro-reason on 2008-10-10
> **loell said:**
> its g++ instead of gcc. ;)


Right you are.

Here's an example:

Paste this into gedit:

(courtesy of [http://99-bottles-of-beer.net/language-c++-833.html](http://99-bottles-of-beer.net/language-c++-833.html))

```

                                                     /* obfuscated 99
						     bottles   program
						     in c++ coded  by
						     paddy   obrien */
                                                   #include <iostream>
                                                  using namespace std;
                                                void beer(int,int);    void
					       wall(); int main() {        int
                                              bottles                        =99;
					      while                      (bottles)
                                            {for(int i=0;    i < 2;          ++i)
                                            beer(        bottles,i);  cout   <<
                                            "take one down pass it around"
                                           <<  endl;                        beer
                                            (--bottles,                            0)
                                            ;cout    <<                      endl;}
                                            return      0                            ;}
                                            void beer      (int  bottles, int i)
                                            {cout <<                       bottles
					    <<            "  bottle(s) of beer ";
                                            if(!i)            wall(); else cout <<
                                            endl;}  void wall(){              cout
                                            << "on the wall"         <<endl;}
                                            /*Yeah I know it's          a sorry
                                            excuse for                    a bottle
                                            but given how little code    was
                                            required it's the               best I
                                            could/felt like doing,    oh  and
                                            by the way all the     comments
					     \are purely                  filler  */

```

Save it as ~/beer.c

Open a terminal.

Type this:

```

g++ ~/beer.c
./a.out

```

There you have a working program.

---

### Post by Calmatory on 2008-10-10
I just love the way things are done w/o actual IDE. E.g. I can ssh to my server machine from remote machine and write code. I can come home and continue the project I started from the remote machine. Then I can go to school and ssh from the computer to continue my project.

Just plain great. Love it. ;)

Nano + g++... <3

---

### Post by johnnyxxxcakes on 2008-10-10
I used Geany a lot, and I find that a lot of people like using Gedit because of it's lightweight and easy to use. Plus, they can compile it through the terminal, and a lot of you say that's easier.

Yes, I did a bit of programming on Windows. Not much though. I'm not too much of a fan of Anjuta though. I tried that a while back and I guess it was just buggy on my machine, or I didn't give it much of a chance. :p I was learning basic Visual Basic .NET programming in my Junior year of high school, but just like the basics of any programming language; such as variables, strings, loops, etc. Over the summer, I bought a C++ For Dummies book and I've been looking into that myself. My senior year, we're learning C++ which is more fun.

I think I'll try out using Gedit with the 'g++' command from the terminal. My only problem is that I don't know what to program. :-k

But thanks anyway guys. :)

---

### Post by johnnyxxxcakes on 2008-10-10
> **Pro-reason said:**
> You sound like someone familiar with programming on Windows.  You may be used to having an IDE that does stuff for you, instead of (much more simply) just doing it yourself on the command line.

I personally don't write C++ code, but I believe that the command that compiles it is “gcc”.  So, if your code is in a file called “hello.c” on your home directory, then you would type “gcc ~/hello.c” to compile it.

I tried your method. I have the follow code I'm trying to execute:

> 
//
// Program to convert temperature from Celsius degree
// units into Fahrenheit degree units:
// Fahrenheit = Celsius * (212 - 32)/100 + 32
//
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{
	// enter the temperature in Celsius
	int celsius;
	cout << "Enter the temperature in Celsius:";
	cin >> celsius;

	// calculate conversion factor for Celsius
	// to Fahrenheit
	int factor;
	factor = 212 - 32;

	// use conversion factor to convert Celsius
	// into Fahrenheit values
	int Fahrenheit;
	fahrenheit = factor * celsius/100 + 32;

	// output the results (followed by a NewLine)
	cout << "Fahrenheit value is:";
	cout << fahrenheit << endl;

	// wait until user is ready before terminating program
	// to allow the user to see the program results
	system("PAUSE");
	return 0;
}


That .cpp file is located in this directory: /home/john/Documents/C++/Conversion.cpp
So when I go: g++ ~/home/john/Documents/C++/Conversion.cpp
I get the error of:
> 
john@john-laptop:~$ g++ ~/home/john/Documents/C++/Conversion.cpp
g++: /home/john/home/john/Documents/C++/Conversion.cpp: No such file or directory
g++: no input files
john@john-laptop:~$ 


Any idea what I'm doing wrong?

---

### Post by thegner on 2008-10-10
> **johnnyxxxcakes said:**
> I tried your method. I have the follow code I'm trying to execute:



That .cpp file is located in this directory: /home/john/Documents/C++/Conversion.cpp
So when I go: g++ ~/home/john/Documents/C++/Conversion.cpp
I get the error of:


Any idea what I'm doing wrong?
The '~' is a shortcut for your home directory. Notice how the error says "/home/john/home/john"? What you want to do is either delete the ~ from your path, or delete the /home/john. Your final result should be:

g++ /home/john/Documents/C++/Conversion.cpp

or

g++ ~/Documents/C++/Conversion.cpp

Give that a try...

Travis

---

### Post by Rich78 on 2008-10-10
Looks like it can't find your cpp file.

Try navigating to the actual project directory and g++ yourfile.cpp

---

### Post by thegner on 2008-10-10
> **Rich78 said:**
> Looks like it can't find your cpp file.

Try navigating to the actual project directory and g++ yourfile.cpp
This is a better idea since the output file 'a.out' will end up in your current working directory.

With Rich78's way, at least the output file will be in the same directory as the source.

---

### Post by johnnyxxxcakes on 2008-10-10
> **thegner said:**
> The '~' is a shortcut for your home directory. Notice how the error says "/home/john/home/john"? What you want to do is either delete the ~ from your path, or delete the /home/john. Your final result should be:

g++ /home/john/Documents/C++/Conversion.cpp

or

g++ ~/Documents/C++/Conversion.cpp

Give that a try...

Travis

Okay thanks! That really helped out a lot.

---

### Post by Pro-reason on 2008-10-10
You can also use “-o” to specify the output file, instead of the default “a.out”.  For example:
```

cd ~/Documents/C++
g++ Conversion.cpp -o Conversion.out
```

See “g++ --help” or ”info g++” for further information.

---

