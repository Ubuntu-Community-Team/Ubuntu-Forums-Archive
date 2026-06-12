---
title: "live usb ubuntu 10.04 won't boot on hp touchsmart tm2"
date: 2010-10-21
forum: Hardware
---

### Post by mafiaspidey on 2010-10-21
Hi,

I booted ubuntu 10.04 off a live usb on an HP touchsmart tm2. It takes me to first screen to select normal boot. I select normal boot. However, next thing I see is a cursor in the top left corner and grey screen. Two seconds later, the screen goes blank and thats it. nothing changes. Just a blank/off dark screen. 


What is the problem? Why can't ubuntu boot on my hp touchsmart tm2? I installed ubuntu on virtualbox on my win 7 and it works fine.


Also, no other live usb linux - fedora, or mint - get past the first select boot option screen. What is the problem?


thank you.

---

### Post by electricj on 2010-10-23
Are you sure that it isn't booting?  I recently tried a live usb (10.10) for my tm2, and it boots, but for some reason doesn't start the lcd backlight.  With a powerful flashlight, I can see some of the stuff on the screen, and click on things with the pen (I must admit I was surprised this worked out of the box) to open menus and suchlike, but I haven't yet figured out how to fire up the backlight so I can work sans torch.

---

### Post by M42 on 2010-10-23
> **electricj said:**
> Are you sure that it isn't booting?  I recently tried a live usb (10.10) for my tm2, and it boots, but for some reason doesn't start the lcd backlight.  With a powerful flashlight, I can see some of the stuff on the screen, and click on things with the pen (I must admit I was surprised this worked out of the box) to open menus and suchlike, but I haven't yet figured out how to fire up the backlight so I can work sans torch.

Try booting with an external monitor attached.  When I did I was able to get the lcd back.

---

### Post by Michael S Corigliano on 2010-10-24
I know how to fix this, I had the same problem. Believe it or not, you actually have to close the lid and reopen it (sometimes you have to do it twice) and it the screen will appear. Hope that helps you, I had the same problem in 10.04 and 10.10 and this fix worked for me with the HP Touchsmart Tm2 2050us.

---

### Post by electricj on 2010-10-24
> **Michael S Corigliano said:**
> I know how to fix this, I had the same problem. Believe it or not, you actually have to close the lid and reopen it (sometimes you have to do it twice) and it the screen will appear. Hope that helps you, I had the same problem in 10.04 and 10.10 and this fix worked for me with the HP Touchsmart Tm2 2050us.


Well, I feel sort of dumb for not trying that.  Worked for me, definitely easier than using a flashlight, or connecting to an external monitor every time.  Thanks!

---

### Post by mafiaspidey on 2010-10-24
**[COLOR="DeepSkyBlue"]_THAT WORKED! _[/COLOR]**


Thank you. Can't believe the solution was stupid like that.

---

### Post by mafiaspidey on 2010-10-27
Now,

Is there any solution for THIS solution? I am getting tired of opening and closing my computer screen everytime ubuntu starts. It's laughably stupid.

---

### Post by Michael S Corigliano on 2010-11-08
What I did to fix that issue was disable the ATI graphics (don't worry, the HP Touchsmart Tm2 has a hybrid graphics card, we're just going to disable the ATI part, the Intel part will still work with no issues). Here is how to do that:

1) Open a terminal
2) Type in "sudo nano /etc/rc.local"
3) Add "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" to the bottom
4) Press CTRL-X, hit Y, then hit enter
5) Then reboot (you can do this with the "sudo reboot" command via terminal)

This should work, if not then let me know and I will try and find another work-around.

---

### Post by Hamburglar03 on 2010-12-12
I also have a touchsmart tm2, and the opening/closing the lid fix works for me, but...

I have tried the vgaswitcharoo switch and it doesn't seem to remedy the problem.

Any suggestions?

---

### Post by electricj on 2011-05-17
well, it has been a long time, but I've got it sorted out on my laptop now.  

I found this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697514](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/697514)
which says that there is a problem with some bios stuff and the backlight gets set to zero when the OS is not windows.

I have moved my laptop over to Gentoo, but since this is a bios problem, it should work for any distro I would imagine.

Follow the directions here

[http://www.lesswatts.org/projects/acpi/overridingDSDT.php](http://www.lesswatts.org/projects/acpi/overridingDSDT.php)

to make the changes in the bug report (I just changed the place where it says Zero to say 0x06 and it worked fine).  You're on your own for compiling your custom kernel tho.  It might just be easier to wait for ye olde bugfix.

---

### Post by Cadeyrn on 2011-09-29
If you want to take advantage of your ATI add-on and would rather wait for that bugfix, I've found an excellent workaround:

[http://ubuntuforums.org/showthread.php?t=1464209](http://ubuntuforums.org/showthread.php?t=1464209)
> **soulspit said:**
> So, I don't know if this works on all machines, but there is apparently a list of shell scripts in /etc/acpi that do things like sleep or lock the computer as well as test out media buttons.  /etc/acpi/screenblank.sh is the script that turns off the screen, so I've set that to a hotkey and I'm all good!

You can set that screenblank.sh script to launch at startup and then just move your mouse around or press a key or something to wake the screen up--way easier and quicker than closing it and opening it twice, plus this solution doesn't shorten the life of the monitor. Note that if you're running GNOME rather than KDE, you won't have a "Pre-Startup" option, so you'll have to login without a backlight and THEN move the mouse around.

---

### Post by lourayr on 2012-12-08
> **electricj said:**
> Are you sure that it isn't booting?  I recently tried a live usb (10.10) for my tm2, and it boots, but for some reason doesn't start the lcd backlight.  With a powerful flashlight, I can see some of the stuff on the screen, and click on things with the pen (I must admit I was surprised this worked out of the box) to open menus and suchlike, but I haven't yet figured out how to fire up the backlight so I can work sans torch.

YES!!  I read this, touched the flashlight all the way to the screen and there it was.  So I connected a monitor and was good to go!  Best way ever to back up files on a broken copy of Win 7 before re-installing!  I've left my laptop dead for 8 months until I finally got around to doing this!

---

