---
title: "can not boot in ubuntu 8.04"
date: 2008-11-23
forum: General Help
---

### Post by jack_the_lad on 2008-11-23
I installed Ubuntu 8.04 over old windows partition and now i have only one Ubuntu partition. When I install and reboot Ubuntu i can't boot again. Everything goes well until the login screen. My display just flickers and freezes. I tried to enter my user name and password to hear if i could log in but nothing happens. When i want to reinstall Ubuntu same thing happens. I can't reinstall because the screen blacks out. Then i put a Kubuntu 8.10 Live CD in and tried it without any changes on my computer. I have logged in to Kubuntu normally and then i pressed reboot and a message "Abort active sessions: Ubuntu: TTY Login VT1, TTY Login VT2.... TTY Login VT6" appeared. I clicked ok and then i ejected Kubuntu cd and tried to login to Ubuntu and i could. Now every time i want to boot to Ubuntu i have to run Kubuntu live cd and then reboot and then login to Ubuntu. Stupid.

If anyone knows how to fix this please help, it's really annoying.

Thanks

---

### Post by oaxacamatt1 on 2008-11-23
Hey Jack Lad,
It kind of sounds like a video driver problem.  Can you start up the LIVE CD in safe video mode?  What knid of card you have?  Look on the Ubuntu forum hardware section and see if your card is supported.  Check to see if your card is mentioned in the logs and has problems specifically.  I am no expert but that is what I would suggest based on the fact that you are getting screen flicker.

Hope that Helps,
MAtt

---

### Post by jack_the_lad on 2008-11-26
yes, i got ati graphics and i have been getting a message that my drivers are not downloaded because they are not authenticated. meanwhile my modem crushed so i don't have internet connection anymore and i'm doomed :D 
ubuntu depends too much about internet and i don't have a connection now. great

thanks a lot

---

### Post by oaxacamatt1 on 2008-11-28
Hey Jack,
If your modem s..t the bed then it slows things down but I have found that Ubuntu doesn't really depend on the internet any more or less than windows.  Thikn about it... verification the windows disk and SN are authentic, etc.

Anyway.  With your 'good' computer go to the ATI(now AMD) driver website and find the correct driver for you system.  Usually the drivers are very easy to install, unzip them and run a shell script of some sort.

As for the modem, that one might be different.  You'll have to figure out if it hardware or software related.  I always go back to my Live CD.  Start up the live CD in 'Safe mode' (I think it is F4 on the Ubuntu start-up window).  Then poke around to see if you can get it going that way.  If you can get it going then it seems like a software problem.  During that time you can also use a thumb drive of some sort and load you ATI graphics card driver too.

Let me know what happens, to see if I can help,
Matt

---

### Post by jack_the_lad on 2009-05-29
Meanwhile i uninstalled ubuntu and now i installed it again now and i have the same problem. I'm a proper ubuntu noob and i don't know how to do anything in terminal except copy/paste XD. i tried to repair broken packages in recovery mode but it seems to have a fetch problem of some sort and i dont know what it is. 

all i need to do is to install graphics driver for my bloody ATI card and i dont know how to do it in a terminal.

noob needs assistance 

cheers

---

### Post by spcwingo on 2009-05-29
EDIT:  Before editing xorg.conf remember to backup the original, like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Try this...after booting, when the screen goes black press CTRL+ALT+F1 that will drop you out to a terminal.  From there log in (you won't see any feedback when entering your password) and enter this command:

```
sudo nano /etc/X11/xorg.conf
```

This will open your xorg.conf in Nano as root.  Scroll down until you see:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

and enter this one line, so it looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

Then press CTRL+O (capital o, not zero) to save then CTRL+X to exit.  From there enter this command:

```
sudo /etc/init.d/gdm restart
```

This should at least get you into the GUI.  Just be aware that the desktop effects will not work with this driver.

---

### Post by jack_the_lad on 2009-05-30
yeah, it works. thanks a lot man.

---

### Post by spcwingo on 2009-05-30
Unless you upgraded xorg to the newer version, there should be something in the xorg.conf on Hardy.  Have you tried booting into recovery mode and choosing the xfix option?  That should at least reset the config of the x server to default.  After you do that select "continue normal boot" and see what it does.  If nothing, try rebooting into recovery mode again, drop to root shell and run this command:

```
apt-get install --reinstall xserver-xorg
```

Then exit the root shell by typing "exit", then try the "continue normal boot" option again and see if that does the job.

EDIT:  I just reread the post and see that you don't have internet connection, so that second part above about reinstalling the x server won't work.

---

### Post by jack_the_lad on 2009-10-22
hello again

i have 9.04 now and same problem. this is extremely annoying. when i install ubuntu and log in for the first time graphics works EXCELLENT. when i reboot it it still works EXCELLENT, but when i turn off and on my pc everything fails and i have to use vesa. can somebody help? i tried everything for past two days and i'm complete noob. i still have RADEON 9600PRO

---

### Post by jack_the_lad on 2009-10-23
anyone?

i heard that the new drivers for this kernel does not support my radeon 9600 card. is that true?

---

### Post by jack_the_lad on 2009-10-23
okay, i installed fglrx drivers and the screen was pretty scrambled then. so i had to uninstall it. so ati drivers don't work, fglrx drivers dont work either, lets go search for some more non-working drivers :p

---

### Post by izg on 2009-10-24
let me know if you get ati drivers to work. I updated 8.04, reinstalled and no luck.

thanks.

---

