---
title: "upgrade from 8.04 to 8.10 messes up my monitor/graphics  settings"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by tjk on 2009-03-06
HELP PLEASE!

I upgraded to ubuntu 8.10 and discovered that there are no options for manually setting up my monitor, and I cannot get my NVidia graphics card to work.  I've spent MANY hours searching the web and this forum for answers -- and tried so many things that I'm sure I'm going in circles already!!
Can someone please help walk me through this problem to get my video working again? (I suspect that this may not be an easy fix -- so extended help may be needed.)

I have  a relatively new ACER LCD monitor - x193w monitor that isn't being detected, and my video card is a NVidia GForce4.

---

### Post by avtolle on 2009-03-06
Reference the video card; did you read [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

---

### Post by tjk on 2009-03-06
> **avtolle said:**
> Reference the video card; did you read [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

it states that: [INDENT]> GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.[/INDENT]Does this mean then that I can't use Compiz?  If so, is there any way I can get back to 8.04?

---

### Post by tommcd on 2009-03-07
> **tjk said:**
> it states that: [INDENT][/INDENT]Does this mean then that I can't use Compiz?  If so, is there any way I can get back to 8.04?

I'm afraid it does. You could try running compiz, but the performance will likely not be very good. I was not aware the nvidia-glx-legacy drivers were not compatible with the newest Xorg in Ubuntu 8.10. This is unfortunate. Perhaps it will be fixed at some point.

It is possible to downgrade according to the Ubuntu wiki, but the process seems to be a bit involved; and I have never tried it:
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

### Post by tjk on 2009-03-14
Just wanted to update this problem...
I DID get a NVidia driver working with my GForce4 card.  I found this site: [http://guitarchasers.org/guchmain/archives/323](http://guitarchasers.org/guchmain/archives/323)  and it gave me a few tips -- like uninstalling envyng and hardware driver nvidia drivers before installing new drivers and headers.  Everything works now!!!

---

### Post by tommcd on 2009-03-15
Glad you got it working!
So it would seem that it is only the nvidia legacy driver in the Ubuntu repos that does not work with the newest xorg. The legacy driver from nvidia.com obviously does work. There should be a "sticky" about this somewhere, since a lot of people are likely affected by this.

---

### Post by Peter Bell on 2009-03-15
I had to go through a similar exercise with my Intel GM945 video in order to return to decent performance after 8.04 to 8.10 upgrade.

---

### Post by tjk on 2009-03-19
Well, everything was running fine until I ran my upgrade/update today.  Now I'm back to square one.  Guess I have to be more careful what I upgrade until this situation is fixed (or I change my video card). :(    I'm wondering if it was the kernel upgrade that messed things up...
Anyone know who I contact to complain about this annoying problem?

---

### Post by avtolle on 2009-03-19
Anytime one manually installs drivers and there is a kernel upgrade, there is the need to reinstall the drivers. I believe there are some ways around this, but I'm ignorant of them. The best suggestion I have is to do a search on the Forums or by Google to see if my belief is correct. Otherwise, one must manually reinstall the drivers on each kernel update (or boot from the prior kernel version where the driver was installed).

---

