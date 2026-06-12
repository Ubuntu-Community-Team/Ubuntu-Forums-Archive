---
title: "Creative Zen Mirco: how to use in Hoary"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by tora201 on 2005-05-07
After lots of searching, I finally got it going. Here is a short and very simple  How To. Believe me, you wife will thank you for having the time to spend more time with your family. ;-) That is until my next project....

1)Importan: First, **DO NOT** install gnomad2 from the Ubuntu depositories, instead go to:

[http://packages.debian.org/unstable/x11/gnomad2](http://packages.debian.org/unstable/x11/gnomad2)

Get the i386 version, download, and install from a terminal:

sudo dpkg -i gnomad2_2.6.3-1_i386.deb

You may have other dependencies that need to be installed before it will let you install gnomad. If that is the case, install the files as needed. I had to install libnjb4_2.0-1_i386.deb

(which is available from: [http://packages.debian.org/unstable/libs/libnjb4](http://packages.debian.org/unstable/libs/libnjb4))

Note: maybe the depositories could be updated with the relevant files?


2) Once you have gnomad2 installed, just connect your Zen, fire up gnomad from a terminal:  :grin: sudo gnomad2

You can then make an icon for it in your menu, but unfortunately you will need to run it as as a superuser: Since I use Xfce, I just made a launcher in the menu, and in the Command line put: gksudo gnomad2

That should be it! (Unless somebody can CLEARLY tell me how to solve the problem of the thing absolutely wanting to run as a superuser! -- not that I really care anymore, but it would be nice if it could be solved in a simple way)
:wink:

Edit: Apparently  this works for most other Creative Jukebox players etc. Just remember to get the latest files, as described above.


A few sources:
[http://ubuntuforums.org/archive/index.php/t-2700.html](http://ubuntuforums.org/archive/index.php/t-2700.html)
[http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/](http://blog.clurrcache.me.uk/index.php/archives/2004/12/15/zens-on-linux/)
[http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2](http://www.nomadness.net/modules.php?name=Forums&file=viewforum&f=2)

---

### Post by vassie on 2005-05-19
Help
I cannot install libnjb4 as it depends on a newer libc6, thus meaning I cannot install the latest gnomad2
Someone please help, as there is no point in me using Ubuntu if I cannot copy music to my Zen Micro
Ben

---

### Post by esh on 2005-05-28
[QUOTE=vassie]Help
I cannot install libnjb4 as it depends on a newer libc6, thus meaning I cannot install the latest gnomad2
Someone please help, as there is no point in me using Ubuntu if I cannot copy music to my Zen Micro
Ben[/QUOTE]
I've had the same problem, had to install libc6 from Debian Sid...
But then it destroys my apt and crashes a lot of other packages... :-?

---

### Post by Gunther_oz on 2005-05-29
Thank you very much. I got this to work after a little playing around. I can pretty much dump windows now because of this find. 

The debian package bawked at first as you said it would. So I got libnjb4_2.1-1, but that was too new and caused worries dependency wise. Start over...Synaptic, remove Gnomad, remove libnjb4. As you said you used 2.0-1 instead of 2.1-1, i searched google and found the right deb package at some obscure mirror in Scotland.

dpkg'ed libnjb, dpkg'ed gnomad2, gksudo gnomad2....scanned in my 502 files in half the time it takes in Creative's Mediasource Organizer.

Thanks again!

---

### Post by Leszek Tarkowski on 2005-06-07
I have zen micro - real shame that ubuntu developers don't see that newer version of libnjb is needed. I managed to install it the same way as describe here.

But i have this strange error - my usb flash memory and micro after kernel upgrade developed strange behaviour - i can move/copy only few Mb and they hangs. nothing in dmesg. they simply stop responding... any help would be appreciated.

---

