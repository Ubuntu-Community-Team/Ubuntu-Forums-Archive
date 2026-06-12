---
title: "Karmic seems to be incompatible with my network controller"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by dr_voodoo on 2009-11-02
further to my 'no internet' thread - I have done some diagnosis. 

KK has installed itself on two old Dell Dimension 4600 machines via auto-update. 

There is no internet connection in Firefox although I can access my router control panel. Eth0 appears correctly connected. 

There is SOME internet connectivity - I can ping google OK from the terminal, and if I open Synaptic I can retrieve the lists of software - however, accessing web pages or trying to download any software results in a time out.

I assumed this might be down to the installation not downloading/updating  correctly so I downloaded the Karmic LiveCD from another machine and booted from that - and still exactly the same problem. 

Have there been any major updates to the way Karmic handles networking and if so is there a fairly n00b-friendly way that I can get round it? Am I simply better off reinstalling Jaunty? 

The fact that I get exactly the same problem on two almost identical PCs leads me to believe it must be updated network drivers being incompatible with my existing hardware :(

---

### Post by EJeanmaire on 2009-11-02
Are you sure your internet itself isn't the issue (try using the web on another "different" machine or o/s.)

Did your internet work in Jaunty, or are you new to linux/Karmic? 

What is your Network Card Model?

It looks like your install is using drivers for the network card, you might want to update the kernel to something even newer and see if that drivers in the newer kernel have fixes for your networking instability (granted this is a more advanced procedure, not sure how technical you are).

---

### Post by dr_voodoo on 2009-11-02
Hi thanks for the help. 

The internet connection itself is fine - I am typing this from a Vista machine on the same network 

Internet on both the PCs worked fine with Jaunty - it was only after they downloaded and updated themselves that problems appeared. 

The network controller is the standard one that is on the Dell Dimension motherboard - I know it is made by Intel but I can't remember the exact model number off the top of my head. 

I'm guessing that there must be a fair few of these older Dells around running Ubuntu so I don't know if it's better to wait a bit for a fix or just reinstall Jaunty again - after all, Jaunty was working fine anyway so I don't know if there are that many benefits to upgrading anyway. If I was to experiment with a newer kernel what would you reccomend? I am fairly new to Linux, only been using it a couple of months - but I am technical enough to be able to follow reasonably clear instructions ;)

---

### Post by dr_voodoo on 2009-11-03
:bump:

anyone got any ideas? I'm on the verge of completely reinstalling Jaunty...

---

### Post by EJeanmaire on 2009-11-04
> **EJeanmaire said:**
> 
It looks like your install is using drivers for the network card, you might want to update the kernel to something even newer and see if that drivers in the newer kernel have fixes for your networking instability (granted this is a more advanced procedure, not sure how technical you are).

Try this.  To upgrade the kernel, use the master kernel thread... try the 2.6.32 rc kernels...  Also make sure you are not blacklisting any intel networking drivers

---

### Post by dr_voodoo on 2009-11-04
Unfortunately that is way beyond the realms of my expertise - I wouldn't know where to start on that (especially as I would need to be downloading updates for my Ubuntu system from my Windows laptop and transferring via USB)

However I have discovered that my ethernet controller is an Intel 82562EZ rev2 10/100 model... can anyone suggest somewhere I can look to see if there is a downloadable fix for this device or something? Have tried googling but didn't see anything that looked useful :(

---

