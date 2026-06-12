---
title: "Ubuntu can't access my iPhone"
date: 2017-02-12
forum: Hardware
---

### Post by oisin000 on 2017-02-12
Hi, 

Something has changed recently and my Ubuntu laptop can no longer access the contents of my iPhone. It just gives a message: 
[I][B]Unable to mount <NAME>'s iPhone
Unhandled Lockdown error (-16)[/B][/I]
I have also seen the error codes (-20) and (-256) but usually it is (-16)
It is an iPhone 6 running iOs 10.2.1 which I just upgraded to today but it also failed to access it yesterday when the phone was running the previous version (iOS 10.2.0 I presume ?) 
I have Ubuntu 14.04 LTS installed 
I tried installing ifuse an libimobiledevice:[B][I]
sudo apt-get install libimobiledevice-utils ifuse
[/I][/B]I then issued the command
***sudo idevicepair unpair && idevicepair pair***
***ERROR: Device c3gac82f1a87cd08f97a4b6d1fe7d2804793341f is not paired with this host***
Its not clear if it was the unpair or pair command that was giving the error. So I tried just pairing:
[I][B]oisin@oisin-Latitude-E6410:~$ sudo idevicepair pair
SUCCESS: Paired with device c3gac82f1a87cd08f97a4b6d1fe7d2804793341f
oisin@oisin-Latitude-E6410:~$ sudo idevicepair list
c3gac82f1a87cd08f97a4b6d1fe7d2804793341f[/B][/I]
So it seems to 'pair' successfully with the phone however this doesn't allow access, when I try to open or mount the iPhone in the file browser it still just gives the same 'Unhandled Lockdown error (-16) message. 

So, does anyone know how to fix this? I know it was working in the past, both my Ubuntu and or my iPhone OS have probably been updated since it last worked.

---

### Post by mörgæs on 2017-02-13
H, welcome to the fora.

Are you able to access the phone from a live boot of 16.10?

---

