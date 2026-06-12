---
title: "USB/Wireless Mouse Not Working - Solution"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by varunrai on 2008-02-28
HI,

I am using Gutsy Gibbon(Kubuntu 7.10). Few weeks back i got some updates to be installed and then suddenly after i restarted my laptop, lost the resolution. Everything became so big!
I started searching for solution to this problem as in the Display Settings I could only see one Resolution 640x480. One of my friend suggested to use dpkg-reconfigure xserver-xorg. Ureaka! I found my answer. Got my resolution back! Everything was working fine except my Wireless mouse.

Now almost two weeks later have been trying to find a solution but could not get any. Many people posted about this but none of them worked. Finally I was able to find the solution. When I was using the live cd my mouse worked. I just copied the xorg.conf file while using the live cd and pasted on to mine. It started working. Was able to use my mouse. This might not be the correct way (as im new to linux world) but for people who cannot find solution for this and at last lost their hope to fix. ;) May be this can help!

Thanks,:guitar:
Varun

---

