---
title: "Please help crashed"
date: 2008-07-22
forum: General Help
---

### Post by namaster on 2008-07-22
[http://woodygates.com/2008/05/get-your-logitech-g5-mouse-to-work-in-ubuntu/](http://woodygates.com/2008/05/get-your-logitech-g5-mouse-to-work-in-ubuntu/)

I followed the tutorials and when i did ctrl alt backspace all and reloging again all crashed and hanged up.

I tried to remove the imwheel and startup script with rm .Xmodmap and still no go. 

I also got changed the xorg.cfg to the working one still no go. Can anyone help me to fix that? 

I can get login screen but and when i login in either xclient gnome anything doesnt work.

Tried recover mode to fix it and still no go.

Any more idea how to revert the tutorial changes?

---

### Post by DagMan on 2008-07-22
Have you tried removing imwheel package using apt and also did you check over your xorg.conf to make sure the old section is indeed what you now have, post it here for help if you're unsure.
try removing the .xmodmap file you created in your home directory (note the tutorial uses a lower case x and you did not btw), and moving /etc/X11/imwheel folder to a differant name.
Look in your home folder at .config/autostart for the entry that you made in the startup group and remove it if you recognise it.  It will have a .desktop extention, though starting a failsafe gnome should bypass the last bit.
From the sound of it, you just can't use your mouse.  you have graphics and a keyboard but the mouse doesn't work?

here's my mouse section of my xorg.conf if it helps
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

```
It's the same on two differant computers for me.


Edit:btw, to get this mouse working that you have, you have to make sure that it's showing up at event 2 as the guy had it in the tutorial.  It isn't going to necisarrily be the same for everyone.  Mine is the keyboard.  do this and not the lines that begin with a capital H if you want to give the tutorial more trys
> cat /proc/bus/input/devices

---

### Post by namaster on 2008-07-22
Thanks for the reply .. I already did tried to remove the imwheel before posting my first post ..but that even didnt solved

Using this
```

apt-get remove imwheel

```

I know that its in small case and hence i used sudo rm .xmodmap. 

I also replaced the xorg.conf as i had made a back up before using it. 

I can login but nothing happens. gnome and xclient both crashes. I can move my touchpad but the desktop is only light grey. Its like totally hanged up. I have no graphics and keyboard but only mouse that moves and i tried to use ctrl alt f1 to get the shell or root and it works. But anyidea how to get all back working?

Atm:
1. imwheel removed
2. xmodmap removed.
3. xorg.conf back to old working one.


I hope this clears up my question.. 

Thanks a lot for help.

---

### Post by DagMan on 2008-07-22
When you say you get a gray screen, is it the fine zig zag patterned screen or solid gray?  Also can you start gnome by going to the terminal at f1, stopping gdm, and doing
/usr/bin/startx /usr/bin/gnome-session
and if not, can you start it on another display, for example
/usr/bin/startx /usr/bin/gnome-session -- :1
which would put it at ctrl-alt-f8 usually.

---

### Post by namaster on 2008-07-23
Thanks for the help.. 

I am getting sometimes solid gray and sometimes i can see wallpaper but no applications or system or preference menus...

I have deleted imwhell, start up scripts, and all.. i have no idea whats going wrong now.. 

I have removed even almost all the things that i had changed and/or modified to original versions.. still no go. 

Any more idea how to solve this? or this cant be fixed?

---

### Post by namaster on 2008-07-23
well another odd thing i noticed.. i was able to login as root itself root user..and everything was working nice but as soon as i did left click on anything that things hang up.. like if i press OK on that thing and it hangs up.. 

So, is it something with my mouse left click messed up?

Edit: I just started again gnome normal session and it crashed asking for imwheel start up script.. i already removed it.. then why the hack it is asking again and hanging up? 

ls /home/username/.config/autostart

sudo rm  /home/username/.config/autostart/filename

Did to remove xmodmap startup script. But it asks for imwheel no where the hack it is stored?



Edit:

It gives me new error now:
```

/etc/gdm/Xsession: Beginning session setup...:2 Can't open /etc/X11/imwheel/startup.conf

```

---

### Post by DagMan on 2008-07-23
Edit: Just saw the error.  Something, most likely xorg.conf, is still looking for the imwheel driver.  try reinstalling it, purging it entirely, doing the autoclean thing, then doing the 
sudo dpkg-reconfigure -phigh xserver-xorg
as described below using the --purge option in the apt-get remove command.  If this doesn't get it anywhere closer to fixed, then can you post your xorg.conf

The thing that strikes me is that root user still has problems with the mouse, even if it's less of a problem than the normal user.  If the mouse was previously working fine then that's not expected except for the xorg.conf file, unless you made a change also to the root user's account using sudo or something :confused:  If not it sort of sounds like the first thing would... well actually would be to try another mouse, if it isn't the mouse itself, then it seems the first thing would be to look again at the xorg.conf file as it's something that effects both the root and normal user, and then from there take a more detailed look at what needs to be done for just the user in question.

Have you tried, and if not then making sure you have backups 0f various xorg.conf files youve had now, reconfiguring the file using 
sudo dpkg-reconfigure -phigh xserver-xorg
if not, and the problem is not the mouse itself, perhaps it can solve the problem for the root user and that part will be squared away.

btw, maybe you want to have a look in /root to see if you might have accidentally used sudo and put the .xmodmap file in the /root folder as well, if you haven't already.  If you find one, look at the contents of it to verify that it's actually one you want to delete.  I personally don't have that file in either /root or my user home folder.

Also, first have a good look around for any imwheel files like the imwheelrc mentioned in /etc/X11/imwheel and move them somewhere else.  It also can't hurt to reinstall imwheel and then remove it using --purge, hopefully deleting any config files, before trying to write a new xorg.conf file.
sudo apt-get install imwheel
sudo apt-get remove --purge imwheel
sudo apt-get autoclean

then look around for any files that might still linger, in
/etc/X11 /etc/*imwheel* /etc/*/*imwheel*
and check the contents of any .xmodmap file to see if it is the same one you added.  Also look inside the contents of any .xinitrc files in your home and root folders to see if there's any lines that are the same as the one you created as .xmodmap or any lines referancing that, and if so remove them.
I don't have an .xinitrc file on my machine.  I'm beginning to wonder, since I don't have some things like that, if they have moved since I last messed with it.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-another-backup
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by namaster on 2008-08-20
I did the way u told but still no success. Then adapted easy way format and reinstall.

---

### Post by dkhajavi on 2008-09-20
I have a similar issue:

Here is what I have come up with (I am a new convert so understand that I have limited Ubuntu skills).

The computer is post gnome login hanging.  It is a soft hang in that I have mouse and keyboard control.  I can keystroke into the terminal.  I just found the 'smoking gun' I think.  I hit CTRL-ALT-F1 after the hang and this is what I saw on the terminal screen:

Loading, please wait... 
kinit:  name_to_dev_t (/dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467) = sda5(8,5) 
kinit:  trying to resume from /dev/disc/by-uuid/51e2f1cb-52a1-4c80-b47b-238fcd73f467 
kinit:  No resume image, doing normal boot... 
Ubuntu 8.04.1 dkhajavi-DellM65 tty1 
dkhajavi-DellM65 login: 

So to my inexperienced eyes that is the hanging file?  Can you guys help to fix this?

---

### Post by dkhajavi on 2008-09-28
Just to give anybody reading this an solution:

I fixed this with the Ubuntu 8.04 CD.  I reinstalled without formating and using the 'import settings' function.  This took all of 20 mins and I am back to the way I was.  Everything is 100% now!  I will travel with the CD from here on out.  I am sure there is a more grassroots, diehard Linux terminal method to fix this but this also worked well for me.  For me this is SOLVED.

---

### Post by namaster on 2008-10-21
> **dkhajavi said:**
> Just to give anybody reading this an solution:

I fixed this with the Ubuntu 8.04 CD.  I reinstalled without formating and using the 'import settings' function.  This took all of 20 mins and I am back to the way I was.  Everything is 100% now!  I will travel with the CD from here on out.  I am sure there is a more grassroots, diehard Linux terminal method to fix this but this also worked well for me.  For me this is SOLVED.

Thanks for the update. People hardly post how they fix something. I did clean install pretty odd way since i am newbie. ;)

---

