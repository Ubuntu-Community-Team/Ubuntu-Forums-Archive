---
title: "Atheros Wireless ar5b125 No Drivers"
date: 2012-03-17
forum: Hardware
---

### Post by Airspace on 2012-03-17
I recently bought an Acer Aspire 722, and installed Ubuntu 10.04, alongside my Windows 7 install, and when I booted into Ubuntu, I was unable to obtain any network access, I could not get the wireless drivers to work as well as the Ethernet card's drivers. After doing some research I found a dead thread that said the only fix was to update to the newest release of Ubuntu, I am not completely thrilled with the idea, so I was wondering if there is any way for either driver to work in 10.04.

---

### Post by ahallubuntu on 2012-03-17
Did you read this thread?

[http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178)

It describes problems with Ubuntu 11.04 on your laptop.  Given the long list of issues there (in a newer version of Ubuntu than 10.04), I'd probably not waste time with 10.04 LTS on your Acer, personally.

12.04 is coming out soon and may work pretty well with your Acer.  I'd give the 12.04 beta a try.  If it works well, you can either go with it nor or wait a few more weeks for the official release.  If you don't like Unity desktop, it's pretty easy to install Gnome 3, which isn't exactly like Gnome 2 in Ubuntu 10.04, but it's fairly close on the surface.

FYI, I had a lot of issues with my Acer netbook from a couple of years ago.  11.04 finally works pretty well on it after some hacks just to get the graphics to work, but your netbook is newer so I wouldn't expect 10.04 to work well on it.  I actually replaced the Atheros wireless G card in mine with a better Intel card.  It was pretty easy to do.

---

### Post by Airspace on 2012-03-17
I was able to get the wired drivers to work, I had used an older 10.04 disc and found a thread detailing that I could use a custom kernel to potentially make it work. When I tried to install it using dpkg it threw a dependency error after looking at the dependency I had noticed that is was just a kernel update and after a little transfer through an external drive, and rebooting into the new kernel, all of a sudden the wired networking worked. Right now I am installing updates to see if my issue is resolved with any of the updates, I will check in afterwards.

---

### Post by Airspace on 2012-03-17
So after some updating and some custom kernels I was still unable to get the wireless working, I really do not like the gnome 3 style, and I also do not like the look of Unity, so I refuse to do a distro-upgrade but I may have to change my mind for this simple reason. We shall see if I can't get it to work in the next few days.

---

### Post by ahallubuntu on 2012-03-17
FYI, it may be easier for you to swap in a different wireless card than fighting for hours trying to get your wireless to work.  I see that Acer offers three different wireless drivers for that machine, so it must have been sold with Realtek and Broadcom cards not just an Atheros card.  Maybe you could do a bit of research and see which exact Realtek and Broadcom cards were sold with it and see what those cards cost on eBay - and then also google to check on Ubuntu support for those cards.  I'd put my money on Realtek, though - they seem to offer decent driver support on their website for their wireless chips, even if you have to build them from a tarball.

Wireless cards aren't too hard to swap out most of the time.  If you can get to your card from the bottom (like I can with my old Acer netbook when I upgrade my card), give it a try.

---

### Post by Yellow Pasque on 2012-03-18
Install the linux backports wireless package (I forget the exact name).

---

### Post by drah022 on 2012-07-18
I cant start network in backtrack 4 with my acer 7250

---

