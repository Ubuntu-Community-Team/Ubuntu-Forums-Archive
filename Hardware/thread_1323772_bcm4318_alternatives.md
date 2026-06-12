---
title: "bcm4318 alternatives?"
date: 2009-11-12
forum: Hardware
---

### Post by SyCo123 on 2009-11-12
Does anyone know if there is a low price card that will replace the Broadcom bcm4318 airforce POS that I currently have in my HP DV5215us craptop? 

I was so impressed with how painless getting the Broadcom BCM4318 wireless adapter working in 8.10 was. I finally thought those wasted hours, and mental pain were behind me. I skipped 9.04 and just did a clean install of 9.10 and, like a sequel to a bad horror movie, the nightmare is back.

> "it just worked, now it doesn't"[SIZE="1"]TM[/SIZE]

I know I can read up and post and screw with it, I have a bit already but no joy yet. I could install an older Ubuntu or many other options, but I'm done screwing with it, my time is more valuable than a 2nd hand replacement card.

My laptop is getting on in years now so there must be a shedload of other cards from more Linux friendly vendors kicking around on ebay but I've no idea how to know which one would be compatible. Any help appreciated.

---

### Post by dvlchd3 on 2009-11-12
Do you have the bcm4318 or 4218?

My 4318 works fine in 9.10.  Just had to install b43-fwcutter...

---

### Post by Dark_Stang on 2009-11-12
All you should have to do is hardwire your computer to a network. Go System > Administration > Hardware drivers. And enable the Broadcom STA driver.

---

### Post by SyCo123 on 2009-11-12
> All you should have to do is hardwire your computer to a network. Go System > Administration > Hardware drivers. And enable the Broadcom STA driver.
Thanks for the suggestion but there's nothing in hardware drivers.
> Do you have the bcm4318 or 4218?
My 4318 works fine in 9.10. Just had to install b43-fwcutter...
Yea.. that's what I did with not joy. I have the bcm4318, my apologies, that was typo, I'll correct it (edit:done). Since 7.04 I've been very familiar with my wireless setup, ndiswraper and fwcutter due to the immense hassle it was getting it working. I'm very happy for you guys who had no trouble with 9.10. There are lots of people who did have problems. I've already tried solutions that have worked for them without success. Fixing it is not the aim of this thread. If I decide to have another go I'll post a request for assistance.

My point is I'm sick and tired of doing this every time I install. I thought I was done messing, but apparently not. I would happily purchase another card and like the idea of supporting a more Linux friendly vendor. 

I suppose I'm a rare breed of Linux user who doesn't want to fiddle every time, I just want the damn thing to work! 

So, back to my question. Does anyone know if there's an alternative card that will fit my HP DV5215us from a more Linux friendly vendor?

---

### Post by darkshadow on 2009-11-12
I personally use that card and it works fine. I think the problem is that no one is updating will on the wired. Since I had to.

1. Clean install 9.10
2. Connect with wire
3. Reload sources
4. Update the system with update-manager
5. Run hardware drivers.
6. Voila it now shows up.

Don't ask me why hardware drivers does not show the driver before a update

---

### Post by SyCo123 on 2009-11-12
Hi darkshadow thanks for that, sincerely, if it comes to it I'll try that. But I'm not asking how to get it working, I want to replace the card. 

I've wasted too much time messing with broadcom, I want it to end. I don't want this to be a feature every time I install in the future. Do I have any alternative?

This is simple economics for me. My hourly rate is high enough for me to save money by buying a replacement and not messing with this now and in the future.

---

### Post by Dark_Stang on 2009-11-12
It should just be your average mini PCI slot. So any wireless card that fits that will work. I can't think of any retailers that would carry them though.

---

### Post by SyCo123 on 2009-11-12
Thanks, then I think I've found a list of [supported wireless network interfaces]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

According to that list the PRO/Wireless 2915ABG is automatically detected and I found one on ebay for $10, with free shipping. I really hope this is an end to it. 

Thanks for your replies.

---

### Post by watersoup on 2010-07-20
bump ....


SyCo123: have found any solution finally.

---

### Post by SyCo123 on 2010-07-20
Yes the Broadcom card is now well supported. After installing look in "System>Hardware drivers" there should be a list of restricted drivers. Enable the Broadcom driver and reboot. Your wireless should then work.

---

