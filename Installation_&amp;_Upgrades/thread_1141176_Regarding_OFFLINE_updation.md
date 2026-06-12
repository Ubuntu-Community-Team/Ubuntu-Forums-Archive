---
title: "Regarding OFFLINE updation"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by codingfreak on 2009-04-28
Hi
 
I am new user of UBUNTU and started with UBUNTU 8.10.
 
I had a problem regarding updation of packages along with dependencies. Previously I am windows user where there are softwares like "AUTOPATCHER" inorder to carry all the software updates in a CD. As a result whenever I install a fresh copy of OS I can simply run the software and it keeps my system Up to Date.
 
My UBUNTU machine does not have a Internet connection. Is there any way where I can download all the packages and their dependencies from a Windows machine and burn them to a CD so that I can install them in OFFLINE ??
 
I searched for the same problem in the forum and found tools like "**NoNetDebs" [**which is no more working**], **"Keryx" **[**It doesnt have a windows installer and should be used only in other debian machine**]** and some even asked to take the updates from a friend using UBUNTU with internet connection which is not possible in my case.
 
So is there any way where I can download all the updates along with dependencies and burn into a CD which can be used in offline to update my UBUNTU machines :frown:

---

### Post by mcduck on 2009-04-28
Actually Keryx should work just fine on Windows machines (in their download page they state that the package includes source code for Linux and an executable for Windows).

---

### Post by dLeon on 2009-04-28
You can check package 'apt-zip'. That will do offline updates using scripts + wget windows/dos.

---

### Post by Partyboi2 on 2009-04-28
> "Keryx" **[**It doesnt have a windows installer and should be used only in other debian machine**]** Keryx works well with windows and is easy to use. Have a look at[[COLOR=Blue] keryx Tutorial[/COLOR]]("http://crashsystems.net/2009/01/keryx-tutorial/") on how it all works. :)

---

### Post by mac9416 on 2009-04-28
keryxproject.org

---

### Post by codingfreak on 2009-04-28
[SIZE=2]It seems even Keryx is supported on WINDOWS.

But I have a doubt when I checked the KERYX tutorial for STEP 2 it says[/SIZE]

"*Keryx uses wxWidgets for it&#8217;s graphical interface, and a default Ubuntu install does not have wxWidgets installed. Therefore you must create your project file in a terminal window. Fear not, as it is really quite quick and painless.* *Simply open up your terminal, and then navigate into the &#8220;linux&#8221; directory inside the Keryx folder. On my computer this was &#8220;/media/disk/keryx-0.91/linux&#8221; but it will look a little different for you, depending upon what your pen drive is called. Once you are in that directory, enter in the following, making sure to replace <project> for whatever you want to call your project and <plugin> for they type of system you are updating, in this case debian.*[INDENT]*python keryx.py &#8211;create <project> <plugin>*
 *note: the above is [I]two dashes*, but my font makes it look like one.[/I]
[/INDENT]*In a few moments the project will be made. When this happens, close out of the terminal and safely remove your pen drive, to take to another computer.*"

[SIZE=2]It means I should I again connect it to a Linux machine and run the python script or can we use the CYGWIN with python support on windows machine ?[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]If I skip that step and directly run the keryx.exe file in windows machine it says to create a new project. When I click the new project button it says "**Please create the project on the plugins supported OS**" and doesn't move further .....[/SIZE] :sad:

---

### Post by mac9416 on 2009-04-28
I'm sorry about the confusion. Keryx 1.0 is coming out soon and great pains will be taken to make it more intuitive.

There's absolutely no need to use CYGWIN, you can do everything with the executable.
The first thing you have to do, codingfreak, is make a "project" on your offline Ubuntu machine. If your Ubuntu machine is at home and you are at, say, a library, then we will have to do a little more work. But if you can get at that Ubuntu machine, follow the HowTo's instructions to make a project on that machine.
Once you have made a project, take your flash drive (or whatever you put Keryx on) back to the online computer and load the new project. Then you can begin downloading software.

