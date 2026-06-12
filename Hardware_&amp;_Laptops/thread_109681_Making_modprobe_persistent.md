---
title: "Making modprobe persistent"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by seoatway on 2005-12-29
Hi

I am looking for a pointer to help with the following.
1. Acer Aspire 1710 with Broadcom chipset wireless
2. Ndiswrapper installed drivers no problem
3. Modprobe Ndiswrapper no problem.
4. Wireless activated in network control panel no problem
5. All works great.

However, when I switch the machine off and back on again I have to re-run sudo modprobe ndiswrapper to get the wireless driver back and then re-activate the interface in the network control panel. How can I make the modprobe persist across reboots ?. I've migrated from Mandriva where I didn't have this problem.

Thanks in advance.

Steve

---

### Post by kamstrup on 2005-12-29
Did you see this thread:
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

In the post linked below I explain how to make an init script that loads the nvidia drivers on each boot. Replacing nvidia with ndiswrapper should make it apply to your case... - Although I'm not sure this is what you really want...

[http://www.ubuntuforums.org/showpost.php?p=89594&postcount=18](http://www.ubuntuforums.org/showpost.php?p=89594&postcount=18)

---

### Post by seoatway on 2005-12-30
Hi

I found out how to do it, which was to add ndiswrapper in the /etc/modules file so it is loaded at startup, works great now.

Cheers

---

### Post by kamstrup on 2005-12-30
[QUOTE=seoatway]Hi

I found out how to do it, which was to add ndiswrapper in the /etc/modules file so it is loaded at startup, works great now.

Cheers[/QUOTE]

Doh! My bad. Your approach is the correct (and easier) one. I'm glad you are here to educate me :-)

---

