---
title: "XPS13 7390 wireless stopped working on 19.10 after update yesterday"
date: 2019-10-23
forum: Hardware
---

### Post by thebeardedone on 2019-10-23
Yes, I am fairly new to Linux, but I love it so far. Long story short, I have the XPS13  dev. Went from 18.04 LTS to 19.04 and all working. THen upgraded to  19.10 last week and wireless stopped working. I have the Killer 1435. 

  I tried stuff from these sites with multiple reboots and it suddenly  started working. Unfortunately I was so frustrated (and stupid) I did  not log what I did to get it working. 


  [https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/](https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/)

  [URL="https://support.killernetworking.com/knowledge-base/wi-fi-issues-with-1435-1535-1525-on-debian-ubuntu-and-arch/"]
https://support.killernetworking.com/knowledge-base/wi-fi-issues-with-1435-1535-1525-on-debian-ubuntu-and-arch/[/URL]

  [URL="https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release"]
https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release[/URL]

  [URL="https://askubuntu.com/questions/1172026/killer-wireless-1650-on-ubuntu-18-04-doesnt-work"]
Killer Wireless 1650 on Ubuntu 18.04 doesn't work[/URL]

  
I did an update yesterday (sudo apt update && sudo apt  full-upgrade -y) and after a reboot, wireless network stopped working. I  have a LAN adapter and using it now. 

  If I go to SOFTWARE & UPDATES | ADDITIONAL DRIVERS, I see "Intel  Corporation: Unknown: THis device is not working".  There are three  options.  -Using iwlwifi driver backport in DKMS format for backport-iwlwifi-dkms  (Open SOurce)      *This is grayed out and I can not choose it to even test -Continue using a manaully installed driver     *This I can click, but after reboot, it is unchecked. -Do not use this device     *This is always selected.

  
Any help would be GREATLY appreciated.

---

### Post by mörgæs on 2019-10-25
Hi, welcome to the fora.

As a first and general experiment I always suggest a clean install of 19.10 using the LAN connection. After that apply all updates and reboot without LAN. Is there any change?

---

