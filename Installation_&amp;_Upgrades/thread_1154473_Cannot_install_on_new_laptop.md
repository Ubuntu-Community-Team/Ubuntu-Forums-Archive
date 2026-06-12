---
title: "Cannot install on new laptop"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by sarwiz on 2009-05-09
Tried to install 8.04 on a new HP G60 notebook and I get an abnormal exit error. 

udevd-event[1549]: run_program: '/sbin/modprobe'  abnormal exit

(some other info about busybox I didn't write down)
Then the cursor after 
(initramfs)_

HELP  I really would like to use it on this computer, as I already have a dual boot with xp on my desktop, and have really not taken a liking to vista. I also tried 7.10 and it cannot find my graphics properties and then just hangs up.
 This has a mobile intel 4 series express chipset family with an intel 7.15.10.1518 driver and 1366 x 768 screen resolution. Am fairly new to ubuntu and am learning, but this has me stumped.

---

### Post by sarwiz on 2009-05-09
bump for help

---

### Post by RedSingularity on 2009-05-10
Did you try installing with the Ubuntu Alternate install cd?

---

### Post by sarwiz on 2009-05-10
NO I used a cd I burned from the download ISO, that I had previously used to install Ubuntu on my desktop. Downloaded and burned 9.04 last night, and may try that later today. So far, I have tried 8.04, 8.04 with Emc2,and 7.10. Will also try 6.06 and 9.04 later. Where do I get the alternate cd? ( I do have the dvd's that came with the book, and that one also failed, plus one I got from canonical in the mail last year, also same error. )Should I also try 8.10? I do have an iso of that as well.

---

### Post by wpshooter on 2009-05-10
> **sarwiz said:**
> NO I used a cd I burned from the download ISO, that I had previously used to install Ubuntu on my desktop. Downloaded and burned 9.04 last night, and may try that later today. So far, I have tried 8.04, 8.04 with Emc2,and 7.10. Will also try 6.06 and 9.04 later. Where do I get the alternate cd? ( I do have the dvd's that came with the book, and that one also failed, plus one I got from canonical in the mail last year, also same error. )Should I also try 8.10? I do have an iso of that as well.

Just go to the Ubuntu website and look for the ALTERNATE (which is a text based "installer" (not to be confused with the X desktop/server)) instead of the desktop/live CD version.  I recommend downloading from the Purdue server.

---

### Post by sarwiz on 2009-05-10
Thank you. I found the alternate dl's and have previously dlled from the argonne site, but since I live right by purdue nw i'll try that one. UPDATE: got 9.04 to install and run correctly, but the wireless will not connect. It found my card ok, and can find nearby networks, but won't connect to mine. I am on the same puter now running vista, and connected fine. I don't know where to look to find a way to diagnose this problem.

---

### Post by angellsl on 2009-05-10
I think network manager is up automatically in the system tray, you can try that

---

### Post by sgosnell on 2009-05-10
We need more information on the inability to connect.  What [exactly] have you tried, and what was the result?  Is the SSD being broadcast?  What security if any are you using?  What wireless card does the laptop have?

---

### Post by sarwiz on 2009-05-11
SSid is hidden with wpa2 security and a mac filter (mac address already installed), card is an Atheros wireless 802.11n . Am now working thru a post from the networking forum and trying to troubleshoot it. I'll post the actual card id when I turn it back on later.

---

### Post by spcwingo on 2009-05-11
I had the same problem on a HP dv6707us with Hardy.  I had to use wicd and ndiswrapper to get it to connect to any network.

---

### Post by sarwiz on 2009-05-11
On it now as I type. Had to delete my network, then connect as if it was the first time, and it asked for the password several times, and finally connected. Late now and have to work in the morning, but I'll poke around tomorrow night and see if I can retrieve some settings in here and post them. This is a new computer and a fresh install of 9.04. Tried 7.10 on up and this is the only one that would install. Thanks for all your help, and I'll be back on tomorrow night.

---

### Post by sgosnell on 2009-05-12
Try searching here and on Google for 802.11n and Ubuntu.  It seems to be problematic.

---

### Post by sarwiz on 2009-05-12
About to fire it up again, after work here, let's see if it connects again now. It was working perfectly last night, except no connection to my wd netcenter and the other network drives with that, (and the laser printer shared thru it) but I think I saw something somewhere that I had to get another program installed to connect to a windows network.  I'll post results in a bit.

---

