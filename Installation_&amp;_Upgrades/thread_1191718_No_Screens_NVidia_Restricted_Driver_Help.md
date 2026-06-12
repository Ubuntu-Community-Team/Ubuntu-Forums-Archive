---
title: "No Screens NVidia Restricted Driver Help"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by silentjon on 2009-06-19
Hello,

I have been searching around on the forums for an answer to my problem and have tried a few different solutions, but none seem to work, or I'm just too much of a noob. (Trying to change that of course)

Basically I've installed Ubuntu 9.04 and everything was running smoothly until I was asked to use a restricted driver to get the flashy window effects. I allowed it to install a driver and now X won't boot. I can get a prompt to log into but X gives me a no screens error. (I'm trying to run Gnome)

It's probably useful for you to see the xconfg? I would be happy to supply that, but I'm not sure now to get it across to my windows partition to put on the web. <- Proper noob.

My graphics card is as follows :-

NVidia GeForce 7300 GS x2 (SLI set up)

Do you need to know anything else? 

Thanks in advance for taking the time on this one . . .

---

### Post by slamhound on 2009-06-19
It might be the same problem I had (which resulted from the use of the two cards).  If so, the steps in this post should fix it.  You need to take an extra step to configure xorg for two cards after installing the nvidia drivers.

[http://ubuntuforums.org/showpost.php?p=7452633&postcount=2](http://ubuntuforums.org/showpost.php?p=7452633&postcount=2)

---

### Post by bryonak on 2009-06-19
Reboot your system and enter the GRUB boot menu if necessary. Choose the the newest kernel with "(recovery mode)" appended and hit enter.
Wait until you get a command prompt, then type:
```
dpkg-reconfigure -phigh xserver-xorg
```
If any errors occure, write back. If everything seems ok, just type ```
reboot now
```.

This procedure will ususally fix a broken X server... you have to activate the nvidia driver again.

---

### Post by silentjon on 2009-06-19
Hey hey,

I tried as u suggested resetting x, was given the following warning :-

Xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/x11/xorg.conf.20090619150442

To me this sounds like its what we were aiming to do. (Replace the file with a standard one)
When I boot though it still drops me back to shell and not into x.

Anything further to try?

Thanks!

---

### Post by bryonak on 2009-06-19
Yep, overwriting is what we want.

What happens if you type "startx" from the shell?
Also try "less /etc/X11/xorg.conf" and tell us how big it is. Press q to quit. The default version shouldn't be bigger than about 15 lines comments (with #) and at most another 15 lines of options.

---

### Post by silentjon on 2009-06-19
Right, seem to be narrowing the problem down . . .

As was stated by Slamhound I do have to of these cards running in SLI so it looks like that is the issue. I found the following :-

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Quater of the down the page. These instructions were very similar to Slamhounds so i gave them a bosh and now get the following errors . . .

```
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) No devices detected

Fatal server error:
no screens found
```I used to get the No devices found when I ran X, but the first two about modules are new and are only since I added the extra line in an attempt to point X at the correct card. Any other thoughts guys? 

Thanks again so much for your help, its hartening to know that the forums here are so speedy and pleasant. 

Thanks,

Jon

---

### Post by silentjon on 2009-06-19
Oh and in answer to the try "less /etc/X11/xorg.conf" . . . 

I get a file naming some of the moduels I spoke about in the previous post 
About 15 lines before the hash ("# generated from default)
About 15 / 16 lines after the hashes begin

Thanks for telling me to press 'Q' to quit as well. Lol!

Jon

---

### Post by bryonak on 2009-06-19
Well, I have zero experience with SLI systems, so I can't help you on that account. You could try to restore the old configuration...
Boot into recovery mode and change to the /etc/X11 directory: ```
cd /etc/X11
```
Then type "ls" to list all the files available. Copy one of the backups, preferably the one that worked, over your current xorg.conf:
```
cp xorg.conf.??? xorg.conf
```
You can always restore the default xorg.conf with the dpkg-reconfigure command mentioned earlier.

Try starting X.
If it doesn't work, use one of those larger xorg.conf files and try changing the driver (in recovery mode): ```
nano /etc/X11/xorg.conf
```
Ctrl+o to save, Ctrl+x to exit.
Go down to the "Section Device" and change the "Driver" from *nvidia* to *nv*.
Maybe you have two Device sections (one for each card), so don't forget changing them in both. *nv* is the Free/OpenSource nvidia driver.

---

### Post by bryonak on 2009-06-19
Oh, and you can try to comment (just put a # in front) those modules in the xorg.conf that fail to load, so they get ignored.
For example, freetype isn't needed anymore for the X version Ubuntu 9.04 has.

---

