---
title: "Ancient Laptop Resurrection"
date: 2011-12-02
forum: Hardware
---

### Post by iloveme661 on 2011-12-02
I have just ordered a Bondwell 486nc laptop it has a 120mb hdd 8mbs of ram and a 33mhz processor. I have been trying to find a release of ubuntu or linux to run on it but have had no luck, does anyone have any ideas about what can run on it ? .Also it needs to be loaded on via floppy drive.

---

### Post by hansdown on 2011-12-02
Welcome to the forum,iloveme661.

Try mepis.

[http://www.mepis.org/mirrors](http://www.mepis.org/mirrors)

It works with "almost" any system I've tried.

---

### Post by staf0048 on 2011-12-02
Damn Small Linux comes to mind.... but loading via a floppy?  Not even sure how to go about doing that anymore.

---

### Post by dandnsmith on 2011-12-03
Its worth looking at the [dsl site](http://www.damnsmalllinux.org/), but [this site](http://www.linuxlinks.com/Distributions/Floppy/) may be better - it includes a link to tom's root 'n boot floppy distro for which I have a couple of versions saved on hdd as well as floppies (which I haven't booted for several years, now systems tend not to have floppy drives and distros take more space).

I note that you say 'loaded via floppy', so that the other interpretation is that you have no CD drive or USB slots.
Do/will you have an ethernet port, as that can be the means of getting stuff onto the HDD.

I did have an early version of RedHat linux as install-from-floppies, but not sure where that is these days.

---

### Post by iloveme661 on 2011-12-03
dandnsmith

How would i go about adding content via ethernet port ?

---

### Post by dandnsmith on 2011-12-03
It gives the chance to obtain files via ftp, and also to network with local PCs.
I haven't really got down to the nut and bolts, as I wasn't sure yet whether it would even be a consideration.
One thing I feel sure about is that you'll be very hard pressed to run any GUI with only 8MB RAM, and you're extremely limited with 128MB HDD as to how much you can have as swap (sensibly)

---

### Post by iloveme661 on 2011-12-03
dandnsmith

Is the ethernet method just for transferring files or could i install an os off of it ?

---

### Post by MartyBuntu on 2011-12-03
What exactly are you planning on doing with this old machine?

---

### Post by iloveme661 on 2011-12-03
Basic Tasks like Word Processing etc.

---

### Post by dandnsmith on 2011-12-04
> **iloveme661 said:**
> dandnsmith

Is the ethernet method just for transferring files or could i install an os off of it ?

I cannot, at the moment, think of an OS which you could possibly install on such a limited machine via ethernet

---

### Post by MoreOrLess on 2011-12-04
You want do word processing? What are you going to run, vim?
DOS 6.22 / windows 3.1 might work well..

---

### Post by Cpierce on 2011-12-04
Look at Slitaz

---

### Post by MoreOrLess on 2011-12-04
> **Cpierce said:**
> Look at Slitaz
...
> Regardless of installation method, however, SliTaz requires at least 16 MB of RAM to run efficiently

---

### Post by iloveme661 on 2011-12-04
I know that this is probably really off topic but would anyone know how to paint a laptop ?

---

### Post by dandnsmith on 2011-12-04
Not on the list of things I've done - but you need to be careful how you do it, and what type of paint to use (depends on materials of the laptop). I have to say that I've found plastics difficult to paint on without some way of achieving a 'grip' - perhaps those treatments to allow kitchen cupboard doors to be painted over would help.

---

### Post by iloveme661 on 2011-12-06
If an operating system says that it requires 16mb and i install it from a different pc but then put the hard drive back into the laptop will it run on 8 ? Is the ram restriction only for installation ?

---

### Post by N00b-un-2 on 2011-12-06
> **iloveme661 said:**
> I know that this is probably really off topic but would anyone know how to paint a laptop ?

As a matter of fact I do. sand lightly with medium grit sand paper (500 grit should be fine) and it wouldn't hurt to use a coat of primer for plastic.  multiple thin coats is the key.

Here's a laptop I did a couple years ago before a deployment to Iraq.  I don't know if Facebook links work here though[IMG]http://a5.sphotos.ak.fbcdn.net/hphotos-ak-snc3/25531_109694259042767_100000065795524_236574_4130340_n.jpg[/IMG]

---

### Post by iloveme661 on 2011-12-09
I found an OS ! Its called colibri os and it has a live floppy image! It seems as thiugh it will run on my hardware but ill have to wait and see

---

### Post by lykwydchykyn on 2011-12-09
You can also try Menuet or FreeDOS.

Does the ethernet port allow you to PXE boot?  That might open up some more possibilities.

I really don't think you'll be able to run X11 on 8 mb of RAM, but you might be able to get something like microcore (tinycore without X11) running.  Not via floppy, though.

---

