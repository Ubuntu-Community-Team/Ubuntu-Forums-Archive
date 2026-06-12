---
title: "Hardy on Thinkpad X22"
date: 2008-04-25
forum: Hardware
---

### Post by David_G_D on 2008-04-25
Overall, I'm very impressed with Hardy.

I'm having a few issues on my Thinkpad X22:

-Suspend to ram - backlight stays on, and machine doesn't come back from sleep.  When waking up, the screen goes black and stays black.

-Suspend to disk - sometimes works correctly, sometimes crashes when resuming.  I can't figure out the pattern yet.

-When computer is idle, the display fades to black (which looks really cool) but the display's backlight stays on.

On previous versions of ubuntu I had issues with the stock system, but everything was perfect after switching to the vesa video driver.  On this one I can't figure out how to switch to the vesa driver.

Where should I begin to try to solve these problems?  Suspend to disk is the one I would most like to get working, but it would be great if all of these issues could be resolved.

Thanks!

-David

---

### Post by dstew on 2008-04-25
> I can't figure out how to switch to the vesa driverI don't have any direct experience with Hardy, but to change to the vesa display driver, you can do```
sudo dpkg-reconfigure xserver-xorg
```and chose the vesa driver when you get to the part about the display. Choose as highest resolution the resolution you actually use.

---

### Post by David_G_D on 2008-04-25
Thanks for the quick reply.

I tried "sudo dpkg-reconfigure xserver-xorg", but it didn't ask any questions about displays or display drivers as it used to in Gutsy.  It only asked about the keyboard.

---

### Post by dstew on 2008-04-25
Try this:```
gksudo displayconfig-gtk
```

---

### Post by David_G_D on 2008-04-25
Thanks dstew.  That worked for changing to the VESA driver.  Is there any terminal program to do that job, just in case X is broken?

Now that I'm using the VESA driver the machine seems to resume from Hibernate and Suspend (tried each once).  The display's backlight still stays on during suspend, though.  Do you have any idea how to approach that one?

Thanks again,
David

---

### Post by dstew on 2008-04-26
Sorry, I don't know what the command line program is to reconfigure your video display. If you lose it, you can use **vesa=force** as a kernel parameter. You add it to the kernel line from the grub menu, by pressing 'e' to enter the edit mode. I don't know about the backlight though.

---

