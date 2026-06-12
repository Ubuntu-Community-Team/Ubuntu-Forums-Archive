---
title: "Gnome doesnt start"
date: 2008-08-26
forum: General Help
---

### Post by Exile32r4 on 2008-08-26
Im having trouble with starting gnome, as you probably have seen on the title. I have Ubuntu Hardy Heron 8.04 installed on a laptop. I was using it when all of a sudden it crashed (even the mouse crashed), so i rebooted the machine. It got to the login screen just fine, but after that it shows the wallpaper and i can move the mouse and everything, but nothing else. So i tried logging in from the terminal (<ctrl><alt><f1>) and it tellms me something about the server display 0 and that if its not in use i should remove /tmp/.X0-lock. So i do that and then i try ```
startx
```, but it is still stuck at the wallpaper.


Ok so Ive looked around everywhere (and im NOT just saying that) and it seems the only option is to re-install ubuntu, but I want to salvage some files if i can. If anyone has any suggestions they would be much appreciated. Thanks in advance.

---

### Post by Crafty Kisses on 2008-08-26
Have you tried reconfiguring X?

---

### Post by Exile32r4 on 2008-08-26
yeah..i tried that too

---

### Post by mike2357 on 2008-08-26
Can you boot into recovery mode?  If so, you could create a new user, and then try logging in as that user.  If you're successful, then the problem is likely to be corrupted files in your home directory, possibly in the .gconf, .gconfd or .gnome2 directories.

The program to add a user is /usr/sbin/adduser.  It needs to be run as the super-user, i.e.

sudo /usr/sbin/adduser <options>

You can run "man adduser" to get all of the options.

Good luck.

---

### Post by mssever on 2008-08-26
Try logging in using the failsafe terminal session. Then, type ```
gnome-session &
```Hopefully you'll get some helpful error messages, which you can post here if you don't understand them.

---

### Post by Exile32r4 on 2008-08-27
thanks for all the replies, but i tried all the above and i also tried changing permissions of the home folder,because it was giving me an xauth error, but now i cant even boot ubuntu, it says error 15: file not found. Im just gonna do a fresh install and hope it doesnt happen again :( . Maybe it had something to do with Compiz Fusion and all the avdanced desktop effects i was trying out.

---

### Post by dkhajavi on 2008-09-18
Looks like I have the same issue.  I have been basically 100% with 8.04 for 45 days now.  Worked all my issues out of major concern.  

However now on my first business trip with my Ubuntu laptop, I am stuck with no computer.  I was experiencing some very reduced batery life and in the repositories I found Kpowermeter or somthing similar which has control over speed step CPUs like I have.  I installed it and played with it (it worked great by the way nearly 2X the battery life than with the other battery monitor only).

At any rate the next day I booted up to check my mail and everyting was normal including my drums and all, entered my user/passord then nothing.  I have the brown Ubuntu background, a mouse pointer that moves but no desktop.  I can see that I have mouse and keyboard control and can get into the terminal.  

I would love some help here guys!  Thanks

Dell M65 
Intel Dual Core
2 Gigs Ram
Nvidia Video
I have -16 Generic and Server upto -19 Generic and server with no difference in the above problem?!?

---

### Post by mssever on 2008-09-18
> **dkhajavi said:**
> At any rate the next day I booted up to check my mail and everyting was normal including my drums and all, entered my user/passord then nothing.  I have the brown Ubuntu background, a mouse pointer that moves but no desktop.  I can see that I have mouse and keyboard control and can get into the terminal.
Please post the results of going through the troubleshooting steps given in previous posts to this thread.

---

### Post by dkhajavi on 2008-09-20
Here is what I have come up with (I am a new convert so understand that I have limited Ubuntu skills).

The computer is post login hanging.  It is a soft hang in that I have mouse and keyboard control.  I can keystroke into the terminal.  I just found the 'smoking gun' I think.  I hit CTRL-ALT-F1 after the hang and this is what I saw:

Loading, please wait... 
kinit:* name_to_dev_t (/dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467) = sda5(8,5) 
kinit:* trying to resume from /dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467 
kinit:* No resume image, doing normal boot... 
Ubuntu 8.04.1 dkhajavi-DellM65 tty1 
dkhajavi-DellM65 login: 

So to my inexperienced eyes that is the hanging file?  Can you guys help to fix this?

---

### Post by mssever on 2008-09-20
> **dkhajavi said:**
> Loading, please wait... 
kinit:* name_to_dev_t (/dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467) = sda5(8,5) 
kinit:* trying to resume from /dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467 
kinit:* No resume image, doing normal boot... 
Ubuntu 8.04.1 dkhajavi-DellM65 tty1 
dkhajavi-DellM65 login: 

So to my inexperienced eyes that is the hanging file?  Can you guys help to fix this?
Nothing wrong there. Those messages are from early in the boot process when the system is deciding whether to resume from hibernation or boot normally.

As instructed above, from the login screen hit F10 and choose Sessions > Failsafe terminal, then log in. You should see a terminal window. In that window, type ```
gnome-session &
```You should get some error messages. Post them here.

---

### Post by dkhajavi on 2008-09-20
Thanks for your help...

I did as you instructed and after 'gnome-session &'  I get:

[1] 5943
The program 'gnome-session' is currently not installed.  You can get it by typing: sudo apt-get install gnome session
bash: gnome-session: command not found

When I hit sudo apt-get install gnome-session I get could not resolve 'archive.ubutu.com' errors and Failed to fetch errors.  I assume this is becasue I am not connected to the internet since I need to use the wireless where I am.

Is there anything else I can do?

---

### Post by mssever on 2008-09-20
> **dkhajavi said:**
> Is there anything else I can do?
Yes, you've made good progress. Apparently you managed to uninstall at least one critical package--maybe more.

Let's set you up with a temporary environment from the failsafe terminal session by launching some of the programs gnome-session is supposed to launch. Note that if you close the failsafe terminal window, you'll be logged out immediately. Run these commands one at a time. If they fail, note the failure and move on. If the failure is because of a missing package, you know what to do. Otherwise, post the message.
```
metacity &
gnome-panel &
gnome-settings-daemon &
# Use this next command only if you don't have wireless by this point
nm-applet &
```If you get an error about dbus, do ```
sudo /etc/init.d/dbus restart
```then retry whatever failed.

Now, you should be able to get on wireless. I recomment that you make sure the package ubuntu-desktop is installed, as it's possible that a bunch of other stuff could have ended up uninstalled as well, and ubuntu-desktop should get all the default stuff via dependencies.

---

### Post by dkhajavi on 2008-09-28
Thank you for everyones help.  I ended up waiting until I got back from my trip and with the Ubuntu 8.04 CD was able to reinstall without formating and was able to import all my settings.  This took me all of 20 mins and everything is back up and running.  I did not lose anything and all my settings are as they were.  From now on I will travel with my CD just in case.  

I will try to reinstall the power management software again which I feel was the start of my problems and see what happens.  If that does not work I will report my issues with that to better the community.  I will mark this issue as SOLVED...

---

