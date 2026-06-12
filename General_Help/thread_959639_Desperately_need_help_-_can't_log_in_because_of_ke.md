---
title: "Desperately need help - can't log in because of keyboard layout!"
date: 2008-10-26
forum: General Help
---

### Post by pelikan555 on 2008-10-26
This is very silly... but I was messing around with the keyboard settings under Preferences->Keyboard looking at Cyrillic keyboards &c., and when I restarted my computer... the log-in screen only types in Russian Cyrillic script so I can't input my username and password... and I don;t know what to do now without reinstalling Ubuntu (I have a separate /home partition so it's not so much of a problem, but...)

Help! How do I get the keyboard input back to British English on the log-in screen? Don't laugh!

---

### Post by pelikan555 on 2008-10-26
Apologies - bump! Silly, silly...

---

### Post by alberto ferreira on 2008-10-26
when you get to login screen do the following:

1-Press Ctrl+Alt+F1   #This will take you to the virtual terminal no. 1
2-Login 
3-type loadkeys us #Try with this one because I don't know the one from your region
4-type startx
5-Wait and now you're at your gnome session! 
6- NOW go to system>preferences>keyboard and choose your keyboard



------ Solution 2
1-Boot your Live CD
2-Mount your hard drive (this should happen automatically, if it doesn't, go to places>"then choose your hard drive - it will now mount automatically"
3-open the console/terminal
4-in the terminal type:
> cd /replace/this/with/the/path/of/your/harddrive  #this will take you to your harddrive
cd /etc/X11/
#now be very careful with this step, do exactly as I say:
sudo nano xorg.conf


5-Now you are editing the file which contains information about a lot of things in your pc so be CAREFUL, one of those things is your keyboard layout. The file should look like the following:
> Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
       [COLOR=Blue] Option          "XkbLayout"     "pt"[/COLOR]

That section of text is in the beginning of the file, change the line that I've marked in blue in your file replacing "pt" or whatever appears there by "us".

6-press CTRL+O then ENTER then CTRL+X # this saves the file
7-reboot
8-if you don't like the keyboard layout change it in System>preferences>keyboard

---

