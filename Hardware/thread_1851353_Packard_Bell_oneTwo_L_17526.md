---
title: "Packard Bell oneTwo L 17526"
date: 2011-09-28
forum: Hardware
---

### Post by Paddy Landau on 2011-09-28
I am considering getting a [Packard Bell oneTwo L 17526]("http://www.pcworld.co.uk/gbuk/packard-bell-onetwo-l-i7526-uk-23-all-in-one-pc-09885822-pdt.html") computer.

Everything looks OK, but I'm a bit concerned about the graphics card: Intel HD Graphics 2000. I've read that nVidia graphics cards work well but that Intel don't.

Does anyone have any experience of it? Do you think this is likely to play well with Ubuntu? At the price, I'd like to be sure!

---

### Post by realzippy on 2011-09-28
Intel HD Graphics 2000 ...
If it is the integrated graphics core of the I5 CPU,[as it seems to be]("http://www.notebookcheck.net/Intel-HD-Graphics-2000-100.37994.0.html"),it should run fine.
(need kernel >= 2.6.38.11)
Myself running a Packard Bell laptop (easynote tk 85),with I3
(pre-sandybridge) graphics + dedicated nvidia420m card.
3D runs smoothly on I3 graphics,more than enough for compiz/Kwin
or casual games.
The nvidia card is twice as fast (only!) when activated via
bumblebee.
Think you will be fine with that machine.

---

### Post by Paddy Landau on 2011-09-28
Thank you, realzippy, for that information.

You mention kernel 2.6.38-11. I am currently on 10.04, which has kernel 2.6.32-33. That means I'll have to use a later version. How can I tell which kernel each Ubuntu version has? I found the following, which seem to say that even 11.04 doesn't have that version yet:

[LIST]
[*][Wikipedia version history]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_history_of_common_programs")
[*][Ubuntu version map]("http://kernel.ubuntu.com/%7Ekernel-ppa/info/kernel-version-map.html")
[/LIST]
  
Does that mean I have to wait until 11.10 to be able to use that computer?

I will go into the shop and try a USB Live CD to check it.

---

### Post by realzippy on 2011-09-28
No problem to use Intel integrated graphics in 10.04...
You have to use Stefan Glasenhard's PPA...
He patched the intel driver;took Mesa 7.10.3 from Debian backports,
patched it for Ubuntu.For some reason Canonical decided not to do this,which is strange since 10.04 lasts until 2013 and Sandybridge graphics are pretty common meanwhile.RedHat Enterprise also has the patched drivers,only Ubuntu refuses...
Here is a link to glasen's blog
["Sandybridge on 10.04"]("http://www.glasen-hardt.de/?p=1292")
It's in German,but the essence is:
```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

```

Note,that a live CD or USB won't help you,since you had to reboot to use
the backported kernel/intel driver.

For 11.04 the solution is similar:
Just install a newer kernel and you are done.
**Edit:**
Have to enable "proposed updates" to get 2.6.38.11 !

---

### Post by Paddy Landau on 2011-09-28
Thank you for that information, realzippy.

I have installed 11.04 on an external hard drive, so I will experiment with that when I have a bit of time; possibly over the weekend.

---

### Post by realzippy on 2011-09-28
Just see at your link that 11.10 is shipped with kernel 3.0 ,so
you could use it to test the  L 17526 in the shop.

---

### Post by Paddy Landau on 2011-09-28
> **realzippy said:**
> Just see at your link that 11.10 is shipped with kernel 3.0 ,so you could use it to test the  L 17526 in the shop.
Not a bad idea, though 11.10 is still in beta mode. Perhaps I'll install both 11.04 and 11.10 on the external hard drive!

---

### Post by Paddy Landau on 2011-09-29
> **realzippy said:**
> Have to enable "proposed updates" to get 2.6.38.11 !
I've gone to do this and discovered that the standard updates take me to 2.6.38.26. So, proposed updates are not necessary on 11.04.

I will let you know the results after I have tested this in the shop.

---

### Post by Paddy Landau on 2011-09-30
I went to the shop armed with a USB stick with 11.04, and an external USB hard drive with 11.04 fully updated and with some software to test.

Everything seemed to work "out of the box".

I shall mark this thread as Solved.

Thank you realzippy for your input.

---

