---
title: "Aspire Aspire 7741Z-4433 Screen Brightness Issue"
date: 2011-02-26
forum: Hardware
---

### Post by Whizard72 on 2011-02-26
I have an Acer Aspire 7741Z-4433 with:

Intel Pentium P6200 CPU
Intel HD Graphics.
1.3MP Webcam
4GB RAM
etc.

Everything works, I mean EVERYTHING works great under Linux and Ubuntu specifically. However, the one issue I have is that the screen brightness stays at a constant full-brightness. 

When I use the FN-<LEFT> or <RIGHT> arrow keys, the brightness indicator in Ubuntu comes up and indicates the change but the actual brightness of the screen does not change..?

I'm not a newbie to Linux at all, I've been around more than a few years but this problem has me stumped. I bought this laptop specifically to run Linux and thought I was careful in choosing one with an Intel chipset in it. 

Investigating the /proc/acpi filesystem didn't seem to yield anything that could be changed or was relevant. 

The fact that Ubuntu recognizes the keyboard input and shows the brightness change indicator should mean the OS is getting the proper keyboard signals for the brightness change okay but the brightness mechanism isn't getting the signal I would suppose. 

Note: I did compile the latest 2.6.37.1 kernel in hopes of a positive change to this behavior to no avail. 

At this point, I need ideas.

---

### Post by Whizard72 on 2011-02-27
There's gotta be some ideas out there for things to try. I have not been successful so far.

---

### Post by panosV16 on 2011-03-06
I have the same problem.

Tried this
[http://askubuntu.com/questions/21523/screen-brightness-not-changing-on-acer-5742-notebook](http://askubuntu.com/questions/21523/screen-brightness-not-changing-on-acer-5742-notebook)
but it didn't work for me.

---

### Post by panosV16 on 2011-03-06
Found a solution! I have an Acer Aspire 7745G but it must be similar to yours since it's the same series.
I followed this [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1636959](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1636959) guide up to a point.
Meaning i just installed the packages from that repo and brightness adjustment works both with keys (FN + arrow left-right) and from the bar in the taskbar.
Previously i did edit the grub.cfg and changed the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=vendor"

but i don't know if this is needed. Anyway hope i hepled.

---

### Post by Whizard72 on 2011-03-09
HOLY SMOKES!!! It works!! THANK YOU. Now all I have to do is figure out how to add that package into the latest kernel..

---

### Post by panosV16 on 2011-03-09
Yes i noticed that something changed with the kernel version. Both in the package list that i downloaded and in the grub list. If you can please tell me what you did. And another question. Can i download these packages in case the repo goes offline in the future? (or for future formats)

---

### Post by Whizard72 on 2011-03-09
Well what you downloaded from that repo was a kernel patch for the default kernel in Maverick which is 2.6.35-xx. You can download the packages by clicking on them in launchpad. 

My issue now is to patch the 2.6.37.3 kernel which I'm using on my Acer. My first attempt was a patch and compile and was not successful. I think I might next try a compile and patch. Will let you know.

---

