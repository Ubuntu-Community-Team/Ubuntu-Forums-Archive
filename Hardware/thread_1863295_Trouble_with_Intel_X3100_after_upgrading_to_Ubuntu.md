---
title: "Trouble with Intel X3100 after upgrading to Ubuntu 11.10"
date: 2011-10-17
forum: Hardware
---

### Post by v_mil on 2011-10-17
Hi Everyone!
I have Acer Extensa 5620Z with Mobile Intel GMA X3100. After upgrading from Ubuntu 11.04 x64 to 11.10 x64 I loss the possibility of plotting graph by SciLab. This program hangs after plot command. I try 5.3.3 version and last nightly build. The nightly build stay UNKILLABLE after plot command. I add a comment to the bug 3843 of SciLab but I receive an answer: this is an Ubuntu 11.10 problem with video card driver. I try a repository "http://ppa.lounchpad.net/xorg-edgers/ppa/ubuntu oneiric main". And no result. There is another way to workaround using 256 color mode but I can't find how to switch to this mode. I see only one possibility to workaround using VirtualBox. But it may slow down calculation speed. Please help me to solve this problem :(.
With best regards!
Viktor.

---

### Post by yrohinkumar on 2012-01-19
Hello Viktor,

I faced the very same problem and came across this solution...

[http://www.equalis.com/forums/posts.asp?topic=321201](http://www.equalis.com/forums/posts.asp?topic=321201)

check if it works for u... It seems to be problem with the libraries in Unity...(It's a confirmed bug now...Hope they correct it soon :) )

Hope this helps,
Rohin!

---

