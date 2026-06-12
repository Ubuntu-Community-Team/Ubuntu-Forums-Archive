---
title: "Nothing but backlight at boot"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by Dlobster on 2009-09-04
I just installed Ubunto on my dell inspiron 1100 and am having issues. It hangs on the boot up. I thought it was just from the original install, but it happened again next night.
No other OS, just ubunto 9.04 on a fresh wiped 10 gig drive.

First attempt at boot I get the text and then nothing but backlight
Hard powered down and restarted and got the password dialog. Things seemed to work fine.

Installed updates and rebooted


Couldn't get anywhere after the updates until I started in safe mode and choose an option to fix graphic problem. I was then able to resume normal boot and was able to start ok. Any ideas for a more permanant fix? Is there a different version which might be better for the machine? or am I just going to need to do a safe start every time I boot?



I am very new to Linux



Dan

---

### Post by QIII on 2009-09-05
From the specs, I'd have to say that if you are using Jaunty then you are running into issues with your Intel video chipset.

Check this out:  [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Scroll down to the section that reads

**Performance regressions on Intel graphics cards**

 
If you need help understanding how to edit your xorg.conf, let us know.

These issues have been largely addressed in Karmic, which will be released next month.

If you are not comfortable modifying a critical system file then for the time being it might be worth installing 8.10 and waiting for 9.10.

---

### Post by Dlobster on 2009-09-05
Thanks QII, 
I like an adventure and learning new things.
I would like help  understanding how to edit my xorg.con
Where do I start?
What do I need to what out for?
Dan

---

### Post by QIII on 2009-09-06
At the GRUB display (the TTY you get at the beginning before the system tries to boot), down arrow to "Recovery Mode".  You should see a lot of text scrolling by (don't worry about it) and then get a blue and red menu.  Down arrow to either "netroot" or "root".

You will first want to back up your current xorg.conf by typing 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.something
```where "something" is just some text that you will use to recognize the file later.  A lot of people just use "bak".  Jot the whole thing down in case you need to restore the file to its original state.  (Remember that in the *nix world, everything is case-sensitive!)

If sudo doesn't work from that prompt, just don't type it.  If it does work, you will be prompted for your password.  All you need to do is type in your login password.  You will not see any characters, so don't think something is wrong when you enter your password.

You can begin editing by typing

```
sudo nano /etc/X11/xorg.conf
```

Unfortunately, at this point you will not be able to use a nicer text editor like gedit.

From there, follow the instructions at the URL I gave you.

If that doesn't work, just come back to this thread and state that.  Someone will eventually come along and tell you how to restore the original file (basically the same as the first command I gave you with the file names switched) and we (or whoever comes on) can try something else.

---

### Post by Dlobster on 2009-09-06
That seemed to do the trick. :D
Thanks
Dan

---

