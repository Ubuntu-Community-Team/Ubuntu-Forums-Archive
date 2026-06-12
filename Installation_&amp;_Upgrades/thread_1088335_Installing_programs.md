---
title: "Installing programs"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by SuperIntense on 2009-03-05
I am very new at linux and I want to learn more. My question is under Ubunto how do I download and install programs? It seems to be confusing to new people like myself. I really want to make Linux work for me. There are a couple of areas such as terminal and Synaptic that I do not understand what they are for. If I can master downloads and installs I think I acn learn more about Linux. I am very familiar with Windows so if you respond and there are ways you need to describe these based on the windows environment it is ok to use that terminaology.

---

### Post by lykwydchykyn on 2009-03-05
Synaptic is how you download and install programs.  You search for things in Synaptic and select "install", hit "apply" and they are installed.

---

### Post by stumbleUpon on 2009-03-06
Read the documentation here

[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by martrn on 2009-03-06
You can install programs like lykwydchykyn said above or open a terminal and type away

Select Run Command From the menu and type ```
gnome-terminal
```

APT The Advanced Packaging Tool
-------------------------------
The Advanced Packaging Tool, or APT, the package name containing the set of tools and core libraries that  handle the installation and removal of software on GNU/Linux debian or Ubuntu systems. A significant part of apt is set of library functions that handle package management tasks to complete the full installation of software. 

There is no single "apt" program.  ```
apt-get
``` and ```
apt-cache
``` are front-end programs that can be used from the terminal for dealing with packages.  Apt-get and apt-cache install and unpack software the vary same way Synaptic does, and uses the apt libraries.

There is no equivalent on the standard windozes environment, and it would be foolish to the two alike.  GNU/Linux and the Ubuntu Distribution use tools that will be familiar to Unix-like operating systems, and it would be foolish to use terminology to non Unix-like operating systems.

---

### Post by bubwitmaingay on 2009-03-06
**A.** ***Go to:***

[http://appnr.com/]("http://appnr.com/")

You just click the "install" button found on the right side of each application selection listed. Voila, it will automatically install to your machine, including dependencies. Just be sure you're connected to the net.

**B.** ***If you want a little typing and tech stuff, use the Terminal***.
1. Go to Application>Accessories>Terminal
2. Click the application with the "Terminal"
3. It will open like a command prompt in MSDOS and it will look like this:
```
mitch@mitch-desktop:~$
```
4. Just type:
```
sudo apt-get install <the app code here>
```
example: ```
sudo apt-get install gxine
```
then hit enter, it will ask for your password. 
5. Type your password (the one you use during log-in). As you type, it will not show anything on the terminal (not even dots or asterisk) but just type the password, then hit enter.
6. The terminal will install it for you, plus the dependencies. Then again, you must be connected to the internet while doing this.
7. Follow the instructions if they will show up; eg. "Do you want to continue? [y/n]", thus hit the "y" key for yes and "n" key for no, then hit enter key and so on.

Remember that GNU/Linux is case sensitive, so copy everything exactly. You can find the application (software) code at the bottom of each selection listed on the same website above.

Hope that helps. 8)

---

### Post by Therion on 2009-03-06
The easiest way for a beginner is to use **Add/Remove Applications** located under the **Applications** menu.

Add/Remove Applications [looks like this](http://sydney.indymedia.org.au/files/sydimc/images/ubuntu-add-remove.img_assist_custom.png).  Be sure you have selected "All available applications" from the drop-down menu at the top-right.

To install new applications select the category on the left, then check the box of the application you want to install. 
When finished click "Apply", then your chosen programs will be downloaded and installed automatically, as well as installing any additional applications that are required.

Alternatively, if you know the name of the program you want, use the Search tool at the top.

---

### Post by rlj1965 on 2009-03-06
> **Therion said:**
> The easiest way for a beginner is to use **Add/Remove Applications** located under the **Applications** menu.

Add/Remove Applications [looks like this](http://sydney.indymedia.org.au/files/sydimc/images/ubuntu-add-remove.img_assist_custom.png).  Be sure you have selected "All available applications" from the drop-down menu at the top-right.

To install new applications select the category on the left, then check the box of the application you want to install. 
When finished click "Apply", then your chosen programs will be downloaded and installed automatically, as well as installing any additional applications that are required.

Alternatively, if you know the name of the program you want, use the Search tool at the top.

Kudos! The OP clearly stated that he/she was completely new to Linux, yet people try to steer him/her towards the terminal when add/remove or synaptic are far less intimidating.

---

### Post by lykwydchykyn on 2009-03-06
> **rlj1965 said:**
> Kudos! The OP clearly stated that he/she was completely new to Linux, yet people try to steer him/her towards the terminal when add/remove or synaptic are far less intimidating.

Hrmm...
[QUOTE=SuperIntense]
There are a couple of areas such as terminal and Synaptic that I do not understand what they are for.
[/quote]
Maybe because the OP asked about the terminal?

---

### Post by SuperSonic4 on 2009-03-06
It is a learning curve too. Although the terminal isn't necessary it can often be easier. Especially with a buggy adept in Kubuntu. I don't have anything to add to what the others have said though

edit: I did remember something! You (the OP) should take a look at [Medibuntu]("https://help.ubuntu.com/community/Medibuntu"). If you add their repositories you can get non-free software (as in speech) such as audio codecs like mp3.

---

### Post by bubwitmaingay on 2009-03-06
Honestly, I am new to GNU/Linux but I find using the terminal easier than the Add/Remove. There are many things there that I can't understand, especially the filenames and little explanation were given. Then all required installation have to be clicked manually especially in the Synaptic.

To make your life simplier while enjoying to browse on the internet, try [http://appnr.com/]("http://appnr.com/").

You know, you guys here taught me to use GNU/Linux. Hahaha. 8)

---

