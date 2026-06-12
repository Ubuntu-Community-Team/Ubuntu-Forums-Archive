---
title: "dual boot problems"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by willannex on 2009-04-05
I have been looking for days for CLEAR answers to this problem but to no avail...
I installed Ubuntu 8.10 on my Dell Inspiron 1545 a few weeks ago and I love it - aside from the lack in music production software, and so I want to dual boot Ubuntu/XP. I have cleared off all of the crap on XP making a lite version exclusively for music production. I re-partitioned my hd in Ubuntu, restarted my comp with the XP disc inside, it checks my system, and then says it cant continue because it doesnt want to corrupt my hd or something to that effect, and thats it... no install. I tried with the full, bloated version of XP and ended up with the same results. I would actually prefer to completely wipe my hd and install windows first and then ubuntu, but ultimately in want a machine with XP and Ubuntu. If anyone can give me a clear and concise plan of action I would greatly appreciate it. The guide [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) which is frequently referred to on these threads was of absolutely no help.

Sorry for the long post!

---

### Post by 80toy on 2009-04-06
Same problem here.  I have ubuntu 8.10 already installed on my new lenovo laptop.  I am trying to install windows xp pro 64 bit on a NTFS partition (single hd), and i keep getting a **stop: 0x0000007b** error.  I am fairly sure that i have a driver problem but i cant figure it out.  I get the blue screen before i even get to the install, which i dont get because i thought that installs were self contained.  any help would be greatly appreciated.  Thank you.

edit: If you have more that 3.5gb of ram you should be using a 64 bit OS, a 32 bit wont work.  i tired this guide but i am still learning this stuff so i dont know how to check my drivers or my bios/boot settings.

guide: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by Mark Phelps on 2009-04-06
Open a terminal and do "fdisk -lu" (that's a lowercase L, not a one).  I suspect that you have your Ubuntu partition first on your drive and the MS Windows (typically) wants itself to be the first partition.

---

### Post by jigyb007 on 2009-04-19
I had a similar problem on my desktop. I keep getting the stop error 0x0000007b. I suggest looking into your bios settings and see which if AHCI or ATA. I changed my bios settings to use ATA and was able to get into windows. After this you probably will have to reinstall the AHCI drivers in windows to able to use AHCI mode again. Hopefully this helps...

---

