---
title: "Just a quick question"
date: 2009-02-07
forum: Hardware
---

### Post by darkproteus66 on 2009-02-07
I am looking at purchasing a new laptop and unfortunately none of the system 76 notebooks meet what I need as far as specifications go (under 15" screen w/ discreet video and 8 gigs max ram) and I was wondering if the Asus [X83Vm-X2]("http://www.bestbuy.com/site/olspage.jsp?skuId=9172879&type=product&id=1218044029788") or the [Dell Studio XPS 13]("http://www.dell.com/content/products/productdetails.aspx/laptop-studio-xps-13?c=us&cs=19&l=en&s=dhs") would have any issues running Ubuntu on them. Thanks in advance and if you have any other recommendations I would love to hear them.
-Darkproteus66

---

### Post by simtaalo on 2009-02-07
it generally seems that if something is not going to work on a laptop when you install ubuntu it tends to be the wireless.

i have a 2-3 yr old HP laptop and never encountered the problem, but i've read cases on here of people with newer ones that have problems.

best thing is just to type name of the wireless card into google with ubuntu and see what the results are. also check with any other bits of hardware.

i would say that you *probably* wouldn't have any major problems.

---

### Post by darkproteus66 on 2009-02-07
Okay thanks. I actually figured that the Dell would be fine because I actually work at Dell and almsot all the parts used in Dell computers now are Linux friendly. The only reason that the Studio XPS isn't a closed deal for me is because the price for performance on it versus the Asus just doesn't scale well for me. Slightly faster CPU + Slower GPU + More expensive but same speed and higher latency ram = an equation that doesn't get me too excited
-Darkproteus66

---

### Post by darkproteus66 on 2009-02-23
So I got the Asus X83Vm-X2, and I cannot get it to load Ubuntu 8.10 64 bit. I've tried with a live dvd, alternate install disk, and through wubi. In the live disk it will get to installing the base system then it will just go back to the desktop, on the alternate install disk it will get to installing components then ask me to insert the disk, i will reinsert the alt disk or install the live disk and it will keep the same message up. and in wubi i've gone through the entire install just fine but when the laptop boots it will just hang on the Asus splash screen. I don't know what else to do at this point and I really want to get ubuntu running on this system b/c it's a really nice laptop. Any help that you guys could give me would be greatly appreciated.
-darkproteus66

---

### Post by darkproteus66 on 2009-02-23
Really need help resolving this issue BUMP

---

### Post by thefoolisme on 2009-03-18
I was wondering if anyone ever resolved this issue with the Asus X83Vm-X2 laptop.  I tried installing 64 bit Ubuntu 8.10 this weekend on my laptop as a dual-boot.  When installing with the disk, it hung at 90% when going through the hardware.  I later tried installing with Wubi, and it seemed to install, but on reboot and choosing Ubuntu, it hung up with a terrible screeching noise.  The uninstall for Wubi wouldn't work either.  The burns both checked out ok, so I don't think it's the disks.  It would really suck not to be able to put Ubuntu on my laptop.

Thanks.

---

### Post by darkproteus66 on 2009-03-18
I actually got it working (I'm actually typing this from that laptop). It turns out that the first laptop I had gotten had a bad HDD so I exchanged it and got another one and was able to install Ubuntu on it with that one after going into the BIOS and changing the setting on the HDD under sata operation from enhanced to compatible. After changing that I did an install off of a 8.10 AMD 64 alternate install disk and have been running just fine since with the occasional boot to a blank screen (1 out of every 15 boots or so), and the wifi card isn't always detected after logging in but that is rare and a restart resolves both issues. Give it a try and good luck.

---

### Post by thefoolisme on 2009-03-18
I don't think my hdd is bad, since I've been using it for about a month, so I wonder if it's the enhanced vs compatible that would make it squeal like it did.  I even thought about trying to install a 32 bit version instead of 64 bit, but haven't gotten around to it yet.  Did you install 64 or 32 bit?  I'm almost afraid to try again, but I might this weekend.  Thanks for the response.

---

### Post by darkproteus66 on 2009-03-19
It's most likely the enhanced vs compatible for your setup, I am using the 64 bit version with no issues on the system.

---

### Post by goumba on 2009-04-29
> **darkproteus66 said:**
> and have been running just fine since with the occasional boot to a blank screen (1 out of every 15 boots or so), and the wifi card isn't always detected after logging in but that is rare and a restart resolves both issues

Don't mean to revive a month old thread, but just a few notes:

1. First and foremost, I've been looking at this laptop, and this is the only forum I've found regarding it and Linux. Thanks.

2. I have an iBook G4 that has always had an issue with occasionally booting to a blank screen. Unfortunately I have switched to Lenny about a month and a half ago and have yet to experience this issue again, so it may be Ubuntu-specific (but this is just my experience on one laptop).

3. The Best Buy website has tons of comments about hard drives and wireless issues. In particular the wireless, even under Vista, t seems to be quirky from what I read, so I'd say that's a hardware issue and not something Linux specific.

---