If anything (or everything) is not clear, please let me know. I will do everything I can to help you out. And if I'm not able to do a satisfactory job you can try the [Keryx forums]("http://keryxproject.org/forums") or #keryx, the Keryx IRC channel.

---

### Post by EXCiD3 on 2009-04-28
> **codingfreak said:**
> [SIZE=2]It seems even Keryx is supported on WINDOWS.

But I have a doubt when I checked the KERYX tutorial for STEP 2 it says[/SIZE]

"*Keryx uses wxWidgets for it’s graphical interface, and a default Ubuntu install does not have wxWidgets installed. Therefore you must create your project file in a terminal window. Fear not, as it is really quite quick and painless.* *Simply open up your terminal, and then navigate into the “linux” directory inside the Keryx folder. On my computer this was “/media/disk/keryx-0.91/linux” but it will look a little different for you, depending upon what your pen drive is called. Once you are in that directory, enter in the following, making sure to replace <project> for whatever you want to call your project and <plugin> for they type of system you are updating, in this case debian.*[INDENT]*python keryx.py –create <project> <plugin>*
 *note: the above is [I]two dashes*, but my font makes it look like one.[/I]
[/INDENT]*In a few moments the project will be made. When this happens, close out of the terminal and safely remove your pen drive, to take to another computer.*"

[SIZE=2]It means I should I again connect it to a Linux machine and run the python script or can we use the CYGWIN with python support on windows machine ?[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]If I skip that step and directly run the keryx.exe file in windows machine it says to create a new project. When I click the new project button it says "**Please create the project on the plugins supported OS**" and doesn't move further .....[/SIZE] :sad:

So for Keryx, the only way I was able to develop it easily is to do this simple process:

1) Create a project for Keryx on the offline Linux machine
2) Take it to a Windows computer with highspeed (or any other computer that can run python) and download the packages. If you use a Windows machine, you don't need Python installed at all
3) Go back to the offline machine and install the packages.

cygwin is not needed. If you want to use Keryx on a Windows machine, you must follow every step of that tutorial so that you can create a project on the offline machine in order to let the Windows part do its thing.

Still following? If you follow the tutorial every step of the way, everything will work just fine for you. I know it can be confusing switching between machines and things but unfortunately this is as simple of a way as I could make it thus far. I'm working on rewriting it from scratch this summer and should have a brand new version that will make it somewhat easier as well. If you have any questions i'd be glad to help.

---

### Post by codingfreak on 2009-04-28
Hoo thanks for the help guys [ **Mac9416** & **EXCiD3** ] ..... 

**@Mac9416** - you were saying that

" *If your Ubuntu machine is at home and you are at, say, a library, then we will have to do a little more work.* "

So is there any hard way atleast where I can simply download all the updates without creating the project in UBUNTU machine ?

**@EXCiD3** - First of all thanks for starting a project like Keryx. But I do have some doubts regarding the usage of the Keryx.

1) What is the need to create the "project" in a UBUNTU machine and then connect it to a WINDOWS machine to download the packages from INTERNET ?? Is this any restriction ??

2) Cant we download all the updates into my windows harddisk itself instead of into a pendrive and then write into a CD or copy into a pendrive to be used to update my UBUNTU machine  ?? I think this would be a more flexible way to update an offline machine.
 
Since I had to save all the updates for my future use I dont think I cant write into a CD if there is any restriction like creating the project in a UBUNTU machine [Correct me If I am wrong]. 
__

---

### Post by EXCiD3 on 2009-04-29
> **codingfreak said:**
> Hoo thanks for the help guys [ **Mac9416** & **EXCiD3** ] ..... 

**@Mac9416** - you were saying that

" *If your Ubuntu machine is at home and you are at, say, a library, then we will have to do a little more work.* "

So is there any hard way atleast where I can simply download all the updates without creating the project in UBUNTU machine ?

