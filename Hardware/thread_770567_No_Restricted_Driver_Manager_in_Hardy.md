---
title: "No Restricted Driver Manager in Hardy"
date: 2008-04-27
forum: Hardware
---

### Post by Speedoo on 2008-04-27
Hi all,
I just upgraded to Hardy Heron, and now my fglrxinfo is returning indirect rendering through Mesa.  I was previously using the ATI driver for my Radeon Xpress 1150 card.  Now when I click on System/Administration, there's no restricted drivers manager in the menu.  When I click on Hardware Drivers I get the message that no restricted drivers are in use.  I installed Envy to install the latest ATI driver, but although everything seemed to work, fglrxinfo still shows the generic ubuntu driver.  I can no longer play World of Warcraft, and apparently have no direct rendering or 3d.  I'm also unable to run Compiz due to no Composite extension.  Has anyone else experienced this, and does anyone have any suggestions?
BTW, I also continue to experience connection problems with my Realtek rtl8187 wireless driver.  Is there an upgrade to the rtl8187 driver for the new kernel?

Thanks!

---

### Post by filip33 on 2008-04-27
try going add or remove programs and serch for your driver thats what I did and now it works hope this helps.

---

### Post by Rocket2DMn on 2008-04-27
You can have Envy search for, download, and install the correct restricted driver for you, and with Hardy, it's now available in the repositories.  Directions here - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by gerben1 on 2008-04-27
> **Speedoo said:**
> Hi all,
I just upgraded to Hardy Heron, and now my fglrxinfo is returning indirect rendering through Mesa.  I was previously using the ATI driver for my Radeon Xpress 1150 card.  Now when I click on System/Administration, there's no restricted drivers manager in the menu.  When I click on Hardware Drivers I get the message that no restricted drivers are in use.  I installed Envy to install the latest ATI driver, but although everything seemed to work, fglrxinfo still shows the generic ubuntu driver.  I can no longer play World of Warcraft, and apparently have no direct rendering or 3d.  I'm also unable to run Compiz due to no Composite extension.  Has anyone else experienced this, and does anyone have any suggestions?

Yep, I have the same problem.
I also do not see an video card driver in System->administartion->hardware devices
it is very well possible that it disappeared after the first time that I used envyNG, as it was there at first after the upgrade.

Also whatever I do fglrxinfo keeps returning indirect rendering through Mesa. I have tried this tutorial
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) 
and have tried envyNG many times with and without first uninstalling the drivers, tried uninstalling via envyNG and also via synaptic.

but see also here for some other suggestions (none of which worked for me but they may work for you):

[http://ubuntuforums.org/showthread.php?t=770460](http://ubuntuforums.org/showthread.php?t=770460)

---

### Post by gerben1 on 2008-04-27
> **filip33 said:**
> try going add or remove programs and serch for your driver thats what I did and now it works hope this helps.

Oh, this is totally new for me, what did you install from there?
(i.e. what do you mean with "your driver"?)

---

### Post by Speedoo on 2008-04-29
Well,
I solved my problem by going to ATI's site and downloading their linux driver installer.  I now have 3d direct rendering again.  Still not sure why Envy didn't work, but all's well that ends well.  Thanks for all your replies!

---

### Post by Tuxaby on 2008-04-29
Restricted drivers manager is now called "Hardware Drivers" under Administration.

---

### Post by jaydubster on 2008-05-02
My Hardware Drivers is completely empty.

Tells me "there are no proprietary drivers installed on this system"
Every time I run Envy, it goes thru fine, reboots, then I get "low graphics mode" and have to change everything from default Vesa Drivers and Plug n Play 800x600 monitor.

I've just enabled the restricted sources for Envy & tried again, but it made no difference. Still no drivers, no hardware acceleration or anything. Hardy's doing badly imho.

---

### Post by hirumono on 2008-10-05
That's because Envy uninstalls the linux-restricted-modules package. Once you reinstall it (after you have removed proprietary drivers through Envy!), you will see again your hardware in Restricted Driver Manager.
Ubuntu's not guilty!  ;)

---

