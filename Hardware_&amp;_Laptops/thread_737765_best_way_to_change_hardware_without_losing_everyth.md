---
title: "best way to change hardware without losing everything?"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by svtfmook on 2008-03-27
i have a ton of pictures/music/videos/settings/etc

i just ordered a new motherboard, cpu, ram and video card

my home is on a seperate partition

what do i do?

---

### Post by munkyeetr on 2008-03-28
Your /home directory is on a separate partition than /, correct?
...And are the files you are concerned with stored on the /home partition?

If they are, then when you reinstall Ubuntu after changing out your hardware, make sure you **manually partition** your disk during the installation. Make a note of which partition holds your /home data and **do not format it**. Just *mount it* as /home

The data will remain intact. Just be very sure which partition it is that holds your data.

---

### Post by munkyeetr on 2008-03-28
An additional thing you can do, if you are going to be reinstalling the same version of Ubuntu on the new hardware, and you want to to quickly get all your programs reinstalled is...

Before you change your hardware run this command:
```

dpkg --get-selections > /home/$USER/installed-packages

```
This will create a file that lists all your currently installed packages.

Then, after you have installed your new hardware and reinstalled Ubuntu, run these commands (pressing ENTER after each line):
```

dpkg --set-selections < /home/$USER/installed-packages
sudo dselect

```

Type ‘**I**‘ and allow dselect to install the the packages listed in your packages document. When it’s finished, type ‘**Q**‘ and hit the ENTER key to exit dselect.

Now you should be pretty much where you left off because all your program configuration files are still in your /home directory, so your program settings should all be there.

---

### Post by jocko on 2008-03-28
> **svtfmook said:**
> i have a ton of pictures/music/videos/settings/etc

i just ordered a new motherboard, cpu, ram and video card

my home is on a seperate partition

what do i do?

Linux detects your hardware on boot, so there should be no reason to reinstall ubuntu.
You may get problems with video drivers if your new card require different drivers than the old one, but this can be fixed without a reinstall.

---

### Post by munkyeetr on 2008-03-28
> **jocko said:**
> Linux detects your hardware on boot, so there should be no reason to reinstall ubuntu.
You may get problems with video drivers if your new card require different drivers than the old one, but this can be fixed without a reinstall.

So you can do a complete hardware change and still use the same hard drive and it will have no ill effects? I didn't know that. Pretty awesome.

If that truly is the case, disregard my posts, as you can just plug your old HD back in.

---

