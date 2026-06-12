---
title: "How do i install the backports module"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by brhokla on 2009-08-10
Hi,

I am a dummy to ubuntu but I'm dead set on using it rather than Windows Vista.  I have a nice little Gateway LT3103U Netbook with an AMD 64, 2 gigs ram, 250gig hard drive and I have installed Ubuntu and it works flawlessly.  I however can't get the wifi to work at all.  I understand that I have to install some backports modules but I cannot figure out how to do this.  I also am unsure of which ones I need.  Anybody know?  I have to download everything in Vista then reboot and install in ubuntu as I can't get the wifi to work It is the ath9k

---

### Post by brhokla on 2009-08-10
Tried installing wireless but here is what I got. 
 
	 	 brhoward@ubuntu:~$ modprobe ath9k  
 WARNING: Error inserting cfg80211 (/lib/modules/2.6.28-11-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted  
 WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted  
 FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Operation not permitted  
 brhoward@ubuntu:~$  
 
Why would it say Operation not permitted?

---

### Post by Partyboi2 on 2009-08-10
> **brhokla said:**
> Tried installing wireless but here is what I got. 
 
          brhoward@ubuntu:~$ modprobe ath9k  
 WARNING: Error inserting cfg80211 (/lib/modules/2.6.28-11-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted  
 WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted  
 FATAL: Error inserting ath9k (/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko): Operation not permitted  
 brhoward@ubuntu:~$  
 
Why would it say Operation not permitted?
You need to put 'sudo' in front of the command so it would be
```
sudo modprobe ath9k   
```

---

### Post by petersra on 2009-08-10
Do you mind telling us how you got the liveCD to install?  I have tried every option with my Gateway LT3103, USB DVD reader and flash disk.  Always get the same errors.

---

### Post by ufoDziner on 2009-08-17
I downloaded the desktop 64 iso and used UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to make the USB stick bootable.

---

