---
title: "Dell C800 Can't display boot off live cdrom"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by macubergeek on 2006-06-03
Hi 
I've got a Dell Latitude C800 with a big screen 1400/1250.
When I boot of the Kubuntu live cd I get no display. I'm guessing that the display probe/detector in the boot setup can't figure out the correct X settings. I had the same problems with Libranet and had to manually set the resolution.
Is there a boot cheat I can enter to set the display resolution?
I know Kubuntu works fine on other laptops I've tried with smaller displays.

Jk

---

### Post by macubergeek on 2006-06-04
Since 11 people have looked at my post and NO ONE HAS RESPONDED...maybe I was unclear.
The laptop I have has a screen resolution of 1600x1200.
The installer can't autodetect this screen resolution and I've had no luck finding the Xfree86 configuration utilities I'm used to on other distros.
Does anyone know how I can successfully install this AND have X11 display properly. Right now I'm seeing the login screen come up but with weird vertical stripes, complete display breakup.

---

### Post by alaman on 2006-06-05
installing on my c800, I used the safe graphics option.  It loaded fine but the resolution was poor.  using sudo dpkg-recnfigure xserver-xorg, I was able to fix the resolution issues.

---

### Post by zmartant on 2006-09-29
I found this thread, as I too have the problem of the verical line which splits the screen.  After several hours and multiple installs and my wife yelling at me for taking so much time on the computer :-# , I have resolve the issue.  I am a newbie to Linux, so I probably did this the long and difficult way. ](*,) Installing from the live CD Ubuntu 6.06 LTS (Dapper Drake), these are the steps I took:
1. Boot with the CD
2. Chose first option on the menu, I believe its LIVE CD/Install
3. After boot, you will see the Desktop (Split)
3a. Click on the Install
3b. Go through the installation
3c. Reboot (part of the installation)

****From this point on, view the menus and windows is difficault as the screen is split in half.  You will have to do a little guessing, and a lot of patience! ****

After the Reboot you will see the Ubuntu login screen, but since the screen is split, you not see the login box.  Just input your login name and press return (enter).  Then, input your password (the one you entered during installation) and press return (enter).  If everything goes fine you will see the Desktop split in half.  At the top left you will see a menu.  You may now proceed with the instructions below:

4. Go to Application-->Terminal (Terminal is the sixth option)
5. cd to /etc/X11
6. su pico xorg.conf
7. enter su password (same password during installation)
8. Go to the following line:
   Section "Divice"
            Identifier     "ATI Technologies, Inc. Rage Mobility M4 AGP"
            Driver         "ati"
            BusID          "PCI:1:0:0"

9. Replace "ati" with "vesa"
10. Ctrl-X to exit
11. enter(return) to save file
12. Reboot

You should now be running at 1400 x 1050, which is the native resolution for the C800.

If you know how to get to the CLI (command Line) after the reboot of the initial installation, and not using the GUI (Graphical User Interface), then the steps above will much simplier.  You will not have to fiddle with the widows to see where you are as the screen is halved.  I concentrated on the right when opening and adjusting your windows.

If you can get to the CLI after the initial reboot (before you get to the GUI), then all you have to do is go to /etc/X11 and sudo pico xorg.conf and edit the file as mentioned above (steps 8 and 9)

As I mentioned, there is probably several methods to complete this process, but since I am a newbie, this is the way I resolve this issue.

Come to think of it, you probably can do the installation via safe graphics, and the screen will not be split.  Then you can do the steps to get the proper resolution!  I did the installation through safe graphics, but my Ubuntu screen was smaller than the actual screen.  So, I took the chance and reinstalled via regular install.  You always think of the easy stuff only after resolving the issues the difficult way!  Just remember to replace all reference to 1024 x 768 with 1400 x 1050 in the xorg.conf file.  Please note, that I did not do the install this way, so I do not know if this way will actually work.  If you do try, please post your result.

---

### Post by AEngineer on 2006-11-25
My thanks to zmartant for his recommendation.  I was reinstalling Ubuntu edgy after an upgrade to it from dapper.  My screen split in three parts.  Thanks to your information I was able to go into safe mode (I think) while booting and make the change without having to reinstall.  All works well now.

Curiosity leads me to ask.  How did you figure out this was the necessary change and where to make it?

---

### Post by zmartant on 2006-12-03
AEngineer,

I figured this out through many hours of the trial and error, and  reading many forum posts.  From what I have read, one can do anything via CLI, any if one knew how ;)

I have tried the install through safe graphics from the Ubuntu Live CD, and after the reboot, I changed the xorg.conf file to meet the figurations with those in my previous post (above).  It worked like a charm and I have not had any problems! :-D

I am Glad that my post helped!

---