**@EXCiD3** - First of all thanks for starting a project like Keryx. But I do have some doubts regarding the usage of the Keryx.

1) What is the need to create the "project" in a UBUNTU machine and then connect it to a WINDOWS machine to download the packages from INTERNET ?? Is this any restriction ??


So maybe I should explain a bit more about how the package management system works. You've got a list of installed packages, this list is updated EVERY time you update the list to see what updates exist. You need this information of the old stuff that is installed before you can figure out which are updates. This is where Keryx comes in. Keryx will grab that information and store it as a project. You open the project on an internet connected machine and it will show you the updates along with all the other packages available so you can get anything else you want too, just like you were connected to the internet on your offline machine.

> 
2) Cant we download all the updates into my windows harddisk itself instead of into a pendrive and then write into a CD or copy into a pendrive to be used to update my UBUNTU machine  ?? I think this would be a more flexible way to update an offline machine.
 
Since I had to save all the updates for my future use I dont think I cant write into a CD if there is any restriction like creating the project in a UBUNTU machine [Correct me If I am wrong]. 
You can go ahead and run Keryx from anywhere you like, but I recommend using a flash drive because you are going to be moving the packages around. It just makes it easier than using CDs which will need to be reburned every time you want anything new. Keryx does not matter what it is run from so you could run Keryx from a flash drive, portable harddrive, the computers local harddrive, an ipod, you name it. Just as long as you can open the project that Keryx created from somewhere so that it knows what you need for updating. You typically run Keryx from a flash drive, where it will store the project on automatically, so then you can run Keryx on another machine without moving files at all and download the new packages, which are also automatically stored on the flash drive. Keryx just keeps the packages and all the information on your flash drive so there is nothing for the user to worry about for moving files or anything. 

Hope that helps explain the concept of projects a bit better for you. Cheers!

---

### Post by codingfreak on 2009-04-29
Thank you for a quick reply **EXCiD3**. Now I understand a bit more about Keryx functionality.> You've got a list of installed packages, this list is updated EVERY time you update the list to see what updates exist. You need this information of the old stuff that is installed before you can figure out which are updates. This is where Keryx comes in. 

Keryx will grab that information and store it as a project. You open the project on an internet connected machine and it will show you the updates along with all the other packages available so you can get anything else you want too, just like you were connected to the internet on your offline machine.So the reason for connecting to a UBUNTU machine for creating the "project" is to know what are the old packages that are already installed in the machine.

But I do have a doubt ..... Let us suppose I just had a fresh installation of UBUNTU 8.10 from the LIVE CD and I haven't upgraded anything from Internet. Then we know what are the default packages that are installed in the system. In this case can't we simply download upgraded versions for the default packages that are in UBUNTU 8.10 directly ??

It is something like just downloading all the UBUNTU 8.10 upgrades [For the fresh installation] where there is no need for me to connect to UBUNTU and make Keryx to know what are the packages that are installed in my machine.

I think it would be a bit complex to make keryx to work in this way ....

Sorry my way of updation is more like MICROSOFT way and also something used in CYGWIN where all the packages are downloaded and can be installed without any changes.

---

### Post by apparle on 2009-04-29
I had been using ubuntu without net for and year and a half. So let me tell you some differences.
Firstly microsoft rarely updates its OS. For eg: Lets say they released SP3 for WinXP then, you can burn the update onto a CD and can use for about 2-3 years or more.

But ubuntu is updated regularly.....sometimes every other day you'll find an update. So if you keep burning CDs then you will get a nice big stack of CDs which will be rendered useless every 6 months as a new version of ubuntu is released every 6 months.
Also why are you being so fussy about creating the project. Don't you think its better to have something which interacts with yor system and then downloads the updates rather than considering it default and downloading everything.

Considering M$ when you upgrade in Windows, it first check what updates you have and then downloads the rest.........same is happening here.

At least there exist a tool like Keryx for.......when I was using ubuntu, I used to check each and every update on my own...........had to write my own scripts to get things working

