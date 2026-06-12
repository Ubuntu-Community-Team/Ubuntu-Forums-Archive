---
title: "Travelmate2300/ dual boot"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by charles_linux1 on 2005-03-31
O.k, trying to enter the wonderful world of Linux.

I see from other posts that the Travelmate2300 is compatible with Ubuntu (wirless and battery issues aside). I also see Acer sells a linpus version of the travelmate 2300 in Thailand. So what I'm attempting should work out. No Acer won't give me the drivers (their support sucks).

 Question1 - Are there any additional drivers required outside of the Unbuntu download for a succesfull installation on the travelmate 2300?

Question2- Anybody try a dual boot Win Xp/ Unbutu configuration on a lap-top? Yes I know drivers, hardware may diifer but I'm trying to assess Win XP compatability. Going to use Partition magic to set up a linux partition then try to install Ununtu. Should it be as easy as all that? 

Question3- **Does Unbuntu come with an interface that 'prompts' one which operating system I want to use? (Very Important)**

Any comments appreciated.

---

### Post by alehorb on 2005-03-31
Question2
I am using WXP/ubuntu on a Travelmate 730TX.
Question3
Yes it comes with a bootloader "GRUB" so you can choose.

---

### Post by charles_linux1 on 2005-03-31
Thanks! Will let you all know how it turns out.

---

### Post by urdoggy on 2005-04-05
Hi - 

I'm running Ubuntu on a TravelMate 3200 and almost everything works perfectly (ATI Radeon, modem, bluetooth, wireless, LAN...)

I dual-boot as well, but prefer using the Windows boot manager on the MBR, and having that kick over to grub which is sitting on the Linux partition. This is a little more work to configure, but it's what I prefer. There are plenty of guides out there to show you how to do it this way.

---

### Post by fernando on 2005-04-24
Be aware that by installing linux and overwriting your mbr you will loose the D-to-D recovery system (the Alt+F10 shortcut is built into the mbr)

Att,

Fernando

---

### Post by addikt on 2005-04-24
i have gotten ubuntu hoary to work fine on my travelmate 2200 ... just a couple of things though ... to get the sound and touchpad working you'll have to disable legacy support in the bios settings and search around the threads here to disable esd ... I suggest getting the synaptics drivers for your touchpad...other than that ubuntu picked up everthing else.

I have a dual boot setup with xp pro and ubuntu ... well during the installation ubuntu wouldn't install grub bootloader so I had to stick with lilo ... but lilo didn't show the xp pro initially so I had to edit lilo.conf and uncomment the required sections then run lilo and reboot and then it showed the operating systems in a menu (xp pro and ubuntu) ... bit of a pain, but hey you learn something. Also, for some reason my keyboard kept freezing at logon but you can solve that problem by disabling legacy support in bios or pressing Shift+C ... really weird problem.

---

