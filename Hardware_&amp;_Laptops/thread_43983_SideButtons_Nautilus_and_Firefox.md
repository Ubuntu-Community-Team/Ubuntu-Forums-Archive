---
title: "SideButtons Nautilus and Firefox"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by doans on 2005-06-24
I have been attempting to get my USB Microsoft Wireless IntelliMouse Explorer to completely work in Firefox and Nautilus for years now. I followed all of the guides on this and other forums and nothing was able to get the back and forward buttons to work in both Firefox and Nautilus.](*,) The side buttons would work in Firefox but not in Nautilus...until now! Here's how I did it (with the help of numerous forum posts which I have lost the links to now). Hopefully this will help someone else out. 

1.  Install imwheel from Synaptic[indent]Make sure Universe is enabled to find this package.
[/indent]2. Edit /etc/X11/xorg.conf[indent]Change protocol to ExplorerPS/2, define number of buttons as 7, and reorder ZAxisMapping, by making your xorg.conf file like the one below.
  
Backup first:[indent] ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` 
  [/indent]sudo gedit /etc/X11/xorg.conf
   
Sample Mouse section from xorg.conf:
      ```
Section "InputDevice"
 	   Identifier	"Configured Mouse"
 	   Driver		"mouse"
 	   Option	   "CorePointer"
	 Option	 "Device" 			 "/dev/input/mice"
	 Option	 "Protocol"			 "ExplorerPS/2"
	 Option	 "Buttons" 			 "7"
 	 Option	   "ZAxisMapping"	 "6 7"
 	EndSection
```
 Your mouse section may be slightly different I am not sure.
   [/indent]3.  Create file .imwheelrc in /home/username[indent]gedit /home/username/.imwheelrc
[/indent][indent]Paste in this code:
[/indent][indent] ```

".*"
None, Up, Alt_L|Left
 None, Down, Alt_L|Right
  
 "(null)"
 None, Up, Alt_L|Left
 None, Down, Alt_L|Right
``` 
[/indent]4.  Backup and edit existing file /etc/X11/imwheel/startup.conf[indent] sudo cp /etc/X11/imwheel/startup.conf /etc/X11/imwheel/startup.conf.bak
sudo gedit /etc/X11/imwheel/startup.conf
  
Find this line:
[/indent][indent] IMWHEEL_START=0
  
 And replace with:
  
 IMWHEEL_START=1 
  
[/indent]5.  This is the final piece in the puzzle:[indent] sudo gedit /etc/X11/Xsession.d/63xmodmap 
  
 and paste in this code:
  
 ```
  
killall imwheel
 xmodmap -e "pointer = 1 2 3 6 7 4 5"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
``` 
[/indent][indent]The Wiki site recommended creating file 57xmodmap that would startup before imwheel but this never worked for me. This has to start AFTER imwheel for some reason.
[/indent]6.  Save this file and then change the permissions so that it can be executed:[indent] ```
 sudo chmod 777 /etc/X11/Xsession.d/63xmodmap 
``` 
[/indent]7. Restart x server with Control+Alt+Backspace, relogin to X, and the mouse buttons and wheel should be working in Firefox and Nautilus!

I love it when a plan comes together! \\:D/

---

### Post by filemanager on 2005-07-02
I'm embarassed to say, I'm stuck on step 1. lol. I'm new to Linux and I'm trying to get my wireless Intellimouse explorer to work. the left click and right click work, but the scroll wheel and back/forward buttons don't =\

Anyway, how do I install imwheel?

---

### Post by mohaham on 2005-07-02
add the  extra repos as shown here:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then type the following in a terminal:
sudo apt-get install imwheel

---

### Post by filemanager on 2005-07-02
[QUOTE=mohaham]add the  extra repos as shown here:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then type the following in a terminal:
sudo apt-get install imwheel[/QUOTE]

Awesome, that was easy enough  \\:D/  Thanks!!

"Make sure Universe is enabled to find this package." - how do I make sure Universe is enabled?

---

### Post by filemanager on 2005-07-03
It worked!! YAY!!! *happy dance*

Thank you for sharing the info!! It made my life tons easier ;)   \\:D/

---

