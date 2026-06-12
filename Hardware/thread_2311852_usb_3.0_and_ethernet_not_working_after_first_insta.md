---
title: "usb 3.0 and ethernet not working after first install 14.04.3"
date: 2016-01-30
forum: Hardware
---

### Post by amandine2 on 2016-01-30
Hello,

I have a PC (built on my own) with the following configuration :
- I7-4770K
- Asus Z87-PRO
- RAM 16Go G Skill Sniper
- NVIDIA GeForce GTX 760

Today, I have installed Ubuntu 14.04.3 in order to dual boot with Windows 7.
At first launch, Ubuntu froze after a few minutes and I had to restart my computer.
Since then, all USB 3.0 ports stop working neither on Windows, nor Ubuntu..

I have also noticed that the wired connection on Ubuntu not working either.

I've read a lot of threads today and tried some solutions but i can't find one to solve my problem.
Any idea to solve this issue?


Thanks a lot.
Amandine.

---

### Post by weatherman2 on 2016-01-30
If the USB 3.0 ports still don't work in Windows, try this:

- Power off
- Unplug the power cord
- wait about 60 seconds
- Plug back in and try again

If still no luck, repeat but remove the CMOS/RTC battery from the motherboard then try again

--

I recently tried to install Ubuntu 14.04.3 on a laptop with an Nvidia video card and I had trouble getting the video driver to work reliably, despite trying some online guides.  I eventually went back to 14.04.2 which worked perfectly - no glitches.

---

### Post by amandine2 on 2016-01-31
Hello weatherman2 and thank you for answering me !

I've unplugged and plugged back the power cord and USB 3.0 ports are working again both on Windows and Ubuntu. Thanks a lot ! : )

However, something is weird with the wired connection on Ubuntu. After the power cord manipulation, the wired connection was back for my first try on Unbuntu, then I switched to Windows to check the USB ports and when I came back to Ubuntu, the wired connection was not working anymore.

---

### Post by mörgæs on 2016-01-31
Hi, welcome to the fora.

We get a lot of questions about i7 / Haswell and similar processors, and most of the people who have problems are using dated software like 14.04. One of them is here: 
[http://ubuntuforums.org/showthread.php?t=2307234](http://ubuntuforums.org/showthread.php?t=2307234)

I suggest that you begin with a fresh install of 15.10.

---

### Post by amandine2 on 2016-01-31
Hello mörgæs, thanks for helping ! Can I use the software updater to upgrade or I have to start all over again ?

Edit: I try to follow this instructions [http://askubuntu.com/a/623027](http://askubuntu.com/a/623027)
But when I run this command line, I have an error :
 ```
~$ do-release-upgrade -d
Recherche d'une nouvelle version d'Ubuntu
Err Signature de l'outil de mise à niveau                                                                                                                                                                   
  404  Not Found [IP : 91.189.91.23 80]                                                                                                                                                                     
Err Outil de mise à niveau                                                                                                                                                                                  
  404  Not Found [IP : 91.189.91.23 80]                                                                                                                                                                     
0  o réceptionnés en 0s (0  o/s)                                                                                                                                                                            
WARNING:root:file 'utopic.tar.gz.gpg' missing
Récupération impossible
La récupération de la mise à niveau à échoué. Il y a peut-être un problème de réseau.
```

---

### Post by mörgæs on 2016-01-31
Maybe you can use the upgrader but I think it's a long jump to upgrade from 14.04 to 15.10.
I recommend a fresh install.

---

### Post by amandine2 on 2016-01-31
Hello again,

I think I've solved the issue ! : )

I have not updated my system yet. Before that, I wanted to check that the problem was not the ethernet adapter. I have this one : Intel Ethernet Connection I217-V. And I've found this related thread :
[https://bbs.archlinux.org/viewtopic.php?id=191981](https://bbs.archlinux.org/viewtopic.php?id=191981)

This solution works for me. Now I can switch between Windows and Ubuntu without loosing the ethernet connection on Ubuntu.

So the following solutions have fixed my problems :

1 - USB 3.0 not working on Ubuntu and Windows : unplug then plug back the power cord => thanks again weatherman2
2 - Ethernet connection (adapter : Intel® Ethernet Connection I217-V) not working on Ubuntu : 
> Turns out that the problem is related to WoL, and the solution is to turn of all the WoL features in the Windows Intel driver. This comes at a cost, as WoL will no longer be possible, but that won't be an issue for most people. Hope this helps :)

I don't really understand why this "Wake on Lan" thing is related to my problem but it's working now !

Thank you both of you for helping me !

---

### Post by weatherman2 on 2016-01-31
Glad you got it working.  I use WOL often myself, so my solution would probably be to disable the Intel NIC and install a PCI-E NIC instead.

---

