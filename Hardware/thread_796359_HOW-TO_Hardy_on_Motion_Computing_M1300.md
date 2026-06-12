---
title: "HOW-TO: Hardy on Motion Computing M1300"
date: 2008-05-16
forum: Hardware
---

### Post by priegog on 2008-05-16
So, I finally solved this thing (had been at it for at least a couple of months) so I'll just post here exactly how to do it. Most of the steps are similar to the ones on [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=110050"), so much of this guide will be a copy-paste of that.

1. Go to the terminal and install all of these```
sudo apt-get install setserial wacom-tools xserver-xorg-input-wacom
```
2. Map the hardware port to a virtual serial port```
sudo setserial /dev/ttyS0 port 0x0238 irq 4 autoconfigure
```
3. Check that all is working; first type ```
wacdump -f tpc /dev/ttyS0
``` and move your pen around the screen. If the numbers move, keep going. If they don't you're out of luck.

4. Put the appropriate entries in the xorg file. type ```
sudo gedit /etc/X11/xorg.conf
```, and paste these lines in there somewhere (I put them at the beginning) ```
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Type" "stylus"
Option "SendCoreEvents" "true"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option    "Button2"    "3"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Type" "eraser"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Type" "cursor"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
```
and then add these lines to the Section "ServerLayout":```

InputDevice "cursor" "SendCoreEvents"
InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
```
4.1. (Optional for screen rotatiOn in step 8 ). Add these lines to the "Device" section:```
	Option		"RandRRotation"	"on"
	Option		"NvAGP" 	"1"
	Option		"DRI"		"false"
```WARNING:This last line will disable3D acceleration but i'ts neccesary.
Click the save button and close gedit.

5. Make these changes permanent by typing ```
sudo dpkg-reconfigure setserial
```and selecting the option "autosave once"

6. Restart and it should all be working!

After this my tablet worked just fine, but the other guides included this last step so I'll post it here as a "last resor" measure.

7. Type ```
sudo xsetpointer stylus
```
I actually don't know what this command is for, so if someone were to illuminate me...

I know there aren't a lot of M1300 users out there but still I wish when I bought mine there was a guide just like this one to set it up. 
This is working for hardy but presumably it would work with future versions as well.

[SIZE="6"]**[COLOR="Red"]UPDATED INSTRUCTIONS FOR INTREPID[/COLOR]**[/SIZE]

All right, so Intrepid is here, so here is what needs to be done differently in order to setup the wacom tablet.
[LIST]
Replace step 4 in these instructions for the ones in [this post]("http://ubuntuforums.org/showpost.php?p=6247888&postcount=20")[/LIST]
[LIST]
For screen rotation, just follow the usual steps (in the next post)[/LIST]
[LIST]
For screen brightness, the steps described 2 posts from this one are no longer necessary. Just add the screen brightness applet to the gnome panel and it should Just Work[/LIST]

[SIZE="4"]**[COLOR="Red"]Got the battery problem solved.[/COLOR]**[/SIZE] _[COLOR="Blue"][Follow these instructions]("http://ubuntuforums.org/showpost.php?p=6357262&postcount=32")[/COLOR]_

[COLOR="Red"][SIZE="4"]**trainerjonathan located the thread where there are instructions to get an onscreen keyboard at login**[/SIZE][/COLOR]
> **trainerjonathan said:**
> 
By the way the instructions to add the on-screen keyboard to the login screen in this [post]("http://ubuntuforums.org/showpost.php?p=1789021&postcount=4") worked perfectly for me.
________________________________________________________
[List of Tablet PC's working with Linux and links to the how-to's]("http://tuxmobil.org/tablet_unix.html")

---

