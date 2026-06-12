---
title: "sound not working - ubuntu 9.04 64-bit"
date: 2009-05-28
forum: Hardware
---

### Post by guya01 on 2009-05-28
I've installed ubuntu 9.04 64-bit. my motherboard (with built-n sound card) is asus p5kpl-cm.

my sound is not working at all. I've tried several sound-troubleshoot guides onthe web with no success so far. Iam not expirienced in linux/ubuntu. Does ubuntu supports my hardware?

thanks :)

---

### Post by Hutchewon on 2009-05-28
You are not alone. I have been working on this for days. In my opinion sound driver support in linux in general is primitive. I have installed the manufacturer's driver and still no go. Good Luck.

---

### Post by guya01 on 2009-05-29
should I try to reinstall ubuntu - this time the 32 bit version?

---

### Post by Hutchewon on 2009-05-29
Go to the oss site download their driver. It is the only thing that has gotten sound from my sound card with the 64bit version. Pulse and ALSA are pathetic jokes. No modern Operating system should have this kludgy of a sound setup. I really like Ubuntu, but it will never challenge M$ until there is reasonable plug and play for standard sound cards. Advising end users to compile there own drivers using sketchy direction, for god knows what version of the OS is total insanity. Good Luck. I am on my 10th reinstall attempting to get a simple audigy x-fi card to work.

---

### Post by guya01 on 2009-06-01
Well, I've installed the 32-bit version of ubuntu 9.04 - everything works fine.

---

### Post by Hutchewon on 2009-06-06
:popcorn:
After reading your solution, I spent a week attempting to get my crippled 64bit, OSS sound setup to work. Ater fighting scratchy distorted sound, no system sound, I through in the towel this morning. I reformated the partition and put 32 bit ubuntu on it, installed the creative driver using the instructions from them. After installing flash support for Firefox I seem to be at 100%.

I don't think the 64bit version of ubuntu is ready for prime time. In addition to the sound issues, there were issues with screen corruption, and remote access working correctly.

 I also am amazed at how difficult it is to get a fairly standard sound card to work with linux in general. I really like Ubuntu, Xbuntu etc. , but I think the bizarre sound setup in Linux in general is a show stopper for the general user.

Thanks again for pointing me in the right direction.

Hutchewon

---

