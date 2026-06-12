---
title: "Problem installing with Asus P5B"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by ddausch on 2006-08-15
I have a new computer with an Asus P5B motherboard and a Intel Core2Duo E6400 processor. I have problems installing any linux on this machine. :)

No matter what mode i set the intel sata controller to (enhanced, combatible, ahci, ide) and no matter what mode i set the jmicron controller to (ide, raid, ahci) no cd-rom gets detected after selecting the language in the ubuntu installer. 

I already connected a dvd-drive to the pata port of the jmicron controller, with an pata2sata adapter to the sata port of the jmicron controller and with the adapter to the intel sata controller. No way, he does not detect any cd drive... :(

---

### Post by ddausch on 2006-08-15
I just connected the cd-rom to a usb adapter. With this i can start the installation and he detects a seagate s-ata hard drive connected to the same s-ata controller without problems. Why does he detect the hd but not the cd-rom? :)

---

### Post by moritz1 on 2006-08-20
It must be possible to get the JMicron driver somewhere, no?

---

### Post by thotz on 2006-08-22
> **moritz1 said:**
> It must be possible to get the JMicron driver somewhere, no?

Moritz, I read that this driver will be added in Linux kernel 2.6.18. The easiest way would be that the Ubuntu developers backport the JMicron driver.

---

### Post by smt on 2006-08-22
Have you tried adding an "all-generic-ide" parameter to the kernel?

I don't know if it does the trick in Ubuntu, but at least it works with Fedora: [http://forums.fedoraforum.org/forum/showthread.php?t=120378](http://forums.fedoraforum.org/forum/showthread.php?t=120378)

---

### Post by langerdan on 2006-08-23
I had the same problem, but worked around using PXE boot. You need to enable this in the BIOS under LAN config - it's off by default.

This worked for me: 
Enable the two LAN ports, one PXE on and the other "boot disabled".
Connect both ports to your LAN
Set up tftp as outlined in [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
Use
 filename "pxelinux.0";
if you're using dhcpd (wiki gives dnsmasq instructions)

---

### Post by Encryptor on 2006-08-24
I just tried to add the "all-generic-ide" in Ubuntu, and nothing happened. Same CD detection problem. I was able to do a minimal network installation, and then used Synaptic to install everything else.

---

### Post by OnkelJens on 2006-08-25
Hello,

I have the same problem with my PATA hard drive. My SATA DVD drive
is detected fine. But I have found no way to let ubuntu detect my
PATA Hard Drive. I tried all bios setting and also "all-generic-ide".
Something strange is that an Win XP installation CD detects the drive,
so it must work with some kind of a "generic driver".

Any ideas?

---

### Post by gruntu on 2006-08-25
I got mine to work. Obviously you can only do this if you have a PATA drive. Go to the Bios - Main - IDE Configuration - Onboard IDE Operate Mode and change from Enhanced Mode to Compatible Mode. Also change IDE Port settings to [PATA Ports Only].

I tried reverting it back after I installed Ubuntu or Knoppix but it failed. So I guess I will have to keep these setting until they release the 2.6.18.

---

### Post by steelfanatic on 2006-08-26
I got mine (Mepis) to work  by DVD USB2 installation.

---

### Post by gruntu on 2006-08-26
I just installed edgy and it is very fast. I didn't try installing it the ide enhanced turned on but I was able to turn it on and boot up after install. Last night I also tried Suse 10.2 beta 3. It is supposed to have the 2.6.18 kernel but it failed. 

Try edgy it has to be the fastest OS I have tried since Gentoo.

---

### Post by andrewpmk on 2006-08-26
Link to the main thread on this problem: [http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron](http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron)

---

### Post by steelfanatic on 2006-08-27
> **gruntu said:**
> I got mine to work. Obviously you can only do this if you have a PATA drive. Go to the Bios - Main - IDE Configuration - Onboard IDE Operate Mode and change from Enhanced Mode to Compatible Mode. Also change IDE Port settings to [PATA Ports Only].

I tried reverting it back after I installed Ubuntu or Knoppix but it failed. So I guess I will have to keep these setting until they release the 2.6.18.

"Also change IDE Port settings to [PATA Ports Only]." I did not see this setting,just the first, is your PATA CD/DVD working at boot?

---

### Post by thotz on 2006-08-28
Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.

---

