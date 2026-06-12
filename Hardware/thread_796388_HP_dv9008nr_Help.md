---
title: "HP dv9008nr Help"
date: 2008-05-16
forum: Hardware
---

### Post by Snyper_Vash on 2008-05-16
I've just installed 6.06 onto my HP Pavillion dv9008nr. I had some troubles with the live cd but i finally got it installed. Fortunately, from what i've read, my quick launch buttons and media remote already work without any extra installing. However, I cannot connect to my wireless network. 

Im new to linux, i have toyed around with it for a while now and know how to do terminal. I've been reading various threads on how to fix this problem. Yet, to no avail have i been able to get anywhere remotely close to getting my wireless working. I also have downloaded the HP Drivers for my laptop on another computer. I have the Nvidia  Drivers as well as the Wireless LAN drivers. I found out, apparently, Ubuntu wont read EXE files, therefore hindering me from installing my drivers.

If anyone could help, or point me in the right direction it would be greatly appreciated.

---

### Post by Snyper_Vash on 2008-05-16
I think the Executables need a program maybe?

---

### Post by Ayuthia on 2008-05-16
> **Snyper_Vash said:**
> I've just installed 6.06 onto my HP Pavillion dv9008nr. I had some troubles with the live cd but i finally got it installed. Fortunately, from what i've read, my quick launch buttons and media remote already work without any extra installing. However, I cannot connect to my wireless network. 

Im new to linux, i have toyed around with it for a while now and know how to do terminal. I've been reading various threads on how to fix this problem. Yet, to no avail have i been able to get anywhere remotely close to getting my wireless working. I also have downloaded the HP Drivers for my laptop on another computer. I have the Nvidia  Drivers as well as the Wireless LAN drivers. I found out, apparently, Ubuntu wont read EXE files, therefore hindering me from installing my drivers.

If anyone could help, or point me in the right direction it would be greatly appreciated.

Can you post your lspci -nn?  It will help us determine your wireless card.

EDIT: 6.06??? Can you also post your uname -a?

---

### Post by Snyper_Vash on 2008-05-16
lsvash@vash-laptop:~$ lspci -nn
0000:00:00.0 0500: 10de:02f0 (rev a2)
0000:00:00.1 0500: 10de:02fa (rev a2)
0000:00:00.2 0500: 10de:02fe (rev a2)
0000:00:00.3 0500: 10de:02f8 (rev a2)
0000:00:00.4 0500: 10de:02f9 (rev a2)
0000:00:00.5 0500: 10de:02ff (rev a2)
0000:00:00.6 0500: 10de:027f (rev a2)
0000:00:00.7 0500: 10de:027e (rev a2)
0000:00:02.0 0604: 10de:02fc (rev a1)
0000:00:03.0 0604: 10de:02fd (rev a1)
0000:00:05.0 0300: 10de:0244 (rev a2)
0000:00:09.0 0500: 10de:0270 (rev a2)
0000:00:0a.0 0601: 10de:0260 (rev a3)
0000:00:0a.1 0c05: 10de:0264 (rev a3)
0000:00:0a.3 0b40: 10de:0271 (rev a3)
0000:00:0b.0 0c03: 10de:026d (rev a3)
0000:00:0b.1 0c03: 10de:026e (rev a3)
0000:00:0d.0 0101: 10de:0265 (rev f1)
0000:00:0e.0 0101: 10de:0266 (rev f1)
0000:00:10.0 0604: 10de:026f (rev a2)
0000:00:10.1 0403: 10de:026c (rev a2)
0000:00:14.0 0680: 10de:0269 (rev a3)
0000:00:18.0 0600: 1022:1100
0000:00:18.1 0600: 1022:1101
0000:00:18.2 0600: 1022:1102
0000:00:18.3 0600: 1022:1103
0000:03:00.0 0280: 14e4:4311 (rev 01)
0000:07:05.0 0c00: 1180:0832
0000:07:05.1 0805: 1180:0822 (rev 19)
0000:07:05.2 0880: 1180:0843 (rev 01)
0000:07:05.3 0880: 1180:0592 (rev 0a)
0000:07:05.4 0880: 1180:0852 (rev 05)



Linux vash-laptop 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

---

### Post by gforster on 2008-05-16
I would check this out

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

I have a dv6607nr, which shouldn't be too much different. When I was on 6.06-7.10 that link helped me out tons. I believe the problem is that broadcom wireless is not too friendly with linux.

I will say that once I did a fresh install of 8.04, most things worked much better. If you wish to go with hardy, this link should get you set up in no time.

[http://ubuntuforums.org/showthread.php?t=769990]("http://ubuntuforums.org/showthread.php?t=769990")

hope it helps

---

### Post by Snyper_Vash on 2008-05-16
That document seems like it would help but since it requires me to put in code to terminal that requires the internet to download tar files, i can't do that since my main laptop wont even connect to the internet. I just tried wired too. If i manually download those files on my windows laptop and transfer them from my flash drive will they still work the same way?

I'll probably switch to Hardy anyway since its newer and it will give me better support. But since this download will take me another 2 hours, i guess i'll just mess with linux some more.

---

### Post by Snyper_Vash on 2008-05-16
I take that back, my laptop is working fine while wired into the router. I guess now i'll try the how to but i think i'll just do a new install of Hardy. I guess i'll keep reading the How To just for  Terminal experience. Thanks a bunch both of you. I knew i left Windows for a reason.

---

### Post by Ayuthia on 2008-05-16
> **Snyper_Vash said:**
> I take that back, my laptop is working fine while wired into the router. I guess now i'll try the how to but i think i'll just do a new install of Hardy. I guess i'll keep reading the How To just for  Terminal experience. Thanks a bunch both of you. I knew i left Windows for a reason.

By the way, if you go with Hardy, your card should be able to connect to the internet by just installing the firmware.  Just go to System->Administration->Hardware Drivers Manager and click on enable Broadcom(Can't remember the exact wording).  It would be the best place to start because the NDISwrapper route has more steps.

---

### Post by gforster on 2008-05-17
> **Ayuthia said:**
> By the way, if you go with Hardy, your card should be able to connect to the internet by just installing the firmware.  Just go to System->Administration->Hardware Drivers Manager and click on enable Broadcom(Can't remember the exact wording).  It would be the best place to start because the NDISwrapper route has more steps.

Not necessarily.  It never even showed up for me when I installed hardy. It wasn't that hard to get it going though. Actually, it was easier than ever.

---

