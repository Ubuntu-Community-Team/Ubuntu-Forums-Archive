---
title: "TRYING to install GCC 4.3.3"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Liveone on 2009-03-15
Okay, so I found a post on here and it got me going with [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

That guy got to (his results):
-------------------------------------------------------
"Then I ran: ./configure
result:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gnatbind... no
checking for gnatmake... no
checking whether compiler driver understands Ada... no
checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for correct version of gmp.h... no
configure: error: Building GCC requires GMP 4.1+ and MPFR 2.3.0+.
Try the --with-gmp and/or --with-mpfr options to specify their locations.
Copies of these libraries' source code can be found at their respective
hosting sites as well as at [ftp://gcc.gnu.org/pub/gcc/infrastructure/](ftp://gcc.gnu.org/pub/gcc/infrastructure/).
See also [http://gcc.gnu.org/install/prerequisites.html](http://gcc.gnu.org/install/prerequisites.html) for additional info.
If you obtained GMP and/or MPFR from a vendor distribution package, make
sure that you have installed both the libraries and the header files.
They may be located in separate packages.

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
then I ran: make
result:

make: *** No targets specified and no makefile found. Stop.
-------------------------------------------------------------------

(supposedly it was already installed after that for him)

Well, after about an hour, I finally extracted the .tar.bz2 GCC file. Then it took me another hour to realize it extracted to /home.

I opened up the folder "gcc-4.3.3" and it contained |another "GCC" folder a "libdecnumber" folder, a "libgcc" folder, and a "libgomp" folder along with 8 script files. Once script file says "configure" another says "compile".

If I open the "GCC" folder there are 8 more folders (different) with a few scripts (one says configure) and a whole mess of text editor files.

What I did: used alt + f2, Typed "./configure". Tried it with/without terminal, got "Error stating file '/home/myusername/configure': No such file or directory" Then I typed ./configure and ran it with both of the configure scripts, with/without terminal, and got the same error. 

Same thing happens when I use alt + cntrl + Fx to enter commands. I need this to compile some text in C language and run it as I'm trying to follow some tutorial to learn C. What am I doing wrong? How do I get this program installed? How do I run it? Thanks for looking!

---

### Post by mc4man on 2009-03-16
Considering that your a bit lost at this stage (configuring), you'd be much better off not trying to install higher ver. of gcc (4.3.3) on  intrepid....?

If your are using intrepid, then it uses gcc 4.3.2 which should be good enough for what you want to do. (note that gcc is a 'core' lib and not as straight forward to upgrade as your thinking.

maybe run this and try your tutorial again

```
sudo apt-get install build-essential
```

It is possible to upgrade intrepid to gcc 4.3.3, it requires 11 package upgrades total, though to do so without compiling requires using mainly non ubuntu packages to keep your libc6, libc6-dev at the intrepid versions.

One of my spare boxes is running gcc, g++ at version 4.3.3 on intrepid, but I couldn't advise you to do so.

If you really need 4.3.3 then jaunty (9.04) uses that and releases next month.

---

### Post by Liveone on 2009-03-16
Thanks for the reply!

Actually I have no clue what intrepid is. I'm a complete noob. Shouldve posted in the beginners section.

Hmmm, So gcc 4.3.2 already game with the system? I entered " gcc -dumpversion" and it came up 4.3.2. I guess that validates what your saying. I've also already run sudo apt-get install build-essential.

How do I use the thing? I entered "gcc script.c -o" like my tutorial said, and ran it with the saved text file. Nothing happened. I also tried running gcc script.c -o by itself. Nothing happened (tut says enter "gcc script.c -o program" I figured by program he meant the text file, but I tried running it anyway with/without the text file, and no results).

------------------------------
The tutorial

A C compiler can't compile
other languages, each one has it's own compiler/interpreter.
I am using the free GNU GCC as the compiler. If you are on
Windows i suggest you download the Bloodshed IDE, which
contains and uses the mingw port of GCC. On unix-like you
can use gcc from the terminal, by typing gcc script.c -o program.
Note for windows users: You might have to add .exe there
eg: gcc.exe script.c -o program

So here we go , open a text editor if you are on unix, or Dev-C++
if you are on windows. Copy and paste this, compile and run it.

---- [ hello.c ] ----

#include <stdio.h>

main() {
	
	printf("Hello World \n");
	getchar();
}

---- [ hello.c ] ----

The command line will pop up with the message "Hello World".
When you press enter it closes.

---------------------------------------------

This is **all** I'm trying to do, but nothing pops up. Hmmm, Could I have to install something from  System>Administration>Synpatic Package Manager ? There are a total of 26167 listed packages, and 1221 installed. I havent messed with any of that because I don't want to mess anything up.

Ahhh! I just want to program :(

---

### Post by jespdj on 2009-03-16
> **Liveone said:**
> Actually I have no clue what intrepid is. I'm a complete noob.
Intrepid Ibex is the code name for Ubuntu 8.10.

If you have installed the package **build-essential**, then you already have gcc version 4.3.2.

If all you want to do is compile a simple Hello World application, then you are making it WAY too complicated for your self by trying to compile gcc 4.3.3! That's like you want to drive to the supermarket, and you decide to first build a car yourself...

See [FAQ: Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635) in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum.

---

### Post by Liveone on 2009-03-16
Build a car, lol.
 
All right well thanks for that link. I think my problem is not understanding how to enter commands correctly.

------------------------------------------------
Directions:

**Open a terminal, go to the directory where you saved main.c**, and [B]type:
Code:

gcc main.c -o test[/B]

If all went fine, nothing is printed and [B]you get back to the shell. Now, run it:
Code:

./test[/B]

"Hello World!" gets printed in the terminal.
-------------------------------------------------

What are the directions I put in bold telling me to do? Heres what I think that means: Press alt + F2 to open up "run application" I then type gcc main.c -o test (I don't click/press anything, just type it in). Then I click run with file. I navigate to where I saved main.c, click it and check run in terminal. 

gcc main.c -o test '/home/lowproguy/C Coding/main.c' is what shows up in the line before I hit "run" and absolutely nothing happens (terminal opens and closes in a split second). No executable is produced, nothing, no error either. Unless the exe is saved somewhere by default. Where the hell did it go?

Then I did the same thing with ./test and I get an error saying no such file or directory. Obviously that happens because theres no exe to test... AH!!!!

---

### Post by Liveone on 2009-03-16
Starting to see the error in my ways! ./test is supposed to simply run the exe produced by compiling main.c which is done by typing gcc main.c -o test which also names the produced exe "test" Cool Cool.

So, now I see the problem is that there is no exe being produced...why is that? Nothing is written (terminal just opens and closes within the blink of an eye) after I enter gcc main.c -o test just as the link says should happen, but no exe is produced either.  

I even tried gcc main.c -o firstcode so that I could search for "firstcode" to find where the exe got sent and nothing was found. Now what am I doing wrong?

EDIT: my fault for the double post, got ahead of myself when the little light bulb went off. Learning linux is actually quite fun when you start to understand all the commands your entering and the purpose of Synpatic Package Manager and ubuntu repositories.

---

### Post by mc4man on 2009-03-16
Are you good to go with this yet? didn't get your 'edit'

(your only problem is/was your not at the directory prompt (in a terminal) for where your 'main.c' is located

---

### Post by oldos2er on 2009-03-16
I see you've got a directory name with a space in it. ext3 doesn't deal with spaces in file or directory names very well. One thing to do is to enclose the name in quote marks, for example
```
cd "/home/lowproguy/C Coding"
```
or use "\"
```
cd /home/lowproguy/C\ Coding
```
 Much easier tho' just to do without spaces in names.

 Alt-F2 is best suited as a program launcher. Use it to open gnome-terminal, then run your gcc commands from there.

---

### Post by Liveone on 2009-03-16
> **mc4man said:**
> Are you good to go with this yet? didn't get your 'edit'

(your only problem is/was your not at the directory prompt (in a terminal) for where your 'main.c' is located

If you could explain how to get there (as if I were 5 years old) that would be great. Seems very simple and basic but I just don't get it. I know I'll slap myself later, but its just not clicking.

> **oldos2er said:**
> I see you've got a directory name with a space in it. ext3 doesn't deal with spaces in file or directory names very well. One thing to do is to enclose the name in quote marks, for example
```
cd "/home/lowproguy/C Coding"
```
or use "\"
```
cd /home/lowproguy/C\ Coding
```
 Much easier tho' just to do without spaces in names.

 Alt-F2 is best suited as a program launcher. Use it to open gnome-terminal, then run your gcc commands from there.

Now that helped out alot. I was looking for this "terminal" forever and now I finally know how to access it (other than pressing alt + fx). Thanks.

So, all I need to do is

> **mc4man said:**
> ...your only problem is/was your not at the directory prompt (in a terminal) for where your 'main.c' is located

and understand what that means. how do I get in a terminal where my main.c is?

---

### Post by mc4man on 2009-03-16
> how do I get in a terminal where my main.c is

In a terminal 
cd path/to/directory   (cd means 'change directory'

based on your previous post, open a terminal and paste this in, press enter
```
cd "/home/lowproguy/C Coding"
```

You can also open a terminal from Applications -> Accessories -> Terminal

Ex.
I have a folder named whatever in home folder
> doug@doug-desktop:~$ cd whatever
doug@doug-desktop:~/whatever$ 


Notice how the prompt changed from ~$ (~ signifies home dir.) to /whatever$  (now I'm at prompt for the whatever directory

Ex. 
I have a folder on the desktop named whatever1

doug@doug-desktop:~$ cd ~/Desktop/whatever1
doug@doug-desktop:~/Desktop/whatever1$

If you make directories (folders) then life is easier if you don't use spaces, if you need 2 or more words then underscore or - (then you won't need " or \

C_Coding
C-Coding

---

### Post by Liveone on 2009-03-16
Thats it!!!

Man, thanks a million. I've been stuck at a stand still for 2 days because of this. I thought cd had something to do with live cd lol. Now I can actually apply what I read in tutorials. Appreciate it man!

Also, thanks to both of you for the advice about spacing.

Man, so relived... also slapped myself as promised :) It makes so much since now. 

I have a few links for Linux commands, but obviously never gave them a look over... Do you have a link that you'd recommend for best learning linux commands? You know, most common, blah blah blah. Thanks again.

---

### Post by oldos2er on 2009-03-16
The command "cd" means change directory. [http://www.mediacollege.com/linux/command-tutorial/](http://www.mediacollege.com/linux/command-tutorial/)

---

### Post by Liveone on 2009-03-16
Thanks Old, I sent you a PM but its not showing up in my sent folder. Let me know if you didn't receive it.

---

### Post by jespdj on 2009-03-17
To open a terminal, select this from the desktop menu:

Applications / Accessories / Terminal

---

