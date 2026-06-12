---
title: "xserver error after first install"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by kittyloaf on 2007-08-25
Just bought a new laptop, installed Debian but it was impossible to get ANYTHING to work at all...so i installed the newest Ubuntu (7.04)

These are my specs

```

15.1" WXGA monitor 1280x800
1.50 GHz Intel® Core™2 Duo T5250 667MHz 2MB
Intel® GMA X3000
1GB DDR2 800MHz/PC6400 Ram
80GB 5400rpm. SATA hårddisk
Intel Pro/Wireless 4965AGN
SAMSUNG COMBO 6xx4w/6xx5WD/3xx5W

```


Installation went well.. but after install when it was supposed to start for the first time, it gave me an error saying that a monitor was found but none of the configurations could be used for it...

i tried this....

sudo apt-get install xserver-xorg-video-intel  (think that was the name)

then

sudo dpkg-reconfigure xserver-xorg

and then i configured everything as it should be (i think)

This time it didn't give me an error though, when i wrote startx it just went blank and nothing happend.


Please help, i am longing to play with my new laptop ='(

---

### Post by tseliot on 2007-08-25
did you choose the "intel" or the "i810" driver when you reconfigured the Xserver?

---

### Post by kittyloaf on 2007-08-25
i tried both just in case =P

none worked....the intel one made the screen blank

the i810 just gave me a can't start xserver error (like if you just choose a random faulty driver)

---

### Post by merlinus on 2007-08-25
You might try the vesa driver until you can research the correct one for your card.

Select it from the options in:

sudo dpkg-reconfigure xserver-xorg

-merlin

---

### Post by kittyloaf on 2007-08-25
tried the vesa one, i got

```

Fatal server error:
Caught signal 11. Server aborting

X10: Fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining.

```

---

### Post by merlinus on 2007-08-25
You might also check your bus id, which is one of the things asked for.

Mine is PCI:1:0:0

-merlin

---

### Post by kittyloaf on 2007-08-25
i launched a live CD ...backtrack, and i checked with lspci and it was

00:02.0

the one in the xorg.conf is PCI:0:2:0

so i guess it's correct

weird thing is that it worked with the live CD...but i don't know how to transfer it to the distro on the HDD  =/

---

### Post by merlinus on 2007-08-25
You might look at

/etc/X11/xorg.conf

whilst booted from the live cd, since those settings work.

Then you can perhaps transfer them to your hdd, via a CLI.

Or even save the live file, and copy it over intact.

Best to make a backup of the hdd file, though.

You can look at the live one this way:

```

cat /etc/X11/xorg.conf

```-merlin

---

### Post by kittyloaf on 2007-08-25
yeah well...i know how to find the live xorg.conf

but i don't know where to place it  =/   can't find the hdd when on the live CD

---

### Post by merlinus on 2007-08-25
You can save it to a flashdrive or cd.

Also, you can mount your ubuntu partition manually, and then navigate to the file.
```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu

```

It may be sda1, which you can easily determine with

```

sudo fdisk -l

```

-merlin

---

### Post by kittyloaf on 2007-08-25
tried the live CD xorg.conf file now  =/  doesn't work

---

### Post by merlinus on 2007-08-25
You might compare the two versions, and perhaps something will come to mind, especially since the live cd one worked.

-merlin

---

### Post by kittyloaf on 2007-08-25
yes well as i said, i tried the live CD one on the "real" one, doesn't work =(

---

### Post by kittyloaf on 2007-08-26
I filmed my problem here...

[http://documentcat.com/doc/test.3gp](http://documentcat.com/doc/test.3gp)

on the video i am first trying a live distro, and then rebooting and trying the "real" distro on the HDD, as you can see the screen goes blank when using the Intel driver...when i use the Vesa one it just gives me an error.....the live distro uses the Vesa one though :/

i already tried to swap the xorg.conf files...

---

### Post by merlinus on 2007-08-26
You might try vga as the driver rather than vesa.  But usually if vesa does not work, it is something else.

Perhaps your monitor?

-merlin

---

### Post by kittyloaf on 2007-08-26
well how can it be? =/

i mean both live distro and Debian works with the monitor..and Suse....

but Ubuntu is the distro that is working the most...well at least the one with the minor problems =/

in the other ones it's ONLY the screen that works....

---

