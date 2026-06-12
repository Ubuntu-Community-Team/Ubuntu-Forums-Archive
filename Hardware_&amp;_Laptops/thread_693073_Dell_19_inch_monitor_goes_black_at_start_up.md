---
title: "Dell 19 inch monitor goes black at start up"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by mildlyhotpeppers on 2008-02-10
I had Ubuntu (Gutsy) working fine with an old monitor...and then I switched to a 19 inch Dell monitor. At that time, I also managed to screw up my xorg.conf file (which is another problem for me).

At the moment, I can turn on my computer, I see the BIOS and everything, grub comes up, I pick the first Ubuntu choice, I see the Ubuntu loader...and then the screen goes black. The power button or the monitor (which lights up when on) is now flashing.

This was the situation a week ago, and then today I tried to show that problem with my friend, and as luck would have it everything worked fine that one time I decided to show my friend. As soon as I restarted the computer, the same black screen came back again.

I've tried using the Ubuntu Live CD, but the black screen appears for that too. Windows XP, however, shows up fine. Since I can't get into the Ubuntu Live CD, I can't reformat my linux partition either.

): Help anyone? (My video card is a not-so-new one, an ATI Saphire Radeon x550.)

---

### Post by pdub on 2008-02-10
Try leaving the system booting for a while, it may just be your splash screen is not set for the proper resolution. If the gui login comes up after a few minutes then you just need to edit your usplash.conf file.

```
sudo cp /etc/usplash.conf /etc/usplash.conf.bak

sudo nano /etc/usplash.conf
```

then locate the section that looks like this:


```
# Usplash configuration file
xres=1024
yres=768
```

And change the xres and yres to match your monitior. Then reboot.

---

### Post by mildlyhotpeppers on 2008-02-10
It's been an hour...no luck. ):

---

### Post by pdub on 2008-02-10
Does it start in low res mode?

Are you able to boot into recovery mode?

---

### Post by mildlyhotpeppers on 2008-02-11
It doesn't look like low-res mode...and how do I boot into recovery mode?

---

### Post by pdub on 2008-02-11
You should see an option for recovery mode when GRUB loads on initial start up.

Can you put the old monitor back on?

What happens if you hit ctrl+alt+F1 after allowing the system to boot? This should give you a text mode login. Then try this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


```
sudo dpkg-reconfigure xserver-xorg
```

Then reboot.

Otherwise, you can boot with the Live CD and then have a look at your usplash.conf (/etc/uspalsh.conf) and your xorg.conf (/etc/X11/xorg.conf). You will have to locate these files on the appropriate disk.

---

### Post by mildlyhotpeppers on 2008-02-13
Pdub you are my hero. I started in recovery mode, and the screen went black the first time. I tried again, and it survived the second time. I changed the usplash settings from 1024 by 768 or something like that to 1280 by 1024 - it works fine now.

:D

Now to go back and fix my screwed up xorg.conf...

---

### Post by pdub on 2008-02-13
Cool, glad to hear it.

Post your xorg.conf file and your desired resolution, i.e. 1280x1024.

**Also remember to mark the thread as solved.**

---

### Post by mildlyhotpeppers on 2008-02-13
The xorg.conf issue is in this thread: [http://ubuntuforums.org/showthread.php?t=686620](http://ubuntuforums.org/showthread.php?t=686620)

---

