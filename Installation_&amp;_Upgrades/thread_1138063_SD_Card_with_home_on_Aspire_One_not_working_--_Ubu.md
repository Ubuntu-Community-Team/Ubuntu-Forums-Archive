---
title: "SD Card with /home on Aspire One not working -- Ubuntu 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by casainho on 2009-04-26
Hello :-)

On my Aspire One (model ZG5 with last BIOS version) the live install session don't show to me the SD Card, where I have my /home directory, so, I can't install Ubuntu 9.04.

I did upgrade from 8.10 to 9.04, all went ok but system can't find the SD Card so I can't login because it is missing my /home. Did put my /home on one SD Card of 16GBytes when using Ubuntu 8.10 and it worked perfect.

Does anyone know how I can put the SD Card reader working? (note: me and my girlfriend, we have the same model ZG5 and the problem happens on both).

We are booting with the SD Card inserted.

I have one desktop PC where the upgrade from 8.10 to 9.04 went perfect (this one where I am writing this message).

Thanks in advance.

---

### Post by nco on 2009-04-29
Hi,

I have the same problem - the SD card slot and the multi format slot both don't work properly but I have found the error to be inconsistent.

Yesterday it was seeing the cards with automount and mapping icons to the desktop but today nothing.

I can see the cards detected with dmesg but for some reason the OS isnt mounting them.  Sometimes dmesg shown errors witht he cards ad sometimes it does not.

I was reading some where that it is a bad idea to powerdown to standby with the cards inserted (people have lost data) but I like to put the PC into standby since it speeds up reboot if I am away for a few hours.

I am using "Linux4One" - this is an ubuntu remix but with many of the patches already worked in to the kernel to make set up out of the box for the Aspire One much quicker.  Everything appears to be working other than the SD cards and Fan control (I need to update the BIOS to apply this fan control patch)

Mostly excellent, just this annoying little bug is making me not use the SD cards and with only 8 gig internal I really do need use of the SD slot!

Neil

---

### Post by casainho on 2009-04-29
I think I will try that version of Ubuntu.

I read after that the problem is with just some SD Cards, not every card!!

I am using a 16GB SD Card bought on Ebay (cheap one from China, slow, and probable bad quality).

---

