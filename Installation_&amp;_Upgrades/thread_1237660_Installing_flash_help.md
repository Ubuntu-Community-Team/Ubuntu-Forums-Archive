---
title: "Installing flash help"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by Thiago511 on 2009-08-11
I just switched from windows to Linux, and I am having some difficulties installing plug ins. specifically Flash. I looked all over the internet, I tried all they told me. and it doesn't work..

I type:

rpm -ivh flash-plugin-10.32.18-release.i386.rpm

This is what I get:


error: open of flash-plugin-10.32.18-release.i386.rpm failed: no such file or directory

I have Xubuntu Linux

---

### Post by Thiago511 on 2009-08-11
bump

---

### Post by Thiago511 on 2009-08-11
guys I really need this

---

### Post by lexe-cc on 2009-08-11
You should use .deb files instead. RPM files can be installed but it's not the normal way of installing things.
You can find the .deb files on the adobe website. Also, if you're using firefox you normally can install flash when firefox requests to do so.

Cheers

---

### Post by kerry_s on 2009-08-11
> **Thiago511 said:**
> I just switched from windows to Linux, and I am having some difficulties installing plug ins. specifically Flash. I looked all over the internet, I tried all they told me. and it doesn't work..

I type:

rpm -ivh flash-plugin-10.32.18-release.i386.rpm

This is what I get:


error: open of flash-plugin-10.32.18-release.i386.rpm failed: no such file or directory

I have Xubuntu Linux

look in your menu-> system-> synaptic package manager
click on the right side & start typing: flash
if no flash shows, then you probably need to turn on all your repos.

---

### Post by ohmman on 2009-08-11
I agree with the previous suggestion, using the package manager.  My son and I successfully installed Ubuntu 9.04 on his Lenovo laptop in about 15 min.  Flash was the first thing he went for.  I guided him to the package manager and searched for Flash.  Presto!  Select, mark for install, Apply.  Done.

---

### Post by p2bc on 2009-08-11
Just download it from Adobe

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Select Linux, and make sure to choose **DEB** file formate.

That is it.  Double click on the downloaded file and enjoy.


take care

---

### Post by XxionxX on 2009-08-12
I Just had the same problem (I too am a windows noob). The suggestion that helped me was from another ubuntu user called warp99. This is what he told me.

> **warp99 said:**
> 
Here's how you can clean up the mess:

1) Open the Synaptic package manager and in the search locater enter "flash" without the quotations.

2) Remove and purge any packages that pertain to Flash, Gnash, Adobe Flash, or SWF. To remove and purge the packages right click on the package and choose "Mark for Complete Removal".

3) Go into your .mozilla/plugins directory, which is located in your user home directory, and remove ANY flash plugins that may have been installed.

4) Go to the Adobe Flash site located here:

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

And Choose the "deb for Ubuntu 8.04+", then press install

5) Choose the gdebi package manager to install the deb if Firefox asks, enter you sudo password and install as normal.

6) Open a terminal and type the following:

 	Code:
 	sudo update-alternatives --config firefox-flashplugin 
There should only be one flash alternative so nothing to configure. If not then choose the alternative that points to the following:

 	Code:
 	/usr/lib/adobe-flashplugin/libflashplayer.so 
After this the flash plugin will work. Be sure to follow all of the steps since we need to back out some of the other flash alternatives that you may have installed.


I hope that helps!

---

### Post by roharme on 2009-08-12
Use alien to convert .rpm to .deb files

---

### Post by Robert6 on 2009-08-12
It is very good.I really want this.Thanks for sharing this.Thank you.

---

### Post by aysiu on 2009-08-12
> **roharme said:**
> Use alien to convert .rpm to .deb files
Why? There's a native .deb already available.

---

