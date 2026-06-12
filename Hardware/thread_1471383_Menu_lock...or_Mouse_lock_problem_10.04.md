---
title: "Menu lock...or Mouse lock problem 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by duke.tim on 2010-05-03
<<May 1, 2011>>This problem no longer exists in Ubuntu 11.04

Mouse and BASIC GUI should work on ANY major OS. anyway no more ranting....

I'm using a hp DV6-1030us laptop
ubuntu 10.04 64bit
syn/ps2 Synaptics Touchpad
Kernel 2.6.32-21 Generic x86_64
Gnome 2.3.0

So The screen will randomly, become partialy responsive. windows and pannels (including Applicaitions menu) will light up but clicking or trying to access them via keyboard will not work. no clue what is causing this didn't see anything in the logs (anything I should look for?) 

So the fix is to enter into tty# (where # is 1-6 {ctrl + alt + #}) and back to the desktop (tty7?) this works well for getting menu's back but now...the mouse dosen't work -_- :@ . I can still navigate with the keyboard but since not all applications have keyboard control this is troublesome. and I can get the mouse to work for a split second on switching from tty# to tty7 then everything locks up again. (edit) It isn't fixed after a reboot...But I can sometimes fix it by rebooting/logging in and then pressing the touchpad keylock switching to tty# and then unlocking the touchpad and switching back to my desktop {ctrl + alt + 7}.

So there are 2 questions
#1 Any Ideas on how to fix this
#2 what information should I submit to launchpad
     I have checked launchpad for similar bug and found some
     but they don't seem to be quite the same.

---

### Post by duke.tim on 2010-05-06
Well it seems to be related to pressing the touchpad lock. maybe i'll wait for some updates and see if that fixes it.

---

### Post by cmcanulty on 2010-05-07
MY mouse and trackpad freeze also,requires restart this started happening once  a day or so after Lucid upgrade. Sometimes space bar freezes also.

---

### Post by duke.tim on 2010-05-13
Okay it's been quite awhile since I posted this...um I've had this problem before any updates, none of them have fixed it I can reproduce the error by pressing the touchpad lock. After I hit the touchpad lock  the menu's freeze and if i switch to another tty I then get the menu's back without touch pad control.

---

### Post by duke.tim on 2010-05-16
bump

---

### Post by cmcanulty on 2010-05-17
Mine always disappears after hibernate, and occasionally other times. Touchpad and mouse gone . Gateway notebook model 7510GX. I've tried all the key combos suggested. Only restart works.

---

### Post by digital-daniel on 2010-05-17
same problem here with DV6 1270el - when I reboot it's fine. If I switch the touch pad off before re booting it's not a problem, it's only if I want to change settings during a session. I also have the same problem if I change any mouse preferences.

---

### Post by cmcanulty on 2010-05-17
This bug needs to be fixed.Mine was fine until Lucid, I haven't changed any settings.

---

### Post by duke.tim on 2010-05-18
The mouse default settings can cause problems for some people just something for people to check is go into > System -->Preference-->Mouse
Touchpad and unmark "disable touchpad while typing"
Mark "Enable mouse clicks with touchpad"
personally I would disable anything in Accessibility unless you either need it or want it.

If you have click issues or anything like that(or just want more control over your touchpad mouse) I would in
System-->Administration-->synaptics package manager
mark > gpointing-device-settings look the settings over.

The issue as far as I can find is not a settings issue but I'm starting to guess is a driver issue.

---

### Post by duke.tim on 2010-05-18
cmcanulty check out these launchpad bugs they might help you find a fix. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867)
[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg47874.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg47874.html)

---

### Post by cmcanulty on 2010-05-18
Unfortunately my mouse settings were already as you suggested.

---

### Post by cmcanulty on 2010-05-18
I have  gpointing-device-settings installed but how do I access the settings file?

---

### Post by duke.tim on 2010-05-25
You can access gpointing-device-settings graphically by going to ```
System->Preferences->Pointing Devices
```or you can access it by the gnome-terminal (bash,commandline, etc...) by entering in ```
gpointing-device-settings
``` No sudo should be needed.
 If you are looking for a text configuration file I'm not sure where it is(if it exsists)

---

### Post by cmcanulty on 2010-05-26
Well there is no setting for the mouse not working after hibernate I need something like telling the system to not disable mouse after hibernate,  a bug that shouldn't happen

---

### Post by Woodwa on 2010-06-07
I'm having the same problem on a lucid desktop! 

I have used 2.6.32 2.6.33 and 2.6.34

my problem is intermittent and usually is fixed by pressing the context key on the keyboard(ie the key next to the windows key)

its driving me crazy..

---

### Post by duke.tim on 2011-05-01
This problem has been resolved in the new version of ubuntu 11.04

---

