---
title: "Jaunty has Compiz that has blacklisted my Intel Graphics Processor???"
date: 2009-06-03
forum: Hardware
---

### Post by Skrean on 2009-06-03
I had Hardy installed and chose to update to Jaunty...When I started up on live CD to try it out I could not enable 'Advanced Desktop Effects' Error read..'Effects could not be enabled.' Googling thru the problem I found that the compiz in Jaunty has blacklisted my Intel card.:-k

Workaround involving ignoring the blacklist was possible.  Is that safe?

I chose to update to Intrepid while waiting for a possible 'whitelisting' of my card in the next Ubuntu or compiz?  Will that ever happen?

Lspci shows that I have a 'Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller' on my Dell Inspiron 1525...

---

### Post by Bios Element on 2009-06-03
Just an FYI: If it's blacklisted then there's a 'very' good reason for it. As in, It 'could' brick your card. You may be fine, or you may have to get a new card. Or since Intel is typically onboard graphics, a new motherboard.

EDIT: But if it was LiveCD then it probably needed a driver. But you can't really install drivers via LiveCD so you can't enable Compiz.

---

### Post by theozzlives on 2009-06-03
I have a Inspiron 1525 and bypassed the blacklist, Compiz works great, and Jaunty is faster than Intrepid.

---

### Post by Skrean on 2009-06-03
> **Bios Element said:**
> Just an FYI: If it's blacklisted then there's a 'very' good reason for it. As in, It 'could' brick your card. You may be fine, or you may have to get a new card. Or since Intel is typically onboard graphics, a new motherboard.

EDIT: But if it was LiveCD then it probably needed a driver. But you can't really install drivers via LiveCD so you can't enable Compiz.

BTW:  I've just had to have the motherboard REPLACED...Is that because the Hardy install spoilt my motherboard?? Should I worry about my current Intrepid install?

---

### Post by Seq on 2009-06-03
The blacklist is there due to some issues with the current intel driver. Some can bypass the blacklist without issue, others can not. There may or may not be stability issues involved. The blacklist is there as it is generally unknown what combinations will work.

There are a lot of threads on the forum already regarding reverting drivers to older or newer versions to try and resolve stability issues encountered. Your mileage may vary. Personally, metacity with compositing enabled is rather decent (and stacks windows better anyway).


> **Bios Element said:**
> Just an FYI: If it's blacklisted then there's a 'very' good reason for it. As in, It 'could' brick your card. You may be fine, or you may have to get a new card. Or since Intel is typically onboard graphics, a new motherboard.

EDIT: But if it was LiveCD then it probably needed a driver. But you can't really install drivers via LiveCD so you can't enable Compiz.

This is the silliest thing I've ever heard. You won't brick your card or motherboard by bypassing the compiz blacklist. You may cause a graphics hang, but a reboot will solve that.

intel drivers are open source and included with the livecd, though there may indeed be updates since the cd image was created. As above, though, your mileage may vary.

---

### Post by Skrean on 2009-06-03
> **Seq said:**
> The blacklist is there due to some issues with the current intel driver. Some can bypass the blacklist without issue, others can not. There may or may not be stability issues involved. The blacklist is there as it is generally unknown what combinations will work.

There are a lot of threads on the forum already regarding reverting drivers to older or newer versions to try and resolve stability issues encountered. Your mileage may vary. Personally, metacity with compositing enabled is rather decent (and stacks windows better anyway).




This is the silliest thing I've ever heard. You won't brick your card or motherboard by bypassing the compiz blacklist. You may cause a graphics hang, but a reboot will solve that.

intel drivers are open source and included with the livecd, though there may indeed be updates since the cd image was created. As above, though, your mileage may vary.
BTW: I've just had to have the motherboard REPLACED...Is that because the Hardy install spoilt my motherboard?? Should I worry about my current Intrepid install?  

Please can someone answer the questions above...Thanks

---

### Post by Seq on 2009-06-03
> **Skrean said:**
> BTW: I've just had to have the motherboard REPLACED...Is that because the Hardy install spoilt my motherboard?? Should I worry about my current Intrepid install?  

Please can someone answer the questions above...Thanks

Most probably no. What was wrong with the motherboard?

Furthermore, we were talking about a compiz blacklist. Not mucking about yourself with applying incorrect drivers to incorrect devices. I've really only heard of one driver "bricking" hardware: the intel e1000 fiasco last year, and even that was rather rare and iirc never made it to any general users.

---

### Post by Skrean on 2009-06-03
> **Seq said:**
> Most probably no. What was wrong with the motherboard?

Furthermore, we were talking about a compiz blacklist. Not mucking about yourself with applying incorrect drivers to incorrect devices. I've really only heard of one driver "bricking" hardware: the intel e1000 fiasco last year, and even that was rather rare and iirc never made it to any general users.
Motherboard was replaced under warranty so I didn't give much thought to it..the support staff could not tell me what the problem really was except that the motherboard had to replaced...I guess it must have been a 'faulty parts' issue and nothing to do with Ubuntu coz they replaced it without questions...knowing full well I bought the computer with Vista and replaced it with Ubuntu Hardy since December 08..

---

### Post by Bios Element on 2009-06-03
> **Seq said:**
> This is the silliest thing I've ever heard. You won't brick your card or motherboard by bypassing the compiz blacklist. You may cause a graphics hang, but a reboot will solve that.

intel drivers are open source and included with the livecd, though there may indeed be updates since the cd image was created. As above, though, your mileage may vary.

Last I looked there were some pretty major (although thankfully limited in scope) issues with a dev release of jaunty that bricked network cards. (Pretty sure they were intel as well.) Admittedly they were not graphics cards but I figured it best not to under-represent the risk until someone more knowledgeable came along.

---

### Post by Seq on 2009-06-03
> **Bios Element said:**
> Last I looked there were some pretty major (although thankfully limited in scope) issues with a dev release of jaunty that bricked network cards. (Pretty sure they were intel as well.) Admittedly they were not graphics cards but I figured it best not to under-represent the risk until someone more knowledgeable came along.

Yes, I mentioned that above, It was the e1000 driver. I believe it was Intrepid Alphas, and it only affected certain cards. Different issue.

---

### Post by Skrean on 2009-06-03
> **Seq said:**
> Yes, I mentioned that above, It was the e1000 driver. I believe it was Intrepid Alphas, and it only affected certain cards. Different issue.

Could I have a link to an article or blog that mentions the above issue?

---

### Post by Seq on 2009-06-04
> **Skrean said:**
> Could I have a link to an article or blog that mentions the above issue?

I'm not sure about any authoritative articles, but [Google has a few hits]("http://www.google.ca/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=mGk&q=e1000+eeprom+issue&btnG=Search&meta=").

---

### Post by Yellow Pasque on 2009-06-05
You're making this way too difficult. None of the e1000 stuff affects you.

1. Enable compiz with the method linked below.
2. Monitor your system for freezing or other video problems.
3. If your system works fine, enjoy your wobbly windows. Otherwise, disable compiz and go on with your life.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)

---

### Post by Skrean on 2009-06-05
> **Temüjin said:**
> You're making this way too difficult. None of the e1000 stuff affects you.

1. Enable compiz with the method linked below.
2. Monitor your system for freezing or other video problems.
3. If your system works fine, enjoy your wobbly windows. Otherwise, disable compiz and go on with your life.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)

Thanks!

---

