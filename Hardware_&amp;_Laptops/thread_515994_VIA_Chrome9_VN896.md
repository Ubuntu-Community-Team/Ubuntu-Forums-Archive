---
title: "VIA Chrome9 VN896"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by metalix on 2007-08-02
Hi,

I just brought my new laptop with VIA Chrome9 VN896 graphics card.

I would like to install Ubuntu first, and then worry about patching the drivers or whatever (according to existing howtos) later, but unfourtunatly, the Ubuntu boot CD won't install as the box is too big and I can't point my mouse onto the bottom.

I did notice however that the boot menu on the cd allows to boot using an additional driver CD. Is there someway to put a compatable driver (I'm talking increased resolution so I can installl - not 3d stuff!) onto a CD or something so that I can install.

Thanks for reading.

---

### Post by metalix on 2007-08-03
No one?

---

### Post by stchman on 2007-08-03
> **metalix said:**
> Hi,

I just brought my new laptop with VIA Chrome9 VN896 graphics card.

I would like to install Ubuntu first, and then worry about patching the drivers or whatever (according to existing howtos) later, but unfourtunatly, the Ubuntu boot CD won't install as the box is too big and I can't point my mouse onto the bottom.

I did notice however that the boot menu on the cd allows to boot using an additional driver CD. Is there someway to put a compatable driver (I'm talking increased resolution so I can installl - not 3d stuff!) onto a CD or something so that I can install.

Thanks for reading.

So you are saying that when you boot the LiveCD up the graphics are all messed up?

Try the safe graphics settings mode.

---

### Post by metalix on 2007-08-03
No the graphics aren't messed up.

The CD loads fine, albeit with a smaller resolution. However, because the installation box is too small, I can't click on the buttons therefore I can't instal it.

If I could install it, I could mess around with the drivers as per some of the online tutorials. But because I can't install the system, I can't.

Some of the other people here have a Fujitsu-Siemens AMILO pro with this graphics card. 

How did they manage to install ubuntu?

Would they be willing to copy the drivers they're using and to email them to me? To those people: how did you manage to fix the driver?

---

### Post by w4ett on 2007-08-03
Hold the <alt> key and click and drag the window up.

---

### Post by metalix on 2007-08-03
Does that allow you to drag the window past the top menu? I ask this because the desktop is too small to fit the whole window on!

---

### Post by w4ett on 2007-08-03
> **metalix said:**
> Does that allow you to drag the window past the top menu? I ask this because the desktop is too small to fit the whole window on!

Yes it will.  You can also change the default install resolution from the CD boot menu. F4 (I believe) is the VGA selection toggle.  Click on it and select your desired resolution.

---

### Post by fifafrazer on 2007-08-03
I just closed the xfce panels, but I havent be able to install a proper driver to get a better resolution, so I went back to Vista waiting for the version 79 linux driver for vn896.

---

### Post by metalix on 2007-08-04
When will this new driver be available?

Do you think it would be included in the Gusty Gibbon distro soon?

Could you send me a PM when you have some luck?

Thanks.

---

### Post by fifafrazer on 2007-08-04
hmm.. I keep checking the linux forum of viaarena.com for a newer driver.. Dont know a release date yet..

---

### Post by fifafrazer on 2007-08-05
Hmm.. I can see that the new driver IS realeased, but they seems to be quite hard to compile. Hope anyone will find a solution.
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=78497&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=78497&enterthread=y)

---

### Post by revees on 2007-08-18
I had the same problem.  The bottom of the window where I needed to click <OK> or whatever was off screen and I could not move the window.

My new laptop is a Everex Stepnote VA2001T.  It uses the P4M900 Chipset and the VIA integrated video chip VT3371 which they call the VIA Chrome9 HC IGP.

I got Ubuntu installed by using the alternative install CD.  In the weird alternative, I also found that if I plugged in an ext. monitor, it fixed the resolution on BOTH screens and I could even install with the "normal" CD.

You might want to try one of these solutions.  I could not stand to live with VISTA more than absolutely necessary.  Still, I have a problem in that I have been stuck with 800 x 600 resolution and no graphics acceleration. 

Right after the install, I could not even get to the GUI but needed to first edit xorg.conf file to change the driver listing from "via" to "vesa".

So I have a working copy of Ubuntu, but on a native 1440 x 900 screen, the 800 x 600 resolution is really painful.  I guess I should start a new thread for help with my problem, but hope this helps you.  (By the way I tried two different solutions posted on the VIA form.  Their instructions were really difficult to follow and neither worked.)

---

### Post by fifafrazer on 2007-08-19
the vesa driver is actually able to do 1280*768 which is close to the native resolution of my laptop (1280*800). It's OK, but 3d acceleration doesnt work. The openchrome project is working on a driver, so I'll wait untill they have fine-tuned the current alpha version.3 times I've tried to compile via's own driver in debian 4.0, which should be supported, using their own guide, but it didnt work.
When I install debian the resolution is automatically set to 1280*768, so I'll stich with this distro for a while. Appearently I had to install debian in GUI-mode. In text installation mode, the screen was cut up, and some of the screen was "missing".


btw.
I was able to install ubuntu by removing the panels in the top and bottom.

---

### Post by epidemiks on 2007-08-21
excuse me for being retarded when it comes to compiling etc, but how do I get this driver installed? The readme for the via arena might as well be in urdu, cause i can't make sense of it.

---

### Post by revees on 2007-08-21
Epidemiks, 

Your not retarded (and if you are, that is totally cool too, plenty of people with mental disabilities are doing more good than most).  If you look at the two posts above as well as posts in other places on the internet, it does not seem that anyone has been able to get this driver to work with their instructions, at least for certain chipsets.

Some of the instructions are just wrong (sending you to the wrong file or code) and others are confusing.

I was hoping someone could update us on the status of the work (if someone is working on it) of this driver.

I posted a bug in launchpad and would invite you to do the same so it encourages them to solve this bug: [https://bugs.launchpad.net/bugs/+filebug](https://bugs.launchpad.net/bugs/+filebug).

---

### Post by epidemiks on 2007-08-21
revees, thanks for the kind words - I'm not really retarded, just frustrated. Everything else is working reasonably well, but this display driver stuff if getting to me. 
Is there perhaps some kind of interim driver I can use that will give me better resolution options until a functioning driver comes along?

---

### Post by impegasus on 2007-09-14
if you edit the xorg.conf file manually in /etc/X11 you can enter the native resolution of your screen, works fine with me so far...

I've also got a unichrome 9 pro adapter and it's annoying the heck out of me, but 2d performance is reasonable (24bpp @ 1280x800) using the vesa driver.

---

