---
title: "URGENT: kernel upgrade broken! :S"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by fazza on 2009-04-08
I've had issues with my kernel recently - it had 27-11, -12 and -14 installed. Every time I installed anything, it always tried to regenerate the boot image.
Anyway, I tried to fix it... by removing all the images, headers and kernels that were extra. Didn't like that. So i forced it to stay on version 27-11. Didn't like that either. Now, I've only got the 27-14 headers installed, because when I install _anything_ else, it says it cannot configure it - doesn't matter which version.
Now I'm afraid that even if I install the rest of the 27-14 parts, that my computer won't turn back on if I reboot it. My computer's currently sat here running on -12, not -14 which was newer, making me think that maybe -14 isn't bootable atm. I can't install any of the others cos they fail in exactly the same way.

At the very least, can someone tell me if it's safe to turn my pc off please?

Thank you very much

---

### Post by fazza on 2009-04-08
sorry but... bump. I really have to sort this out :S obviously

---

### Post by drs305 on 2009-04-08
> **fazza said:**
> At the very least, can someone tell me if it's safe to turn my pc off please?


Here are a couple of things you should probably do before you turn off the system:

Check the kernel you are currently running:
```
uname -r
```

Check the default kernel in grub. If you aren't sure how to do this, install StartUp-Manager:
```
sudo apt-get install startupmanager
gksu startupmanager
```
If you need help with this, there is a link in my signature line to using SUM.

In the "boot options" tab make sure the default OS is the same as the kernel you are currently running.
Also in StartUp-Manage, make sure to set the timeout to greater than 0 so that you can access the grub menu manually during boot should you run into problems the next time.

If you haven't messed with the kernel you currently have installed you should be able to get your system back on. The above steps will help if you have problems.

If you have critical data that you might need in a hurry, back it up before turning off your machine.

---

### Post by fazza on 2009-04-09
ok thanks well I've done that... got 27-12 running. That one's not installed... so i'm gonna have another go now. Neither 12 nor 13 were in the force package list, so I'll have to try it manually and lock it if it works.

oh and I set default kernel to last used, which was (obviously) 12.

Cheers

---

### Post by fazza on 2009-04-09
I removed everything kernel/header/image related, and started again, installing the different parts bit by bit. Well, the headers installed fine. But then I tried to install the image and the backport-modules. And now it returns this:
```
E: linux-image-2.6.27-12-generic: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.27-12-generic: dependency problems - leaving unconfigured
```
This is what it did every time before, and now I'm only trying to install the one that's running! I've hunted through the dependencies and all seems fine :S

---

### Post by fazza on 2009-04-09
bumpedy bump

---

### Post by fazza on 2009-04-09
bump? is this working?

---

### Post by fazza on 2009-04-09
hehe bump again cos no one on the uk mailing list seems to know atm...
(not getting at anyone btw :p)

---

### Post by drs305 on 2009-04-09
Ok, try this. It will rename the linux-image postinst file that is giving you the error message (and create a new empty one if necessary). If it doesn't do anything, you can put it back.

Rename the postinst file:
```

sudo mv /var/lib/dpkg/info/linux-image-2.6.27-12-generic.postinst /home/*[COLOR="Red"]yourusername[/COLOR]*/Desktop/linux-image-2.6.27-12-generic.postinst

```
Then try running:
```

sudo apt-get update
sudo apt-get install linux-image

```

If you get an error message about a missing postinst file, create one:
```

sudo touch /var/lib/dpkg/info/linux-image-2.6.27-12-generic.postinst

```
Try installing the linux-image again.

If unsuccessful, but it back the way it was originally:
```

sudo mv /home/*[COLOR="Red"]yourusername[/COLOR]*/Desktop/linux-image-2.6.27-12-generic.postinst /var/lib/dpkg/info/linux-image-2.6.27-12-generic.postinst

```

---

### Post by fazza on 2009-04-09
ah ok thanks well that looks like it should work... except I don't have that file in my /var/lib/dpkg. I haven't got any images in there at all... is that right? Shall I try the commands you gave me, replacing /var/lib/dpkg with /boot or something?

thanks :)

---

### Post by drs305 on 2009-04-09
I had the right idea but not quite the full path. Try running it again with the "info" path added to the previous corrected post.

---

### Post by fazza on 2009-04-09
well that's weird... the files definitely there, I checked with ls linux-image* and several came up. But when I run your command, for some weird reason it complains...
```
mv: cannot move `/var/lib/dpkg/info/linux-image-2.6.27-12-generic.postinst' to `/home/yourusername/Desktop/': No such file or directory
```
anything else?

[EDIT] sorry I'm being really stupid
it says 'yourusername' in it.
duh

thanks

---

### Post by fazza on 2009-04-09
thank you A LOT, you're great :D everything seems to be fine now, just got to try out the graphics card :)

---

### Post by fazza on 2009-04-09
gahh well the kernel bit is fine now... except that neither startup-manager nor update-grub will see the new kernel! So when I boot, it fails, so I have to edit the boot commands myself. Only as simple as changing the -12 to -14 (I left it on v14).
How can I fix this please? I ran update-grub and rebooted.. nothing changed :S

cheers :)

---

### Post by drs305 on 2009-04-09
> **fazza said:**
> How can I fix this please? I ran update-grub and rebooted.. nothing changed :S
cheers :)

I recommend installing and running StartUp-Manager. I will edit grub for you via gui rather than opening it and manually editing it.. On the Boot tab is a section for selecting the kernel to boot. It will look at your system and should recognize which ones are available.

The first installs, the second runs it.
```

sudo apt-get install startupmanager
gksudo startupmanager

```

There is a link to using StartUp-Manager in my signature line.

---

### Post by fazza on 2009-04-09
yeah I've already got that installed and it hasn't found it :/ not sure why cos it's always had them in there before.
??

---

### Post by drs305 on 2009-04-09
I forgot you mentioned startupmanager already. 

To backup and then edit menu.lst:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst

```
The entries you want to change will be near the bottom of the file, probably the first entry with the line beginning with "title"


If you need help, you can post your menu.lst as well as which kernels you have installed:
```

cat /boot/grub/menu.lst
ls -la /boot
sudo blkid

```

I'm about to sign off, but check to see from the above commands that you have a listing for "vmlinuz-2.6.27..." and an "initrd.img-2.6.27..." in /boot. 

Check that the entry in menu.lst  references the correct UUID from your system or /boot partition, and as you mentioned make sure grub references the correct kernel.

---

### Post by fazza on 2009-04-09
ok cheers, I thought it would probably be something like that, but didn't want to risk it seeing as neither of the above apps saw it...
I now only have 27-14 installed, but it's running fine atm. Now I shall fight with my stupid nvidia graphics driver that worked yesterday and not today :p

thanks a lot for your help :)

---

