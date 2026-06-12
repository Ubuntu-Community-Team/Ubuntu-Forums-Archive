---
title: "Toshiba L300 - /sbin/modprobe' abnormal exit"
date: 2008-10-15
forum: Hardware
---

### Post by trapula on 2008-10-15
I know that this has been already posted, but I just have to bring the subject up again. I'm really going crazy about this, I would hate to use Windows all the time now when I got used to Ubuntu.
But there's no way to finish the installation process, I get the above error all the time. When I disable LAN-OnBoard the installation completes, but when I go back to BIOS and enable it, Ubuntu just won't load.

I'm not sure if there's a fix for this, but I would appreciate any help on the subject.

---

### Post by prshah on 2008-10-15
> **trapula said:**
> Toshiba L300 - /sbin/modprobe' abnormal exit

This is a common problem on the new Atom CPU + GL945 board combo. It has been traced to the Ethernet adapter. 

From the 'net I see the specs for your laptop to be a Core 2 Duo, so I don't know how far this is applicable to you; here's a quick test: Disable Ethernet in the BIOS, and then boot into Hardy (Intrepid?); does it work? If so, post back for more steps to enable Ethernet as well as use Ubuntu.

---

### Post by jfdunbar on 2008-10-16
I have a Toshiba L300 and have the same problem. I have run Wubi under Vista without trouble except that the WIFI didn't work. I didn't try to fix this as I wanted to get at least to running off the live CD first. I tried both 32 bit and 64 bit CD's with the same result as "trapula", then found this post and disabled the LAN, rebooted and, yes, Hardy loads fine but with no internet access. I too don't want to have to deal with Windows ever again so any help to go forward would be greatly appreciated.

---

### Post by jfdunbar on 2008-10-16
Correction on my last post, I have a Toshiba A300, not L300

---

### Post by trapula on 2008-10-31
> **prshah said:**
> This is a common problem on the new Atom CPU + GL945 board combo. It has been traced to the Ethernet adapter. 

From the 'net I see the specs for your laptop to be a Core 2 Duo, so I don't know how far this is applicable to you; here's a quick test: Disable Ethernet in the BIOS, and then boot into Hardy (Intrepid?); does it work? If so, post back for more steps to enable Ethernet as well as use Ubuntu.

Hi, thank you for your time.
Yes it's Core 2 Duo machine.

When I disable Ethernet I'm able to boot into Hardy without any problem. Let me know what I should to get my ethernet up again. Thanks!

---

### Post by prshah on 2008-10-31
> **trapula said:**
> 
When I disable Ethernet I'm able to boot into Hardy without any problem. Let me know what I should to get my ethernet up again. Thanks!

Install Hardy (or maybe now, better for you to install Intrepid), update it fully, and _then_ enable the ethernet in the BIOS.

The problem arises with 8.04, and goes away with 8.04.1.

---

