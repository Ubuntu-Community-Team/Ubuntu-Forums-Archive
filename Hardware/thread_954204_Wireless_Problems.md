---
title: "Wireless Problems"
date: 2008-10-20
forum: Hardware
---

### Post by elliott229 on 2008-10-20
Hey I have an Atheros 802.11 wireless card in my acer aspire 4520 and it won't work. i took it out of my computer and the driver in the restricted driver program went away but my nvidia graphics card stayed. but when i plugged it back in the drivers showed up again. i know my computer finds it but the network utility in ubuntu won't give me the wireless network option. 

2.) also i want to get back vista and set up a dual boot with linux. in the manuel for my computer it says there is a 10 GB hidden partition that is accessable by pressing alt-f10 when you have the option to get into cmos but when i do that nothing happens. i did read online that it will only work with a FAT32 hard drive not ntfs or ext3 or any of that good stuff. i am okay with reformatting my hard drive because i have a 320Gb external to back up whatever. i think if i could reformat to FAT32 i might be able to work this thing. oh yeah and i found i file called lost and found and i was thinkin that might be my long lost partition

if anyone could solve either of those that would be amazing. 

thank alot,
Elliott

---

### Post by theirishfozz on 2008-10-21
What is the exact model of your wireless card? You can find out by typing 
> lspci | grep Atheros

If that doesnt work then try just "lspci" and scroll down the list.

Check the device compatibility on Madwifi and if the device is supported then follow the instructions on that site.

> [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
> [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If its not supported then try using ndiswrapper.

---

### Post by AndyCat on 2009-01-07
Hey there Elliot, i had the same problem with my aspire 4520. I installed ubuntu 8.10 on it and the wireless support was gone. Even though it says that the restricted drivers for the atheros card are present it just wont work. So i decided to go back to vista for a while (i dont like it but at least works).
About your partition... well let me tell you that if you installed a fresh guided installation (it means that ubuntu formatted your hard drive and everything was deleted, even the hidden partition) then what you are gonna have to do if you want to go back to vista is:
1. either you buy a recovery set of discs from acer online (mine were 30 bucks)
2. you get a vista cd and install it by yourself.

in both cases if you want to install vista again you are gonna have to format your hard drive again but this time with a fat partition. you can use any version of windows for that.

If you need more help just let me know.

hope this helps

---

