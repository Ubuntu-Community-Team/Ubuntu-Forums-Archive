---
title: "HP Pavilion DV6000 - webcam not detected."
date: 2010-05-20
forum: Hardware
---

### Post by eluminBe on 2010-05-20
**Laptop:** HP Pavilion DV6000
**Webcam: **Ricoh Co., Ltd Pavilion Webcam [R5U870]

I've enabled the R5U870 driver ( Hardware Drivers ) but it still doesn't work - Cheese says there are no webcams available.
The device is being detected by lsusb and I can't figure out what else should I to make it work.

Any help / suggestions appreciated.

---

### Post by eluminBe on 2010-05-21
Anyone ?

---

### Post by eluminBe on 2010-05-23
So just to let everyone know - even uvc didn't helped .. Switching back to Windows till the next Ubuntu release / driver update.

---

### Post by dino99 on 2010-05-23
you need a bios update: at least F.3D or higher from HP

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)

---

### Post by Lepy on 2010-06-25
I absolutely hate this laptop. No boot problems, wireless problems, huge heat generation, speakers stopped working, and leads to both power and quickplay buttons broke from crappy materials/heat on top of the webcam not functioning for as long as I can remember. 

My DV6045nr broke for the 6th time yesterday. The first two times, it was under warranty. The last 4 times, after the DV series solder problem was admitted, have not been honoured by HP, so I've had to fix it myself by placing the motherboard in oven @385 for 8 minutes and then re-affixing the heat sink with a penny placed on top of the graphics chip. This usually fixes it for months, but then sometimes, it'll just stop and need to be fixed again.

All problems with this laptop, excluding the heat, speakers, and webcam, are fixed with the oven method described above.

Anyway, after fixing the laptop today, I decided to see if there was a trick to getting the webcam working under ubuntu and perhaps getting the laptop working 100% again (besides the massive amount of heat it puts off) ](*,)

I updated to F.3D a loooong time ago, but I know of no other BIOS upgrades. lsusb does not report any sort of webcam, hardware drivers show no indication of a webcam, and there is no listing of it in the bios. 

The cable leading to the lcd seems solid, but it is possible it has been damaged by heat. I have not checked the cable behind the lcd panel, but I don't see how that could have become damaged.

I won't be surprised if its dead considering the rest of the build quality, but any ideas?

---

### Post by lidex on 2010-06-27
This may be helpful:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/5#webcam")

---

### Post by Lepy on 2010-06-29
Thanks. I tried the suggestions from that page, but still nothing shows up with lsusb:

```
:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think the webcam has probably kicked the bucket, and I'll never be buying an HP product again. 

Any other ideas?

---

