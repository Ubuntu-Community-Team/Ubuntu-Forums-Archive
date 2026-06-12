---
title: "Ubuntu Jaunty 9.04 update &amp; restart results in white screen after login"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Fuchur777 on 2009-10-18
Need your help!

Have two different laptops configured in similar manner.
Toshiba u300 and MSI x-slim 340.

Last fridays update 16-10-2009 was 3 packages big. Only about 713 kb and where "x-....." packages if I remember right.

Both Laptops get to the login screen although it looks distorted (widescreen). After login you see your system load.
Pidgin signs in as it logs me out on my account on my PDA.

But then the screen turns completely White.

I know where the restart button is and if I click it... I briefly see my whole desktop before signing out.

Searched the forums and tried possibly every solution on the board but no result.
They seem to suggest compiz and x-server issues or driver issues.

I uninstalled compiz. Replaced it with emerald or metacity. Replaced xorg.conf but all to no result.

Does anyone have any suggestions?
If you need logs please let me know how to get them.

In graphic mode I know my way around ubuntu quite well.
However command line knowledge is minimal...

Thanks for any advise!

Ta Fuchur

---

### Post by loomnie on 2009-10-18
I have the same problem as Fuchur777. I have been looking through different forum threads but it seems this is a very recent problem. Could someone help?

Thanks!

> **Fuchur777 said:**
> Need your help!

Have two different laptops configured in similar manner.
Toshiba u300 and MSI x-slim 340.

Last fridays update 16-10-2009 was 3 packages big. Only about 713 kb and where "x-....." packages if I remember right.

Both Laptops get to the login screen although it looks distorted (widescreen). After login you see your system load.
Pidgin signs in as it logs me out on my account on my PDA.

But then the screen turns completely White.

I know where the restart button is and if I click it... I briefly see my whole desktop before signing out.

Searched the forums and tried possibly every solution on the board but no result.
They seem to suggest compiz and x-server issues or driver issues.

I uninstalled compiz. Replaced it with emerald or metacity. Replaced xorg.conf but all to no result.

Does anyone have any suggestions?
If you need logs please let me know how to get them.

In graphic mode I know my way around ubuntu quite well.
However command line knowledge is minimal...

Thanks for any advise!

Ta Fuchur

---

### Post by greg batmarx on 2009-10-18
same problem with me!
I run kde for now since this problem affects only gnome...
I have an intel gpu...
This is not the only thread that posts the problem and it seems that it is a widespread problem...
This upgrade broke something....

---

### Post by greg batmarx on 2009-10-18
the problem with the white screen started when I upgraded the intel driver...

---

### Post by tomjoad_hun on 2009-10-18
Hi,

 I had the same problem, my solution that works:
