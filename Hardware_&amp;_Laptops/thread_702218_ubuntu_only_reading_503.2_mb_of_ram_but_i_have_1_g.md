---
title: "ubuntu only reading 503.2 mb of ram but i have 1 gb installed"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by pympnplaya on 2008-02-20
I have a sony vaio pcg-grz630 and i recently switched from xp to ubuntu. i have been fooling around with ubuntu for a while now and i love it. but i was checking out my system monitor and i noticed that it was only reading 503.2 mb of ram, but i have 1 gb of ram installed in the form of two 512 sticks. any help on this issue would be appreciated. thank you.

also i was running xubuntu and thought that it might have a limit on the ram it can use so i switched to ubuntu but it still reads only 503 instead of 1 gb. is there a limit on xubuntu for ram? because it runs better than ubuntu. than

---

### Post by pympnplaya on 2008-02-20
also i was running xubuntu and thought that it might have a limit on the ram it can use so i switched to ubuntu but it still reads only 503 instead of 1 gb.  is there a limit on xubuntu for ram?  because it runs better than ubuntu.  thanks.

---

### Post by fogNL on 2008-02-20
Stupid question, but do you have on-board video?  Perhaps that's taking up a big chunk of your RAM.  If so, you can alter that in your system's bios to use less.

---

### Post by pympnplaya on 2008-02-20
i am not sure i have a mobility radeon 7500c video card if that helps.

---

### Post by Zeotronic on 2008-02-20
I run Xubuntu, and I have 512mb ram... the system monitors I have recognize only 503... at first I though it wasn't taking into account what it needs, but after hearing this I am suddenly unsure. My hardware is completely different than pympnplaya's. I have two 256mb Rambus sticks.

---

### Post by Yellow Pasque on 2008-02-20
How are you folks determining the amount of RAM you have?
Try these commands:
```
sudo free -m
sudo dmidecode -t memory
```

Here is what I get from mine (I have two 1GB sticks with 256MB devoted to onboard video)
```
[root@myhost xf86-video-ati-6.8.0]# free -m
             total       used       free     shared    buffers     cached
Mem:          1759       1720         38          0        146        964
-/+ buffers/cache:        609       1149
Swap:          517          0        517

...relevant DMI decode output:
Handle 0x002B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 72 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

```

> is there a limit on xubuntu for ram? because it runs better than ubuntu.
No, there's no limit on RAM besides what the OS can physically handle (4GB for 32-bit, much higher for 64-bit). Xubuntu runs better in general because Xfce is less resource-intensive than GNOME.

---

### Post by Zeotronic on 2008-02-20
>              total       used       free     shared    buffers     cached
Mem:           503        497          6          0          5        155
-/+ buffers/cache:        336        166
Swap:         2000         14       1985

:( I normally just use the system load monitor in Xubuntu, which I simply LOVE. Whatever, unlike pympnplaya I am not missing enough ram to really need to care.

---

### Post by pympnplaya on 2008-02-21
i have 1 gb of ram installed so i can play WOW but since i switched from xp to ubuntu and tried to install WOW on wine it says i do not have enough memory so i checked and it is only reading one 512 stick and not the other.  ubuntu and xubuntu run great with it only reading 512 ram but i have 1 gb so i figure i should use all i got and i definitly need it to play WOW.  any tips/suggestions, thanks.

---

### Post by ZeroZ400 on 2008-02-21
Sounds like a hardware issue.  503 sounds like a normal number if you had just ond 512 stick installed and you have onboard video.  When you boot up, does the bios recognize the ram?  Have you tried reseating the ram?  Or booting up with 1stick in at a time?  Try that and let us know the outcome.

---

### Post by pympnplaya on 2008-02-21
well i took both my memory cards out and switched them and tested each seperatly in different slots and they both worked and then i put them in together and it only read 512 so i took them out and put them back in and now it is reading 1024 so i guess the actually memory slots are messed up but it is working now.  i should have known it was not xubuntu or ubuntu causing the trouble because they are awesome.  thanks for all the help!

---

### Post by Zeotronic on 2008-02-21
> i should have known it was not xubuntu or ubuntu causing the trouble because they are awesome.
While its uncalled for, I have to rain on your parade and point out that Xubuntu and Ubuntu have their faults too... everything does.

---

