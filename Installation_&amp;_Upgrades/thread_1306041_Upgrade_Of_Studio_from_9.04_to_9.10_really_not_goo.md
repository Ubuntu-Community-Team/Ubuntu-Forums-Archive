---
title: "Upgrade Of Studio from 9.04 to 9.10 really not good...."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by maaarcooose on 2009-10-30
I upgraded my Ubuntu Studio lappy from 9.04 to 9.10 last night.

After trying to get the standard upgrade to work, I failed and used the kubuntu update method as I've been using KDE.

To be honest my system is pretty much hosed.

To start off, the update didn't update grub with the newer kernels, so I had to reinstall grub and update it from recovery console.

The display drivers seem to be really messed up.

It boots, gets to the point of starting either kdm or gdm (I've tried both) and it sometimes crashes with a blank screen.
If I try to do CTRL+ALT+F1 for a proper console, the screen is pretty much seriously corrupted, flashing on the screen and the cursor takes up the full hight of the screen, and it's unusable.

On the occasions where I do get into KDE, it crashes as soon as the powersave screen blank cuts in.
In Gnome though, this seems mostly okay.

This laptop was originally installed with Ubuntu Studio 8.04 and has been updated to 8.10 and 9.04 with no hassle.
This time though.....

If I boot the older kernels it's still fine. I'm tempted to download a full CD and have another go.

It's a Dell Latitude X300, 1.4, 1GB mem, Intel 915 graphics.

I suppose a reinstall is probably in order, but I really wanted to avoid that.
To everyone in a similar weird config position as me, donwload and upgrade from the CD. I think it will be safer.


So not impressed.....


!m!

---

### Post by Roasted on 2009-10-30
This is why everybody always recommends to do a fresh install. Windows users and Linux users alike often have issues when attempting to upgrade from version to version like this.

I suggest you set up partitioning so your home directory is on a separate partition. That way any time a new version of Ubuntu comes out, you can selectively choose root (format) and home (do not format) and when you boot up after your first time installing, your files and stuff are there along with the new OS. This is done in the advanced partitioning menu (the manual option at the bottom). Just make sure you don't format that home directory!

---

### Post by maaarcooose on 2009-10-30
I'm certainly considering doing a fresh install and putting home in a seperate partition I just like to use 1 partition usually because it makes it much more flexible.
Time to bite the bullet I suppose...

I just find it really anoying that I have to do this.

I've been using Linux of various distros for the last 15 years and mostly upgrades work.

Mandrake I upgraded 3 times in a row on the same box. Ubuntu I've done much the same over the years.
I switched to Ubuntu some time ago becuase I found Debian to be a bit of a hassle to keep working well, and up till now, it's delivered.

Time to go backup my home folder.....


!m!

---

### Post by dummy910 on 2009-10-30
> **maaarcooose said:**
> 
* I failed and used the kubuntu update method as I've been using KDE.

* So not impressed.....

Not so impressed because you failed to use a Kubuntu upgrade for a Kubuntu system, Huh?

Any who, why not just download the **Alternate** flavored Kubuntu, burn the iso image to either a cd-rom or thumb-drive, and do an in place upgrade. The 'Alternate' has a command program in the root structure called _cdromupgrade_.

Just mount the iso image, load your terminal, navigate to the folder where you mounted it and type the following:
```
gksudo ./cdromupgrade
```

ez, peezee, lemon squeezie ;)

---

### Post by maaarcooose on 2009-10-31
Have tried a fresh install and it still doesn't work.

I get a crash in the installer during the package unstall section.

I'ver even tried in expert mode with no sucess.

I'm now going to try installing standard Ubuntu and then install the studio parts afterwards.

Anyone actually managed to install the new version of studio?

!m!

---

### Post by maaarcooose on 2009-11-02
Have had to do and install of standard Ubuntu and then install the studio packages via apt afterwards. 
Working now, but now have new problems with the lid close/suspend.

!m!

---