- change to a terminal (Ctrl+Shift+F6)
- log in (type user name and password)
- edit the apt sources and delete the optional intel driver package source:
--- 'sudo apt-get install mcedit'
--- 'sudo mcedit /etc/apt/sources.list'
--- edit the bottom part, where the optional sources are listed (comment them by putting an # to the start of the line, or simply delete the lines)
```
#deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
#deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
```--- save the file with F2, exit with F10
- remove the intel driver: 'sudo apt-get remove xserver-xorg-video-intel'
- update package meta-information: 'sudo apt-get update'
- delete old (hacked) xorg config file: 'sudo rm /etc/X11/xorg.conf'
- install official intel package: 'sudo apt-get install  xserver-xorg-video-intel'
- reboot 'sudo reboot', or maybe a gdm restart is enough, i don't know, maybe try 'sudo /etc/init.d/gdm restart'

So this is for the solution, but for me a new bug is present since then. When I put the totem media player to full screen, and then I try to exit from full screen mode, it logs out of my gnome session (surely X restarts). If anyone knows something about this, please help!

Tamás

---

### Post by zoli4290 on 2009-10-18
Hi Tamás,
Your efforts are really appreciated. Just to make it more precise and easier let's summarize what to do:
1. From the white screen press Ctrl+Alt+F6 (not Ctrl+Shift+F6) to switch to terminal.
2. Login with your username and password.
3. Edit apt sources with
   sudo nano /etc/apt/sources.list
   (It does not seem to be necessary to install mcedit as the nano editor should be available.)
4. Find the optional Intel driver package source # X-Updates and comment out (put # at the beginning of the line) or delete the two lines:
   deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
   deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main
5. Save the modification with Ctrl+O and exit with Ctrl+X
6. Remove the intel driver:
   sudo apt-get remove xserver-xorg-video-intel'
7. Update package meta-information:
   sudo apt-get update
8. Delete old (hacked) xorg config file:
   sudo rm /etc/X11/xorg.conf
9. Install the official intel package:
   sudo apt-get install xserver-xorg-video-intel
10. Reboot:
   sudo reboot

As far as the crash with Totem Player is concerned (confirmed anyway) a simple workaround can be to use VLC until Totem/Intel video are debugged.

---

### Post by greg batmarx on 2009-10-18
dear zoli!
I followed closely your instructions,
yet the problem persists and this white screen remains as before...:(
I can still use my ubuntu through kde or xfce but i would like to have my gnome back!
What is going on here?:confused:
What broke the gnome so much that even following such useful instructions,the gnome can't come back?
Anybody has any other ideas??
Thanks for everyone that tried to help anyway!

---

### Post by greg batmarx on 2009-10-18
ok the problem for me solved after upgrading to karmik koala beta!
everythying runs fine for now and my gnome is back at last!:guitar:

---

### Post by jefnert on 2009-10-18
Followed Zoli's post and now my system is back working fine.  Thanks guys for posting the solution.

If not for the people who post these answers I would have given up on linux a long time ago.

Thanks again.

---

### Post by FreezWay on 2009-10-18
sweet, i had teh same problem, followed zolis instructions and fixed it. you saved my world history HW... +1

also, about the lines you comment out, do we ever uncomment them?

---

### Post by dhelix on 2009-10-19
Hi,
I had same problem.I was using the driver from X-Swat and the 2.6.31.3 kernel.The problem occured after i updated xserver-xorg-video-intel to 2.9.0-1ubuntu2 and the kernel to 2.6.31.4.After restart i had white screen after login.I tried to revert with no success,also tried to revert to 2.6.28 with the latest driver in the ubuntu's repositories with no additional configuration in xorg.conf - again no success.Finaly i did dist-upgrade to Karmic and now my box is fine,except that it boot successfuly 1 time on every 2 boots :) ....anyway I'll fight this later

---

### Post by greg batmarx on 2009-10-19
btw,after upgrading to karmic koala beta,
I enjoy a desktop that is 3 times faster and hence a totally new computer experience!
This is not exaggeration!
The ubuntu developpers have done an excellent job providing us the best ubuntu ever :guitar:
Intel gpu had never been so responsible and fast at least in my modest computer.
And for the first time,totem is exciting and functional.
WELL DONE!

---

### Post by Fuchur777 on 2009-10-19
Hi All,

I am back up and running.

Seems that a program changed my xconf.org removing the driver data.
Suspect it was EnvyNG

However solution is easy. ( I have an intel GPU as well)
Soulution worked on both laptops I have.

Steps:
Fire up your laptop.
Login as normal.

Wait for the white screen ;-)

Press CTRL+ALT+F2
Type username
Type password

Type: sudo nano /etc/X11/xorg.conf
Type password

Look for the line: Identifier "Configured Video Device"
Add a line below: Driver "Intel"
Press CTRL+O
Press Y
Press CTRL+X

Type: sudo shutdown -r now

And enjoy your ubuntu again. :guitar:

I removed EnvyNG completly to avoid this and program was mad redundant anyway...

Let me know if this works for you.

Ta Fuchur

---

### Post by ArjenV on 2009-10-22
I can confirm the instructions  of [Fuchur777 ]("http://ubuntuforums.org/member.php?u=608469")do work on my Lenovo T61 !

Thanks again all to help solve problems!

Arjen

---

### Post by pSYcl0Ne on 2009-12-21
hey there, i'd just thought I'd bump this post and add a solution I found myself after scouring the internet for a while. 

this white screen seems to happen quite a lot due to bad lines in xorg.conf . 

this problem occured for me when i tried to use an external monitor with my MSI Wind u100 + . the external monitor/display settings automatically adds a line into xorg.conf to compensate for the second output which messed with my netbook display (something to do with two instances of X?) 

I had a backed up version of xorg.conf that i replaced over the current messed up one and i have my compiz back! just thought i'd put it out there if anyone else has the same thing happen - finding the solution wasn't much fun but now that i've learnt it im pretty stoked to have things back and better than before.

---

### Post by nuffy on 2009-12-23
Hi Guys,

I have the white screen of death on my fresh install of Karmic Koala and I am wondering if Fuchur777's fix will work for me if I replaced 'intel' in the Driver section with 'ati'?  I have a desktop pc so I am thinking this may help??

BTW... I experience extraordinary long boot time of 10+ minutes... will the video driver problem cause this??

Thanks in advance

nuffy!

---