### Post by priegog on 2008-05-16
8. SCREEN ROTATION. After step 4.1, you now only need to make sure the package xserver-xgl is NOT installed. After that,take the 2 scripts I made (attached) and place them in /usr/local/bin/ (you'll need to be root. if you don't know how to, type in the terminal ```
sudo nautilus /usr/local/bin/
```and move the script files to the window that opens. Then you can create a panel launcher for each one (right-click on panel > add to panel > custom application launcher) and pasting in the "command" field```
sh /usr/local/bin/portrait.sh
```. Do the same for the other launcher, but changing "portrait" with "landscape" And that's it, it should work.

---

### Post by priegog on 2008-06-25
9 SCREEN BRIGHTNESS
This one took me a while to figure out. It's not as easy as, say, the rotation scripts since to do this it is necesary to have root acces. So 
this will be divided into 2 parts: One to help us make our scripts run without giving them a password and another one to make the scripts themselves.
9.1 sudoers file.
So this is a weird little file that tells the system which parts of the system can be run without requiring a password, so we're gonna modify it to let us run the brightness scripts from a desktop or panel launcher.
So since this file is weird and won't let itself be modified we have to change the permissions. I do it all graphically, so type ```
sudo nautilus /etc
``` There you can find the sudoers file, so right-click on it and select properties. Go to the permissions tab and change both access properties to Read and Write. Then close and we're ready to modify it. ```
sudo gedit /etc/sudoers
``` and at the end (the position is important), paste this ```
jerry ALL=NOPASSWD: /home/jerry/myscripts/
``` substituting of course jerry with your username and the path to a folder where you will keep the scripts we'll make next.
Now, click on save, close gedit and do the same thing we did to change the permissions and change them back to Read-only. 
If you're paranoid (or careful) enough I'm sure you backed up the sudoers file before modifying it, so now comes the moment to check if your modification is valid or not. ```
sudo visudo -c
``` If it passes the test, it will give you a one line output saying so. If not, restore from backup and try again. 
9.2 The scripts
So now it's time to make the scripts that will change the brightness themselves. Just download the one I uploaded and copy/modify it to make for the rest of brightnesses. This one is already an executable, so if you want to make your own make sure to make them so. The first script is called br1 because it will set the brightness to 1 (on a scale from 1 to 10). So when copying/modifying them (right click > open with > text editor) change the 1 in ```
echo 1 > /proc/acpi/video/GFX0/LCD/brightness
``` to the number you want it to set it to. Make sure to change the filename to reflect the brightness it will set the backlight to, and also make sure to move all of the scripts to that folder you specified in the sudoers file. 
Now it's time to create the launchers that will execute the scripts. Create a new launcher in a folder, the Desktop or the Panel, name it and in the command field put ```
sudo /home/jerry/myscripts/br1.sh
``` (again substituting with your own path).
And that is all, it should work when you activate the launchers.

---

### Post by sarah.fauzia on 2008-08-03
I had been reluctant to take another stab at fixing my screen brightness after experiencing a chmod error because I edited the permissions on sudoers. However, recent troubles with my tablet´s battery life prompted me to try again, and using visudo (without changing the file permissions) worked perfectly! (I followed the instructions for editing sudoers from [this]("http://www.unixcities.com/sudo/index.html") site; in short, I typed o to put it into editing mode, and :wq to save my changes). Now I´m going to add brightness launchers for 1-10--Xubuntu has a neat option of putting launchers in menus, which conserves space and makes this more convenient to do. Thanks for posting this how-to!

---

### Post by priegog on 2008-08-03
yeah, I reckon visudo is the best way to do it but since I can't use vi to save my life I had to work around that. I'm glad it worked out for you in the end.

---

### Post by SpazTheCat on 2008-08-21
Hi,

Great post, thanks for doing this. Today I installed Ubuntu on a Motion LS800 we had laying around at work. With a few pointers from your How-To, the digitizer is working great.

If you don't mind, I do have a couple of questions.

1. How do you deal with not having an on-screen keyboard at the Ubuntu login window? The pen works great, but with no keyboard, I can't input my username and password.

2. Do you use any kind of handwriting recognition software? If so, what? Or do you just use OnBoard for text input?

Thanks,

Andy

---

### Post by priegog on 2008-08-22
Hi: I'm glad it worked for you.
To answer your first question, the truth is that on all my computers I like to have them autologin to save time, so I do not have to deal with the login screen. I do know, however about a little hack people use for exactly these situations for summoning an onscreen keyboard at login. I do not exactly know how it's done, but I'm sure if you search these forums for "login onscreen keyboard" you'll find what you're looking for.
As for the second question: the answer is a little complicated. When I need to do serious writing (like I'm doing right now answering to this post) I use a bluetooth foldable keyboard, and that works great. However, when I'm surfing, checking emails and stuff I use a program called CellWriter (available in the official repos) which works pretty well for recognizing handwriting, even tho it has the limitation of requiring you to write each letter in a separate box. It also has a toggle that transforms it into an onscreen keyboard, so there's no need for 2w separate programs there. It is truly sad the state of handwriting recognition software is  in on Linux.
Hoperfully ubuntu mobile and all these projects will push all of this forward. 
So there you go, hope that helps.

---

### Post by SpazTheCat on 2008-08-23
Hi again,

Does suspend and/or hibernate work on your M1300? I can get my LS800 to sleep without a problem. It just won't wake up unless you toggle the power button. Ubuntu then wakes the computer and promptly shuts it down. I imagine that pressing the power button is interpreted as a power-down acpi event. I haven't quite figured out a way around that.

Just FYI, I gave Ubuntu 8.1 a try on it and the issue with 3D acceleration and xrandr appears to be fixed.

Thanks,
Andy

---

### Post by priegog on 2008-08-25
Hi. Yeah, suspend works great on mine, but I do need to press the power button to wake it up. I don´t use hibernate so I wouldn´t know about that one, tho. I imagine you could solve the shutting down problem by associating a different function (or none at all) to the power button on the power settings.
I have a lot of expectations from 8.10 so I´m glad to hear stuff is being fixed on it.

---

### Post by SpazTheCat on 2008-09-06
Hi,

I'm still unable to get suspend to work correctly. I've been digging into it a bit further and I don't think hitting the power button to wake the computer is creating an ACPI event. When I look through the acpid logs I see the power button press to suspend the computer but nothing after that when I press it to wake the computer.

I was wondering if you could do me a favor and look at your acpid log to see if using the power button to wake the computer logs an event?

Thanks,

Andy

---

### Post by priegog on 2008-09-07
Sure, however I'm not as knowledgable as you seem to think I am. Where do I find this acpid log?

---

### Post by SpazTheCat on 2008-09-07
Hi,

I think I'm probably not as knowledgable as I might seem;) The only reason I know about looking in the acpid log is because I've been trying to resolve this sleep issue.

It's in /var/log

What I would suggest you do is set gnome power manager to sleep when you press the power button. Then, press the power button to sleep the computer and make note of the time. Wait a couple of minutes and wake the computer using the power button. Again, noting the time. Then take a look in the acpid log. You should see something like this at the time you put the computer to sleep:

"received event "button/power PWRF.........."

Then look further down the log and see if you can find a similar entry at the time you woke the computer.

Also, if you don't mind, open a terminal and do a "dmesg | grep Power" and post what output you get. For some reason I have two power buttons registered and I'm not sure why. I'm curious to see if you have that also.

Thanks,

Andy

---

### Post by hal2000 on 2008-11-12
> **priegog said:**
> So, I finally solved this thing (had been at it for at least a couple of months) so I'll just post here exactly how to do it. Most of the steps are similar to the ones on [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=110050"), so much of this guide will be a copy-paste of that.

1. Go to the terminal and install all of these```
sudo apt-get install setserial wacom-tools xserver-xorg-input-wacom
```
2. Map the hardware port to a virtual serial port```
sudo setserial /dev/ttyS0 port 0x0238 irq 4 autoconfigure
```
3. Check that all is working; first type ```
wacdump -f tpc /dev/ttyS0
``` and move your pen around the screen. If the numbers move, keep going. If they don't you're out of luck.

4. Put the appropriate entries in the xorg file. type ```
sudo gedit /etc/X11/xorg.conf
```, and paste these lines in there somewhere (I put them at the beginning) ```
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Type" "stylus"
Option "SendCoreEvents" "true"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option    "Button2"    "3"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Type" "eraser"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Type" "cursor"
Option "Device" "/dev/ttyS0"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
```
and then add these lines to the Section "ServerLayout":```

InputDevice "cursor" "SendCoreEvents"
InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
```
4.1. (Optional for screen rotatiOn in step 8 ). Add these lines to the "Device" section:```
	Option		"RandRRotation"	"on"
	Option		"NvAGP" 	"1"
	Option		"DRI"		"false"
```WARNING:This last line will disable3D acceleration but i'ts neccesary.
Click the save button and close gedit.

5. Make these changes permanent by typing ```
sudo dpkg-reconfigure setserial
```and selecting the option "autosave once"

6. Restart and it should all be working!

After this my tablet worked just fine, but the other guides included this last step so I'll post it here as a "last resor" measure.

7. Type ```
sudo xsetpointer stylus
```
I actually don't know what this command is for, so if someone were to illuminate me...

I know there aren't a lot of M1300 users out there but still I wish when I bought mine there was a guide just like this one to set it up. 
This is working for hardy but presumably it would work with future versions as well.

________________________________________________________
[List of Tablet PC's working with Linux and links to the how-to's]("http://tuxmobil.org/tablet_unix.html")

Ubuntu 8.10
M1300
I tried fon my pen on screen   but, after restart, KDE don't run.

??????

I apologize for my english

Alberto

---

### Post by priegog on 2008-11-12
Hablas espanol? O es portugues? Te respondere en espanol. 
Pues aun no se como seran las instrucciones para hacerlo funcionar con 8.10. Asi que puedes esperar a que averigue como funcionara, y mientras tanto instalar hardy, que funciona perfectamente con estas instrucciones. Por eso en el titulo de este tutorial pone "Hardy".
Suerte

---

### Post by hal2000 on 2008-11-13
> **priegog said:**
> Hablas espanol? O es portugues? Te respondere en espanol. 
Pues aun no se como seran las instrucciones para hacerlo funcionar con 8.10. Asi que puedes esperar a que averigue como funcionara, y mientras tanto instalar hardy, que funciona perfectamente con estas instrucciones. Por eso en el titulo de este tutorial pone "Hardy".
Suerte

I'm italian.
	
I understand enough English, but speak little!
Step 1, 2, 3: all OK!
Step 4: done!
The PC restart but the system remains in text mode.
What's the command to start KDE?
Thanks

Alberto

---

### Post by priegog on 2008-11-13
If it is not starting on it's own, it won't start unless you fix what's wrong. 
What I was trying to say is that X.org changed a lot from hardy to intrepid, and so the same method cannot be used to make it work. You can either wait for me or someone else to figure out what the new instructions are going to be, figure them out yourself, or install hardy and follow these instructions as they are.

---

### Post by hooligan1975 on 2008-11-24
Hey, Priegog, love the scripts, works up to adding the script for the server, I see the numbers move and try to add the server settings, but I don't have server side in my Xorg file. Couldn't find it, tried to add it but to no avail. I'm new when it comes to Linux script side but trying to learn. I can follow up with what I have input so far, I saw the numbers move as I used the stylus, but after I restarted assuming I put all else in of course after the server side scripts. 
and then add these lines to the Section "ServerLayout"?
InputDevice "cursor" "SendCoreEvents"
InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"

Didn't have it in the XORG file.

The rest was fine since it was optional, restarted and pen didn't work, Am I doing a step wrong. Do I open one terminal for all of these and save as I go. Still working on the Ubuntu newby barrier sorry, andy input would be appreciated. I am running the latest and greatest from Ubuntu.

---

### Post by priegog on 2008-11-24
Hi. Don't worry about the newbie barrier, we've all been there. Just a quick question: what version of ubuntu are you using? This guide was made specifically for 8.04 and it doesn't work for the current 8.10 due to changes in xorg. I haven't quite figured out how make it work in 8.10, but when and if I do I'll be posting a similar how-to. If anyone else reading this has ANY idea on how to get wacom tablet pc's to work with 8.10 (specifically what has changed since 8.04) please let me know.
hooligan 1975: If all else fails, just download 8.04 in the meantime. It's not terrible. It's an LTS after all.

---

### Post by hooligan1975 on 2008-11-24
Fantastic, I will do that, I first used my 6.04, and figured that was the issue. So I assumed,<-----(the Mother of all f-ups) that this worked for 8.1. I will download the 8.04 and try it with that, In the meantime, I will try and dive into the code and post new info for it, that might help the future progression of 8.1. I thank you for the information. I will re-post after I reload 8.04.

---

### Post by priegog on 2008-11-25
Hey wait!
No need to install 8.04.
You motivated me to troubleshoot the issue and I figured out that with the previous release's xorg.conf, and skipping step 4.1, the tablet works. Of course I still have to figure out the screen rotation thingy, but at least it's usable. I figure you won't be able to get last version's xorg.conf, so I'll attach it here for you. All you have to do is follow the instructions as usual (in 8.10), but substitute step 4 for substituting your xorg.conf file with this one.
If this is all too confusing for you let me know and I'll give you more detailed instructions.

edit: you'll have to rename the attached file to xorg.conf, since to attach it I had to add the .txt

---

### Post by hooligan1975 on 2008-11-26
Laughing my A$$ off, I already installed it, too late, although I have to admit it works perefctly as described. My M1300 has been thru the ringer, so it's been used and abused. But it hasn't worked this great in a while, I haven't had any issues so far the stylus works great, wireless works great, all said and done I don't have any current issues. Knock on wood. I was trying to find a quality virtual keyboard, and decided to try the cell writer. Working thru the learning stage as we speak. I found a new use for my M1300 thanks for the help. I might even put this or 8.10 on my Acer Laptop. Get rid of the memory hog Vista I have on it now. I've heard some good feedback from others using it on there Acer so I will give it a try. My only dilema is that I play WOW, and trying ot integrate Wine with Ubuntu and WoW should be pretty simple, but haven't tried it yet, So maybe over the weekend. Will take a look at the Xorg config you included, and maybe try it over the 8.04. Thanks fro the feedback, I appreciate it.

---

### Post by priegog on 2008-11-26
Oh, such a shame... in 8.10 the brightness scripts are no longer necessary as teh system can control it... but 8.04 is a great distro... and 8.10 didn't quite get its act together so maybe you're better off waiting for the next one. 
For the other computer, May I suggest that you try using wubi on it first and see how that goes? wubi is a way to install ubuntu without repartitioning your computer and can be removed like a normal program if no longer wanted... or even try dual-booting ubuntu & windows to check out the wine-WOW situation... my understandin is that at this point WINE works flawlessly and out of the box with WOW.. so if that's the reason for staying with windows, by all means, try it first, and then dive in!

---

### Post by hal2000 on 2008-11-26
> **priegog said:**
> If it is not starting on it's own, it won't start unless you fix what's wrong. 
What I was trying to say is that X.org changed a lot from hardy to intrepid, and so the same method cannot be used to make it work. You can either wait for me or someone else to figure out what the new instructions are going to be, figure them out yourself, or install hardy and follow these instructions as they are.

Installed Kubuntu 8.04.1
All OK!

---

### Post by priegog on 2008-11-26
Yeah, I figured just yesterday... as long as you don't do 4.1... Which might no longer be necessary, since a few minutes ago I rotated the screen from the screen resolution thing and it worked fine. Will try my scripts out...
I'm glad it's all working out...

---

### Post by hal2000 on 2008-11-26
> **priegog said:**
> Yeah, I figured just yesterday... as long as you don't do 4.1... Which might no longer be necessary, since a few minutes ago I rotated the screen from the screen resolution thing and it worked fine. Will try my scripts out...
I'm glad it's all working out...

	
Do you think it works with Ubuntu 8.10?
Do you know a program of handwriting recognition?
Thanks!

---

### Post by priegog on 2008-11-27
Yeah, that's what I was saying. These isntructions are for 8.04, but they can be modified to work for 8.10. in [this link]("http://ubuntuforums.org/showpost.php?p=6247888&postcount=20")I explain what needs to be done to make it work with 8.10. It seems I might have to write another how-to.
And yeah, for handwriting recognition pretty much the only one that is currently being mantained is cellwriter.It's not great, since you have to enter each caracter in different sqare, but it works and it has an on-screen keyboard. I think I've heard there is at least one such program being developed for linux, so maybe we'll have a good one soon. However, for REAL text input I bought a foldable bluetooth keyboard and it works great.

---

### Post by hal2000 on 2008-12-01
> **priegog said:**
> Yeah, that's what I was saying. These isntructions are for 8.04, but they can be modified to work for 8.10. in [this link]("http://ubuntuforums.org/showpost.php?p=6247888&postcount=20")I explain what needs to be done to make it work with 8.10. It seems I might have to write another how-to.
And yeah, for handwriting recognition pretty much the only one that is currently being mantained is cellwriter.It's not great, since you have to enter each caracter in different sqare, but it works and it has an on-screen keyboard. I think I've heard there is at least one such program being developed for linux, so maybe we'll have a good one soon. However, for REAL text input I bought a foldable bluetooth keyboard and it works great.

How-to calibrate the stylus on the screen?

---

### Post by priegog on 2008-12-01
That is not necesary for wacom tablets. I've never had to have mine calibrated... I believe external wacoms CAN do so to compensate for screen viewing angle, but not for pc's. Is your mouse pointer off or something?

---

### Post by hal2000 on 2008-12-02
Is only a tiny problem.
Another question.
The battery is fully charged, but the system shows only 33% and often lost.

---

### Post by priegog on 2008-12-02
Ah yes, that, I don't know... Notice, however, that when you suspend it, and then wake it up, the battery shows correctly. I've been looking for an answer to this for a long time. I'll start actively looking again.

---

### Post by technoguy on 2008-12-08
Here is the xorg.conf.txt file properly formatted...
Please reply if there are problems..
BTW, I am using the Motion M1300 and hve gotten mine to work great!
Haven't tried the screen roation yet, but so far, so good!!!

---

### Post by priegog on 2008-12-12
Ok, I figured the battery thing out. 

1 You have to download the battery.sh script attached here, and put it in a folder where it will need to stay. I used a folder named "scripts" in my home folder.

2 Open the terminal and type ```
sudo visudo
```A text-based text editor will appear with the sudoers file. To make a long explanation short, you need to paste to the END (position is important) of the file the following line ```
jerry ALL=NOPASSWD: /home/jerry/scripts/

``` (but substituting "jerry" for your username and the path to the path where you're going to put the script.
Then press "Ctrl + X", followed by "y", and followed by "Enter" to save the changes. 

3 Click on the menu System>Preferences>Sessions, and click on the "Add" button. In the "Name" field put whatever you want, and in the "Command" field paste this ```
sudo /home/jerry/scripts/battery.sh
```Substituting the path to the path of your script. 

And that should be it. Finally the battery will be correctly measured.

---

### Post by Merkidemis on 2009-02-18
anyone else having issues getting the audio to work under 8.10?

---

### Post by priegog on 2009-02-19
No, not really... what kind of problems?

---

### Post by trainerjonathan on 2009-03-12
Hi priegog!

First I'd like to thank you for this wonderful how-to!  I wanted a slate with linux on it and this how-to strongly influenced my purchasing decision.

I have Linux installed under Wubi right now and every thing works great except for screen rotation.  I followed the instructions and the Protrait script works fine.  Unfortunately when I click the button I set up for the Landscape script, the screen goes blank and when it clears I have to login again. (though it is landscape!)

I would be thankful for any advice you have?

By the way the instructions to add the on-screen keyboard to the login screen in this [post]("http://ubuntuforums.org/showpost.php?p=1789021&postcount=4") worked perfectly for me.

Thanks again for this awesome How-To!

Jonathan

---

### Post by priegog on 2009-03-12
Huh... No idea, my scripts work just great. My best guess is that it has something to do with wubi... but I don't really know how that works so I can't say. But a suggestion I can make is to enable the proposed updates (and probably backports too) in software sources. That way you'll have the absolute latest. In any case, Jaunty is coming and I guess it'd probably fix any bugs that are left with the interaction between xrandr and compiz, which was a cause for problems back in hardy, and probably has something to do with this.
Id' DEFINITELY suggest you installed a "full version" and at least double-boot, not for this problem, but because ubuntu is really mature and ready for daily use, as oposed to some neat experiment. And if it fixes this issue, all the better. 
Anyways... you're very much welcome. One tip I think I already gave in this thread was to get some TINY USB bluetooth adapter (for it to remain connected at all times) and a bluetooth foldable keyboard. 
Thanks for the tip on the login-time OSK, I'll add it to the main post!

---

### Post by trainerjonathan on 2009-03-13
> **priegog said:**
> bugs that are left with the interaction between xrandr and compiz, which was a cause for problems back in hardy, and probably has something to do with this.

Thanks Priegog!  I disabled visual effects and now screen rotation works both ways.

---

### Post by priegog on 2009-03-13
Glad it worked out for you :)

---

### Post by Merkidemis on 2009-03-15
> **priegog said:**
> No, not really... what kind of problems?

no matter what I do, I can't get any sound, form any app, even the test tools.  I know the sound card works, as it was running under xp.

---

### Post by priegog on 2009-03-15
Sorry, don't know what's going on. For the last 2 or 3 releases pulseaudio has acted up a lot for a lot of users. There are a couple of threads around in this forum that explain how to properly setup pulseaudio. It's worth a shot.

---

### Post by trainerjonathan on 2009-03-18
Hi Priegog!
[Bug #295292]("https://bugs.launchpad.net/bugs/295292")
Can cause the calibration to go off when resuming after screen rotation. The Bug report lists a work around I was unable to implement.

My solution has been to add a panel button that launches "wacomcpl", which has a calibration tool.  Just make sure you put the launcher in the upper left of the screen!

Edit: I was able to implement the work-around using the instructions in this post:

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/295292/comments/15](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/295292/comments/15)

---

### Post by priegog on 2009-03-18
Hi. 
Well, that bug doesn't affect me because since Intrepid it just can't suspend correctly. Hope both bugs get fixed in Jaunty. I really miss suspend.

---

### Post by trainerjonathan on 2009-03-21
Hello Again,

That's strange about suspend, I followed your directions to install intrepid and except for the calibration bug I mentioned in another post suspend/resume seems to be working fine for me.  

My question is probably a simple one, but a search of the boards did not find a post addressing it:  How do I change the functions of the hardware buttons?  I can remap them if I can figure out what they are mapped as, probably.

What I know so far:
Triangle = Alt+Home
The triangle brings up a file browser of my home directory when there is nothing else running, and acts as the Home button in Firefox.

X = Escape?
It takes me out of full-screen mode in Adobe Acrobat but does nothing in Firefox, also closes some windows.

Dark Circle = ?
Mar 21 17:08:39 ubuntu kernel: [24881.718948] atkbd.c: Unknown key pressed (translated set 2, code 0xf9 on isa0060/serio0).
Mar 21 17:08:39 ubuntu kernel: [24881.718964] atkbd.c: Use 'setkeycodes e079 <keycode>' to make it known.

Square = ?
Mar 21 17:02:56 ubuntu kernel: [24538.131991] atkbd.c: Unknown key pressed (translated set 2, code 0xf4 on isa0060/serio0).
Mar 21 17:02:56 ubuntu kernel: [24538.132008] atkbd.c: Use 'setkeycodes e074 <keycode>' to make it known.

Thanks,
Jonathan

---

### Post by priegog on 2009-03-21
Well, on that, I can't help you. I know that there must be SOME way to do it, but I haven't found it. I haven't looked too hard either, mind you. If you do find out, let me know!

---

### Post by Favux on 2009-03-21
Hi,

You probably want to see if you get a key code.  Type "xev" in a terminal.  It pops up.  Press the key.  There will be a lot of output.  Buried in it should be the key code, like keycode=68.  Xev doesn't detect all keys though.

Then you can bind the keycode to whatever you want.  Remember that HAL in Intrepid breaks single key key bindings.  So I have to leave my keyboard section uncommented out in Intrepid.  That way pressing one button can be bound.  In my case to my rotation script.  I don't know what you folks would have to do.

---

### Post by priegog on 2009-06-12
**[COLOR="Red"]ATTENTION TO ALL M1300 USERS[/COLOR]**

Surely most of you have noticed that since Jaunty, Ubuntu no longer works properly in these tablets. And if you don't specify the acpi=off parameter to boot, it won't boot at all. This is a regression. 
Unfortunately I noticed this too late, almost when Jaunty was launched. So I couldn't file a bug report in time, and instead decided to wait it out to see if the Karmic development would make it work again. 
But needless to say, it didn't happen. So I filed the bug. 
[Here is bug 386272]("https://bugs.launchpad.net/ubuntu/+bug/386272") If you can reproduce the bug, it would be really helpful to all M1300 (and possibly other models) users out there if you were to subscribe to this bug, to let the developers know we care.

Thanks

---

### Post by rrwood on 2009-06-21
It seems that the brightness applet is also broken in 9.04, though maybe it's a WUBI problem.

Anyone else having problems with the Gnome brightness applet in 9.04?

---

### Post by rrwood on 2009-06-21
Maybe it's acpi/apic problems?  This is my kernel boot option list:

$ cat /proc/cmdline 
root=UUID=448023BF8023B678 loop=/ubuntu/disks/root.disk ro acpi=off noapic nolapic quiet splash 


What are you guys using as boot options?

---

### Post by pmbuc on 2009-06-21
I experienced this problem on Dell Inspiron 6000 (Intel grpahics) I recently repaired. Jaunty booted up fine, with brightness maxed as desired. Just before the desktop was completed, the screen dimmed to the point where it was barely readable. The keyboard controls for brightness *and* the panel applet for brightness control work to correct this only for the duration of the session and they work in reverse. From what I have read, the problem may lie in the way Gnome power management is handling the hardware. It also appears to be tied to Intel-based video graphics, as some Lenovos/Thinkpads with Intel graphics are experiencing dimming and keyboard mapping issues, as well.

---

### Post by priegog on 2009-06-21
> **rrwood said:**
> It seems that the brightness applet is also broken in 9.04, though maybe it's a WUBI problem.

Anyone else having problems with the Gnome brightness applet in 9.04?

> **rrwood said:**
> Maybe it's acpi/apic problems?  This is my kernel boot option list:

$ cat /proc/cmdline 
root=UUID=448023BF8023B678 loop=/ubuntu/disks/root.disk ro acpi=off noapic nolapic quiet splash 


What are you guys using as boot options?
Yeah, that is exactly what I was trying to explain. 9.04 broke the ability of talking to the hardware via the ACPI. That is the reason the brightness applet won't work, as well as a couple of other things; probably the motherboard's ability to shut itself down when turning off the computer too. Oh, and most importantly probably the wacom tablet too (can you confirm this?)
As far as I know there's no workaround (like there was in hardy) unless the bug gets fixed (probably in the kernel). Which is why I've asked you to subscribe to the bug I mentioned, to tell the devs we want this regression fixed. 
So yes, it is an ACPI problem. For this very reason I'm still in Intrepid on my M1300, but when I installed jaunty to try it out I did have to add the acpi=off line to make it boot. Otherwise it won't, but that the very problem: that line turns off the OS's communication with the motherboard. 

@pmbuc: What you describe is a completely different issue to the one we have.

---

### Post by rrwood on 2009-06-21
The Wacom tablet works fine for me, but the brightness control is definitely NOT working.  As you suspected, the machine also does NOT shut off via the usual software-initiated shutdown procedure (it hangs at the end and I have to manually kill power).

I'll subscribe to the bug and hope that a fix is in the works.  Other than the issues mentioned above, things are working really well....

---

### Post by priegog on 2009-06-22
Great, thanks, now let's hope someone picks up the bug.

---

### Post by abibosty on 2009-06-30
Hi. I have buyed a M1400 a few weeks ago on Ebay without any external device. I tried to install Windows XP: from external CD, from hard drive partition and with PXE. And I failed. So I tried to install Ubuntu via PXE. The last release did not work (known ACPI error). So I am pleased to use now the 8.04 release.  Thank you Priegog for your post which really help me. 
But I have a sound issue. Sound work only when I plug headset. The internal speakers are mute. Has someone any tips to make them work?
Thanks.

---

### Post by priegog on 2009-06-30
> **abibosty said:**
> Hi. I have buyed a M1400 a few weeks ago on Ebay without any external device. I tried to install Windows XP: from external CD, from hard drive partition and with PXE. And I failed. So I tried to install Ubuntu via PXE. The last release did not work (known ACPI error). So I am pleased to use now the 8.04 release.  Thank you Priegog for your post which really help me. 
But I have a sound issue. Sound work only when I plug headset. The internal speakers are mute. Has someone any tips to make them work?
Thanks.

Hi, the 8.10 release should also work fine, and also fixes some inconveniences. And about the sound problem, I honestly don't know, I have an M1300 and never any issues with that. It could happen that 8.10 fixes it.

---

### Post by andrewPCT on 2009-09-18
> **abibosty said:**
> Hi. I have buyed a M1400 a few weeks ago on Ebay without any external device. I tried to install Windows XP: from external CD, from hard drive partition and with PXE. And I failed. So I tried to install Ubuntu via PXE. The last release did not work (known ACPI error). So I am pleased to use now the 8.04 release.  Thank you Priegog for your post which really help me. 
But I have a sound issue. Sound work only when I plug headset. The internal speakers are mute. Has someone any tips to make them work?
Thanks.

My first impression with the sound is that the internal speakers might be bad. Otherwise I'm not sure what the issue could be.

---

### Post by pgcudahy on 2011-10-22
Hey, this thread has been dead for two years but it's just what I need. I've been trying for a while to get ubuntu on my m1400 to make an xbmc front end. I got natty working but it was too slow with the latest xbmc. Now I've downgraded to hardy with xbmc 8.04 but run into a little trouble with the stylus.  "wacdump -f tpc /dev/ttyS0" works great, but in X the cursor just jumps down to the lower right hand corner whenever I bring the stylus near the screen. The cursor works fine with the mouse. Any thoughts why this might be happening?

---

### Post by priegog on 2011-10-22
What do you mean you've "downgraded to Hardy with xbmc"? Is xbmc a distro based off ubuntu? If it is, I think the obvious solution is to give it a try with vanilla Hardy. But honestly I'm not sure this couldn't be explained by the fact that you're using an m1400 instead of an m1300.

But if the tablet was working right with natty (now we're on oneiric), I'd honestly try to make that work instead. I can't stand that much older releases. Try Natty with a completely 2D session without unity, you'd need to install the gnome fallback session and log in using that. AFAIK newer versions of Ubuntu shouldn't be any more resource intensive at all, excepting for the UI which is what the fallback session is for.

---

### Post by pgcudahy on 2011-10-22
I could try that but I feel like I'm so close now. The problem is that XBMC (a media center app) has become much more resource intensive over the past few years. They don't support older versions so there are no natty or oneric repos for the older xbmc. I tried to compile an older version but so many of the dependencies have been changed that it's a real pain. The easiest thing to do was to install the old xbmc on an old ubuntu release. Now wacdump makes it look like everything's working but the cursor just jumps to the corner. Have you ever heard of this before?

---

### Post by Favux on 2011-10-22
Usually the cursor jumps to the upper left corner on a monitor because that is the 0,0 coordinate for X.  That indicates the Wacom X driver isn't sending any coordinate data to the X server.  What's your xorg.conf look like?  And do you have xserver-xorg-input-wacom installed?

---

### Post by pgcudahy on 2011-10-23
Here's my xorg.conf

---

### Post by pgcudahy on 2011-10-23
And my Xorg.0.log

---

### Post by Favux on 2011-10-23
Your xorg.conf looks OK with a couple caveats.  You shouldn't need this line in the stylus section:
```
        Option          "SendCoreEvents" "true"
```
Don't know if that will make a difference though.

In Hardy in "ServerLayout" didn't we need something like the following?
```
      InputDevice    "Mouse0"    "CorePointer"
      InputDevice    "Keyboard0" "CoreKeyboard"

```
I guess using your mouse and keyboard Identifiers.  I can't remember.  I suppose the *Option "CorePointer"* takes care of the mouse.

And when we set the xorg.conf up in Natty didn't you have an eraser?

Since wacdump shows the stylus is on the ttyS0 port that isn't the problem.

Xorg.0.log looks good.  You are seeing a:
```
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
```
which is why I brought up the "ServerLayout" question.  Otherwise the stylus seems to be set up correctly.  So unless there is some conflict between the stylus and mouse as to which is the core pointer that should be good.

So then the question is it the default linuxwacom 0.7.9-8?  I don't remember there being a problem with it and serial tablets.  USB tablets yes, since usb was just being introduced to the driver.  But things that long ago are vague.

---

### Post by pgcudahy on 2011-10-23
Looks like it's a problem with xbmc rather than X11. When I exit xbmc and start fluxbox the pen works great. XBMC also has an option to "enable mouse" and when I turn that off the regular cursor appears and follows the pen but can't click. When I "enable" the mouse in xbmc, the custom xbmc cursor (a bigger, green arrow) comes on and will follow the mouse but not the pen. Frustrating! Thanks again for your help Favux

---

