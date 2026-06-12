---
title: "Download Jaunty packages in intrepid"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by pratiks19 on 2009-06-02
The title may be sounding ridiculous.
But I really want to know if this is possible.

Jaunty does not come with "**wvdial**" package installed.

I connect to the internet using wvdial. So unless I have wvdial installed, I cannot connect to internet to update my repositories. It is a running-around-the-bush type of problem.

I currently use intrepid. So is there any method by which I can download the wvdial package for jaunty with all dependencies satisfied (automatically) ?

---

### Post by Therion on 2009-06-02
I suppose the enterprising Ubuntu user could add the Jaunty repositories to their sources.list file - JUST long enough to use Synaptic to download the package and any required dependencies - and then remove those entries before one's system got hosed.

---

### Post by GeorgeVita on 2009-06-02
Hi **pratiks19**,
please read [http://ubuntuforums.org/showpost.php?p=7386429&postcount=8](http://ubuntuforums.org/showpost.php?p=7386429&postcount=8)

There are 5 .deb packages to install. You could make a zip file with all of them (be sure to check their integrity and 32/64 bit version).

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

My .zip file for i386 32bit (size: 1,04 MB):
[http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip](http://acomelectronics.com/GeorgeVita/wvdial_904_i386.zip)

Info and checksums included (read them: [http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html))

I test it by copying all to a USB memory stick, and then paste them (or unzip them) to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking each icon (of .deb package) in "as listed in above" order (1,2,3,4 and finally 5).

I think if anybody wants to automate this, he could edit the .iso creating a new 9.04_wvdial distro:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

Regards,
George

---

### Post by pratiks19 on 2009-06-03
Thanks to both of you.
I dont think it is safe playing with the repos..
so I downloaded the wvdial packages and the dependencies manually.

I'll try the Live CD customization after my jaunty is set up.

Again, thanks for the great support !!

---

