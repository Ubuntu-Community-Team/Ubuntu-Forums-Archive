---
title: "Error: There already appears to be an X server running on display :0."
date: 2004-12-19
forum: General Help
---

### Post by nder on 2004-12-19
Whenever Ubunbtu attempts to launch XServer i get this error: 

"There already appears to be an X server running on display :0." 

And it asks if it sould try restarting X or sugesting using a different console.  If I tell it to restart, same error.  What happens is that a black X comes in the middle of the screen, and when I move the mouse it dies and I get the error.

I found a user with a similar error, except his was on a new install and was fixed by installing GDM.  I have been running Ubuntu for a few days (after a clean install) when I got this error.

Before the error I has installed mail-notification, firefox-1.0 (from the Hoary reps, I changed back the sources list after), mozilla-mplayer, and the video codecs.  MPlayer didnt work (I'm using a celeron processor) and xine died when I tried to view a quicktime movie in firefox.  That about what I was doing the day and night before i started having the XServer problem.

I am able to kill the X server process and startx manually and it works ok, but returns me to the console on log-out from Gnome.

I have tried purging my recent installs.  I have also re-installed gdm.  Nothing has worked so far.

I have attached my XFree86 logs to this post.

Thanks for the help.

---

### Post by clparker on 2004-12-19
It's the damned Hoary Reps, I know for a fact it is. I had to reinstall ubuntu, but word on the street says you can fix it by reinstalling X server or another.  by pressing CTrl + Alt + F1 you can get to  a text login, and once you login you should try, 
 
 apt-get remove xserver-xorg
 apt-get install xserver-xfree86
 
 you may have to tye sudo before those. Lemme know if that fixes it.

---

### Post by nder on 2004-12-19
Hmm, I didnt think it would update xserver if I only told it to get firefox.  I will see if your suggestion works.

---

### Post by clparker on 2004-12-19
I know it sounds stupid, but you would be suprised what happens when you tell it just get firefox. Read around, other have had the problem your talking about just after downloading the hoary repositories...you hvae an ATI card? that may be part of it...

---

### Post by nder on 2004-12-19
[QUOTE=clparker]I know it sounds stupid, but you would be suprised what happens when you tell it just get firefox. Read around, other have had the problem your talking about just after downloading the hoary repositories...you hvae an ATI card? that may be part of it...[/QUOTE]
 I've read about problems associated with mixing Hoary and Warty packages, but I really wanted Firefox 1.0 and didnt want to do the manual install.  But I have been using firefox for days and did many re-installs in between.  So I doubt that its firefox thats the culprit.  I do however suspect mail-notification.  But I have noting more than my suspicions.  I purged it, but that wont undo any damages.

Well, it turns out xorg wasn't installed (whew) and the reinstall of xserver didnt fix the problem.

---

### Post by Averatec5400 on 2004-12-19
[QUOTE=nder]I've read about problems associated with mixing Hoary and Warty packages, but I really wanted Firefox 1.0 and didnt want to do the manual install.  But I have been using firefox for days and did many re-installs in between.  So I doubt that its firefox thats the culprit.  I do however suspect mail-notification.  But I have noting more than my suspicions.  I purged it, but that wont undo any damages.

Well, it turns out xorg wasn't installed (whew) and the reinstall of xserver didnt fix the problem.[/QUOTE]
 this is slightly off topic, but the backports project is nice, and much "safer"

---

### Post by nder on 2004-12-19
I found the backports projects after going ahead with the Hoary install.  I really don't want to go back and re-install Ubuntu (thats too Windows like, brrr).  But i'm running out of options...

---

### Post by clparker on 2004-12-20
It's hard, I had the same problem, never could fix it, All i know is when i edited my sources file and updated then installed firefox, something hosed my x-server, I had to reinstall, which sucks. Try Alt + ctrl + F1 to login, you can use Crtl + alt + backspace to kill the xserver that is running, and typing 'startx' once logged in would force it to run xserver again i think, all i know is at some point i gave up and reinstalled.

---

### Post by taygan on 2004-12-20
I had the SAME problem installing firestarter from hoary into warty..  I figured if I wanted to run hoary files I should just dist-upgrade to hoary..  changed my /etc/apt/sources.list to say warty everywhere is said hoary, ran a sudo apt-get update then sudo apt-get dist-upgrade and you know what, IT WORKS!  (after 508MB of downloads)

only thing is I had ubuntu-dektop metapackage uninstalled, so I'm still running xfree instead of xorg and everything is running great .. kernel 2.6.9 with xfree nv drivers from ubuntu!

---

### Post by EdCrypt on 2004-12-20
[I had the same problem...](http://ubuntuforums.org/showthread.php?t=7903)

---

### Post by tavon on 2004-12-21
I'm replying to get this post to the top.

I'm experiencing the same problem and I'd like someone to take a look at this... :sad:

---

### Post by bob k on 2004-12-21
It looks like one of the Horay lib dependencys is tying start Xorg after Xfree has started or vice versa. Thats some tough code to follow at that level. Basically interrupt and signal service routines.

---

### Post by tavon on 2004-12-22
hmm....

So is the only way to fix this to upgrade to hoary or reinstall warty?

Thanks for the reply

---

### Post by nder on 2004-12-22
I tried upgrading to Hoary and it didnt work.  So I just did a fresh installation.  I reinstalled everything I had before except Firefox from Hoary (I used the backport).  I haven't reinstalled mail notification, I'm using a Firefox plugin instead.  I might try it again later cuz I doubt its the culprit.

---

### Post by techn9ne on 2004-12-23
I'm having the same problem when I updated to firefox 1.0 . Still working on solution.

---

### Post by jlbrt on 2004-12-29
I fixed the problem by installing **xserver-xorg**, **gdm** and their dependencies from hoary.

Most people should use [warty backports](http://ubuntu-bp.sourceforge.net/) when possible. If using hoary is necessary, one should try [pinning](http://www.ubuntulinux.org/wiki/PinningHowto) it.

---

### Post by xleon on 2004-12-29
I'm having the same problem right now. It has nothing to do with Firefox for me as I've not  upgraded the default install.

I installed PHP4 and a few other apps. Switched off and on again and get the exact same message,

---

### Post by xleon on 2004-12-29
The other thread suggested...

"sudo apt-get install gdm"

... and I can confirm this fixed it for me.

---

### Post by somekool on 2007-12-29
check what runlevel you are running.

```
somekool@somekool-laptop:/etc/init.d$ runlevel
N 2
somekool@somekool-laptop:/etc/init.d$
```

check corresponding init script folder
```

somekool@somekool-laptop:/etc/init.d$ cd /etc/rc2.d/
somekool@somekool-laptop:/etc/rc2.d$ ls
README                       S11klogd   S20apmd           S20powernowd     S30gdm      S98usplash
S05vbesave                   S12dbus    S20apport         S20rsync         S50ntp      S99acpi-support
S10acpid                     S12hal     S20hotkey-setup   S22consolekit    S89anacron  S99laptop-mode
S10powernowd.early           S13kdm     S20kde-guidance   S24avahi-daemon  S89atd      S99rc.local
S10sysklogd                  S16ssh     S20makedev        S24dhcdbd        S89cron     S99rmnologin
S10xserver-xorg-input-wacom  S19cupsys  S20nvidia-kernel  S25bluetooth     S91apache2  S99stop-readahead
somekool@somekool-laptop:/etc/rc2.d$
```

check in this list if you cannot find KDM and GDM ... my guess is that you have both in this list. if so, those files are symlinks, just remove or move away one of the two.

I think people who got this problem is because they install Ubuntu and then did apt-get install kubuntu-desktop or vice-versa.

welcome to linux

---

### Post by synistics on 2008-01-21
HELP!!!!!!

I am having this same problem, but I have not installed anything new.  I set up 7.10 and have been working on it for 2 weeks.  The last thing I changed was a CSS file.  I have been refusing to update in fear of something going wrong and the loss of all my work.

Is there anything that can be done to fix this?  I have done the remove xserver, found out it was not there, did the install gdm, newest version.

HELP!!!!!!

---

### Post by synistics on 2008-01-21
Answer for my own post.  Went IRC and asked the question and the solution is

DO not select yes or no

control - alt- F2

either sign in as root or sudo

/etc/init.d/gdm stop  (if using sudo, put sudo in front os the command)

this will return you to the command promt

type startx   

go into admin/services and remove the check in the gdm box

the next time the machine boots you will need to login from the command prompt and startx manually, but it eliminates the need to re-install

thanks to dalnet/linux user Al-Ashtar for the help on this one.

---

