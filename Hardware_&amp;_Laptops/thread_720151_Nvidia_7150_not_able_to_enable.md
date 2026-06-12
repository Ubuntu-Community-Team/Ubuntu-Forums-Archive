---
title: "Nvidia 7150 not able to enable"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by ryan22158 on 2008-03-10
Hey I just installed Gusty on my dv2615nr and it seems like I am the only person that can't get the Nvidia 7150M graphics to work. My problem is that when I go to enable the resricted driver it gives me "The software source for the package nvidia-glx-new is not enabled" 

I have tried envy, I tried the drivers from nividia neither worked. And have read about 50 how to articles

please help......

specs
Hp dv2615nr
Amdturion64 1.9 ghz
2gb RAM
Geforce 7150m

---

### Post by ebe0 on 2008-03-10
I think you have not enabled all the repositories (main, universe, restricted and multiverse). To do this goto
System > Administration > Synaptic Package Manager > Settings > Repositories > Ubuntu Softwaare (it is the first tab there) > then enable all the options under "Download from the internet" . You can skip the Source code.
After this you can again try restricted drivers. It should work. Also this will work only if you have a working internet connection.
Please let me know it this helped.

---

### Post by ryan22158 on 2008-03-10
Okay so that worked. Thanks a lot. 

but now the walk through I have printed for my computer does not seem to work. As you can tell I have pretty much no idea what I am doing but I really would like to know how to get this working. 

But anyways the problem now is that the sort of walk through I have is having me reconfigure my x-server with this command "sudo /etc/init.d/gdm stop" and then after I get the okay that gdm is stopped they have me put in "sudo dpkg-reconfigure xserver-xorg" i follow the steps they have and it all seems to work in a logical sense(I am not stupid in the sense of how a computer should work, just how ubuntu works) but at the end Ubuntu restarts and says it is still in safe mode. Any ideas?

---

### Post by ryan22158 on 2008-03-11
Okay I got the graphics working but now I can't seem to get the wireless up and running. Same thing I followed my walk through that I have and once again it is not working. I have a BCM94311 wlan mini-pci (rev. 02) if anyone can help.

Like I said I tried the walk through which once again made sense to me. I installed the driver, supplied blocked a differed driver by putting it on the blacklist, and the added ndiswrapper to "sudo /etc/modules" but still a no go.

---

### Post by ebe0 on 2008-03-11
Go through this post: [WifiDocs/Driver/bcm43xx/Feisty No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). It has step by step instructions. For your hardware u'll have to use step 2a.
Please update info if you succeed in [http://ubuntuforums.org/showthread.php?p=2994162](http://ubuntuforums.org/showthread.php?p=2994162).
Let me know if this helped.

---

