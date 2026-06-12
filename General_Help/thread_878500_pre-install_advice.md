---
title: "pre-install advice"
date: 2008-08-03
forum: General Help
---

### Post by maxreason on 2008-08-03
#1: When I tell the ubuntu download page that I have a 64-bit CPU (phenom x4 9850), does that mean it downloads the 64-bit version of ubuntu, or something else?
 
#2: I see ubuntu distribution CDs and distribution DVDs for the same version. But when I download, all I see is one choice, which is 692MB - which fits on a CD. Do the DVD distributions contain more software, or do they contain the exact same contents as the CD? If they are not identical, how do I download the DVD distribution? The fedora8 and fedora9 distributions I have downloaded and installed over the past year fill most of a DVD - hence my question about ubuntu.
 
#3: If a 64-bit ubuntu does in fact exists (which appears to be the case), what kind of problems should I expect?
 
#4: If I install 64-bit ubuntu, can I develop (debug and test) 32-bit and 64-bit versions of my programs without needing a 32-bit ubuntu somewhere?
 
#5: I am trying this switch to ubuntu because fedora9 has become so overwhelmingly difficult and time-consuming [for me] to get working well enough to continue developing the software I was developing on fedora8. The software is a 3D simulation/graphics/game engine that assumes [at least] OpenGL 2.0+ and GLSL 1.1 - and I was developing in the eclipse C/C++ development environment with nvidia graphics cards (7800 and 9800, and soon to include a 280 series) - which absolutely, positively need to have full nvidia driver support for the GPU hardware/features. Is any of the above likely to be problematic or difficult on ubuntu (32-bit or 64-bit)?
 
#6: What is the ubuntu equivalent of the livna package for fedora?
 
Thanks in advance for your suggestions.
 
-----
 
my 2 nearly identical computers:
motherboard = MSI K9A2 platinum
disk drives = SATAII: 1x 1TB + 2x 250GB
memory = 2 x 2GB 800MHz DDR2-SDRAM
CPU = AMD phenom x4 9850 (not overclocked)
video = nvidia 7800GTX and nvidia 9800GTX video cards
monitor = Dell 2405FPW 1920x1200 LCD DVI display screens
two extra gigabit ethernet ports with RJ45 connectors on PCIe card
 
-----

---

### Post by tamoneya on 2008-08-03
its usually best to post separate questions in separate threads because when you have one mega thread you get several discussions going in separate directions but I will try my best

1. Since you have a 64 bit CPU you can run either 64 bit or 32 bit ubuntu
2. the version you are seeing is the CD version.  There is a larger 4 GBish version and it does contain more stuff.  It contains additional programs that you can install.  You can still install these programs though if you have the CD version.  Instead the CD version queries the ubuntu servers for the software when you request it.  The dvd's are nice if you need to install on a computer that doesnt have internet access.  Otherwise the DVD is a waste of bandwidth as 99% of the extra packages will never be used.
3. 64 bit is pretty problem free now.  Take a look here:[http://www.google.com/search?hl=en&safe=off&pwst=1&q=+site:ubuntuforums.org+ubuntu+64+bit+vs+32+bit](http://www.google.com/search?hl=en&safe=off&pwst=1&q=+site:ubuntuforums.org+ubuntu+64+bit+vs+32+bit)
4. Yep.  You can just use the package ia32libs.
5. This sholdnt be a problem.  The hardware driver manager should detect your card and take care of the restricted drivers.   Otherwise you can use envy.
6. That is most likely medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Sef on 2008-08-03
It looks like a mixture of Medibuntu and Multiverse.  The latter is packages that are not open source.

---

