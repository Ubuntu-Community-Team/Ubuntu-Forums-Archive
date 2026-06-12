---
title: "Nvidia 185.18.36 Linux x64 Driver Installation &amp; Visual Effects Made Very Easy"
date: 2009-08-27
forum: Hardware
---

### Post by Handy Andy on 2009-08-27
Nvidia 185.18.36 Linux x64
Display Driver Installation Instructions
This will also allow you to enable the "Visual Effects" options.
(For instructions see below, "Enabling Visual Effects")
Instructions by HandyAndyNY 2009-08-27

First you must download the driver from Nvidia, which you will find by clicking the following link:
[http://www.nvidia.com/object/linux_display_amd64_185.18.36.html]("http://www.nvidia.com/object/linux_display_amd64_185.18.36.html")

Display Driver Installation Instructions
***Before continuing you must write down or print the following instructions!***

 1) Right-Click on the file: "Nvidia 185.18.36 Linux x64.run"
 2) Click on "Properties"
 3) Write down the text to the right of "Location:"
 4) Close the "Properties" Window, and any other open Windows
 5) Press "CTRL + ALT + F1"
 6) Type: sudo bash
 7) Press "Enter"
 8) If prompted, type your password, and then press "Enter"
 9) Type: sudo /etc/init.d/gdm stop
10) Press "Enter"
11) Type the text you wrote down from Step 3
12) Now immediately after what you typed in Step 10, Type: Nvidia 185.18.36 Linux x64.run
13) Press Enter
14) Follow the prompted instructions until the installation is complete
15) Once the installation has completed, press "CTRL + ALT + F1"
16) Restart your computer
Display Driver Installation Completed


Enabling Visual Effects
1) From the "Desktop Panel" Click on System
2) Click on "Preferences"
3) Click on "Appearance"
4) From the "Appearance Preferences" Window, Click on the "Visual Effects" Tab
5) Click on one of the "Visual Effect" options from the list
6) Click on the "Close"
Enabling Visual Effects Completed


Hope this helps many people out. I am new to Linux if you haven't already guessed by my detailed instructions, but I guess that makes me a good tutor for a beginner. :)  I posted this so no one who is new to Linux or has had problems installing the driver will go through the headaches I have.  The information in this post was put together from other posts and simplified by me HandyAndyNY. To be honest I am mainly a Windows user, but Linux isn't all that bad.  You just have to be patient and keep trying and stay relaxed.  Which I have went through for years with Windows.  I wish more people used Linux though, so I could completely switch over and help people use Linux rather than Windows.
PS: TUX Rules! :smile:

---

### Post by madmax.santana on 2009-10-11
When I type
> /home/madmax/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run

It returns the following error:
[quote]bash:NVIDIA-Linux-x86_64-185.18.36-pkg2.run : Command not found[//quote]

Any ideas?

---

### Post by Sylslay on 2009-10-11
to madmax :

at step 1) Right-Click on the file: "Nvidia 185.18.36 Linux x64.run"
2) Click on "Properties"
!!!??? 3) enable in therd tab skript as an executable file (a program)

or use command chmod and change rights to file

---

### Post by madmax.santana on 2009-10-15
> **Sylslay said:**
> to madmax :

at step 1) Right-Click on the file: "Nvidia 185.18.36 Linux x64.run"
2) Click on "Properties"
!!!??? 3) enable in therd tab skript as an executable file (a program)

or use command chmod and change rights to file
I am sorry! I complete noob mistake on my part... Instead of Sylslay's tips I simply used 
> **sh** /home/madmax/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run                      And it worked... The setup runs!
(However it doesn't mean that I am neglecting the tip by Sylslay! My problem has not yet solved And I shall surely try it your way Sylslay!)

However I am facing another problem. The setup returns some error about Kernel... I don't exactly recognize the error! In short the setup finishes without installing the driver. Any ideas on that one? Thanks a lot Sylslay... It's guys like you who make me rely the Ubuntu forums for help...

---

### Post by Sylslay on 2009-10-23
thx for **sh** /home/tip

ps I do lern very quickly,
no offence
:guitar:

[http://translate.google.com/translate_t#](http://translate.google.com/translate_t#)

---

### Post by madmax.santana on 2009-11-19
@Sylslay
What was offensive??? Let me know... It's been long since I have been offended. :) 
:D :D :D :D

---

