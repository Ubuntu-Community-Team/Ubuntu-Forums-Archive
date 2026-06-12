---
title: "Beginners guide to linux"
date: 2008-09-04
forum: General Help
---

### Post by matdombrock on 2008-09-04
So I wrote this tonight and I'm thinking of posting it some places around the web but i wanted your opinion first.

If you would like to add anything or see any errors (I'm sure there are many) please let me know and I will give you credit.

I will be doing some screen shots to accompany it later.
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::


Intro:

So you're interested in using Linux but you don't know where to start? Then your in the same boat I was less then a year ago, and now I'm more comfortable on Linux than any other operating system.  But I did it the hard way, I just sat there and messed with things until I figured them out.

If I knew then the things then that I know now I would have had a much easier time with getting started in Linux. Thats why I'm writing this, not because I am an expert, but because It would have helped me so much to have a tutorial written in plain English that is understandable by people other than computer scientists. 

This tutorial will not make you an expert on linux, it will not be in any way comprehensive and it will defiantly not solve all the problems you encounter while using linux. What it will do is give you a general idea of where to start and point you in the right direction.



Some things you need to know and keep in mind before you start are:

If you are not either a little dedicated or a little lucky you probably won't be too successful.

Linux can be very different than Windows and some times confusing, but remember, Windows would be just as confusing if you had been using Linux your whole life.

If you are stuck ask for help! Join a Linux forum( like [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)), there are plenty of people out there that love to help newcomers!



Lets get started:

So, the first thing you need to decide on before you can use Linux is what distro you want to try. If you don't already know, a distro, short for distribution, is basically a set of pre-installed  applications packaged together with the Linux operating system. That might sound a little confusing but it is a lot like how Windows is available in Home Edition, Professional Edition and Media Center Edition.

In my humble opinion the best distro for a newcomer is Ubuntu because it is completely free and has an awesome online community. You might also try Mandriva (not free), Dream Linux or Fedora, but for the purposes of this tutorial we will stick to Ubuntu. 

The first step to using Ubuntu is to download it from "http://www.ubuntu.com/getubuntu" (You can also request a free CD or purchase one online). If you download it, the file will be a .ISO, if you have never encountered a .ISO before, its a disk image meant to be burned to a CD or DVD. If your using Windows you will need a program that can burn .ISO's. I recommend 'Burn at Once', you can get it at "http://www.burnatonce.net/downloads/". Once you have the .ISO and have successfully burned it move onto the next section.

I would defiantly recommend that you try Ubuntu out before you actually install it. There are a few different ways to do this:

One way is to just put the CD in your CD-ROM drive and reboot your computer, When you boot up you should be asked to select your language. After that select the option "Try Ubuntu without any change to my computer". Once your in you can try it out and see if things like your internet, sound and video work correctly. You can also Install Ubuntu to your hard drive from here but we will talk about that later. 

The second way you can try it is to  use Wubi, you can get it at "http://wubi-installer.org/" or just put an Ubuntu CD in while running windows and select the Wubi option from it. This is a slightly more permanent method of trying Ubuntu. It will install Ubuntu on your computer as if it were any other program and then let you decide whether to boot into Windows or Ubuntu when you start your computer. Since it installs like any other program it can be removed from add/remove programs in Windows if you don't decide to keep it.



Using Ubuntu:

When you first get into Ubuntu you may get a balloon window on the top of the screen informing you that restricted drivers are in use. If you get that click the balloon and it will bring up a window. In that window click the check box next to the driver then click the button that says "enable" at the bottom of the window.

Ubuntu does not come with the ability to play some media formats such as Mp3's because they are not free for anyone to use, and everything included in Ubuntu is free for anyone to use. If you want to use Mp3's and things like that anyway, don't worry is not that hard. Here is how to do it. taken from "https://help.ubuntu.com/community/RestrictedFormats":
---------------------------------------------------------------------------------------------------------------------
Follow these steps to play most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages.
   
      Go to Applications &#8594; Add/Remove...

      Set Show: to All available applications

      Search for ubuntu-restricted-extras and install it. 

Or open the Terminal, and execute the following command:

      sudo apt-get install ubuntu-restricted-extras
---------------------------------------------------------------------------------------------------------------------

The program that you just used (if you didn't use the terminal) is called Add/Remove, It's a lot like the Add/Remove program in Windows. The main difference however is that, in Linux Add/Remove is actually what you use to download and uninstall all of your programs. For instance, lets try downloading the game "Frozen Bubble". Open Add/Remove the way you did before and in the search box type: "Frozen Bubble" (without the quotations) and hit enter. You should now  see Frozen Bubble, click the check box next to it and then click apply changes at the bottom of the window. It will then ask you for you password and start to download and install Frozen Bubble. When it is done click "close". Now when you go to Applications>Games you should see Frozen Bubble. Some more programs you might want to download are: Nexuiz (a first person shooter), AbiWord (a word possessor), Inkscape (a drawing program) and Battle For Wesnoth (a strategy game).

You almost never need to download a program for the internet to use it. 

To access you files in Ubuntu just click "Places" (in the top bar).

To preform Administrative tasks click "System" (also in the top bar).

To surf the web click the Firefox logo next to the "System" button.

To get really cool desktop effects (compiz) go to System>Preferences>Appearance. Then click the visual effects tab and select the level of effects that you want.

Installing:

Now that you have tried Ubuntu you are ready to install it. However, for some people this might not be necessary. You might be completely content with using Wubi to install Ubuntu, and thats fine if you don't mind loosing a little speed and having a max hard dive size of 30GB. If you do wish to install it though I recommend you use wubi for a while (a few weeks) first to get more comfortable with Ubuntu. Then when you are ready, BACK UP ALL OF YOU IMPORTANT FILES AND PRINT OUT THIS GUIDE! After that the best way to install Ubuntu is to put the CD you downloaded earlier back into you your computer and act like you were going to test it out again but this time instead of selecting "Try Ubuntu without any change to my computer" select "Install Ubuntu".

The first few parts of the install will be self explanatory. Then the tricky part comes; partitioning. If you want to keep windows on your computer (Which I suggest you do, at least for now) you need to use the fist option "Guided - resize ...". For this you just drag the slider to represent the amount of disk space that you want to leave for windows (It will probably need at least 20GB).
If you want want to get rid of Windows and just install Ubuntu select "Guided - use entire disk".
Then you can click next and fill in the rest of the easy questions. After the installation is done you will be asked to reboot and remove the disk. Then you should be able to boot into Ubuntu when your computer starts. 

Where to go from here:

Register an account on the Ubuntu forums at "http://ubuntuforums.org/index.php".

Try some new distros. Ubuntu is cool but there might be some ones out there you like better.
Most Linux distros are fundamentally the same. Check out "http://distrowatch.com/" for info on other distros.

Get involved! Lend your talent to the community whether it's artistic, programing, documentation, or just looking for bugs. With out the community Linux would not be what it is today.

---

### Post by Flimm on 2008-09-09
Cool. I've seen guides like this before, but this one seems more updated (it explains Wubi, for example).
One mistake I found was:
> You almost never need to download a program for the internet to use it.
Don't you mean: "You almost never need to download a program *from* the internet to use it" ?
Even that's not quite true, Add/Remove downloads the files from the Internet. What it should be is:
"You almost never need to browse the web and manually download a program to use it". 
How's that?

---

