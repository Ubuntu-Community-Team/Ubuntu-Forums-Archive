---
title: "SiS Real256E / SiS661 FX video problem"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by teapot on 2005-08-11
This hardware on my Asus motherboard is not being autodetected, and I'm having problems installing a driver.

The SiS Real256E is actually just another name for the SiS661 FX video controller. There is a driver available online at 
[http://www.winischhofer.at/linuxsispart3.shtml#download](http://www.winischhofer.at/linuxsispart3.shtml#download)
but I'm unable to get it installed properly, probably because I'm doing something wrong.

I used Synaptic to install the x-driver-sis package from that site. Then I ran
sudo dpkg-reconfigure xserver-xorg
but had to manually answer many questions.

All I really want is to have my screen resolution at 1280xWhateverWillWork. And I want it to stay that way after a reboot.

Any help? Anyone?

---

### Post by teapot on 2005-08-12
Anyone?

---

### Post by teapot on 2005-08-13
Anybody have any ideas?

---

### Post by wvslkr on 2005-08-13
You really need to post more info to enable someone to help you.  Do you have any display at all?  Any error messages?  And post Xorg.conf if you can.  I am sure if you can be more specific someone will try to help. :)

---

### Post by az on 2005-08-13
The drivers at [http://www.winischhofer.at/linuxsispart3.shtml#download](http://www.winischhofer.at/linuxsispart3.shtml#download) are for 3d acceleration for certain sis chips.

If all you want is 1280x1200 or any other resolution, all you have to do is use the default xserver without changing anything.  How much video ram is allotted for your card?

If you need to reconfigure X, install xresprobe and then boot into recovery mode and do
dpkg-reconfigure xserver-xorg

Let it auto detect your hardware and when it ask your about monitor settings, pick medium and find 1280xwhatever at the highest refresh rate that will work for you.

type
init 2
 to get into the desktop after you finish with the reconfigure.

---

### Post by teapot on 2005-08-14
wvslkr:
Yes, I have video. The driver keeps coming up as "vesa" if I let Ubuntu have its way. Manually modifying it to "sis" as instructed on that website has no different effect or any other display modes available. I conclude I installed the package incorrectly, but I certainly don't know how to prove or disprove that.

azz:
The drivers do not deal with 3D acceleration. They do provide support for various parameters, such as gamma correction, and outputs. Also, they are optimized for use with the SiS chipsets. I'd rather use them then the vesa driver, mainly because it will let me do more things later than I'm doing right now. Auto-detecting ALWAYS gives me vesa.
I don't know the answer to "How much video ram is allotted for your card?" or how to determine it in Linux.

---

### Post by teapot on 2005-08-16
Anyone have any ideas? Please?

---

### Post by floppy on 2005-08-16
teapot,

Don't get too discouraged. I'm having problems with the SiS chipsets based on an Asus P4S800-MX motherboard.

I hope someone has some answers!

---

### Post by teapot on 2005-08-17
I guess I'll give up on this and simply get different video card. I was really hoping that my Asus motherboard's builtin video chipset would give ok performance under Linux, but I don't know how to accomplish that.

Just for the people using search: Don't use SiS video bridges, chipsets, Real256E, SiS661 FX or related items in Ubuntu, or perhaps in Linux in general. You won't get decent performance, and you won't get any help trying to get the SiS driver working.

---

### Post by floppy on 2005-08-17
teapot:

Don't give up yet. The thread I started yesterday about this has received a reply which might help you:
[http://www.ubuntuforums.org/showthread.php?t=57430](http://www.ubuntuforums.org/showthread.php?t=57430)

Perhaps we'll both learn how to do this after all.

---

