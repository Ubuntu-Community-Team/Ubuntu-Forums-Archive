---
title: "ubuntu 7.10 help (ati xpress radeon 200m)"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by ajkiwi88 on 2007-12-15
ok i have ati xpress radeon 200m graphics card 
first question i installed ubuntu 7.10 and it installed i go to the grub screen wait for ubuntu to start booting and then it just disapears i mean the screen goes black so i left it and after about 5mins i get the loggin screen and everythings fine how can i sort this out?

also is there a way to get this graphics card working dual head?

---

### Post by woland on 2007-12-16
Same sh*t with my laptop.

If you would try to turn the desktop effects on, you will mess your entire setting.
I didn't succeed with dual head either.


By the way, a question back to you: did you try to connect a wide screen monitor to your laptop under Windoze? Did you succeed?
Due to lousy driver from ATI (for Windoze), it does not support the resolution of my new 22" monitor.

In short 200M is a sh*tty chipset, not because of the hardware, but because of the abysmal driver support.

---

### Post by Pgi947 on 2007-12-16
Same chipset, sorted it by changing the splash resolution values, there default set to 1200x1024, needs to be set to 1200x800 for to sort things changed my boot times from 5min+ to under 30 seconds :-)

GPU driver is fine, installed the restricted fglrx driver, along with XGL and compiz, all is fine :-)

---

### Post by woland on 2007-12-17
Pgi947&#1073;, I'm glad to read this.
Is you 200M, for AMD or Intel processors?

---

### Post by Pgi947 on 2007-12-17
Intel, run this in terminal...

sudo gedit /etc/usplash.conf

Then edit settings as follows:

yres=1280
xres=800

Save and exit, reboot your system and now your boot times SHOULD be sub 30 seconds :-)

---

### Post by crouton on 2007-12-17
> **woland said:**
> Pgi947&#1073;, I'm glad to read this.
Is you 200M, for AMD or Intel processors?

This happens to many different desktop/laptop configurations because the LiveCD incorrectly sets the bootsplash resolution too high.

---

### Post by woland on 2007-12-17
Pgi947, thanks!

I'll try that as soon I get to deal with my laptop.

About the fglrx, did you use the default driver?

What is your laptop's model?
Mine is MSI S420.

---

### Post by woland on 2007-12-21
My results so far:

I've installed Ubuntu Gutsy from alternate CD.
On the first boot the OS froze with blanc screen, like it did on previous installs from alternate CD.
On the second boot it did load normally.
The first thing that I did was installing updates.
Next I've tried to turn on the restricted driver from the respective menu.

I've wanted to enable the external monitor, but when I tried to load the Screens and Graphics" menu the screen went white, and the whole system froze, I  did have this experience with restricted drivers on Gutsy before.

I've installed ATI drivers from Alberto Milone's Envy packege.
I've used [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") to enable compiz.
It works now, sort of.
However, I could not enable my external monitor as extended desktop.

---

