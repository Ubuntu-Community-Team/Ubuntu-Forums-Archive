---
title: "USB devices take 45-90s to recognize"
date: 2014-01-24
forum: Hardware
---

### Post by BoogeyOfTheMan on 2014-01-24
Whenever I plug in a USB device  (phone, usb drive, external hdd, kb, mouse, etc) to my desktop, it takes a while to be recognized. Usually around 1 minute, but sometimes long enough for a quick bathroom break. Last night I was trying to put something on a USB drive and transfer it to my laptop, but the drive was recognized right away by my laptop, so I knew it wasn't the drive and it was most likely an issue with my desktop. The devices seem to work fine once recognized though.

It doesn't seem to matter what port I plug a device into, the USB2 or USB3 ports on the back of the mobo, or the USB2 or USB3 ports on the front of the case connected to the pins on the mobo.

Unfortunately I had assumed it was a problem with my phone at first, (my phone was having a similar issue when connecting to my laptop) so I'm not sure when it started. It used to work fine though. 

I've tried searching for a solution, but every time I run a search with the words "usb" and "slow" in the search terms, I end up with numerous pages of issues about USB speed, which I am not having. So I apologize if this has been covered, as I could not find it.

I'm also experiencing some graphics issues at the moment, so I'm listing my specs from memory, I will update with more information when possible.

Kubuntu 13.10
ASRock Mobo
Intel i5 Haswell @ 2.9ghz
16gb DDR3
128gb Samsung 840 SSD
Onboard gfx (trying to get a Geforce GTX 580 to work again atm)
Onboard sound
Asus wireless card

---

### Post by sudodus on 2014-01-25
Things like that can be hard to debug. Maybe a good start would be to check if it is caused by some software issue of your current installed system.

- Try how the USB devices are found, when you boot from a live CD/DVD/USB drive, for example the Kubuntu install drive (if you still have it). You could try some versions, flavours, distros, that you might have available or can download.

---

### Post by BoogeyOfTheMan on 2014-01-27
Thank you sudodus, I dont know why I didnt think of trying that. Unfortunately I encountered the same problem when booting a live distro (Kubuntu 13.10). It also took an extremely long time for the live distro to run, so I'm leaning towards a hardware issue of some sort. I've also been experiencing a problem where my pc hangs on shutdown/reboot, causing me to have to hold the power button down, and the live distro also hung on reboot.:(

---

### Post by sudodus on 2014-01-27
Well, I'm no hardware expert, but it is possible that there is a hardware problem.

Have you always had this problem (with slow USB) on this machine, or is it something that just started recently?

There might also be problems for the software and hardware to cooperate. In that case another version of Kubuntu might work better. Maybe you can try 12.04 LTS instead of 13.10?

---

### Post by BoogeyOfTheMan on 2014-01-27
It did work when I first built the pc last July. The problem started sometime this fall, as I said in the other post, I first thought it was an issue with my phone because I was using Cyanogenmod nightly's. 

My internet connection is really slow DSL atm, so its going to take me a few days to get the older distros. I'll give that a shot and see how it works out.

---

### Post by sudodus on 2014-01-28
1. Have you connected some ***other hardware*** (printer, scanner, webcam, wifi ...) that might interfere and make it slow connecting to the USB devices? In that case disconnect it and try again!

2. Have you tried manual mounting? It works if for example parted will see it, but if that is also slow, you'll have to wait.

```
sudo parted -l
sudo mount /dev/sdxy /mnt
```

where x is the device letter and y is the partition number, as seen by parted (typically /dev/sdb1)

3. It is also possible that some hardware is damaged, and makes the USB identification slow.

Let's wait for your results, when the other version of Kubuntu is downloaded. Do you get it via ***torrent***? That is probably better with a slow internet connection.

---

### Post by BoogeyOfTheMan on 2014-02-01
Well, it turns out that it was indeed a hardware issue, and yes, that hardware was a USB device, like you suggested. While investigating another issue, I was looking in my syslog when lo and behold, it was filled with USB device re connections. Apparently, my USB 3.0 hub was being rediscovered every 30 seconds. Since I have it plugged in via a 15' USB 3.0 extension cable, I tried eliminating that from the setup and sure enough, my hub was recognized right away, syslog showed the hub and everything that was plugged into it right away and hasnt had any messages since. I've since tested it by plugging my phone into the hub and a USB drive into one of the ports on the PC and they both worked right away.

I thank you for your time and effort in helping me try to figure this out :)

I still dont know why that would cause a problem with every USB port on the PC, but it works now so I'm happy :)

---

### Post by sudodus on 2014-02-02
Congratulations :KS

---