My suggestion, use Keryx to update the system but don't keep backup of the updates............just get the latest version of ubuntu every 6 months.

Also unlike windows, you don't need to format ubuntu regularly as virus don't try to mess with the system every other day

---

### Post by mac9416 on 2009-04-29
Yes, the main reason for using the "project" model in Keryx is to have the following information:

[LIST]
[*]Your version of Ubuntu (you can't use 8.04's debs on an 8.10 install)
[*]What your sources.list file is (what repos to download from)
[*]What software is already installed (so you don't download unnecessary debs)
[/LIST]

Of course, all this information could be guessed or assumed, but that makes for an inflexible piece of software. Keryx isn't just intended for updating fresh installations; it allows you to install new software without having to hunt down all its dependencies.

If you have any reason why you can't or don't want to create that project on your Ubuntu machine, just let me know, and I'd be happy to email you a project created on a fresh install of 8.10, but it would be identical to the one you would create.

I hope that helps!

---

### Post by EXCiD3 on 2009-04-29
> **codingfreak said:**
> Thank you for a quick reply **EXCiD3**. Now I understand a bit more about Keryx functionality.So the reason for connecting to a UBUNTU machine for creating the "project" is to know what are the old packages that are already installed in the machine.
Yes

> But I do have a doubt ..... Let us suppose I just had a fresh installation of UBUNTU 8.10 from the LIVE CD and I haven't upgraded anything from Internet. Then we know what are the default packages that are installed in the system. In this case can't we simply download upgraded versions for the default packages that are in UBUNTU 8.10 directly ??

It is something like just downloading all the UBUNTU 8.10 upgrades [For the fresh installation] where there is no need for me to connect to UBUNTU and make Keryx to know what are the packages that are installed in my machine.

Keryx is still early in development. I am planning on including default projects that would contain the list of packages for a fresh installation of Ubuntu 8.10 so that a project would already be setup for you, but you must understand that not everyone is going to be in the same boat as you. I have to accomodate to any type of user, even the ones that have dialup who do not wish to upgrade everything, but they are able to update their package lists here and there. In the near future I will be providing default projects that you could use for an 8.10 i686 machine that has never been updated before without ever having to go and create a project. As soon as you install those packages however, that project is going to need to be updated. You will still need to modify the project EVERY time something changes on the offline machine. Creating a project only takes two seconds and allows flexbility for every user, even the ones who have some little internet to their machine. I want Keryx to work for anyone who wants to use it, not just a certain group of users, and the best way this can be accomplished is by taking two seconds to create a project at home before you go and download the updates and new software that you would like.

> I think it would be a bit complex to make keryx to work in this way ....

Sorry my way of updation is more like MICROSOFT way and also something used in CYGWIN where all the packages are downloaded and can be installed without any changes.Microsoft does not provide any sort of package management system so you can't really compare it. They are completely different beasts. Cygwin is much more like Linux obviously but since its on Windows it has its own quirks as well.

Hope that explains the mindset we have for Keryx somewhat better for you. And remember, its still early in development, there are features I'm still working on such as those default projects for fresh installations.

---

### Post by codingfreak on 2009-04-29
Thanks for patiently replying me **EXCiD3**, **mac9416**, **apparle**

Sorry I might be more stubborn with my questions .....

I agree that Keryx is in the initial stages of development and we can expect more upgrades in future.

I never used Windows Update as I am a fan of **[AUTOPATCHER]("http://www.autopatcher.com/")**. I just started using UBUNTU few months back and searching for a software that helps me in offline updation which landed me in **KERYX**. I was wrongly expecting KERYX to work the way AUTOPATCHER work's :lolflag:

---

### Post by EXCiD3 on 2009-04-30
No problem, glad to have helped you understand how Keryx works. :)

I will look into Autopatcher and see if there are any useful features that i could use with Keryx and see what happens. If you need any help running Keryx let me know, the tutorial should be able to get you through it without a hitch.

---

