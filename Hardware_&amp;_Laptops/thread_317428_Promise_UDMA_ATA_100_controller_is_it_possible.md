---
title: "Promise UDMA ATA 100 controller is it possible?"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by ratanjska on 2006-12-12
Hi!

I am planning to replace an old win2k installation with Ubuntu on a computer based on:

Asus A7V motherboard with on-board audio and a Duron 700 processor.

The 2 pcs. (identical) hard drives are hooked on the on-board Promise UDMA ATA 100 controller.

As far I could find there is a problem with this controller.

Has anybody working instalation of Ubuntu with Promise ATA 100?

How to make this working?

Thank you in advance

Ratanjska

---

### Post by John.Michael.Kane on 2006-12-12
You can try one these guides

[http://www.geocities.com/ender7007/](http://www.geocities.com/ender7007/)
[http://www.openfree.org/pet/index.php/How-to_get_ATA100_running](http://www.openfree.org/pet/index.php/How-to_get_ATA100_running)

---

### Post by jeffc666 on 2006-12-13
Just today I installed Edgy on my Asus A7v with two identical hard drives on the Promise ATA 100 controller. The install went swimmingly, however my first reboot brought a harsh reality... failure. 

So in short, the Live CD starts fine, allows me to install Ubuntu to the drive on the ATA 100 controller. I then ran fine for most of the day, installed new stuff, mounted the other drive, etc... Then I restarted and am now unable to get Ubuntu to boot. I fiddled with the boot settings in BIOS to no end but no luck. 

I will post more if I make more progress...
](*,)

---

### Post by jeffc666 on 2006-12-14
Ok it works like a charm! The reason for my previous failure was that I failed to notice during setup where GRUB was written to and it was written to a disk that I removed from the system. Now all is working swimmingly.

8)

---

