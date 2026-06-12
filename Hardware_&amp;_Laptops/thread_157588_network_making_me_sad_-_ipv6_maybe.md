---
title: "network making me sad - ipv6 maybe?"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by jswan on 2006-04-09
I've set up linux on my laptop pretty easily but I've had some problems getting it working on my desktop.  Both for my laptop and desktop I followed this guide [http://ubuntuforums.org/showthread.php?t=87643&highlight=wired+ethernet+wiki](http://ubuntuforums.org/showthread.php?t=87643&highlight=wired+ethernet+wiki) to help me set up my network.

basically a few notes that might help is that I can reach the internet by both name and number through the terminal.  BUT I cannot reach the internet through my mozilla, apt-get command, or through Synaptic (a few places I tried).  To try and fix this I did this as the guide says
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

Still it works in the terminal but not anywhere else.  Now to make it more confusing, to get my network drivers to run I actually had to set up my repositories and apt-get the files.  So I know I have gotten it to work before.

Let me know if you have any suggestions or if you need more infor to make a suggestion

Thanks for any help!

---

