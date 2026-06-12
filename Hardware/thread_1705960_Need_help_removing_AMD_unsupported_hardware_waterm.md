---
title: "Need help removing AMD unsupported hardware watermark on radeon HD 6470M card"
date: 2011-03-13
forum: Hardware
---

### Post by king EZi on 2011-03-13
Hello

I installed ubuntu 10.10 on a new laptop that i recently bought (ASUS A42JY) with the radeon HD 6470M card. And the resolution was horrible so i installed the additional drivers and after that everything looks and works great except for the annoying watermark on the bottom right of the screen. I would appreciate any help. I tried a few suggested methods like replacing the /etc/ati/control file but that didnt work. 


Thanks

---

### Post by codedivine on 2011-03-17
1. What type of watermark are you seeing?
2. Where did you install the driver from? From the Ubuntu repositories or from AMD website?

---

### Post by king EZi on 2011-03-17
> **codedivine said:**
> 1. What type of watermark are you seeing?
2. Where did you install the driver from? From the Ubuntu repositories or from AMD website?

1. I see a watermark saying "AMD Unsupported Hardware"
   I cant take a screenshot of it because it doesn't appear on the images, but it looks like this: [http://img85.imageshack.us/i/phoz.jpg/sr=1]("http://img85.imageshack.us/i/phoz.jpg/sr=1") 

2. I installed the driver from ubuntu repositories, the driver from AMD somehow doesn't detect any cards.

---

### Post by codedivine on 2011-03-17
Ok. I would suggest waiting for newer drivers (catalyst 11.3) from AMD to be released. I think they should be released in a few days. It is likely that they will come with support for Radeon 6470M.

---

### Post by king EZi on 2011-03-17
> **codedivine said:**
> Ok. I would suggest waiting for newer drivers (catalyst 11.3) from AMD to be released. I think they should be released in a few days. It is likely that they will come with support for Radeon 6470M.

Ok thanks...i will do that. It's just puzzling that AMD site had the 6XXX HD driver section which doesn't work. Roughly when are the new drivers being released? 
Thank you.

---

### Post by codedivine on 2011-03-23
Well still not released. But since Catalyst releases are done every month, the March release should come soon. 
If you don't mind, can you share some other impressions with the laptop? For example, how did you find the battery life? And did you have issues with wireless?

---

### Post by king EZi on 2011-03-23
> **codedivine said:**
> Well still not released. But since Catalyst releases are done every month, the March release should come soon. 
If you don't mind, can you share some other impressions with the laptop? For example, how did you find the battery life? And did you have issues with wireless?

The laptop is ok so far, just the ATI drivers. Are you interested to get one?

---

### Post by PsyForce on 2011-03-24
I have the same watermark with an Acer Aspire 5552G, which has an AMD Radeon HD 6650M. Currently just installed Ubuntu 10.10 and Catalyst 11.2 drivers. I suppose I'll also wait around for the next version, unless there are any better ideas.

---

### Post by codedivine on 2011-03-26
> **king EZi said:**
> The laptop is ok so far, just the ATI drivers. Are you interested to get one?

Yeah, looking at it but perhaps I should get a Sandy Bridge one now.

---

### Post by JTFlint on 2011-09-09
> **PsyForce said:**
> I have the same watermark with an Acer Aspire 5552G, which has an AMD Radeon HD 6650M. Currently just installed Ubuntu 10.10 and Catalyst 11.2 drivers. I suppose I'll also wait around for the next version, unless there are any better ideas.

Im running an F1A75-v PRO with an A8 3850. Im also getting this watermark, and I'd like to know how to get rid of it :) . I got it after installing the ATI/AMD Proprietary FGLRX graphics drivers.
Is there a way to track down what its finding to be "unsupported"? For being unsupported, it let me set up dual monitor support, easy enough , and seems to detect the screens and graphics info ok.

Output of cmd:
:~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9640]

---

### Post by king EZi on 2011-09-09
> **JTFlint said:**
> Im running an F1A75-v PRO with an A8 3850. Im also getting this watermark, and I'd like to know how to get rid of it :) . I got it after installing the ATI/AMD Proprietary FGLRX graphics drivers.
Is there a way to track down what its finding to be "unsupported"? For being unsupported, it let me set up dual monitor support, easy enough , and seems to detect the screens and graphics info ok.

Output of cmd:
:~$ lspci -nn | grep VGA
00:01.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9640]


What version of Ubuntu are you running and what kernel version is it? In my experience 11.04 should work fine.

---

### Post by Mithrandir95 on 2011-09-11
If you just need to get rid of the symptom (watermark), then this thread will help you.

[http://ubuntuforums.org/showthread.php?t=1680093](http://ubuntuforums.org/showthread.php?t=1680093)

---

