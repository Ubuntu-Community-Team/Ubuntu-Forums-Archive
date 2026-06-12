---
title: "ACER 4202 WLMi and Dapper?"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by roobee on 2006-06-12
Hi there, 
I'm fairly new to Linux and was wondering if anyone could please offer advice on whether Dapper Drake will work on my Acer 4202 WLMi laptop? It's got an Intel Core Duo processor T2300, WXGA wide TFT lcd, Intel graphics media accelerator 950 and 802.11a/b/g wireless LAN. 

I've tried running the Breezy Badger live CD in the past, but it won't work - something to do with the graphics/lcd. 

Any advice on how I could make this work would be most appreciated.

Thank you very much, 
roobee

---

### Post by plaz42 on 2006-06-12
It seems like Dapper should work on your laptop, this thread has some info:

[http://ubuntuforums.org/showthread.php?t=138712&highlight=acer+4202](http://ubuntuforums.org/showthread.php?t=138712&highlight=acer+4202)

---

### Post by vr6stress on 2006-06-14
i'm running on one as i type this...

i've only had a couple of issues

1. video resolution didn't work out of the box - 915resolution fixed that
2. core duo wasn't recognized, downloaded a kernel that supported SMP and fixed that
3. cd rom/dvd no longer works - i think it happened after that new kernel, i haven't really got into fixing that yet, but there's a post around here about it
4. WPA support, it doesn't work as far as i can tell, i had it set up and the system would connect but i couldn't go anywhere, even found it to be a problem with WEP 128bit - so i'm back to WEP 64bit and it's working fine...

other then that everything worked out of the box - just watch out, your wireless won't turn on automactically if you shut down from linux so you have to turn it on with the switch up front, also with sound - go into the preferences and check everything on - the 'Front' is the most important..., one last thing install easy ubuntu or automatix and then movies and junk will work...

i set mine up as a dual boot and i'm super happy...i just need to get my dvd drive working again....lol

---

### Post by kingsidy on 2006-06-16
i own an acer 4202 wlmi. Everything works pretty good. Although when i boot i get an error: pci cannot allocate ressources. but it does not affect anything at all. Wireless work right out of the box. The resolution was screwed up, but it is easy to fix by installing 915resolution. In order to get both cores to work, install the 686 kernel, otherwise only one core will be used. It works pretty nice better than my old aspire

---

