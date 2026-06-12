---
title: "Viewsonic VG1930WM 19&#8243; widescreen"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by Ingla on 2008-03-10
Hello.

I'm running Ubuntu Feisty on one machine and Dapper on another. They share a monitor. I also run XP sometimes of the Fesity box.

My monitor seems about to die. My son wants my to get a Viewsonic VG1930WM 19&#8243; widescreen

He's a Windows guy, so he doesn't worry about it, but I spend my time on Linux. I need to know that monitor would work - or could be made to without extreme measures.

The Feisty box is an AMD Althon 64 x2  dual core processor 4200+    using  VIA  and the video is nVidia Corporation GeForce 7100 GS, driver: "nv".

The Dapper box is old (maybe Pentium II or III?) Hardware information can't even identify it. The video card is Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter
driver: "sis"

Does anyone know if this monitor will work for me ... or can be made to with something simple like dpkg-reconfigure xserver-xorg?

Maybe Feisty could just recognize it? Dapper?

Any info much appreciated.

---

### Post by zubrug on 2008-03-10
Yes it works fine, if you have a decent graphics card then get a dvi cable if it is not included, I noticed an improved image after switching to a dvi cable, they are not cheap, wallmart was cheapest.

---

### Post by EXCiD3 on 2008-03-10
You will need a vga cable to use it on the Dapper box. You can buy an adapter (if one isnt included already) and do what zubrug said.

---

### Post by Ingla on 2008-03-11
Thanks for the replies.

Will I have to do anything to get Ubuntu to recognize it, or will it just work?

There's a howto at:
[http://ubuntuforums.org/showthread.php?t=274291]("http://ubuntuforums.org/showthread.php?t=274291")

It relates to a similar monitor and says basically to run

dpkg-reconfigure xserver-xorg
then
sudo nvidia-xconfig
then
add the frequency in xorg.conf as is 1680x1050[COLOR="Red"]_60 [/COLOR]and maybe change the horizontal and vertical sync rates in the Xorg.conf file
then
sudo /etc/init.d/gdm restart

Did you need all that to get it running? I've never done these things because I've never changed monitors since moving to Linux. Doesn't sound terrible but I'd like to be prepared. In the past I've needed to run dpkg-reconfigure xserver-xorg a couple of times and it was mainly accepting the defaults and hoping ... with a new monitor, I'll know all the specs.

---

