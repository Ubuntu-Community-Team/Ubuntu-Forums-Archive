---
title: "lenovo t61p wireless led"
date: 2008-08-02
forum: Hardware
---

### Post by stefansjs on 2008-08-02
I just recently bought a Lenovo thinkpad t61p and installed Ubuntu 8.04.  Everything works great except for on little thing that's not very important, but still bothers me.  The Wireless status light does not turn on at all.  When I boot the computer the bluetooth indicator seems to show the status of wireless, but when I suspend and bring it back up, that doesn't even work.  Does anybody know how to make the wireless and bluetooth status indicators work properly?
thank you

---

### Post by cprofitt on 2008-08-03
> **stefansjs said:**
> I just recently bought a Lenovo thinkpad t61p and installed Ubuntu 8.04.  Everything works great except for on little thing that's not very important, but still bothers me.  The Wireless status light does not turn on at all.  When I boot the computer the bluetooth indicator seems to show the status of wireless, but when I suspend and bring it back up, that doesn't even work.  Does anybody know how to make the wireless and bluetooth status indicators work properly?
thank you

I will look at this on Monday for you... my T61 is a work laptop and I do not have it with me right now.

---

### Post by geminiviper on 2008-08-05
I'm having a similar problem on my Lenovo 3000 N200, I just don't have a working wireless LED...

---

### Post by beercz on 2008-08-20
> **geminiviper said:**
> I'm having a similar problem on my Lenovo 3000 N200, I just don't have a working wireless LED...
Same here on the same laptop.
Any ideas anyone?

---

### Post by spawn. on 2008-11-25
This may be old, but I'm relatively new on the forum. I own a new T61p myself.  You can fix it by checking out this thread...

[http://ph.ubuntuforums.com/showthread.php?t=774625&page=2](http://ph.ubuntuforums.com/showthread.php?t=774625&page=2)

---

### Post by spawn. on 2008-11-25
Okay, if the above thread did not help you - in the case that you haven't already solved your problem. 

Here is what I did to fix my led light issue. This works for both WiFi and Bluetooth Led lights on the ThinkPad T16p.

Open Synaptic Package Manager:

Search term "linux backports"

Install or reinstall the following:
> linux-backports-modules-hardy 2.6.24.21.23 -->Section: metapackages
linux-backports-modules-hardy-generic 2.6.24.21.23 -->Section: generic
linux-backports-modules-2.6.24-21-generic [2.6.24-21.27] -->Section: Base


As you can see, I'm running Ubuntu 8.04. I haven't checked how things work on 8.10. I'd rather stick with long-term-releases.

---

