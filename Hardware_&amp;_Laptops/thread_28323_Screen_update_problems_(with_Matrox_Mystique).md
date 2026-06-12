---
title: "Screen update problems (with Matrox Mystique)"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by Michiel Wittkampf on 2005-04-19
Hi all!

I use Hoary with a Matrox Mystique graphics card. It is difficult to use the computer because the screen doesn't update correctly, especially when I scroll in for example a browser. Parts of the screen are duplicated, others are not shown. I can not make a screen shot of it, because when I do, the screen updates correctly again. Other way's to temporarly solve the problem are: reloading the webpage (if it is a browser) or minimizing and maximizing the window.

Does anyone know how to solve this? I looked up for a solution for quite some hours now, but I can't find a solution. Probably because I'm new to Linux.

Thanxs in advance,
Michiel

---

### Post by alastair on 2005-04-19
What X driver? Maybe a problem with it.

Post your :

/etc/X11/xorg.conf

and

/var/log/Xorg.0.log

Maybe try the "vesa" driver.

---

### Post by Michiel Wittkampf on 2005-04-20
Hi alastair,

X driver: mga

Requeste files are attached (to long to include).

I changed the xorg.conf a bit because the monitor was not identified. But that did not change the problems I spoke about, it only solved another one.

I would be very glad if you know a solution. I will try the vesa driver.

Greetings,
Michiel

---

### Post by Michiel Wittkampf on 2005-04-20
Hi again,

The vesa driver solves the mentioned problem. YET, with the vesa driver:
- I only have a resolution lower then I use in my other operating system
- while the refresh rate in the system->preference->screen resolution is high enough, the actual refresh rate is very low according to my observations

So, I hope that there is an other solution.

Greetings,
Michiel

---

### Post by alastair on 2005-04-26
Hi Michiel,

I might not be able to help much. You should definitely do some web searching and see if others have the same problem. I had a quick look and found a bug that /might/ be relevant to you :

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=144071](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=144071)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124028](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=124028)

There might be other things around.

Some points :

1) Your log file seems OK generally, but does have the error :

(EE) MGA(0): Static buffer allocation failed, not initializing the DRI
(EE) MGA(0): Need at least 5832 kB video memory at this resolution, bit depth

Earlier, it probes :

(--) MGA(0): VideoRAM: 4096 kByte

Do you only have 4 MB video ram?

If not, you could try the "VideoRam  <mem>" option in the conf file (see : man xorg.conf)

2) You are using depth "16" - have you tried other depths? e.g. 24, maybe at 1024x768? (assuming you have only 4 MB vram). Or 8 bits, as a test.

3) At depth 16, you are using ONE mode "1152x864" - the "vesa" modes probed include (are listed as) : 

1024x768@75Hz
1280x1024@75Hz
1152x870@75Hz

Futures modes add "1600x1200" (see the X log file). Have you tried different modes/res? Why "864"?


You can also do : "man mga" to look at the MGA driver manual page for some settings you could try changing.

Sorry I cannot help more. I will have a think.

---

