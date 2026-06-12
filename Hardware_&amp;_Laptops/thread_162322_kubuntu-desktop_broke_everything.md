---
title: "kubuntu-desktop broke everything"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by adam.mech09 on 2006-04-18
Hi

Installed kubuntu-desktop with apt-get install kubuntu-desktop.  When I restarted, I got the login screen, tried to log into KDE and nothing.  A few error mesages flashed, and then it booted me back to the login screen.  I tried gnome to see if that still worked, and the same type of messages appeared, and again kicked me back to the login screen.

I can go ctrl-alt-f1 and get a terminal, but I dont know where to start.

KDE isnt as important to me as my files, so I can ditch it if i have to.  

What should I do?

---

### Post by aysiu on 2006-04-18
A few things...

1. Do you know if KDM or GDM is in charge of your login screen? If KDM is, you may want to try ```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm restart
``` If GDM is in charge, try the other way around.

2. Another tactic--one that's less likely to be successful--is [uninstall kubuntu-desktop along with all the packages that came with it](http://www.ubuntuforums.org/showthread.php?t=96048). I don't think this'll work, since breakage usually doesn't get fixed by removing what broke it. May be worth a shot, though.

3. In terms of recovering files, there are ways to do this through the command-line. What do you have for backup? CDs? Floppies? An iPod? An external USB drive? DVDs?

---

### Post by adam.mech09 on 2006-04-19
Thanks

I have an external usb hard drive, formatted as FAT, so i can just dump my home folder there, but i'd really like to not have to go back through and re-configure all of the things i've done (it's a laptop....Ibm, so most things worked out of the box, but a few things needed tweaking".

I read over the other thread, but i think you're right about the whole removing-the-cause-doesnt-fix-the-problem.

I believe GDM is in charge, as it was regular ubuntu with kubuntu-desktop added, and when prompted i picked gdm....

any ideas other than copying and reinstalling?

---

### Post by Tom Tiger on 2006-04-21
Mm.... well I got another idea,  if you have the live cd of Ubuntu handy (or Knoppix for that matter) load it in, mount your usb drive and your harddrive and rescue your data.
after that, clean install,  put back your homedir.....

I know.... it sounds easy....  but it is easier than you think :-k

Sometimes I find it easier to simply wipe a drive, put a clean install on it and just put back a home dir..... (these are usually the days that I'm lazy and don't want to troubleshoot)

---

### Post by .t. on 2006-04-22
Put up your /var/log/Xorg.0.log, if you can. Also, see if you can get into GNOME from your GDM login screen. It's in the options menu (at least in Dapper); perhaps it is in the Session menu.

---

### Post by adam.mech09 on 2006-04-23
Hi

Umm...I cant put up my /var/log/Xorg.0.log file...or at least i dont know how i'd do it from the command line.  I'd like to get this figured out, as it seems like a pretty common thing to do  (installing kubuntu-desktop) and i dont think it shoud have screwed things up....I'm hoping it wasnt something else i did.  Any ideas?

Regarding the live CD image, that sounds like it'd work.  I'll give that a try.

---

### Post by Basho on 2006-04-23
Either display manager will run either desktop. I've been running KDE on GDM for a long time, though I do find glitches that something in me wants to blame on GDM (right or wrong). You might want to switch to KDM.

Open a terminal and type:

<CODE>sudo dpkg-reconfigure kdm</CODE>

It'll ask you whether or not you want to use KDM or GDM as your default display manager. Choose the other one (KDM, if you're sure that you're using GDM) and restart the computer.

Does it work now?

It's easy to switch back if everything's now broken:

<CODE>sudo dpkg-reconfigure gdm</CODE>

---

