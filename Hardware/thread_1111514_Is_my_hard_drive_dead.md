---
title: "Is my hard drive dead?"
date: 2009-03-30
forum: Hardware
---

### Post by deusdies on 2009-03-30
Hi,

I have HP Pavillion DV6600 . The hard drive is Seagate's 160 GB (I'll let you know of the model number if you really need it). The other day, I was at my girlfriend's house and I left the laptop on. I came back home, and the laptop was off (even though it was plugged in). I have Vista and Ubuntu installed (w/ GRUB loader).

I pressed the power button, the POST screen goes by (actually, the HP logo), and the GRUB hangs at

**"GRUB Loading Stage1.5."**

I googled, and I saw many people have similar problem, but theirs also says "Loading, please wait", or points out an error. Mine doesn't.

Also, I tried booting from these live CD's: Ubuntu, openSUSE, Mint, gentoo...even Kalyway MacOS. They won't boot. They're stuck at
[B]
"ISO Linux version 3.04 27-12-2008 by ... "[/B] and similar. All of them.

I can't even get to the command line. So now I can't boot neither to the hard drive, nor to the CD.

I executed Hard Drive test from BIOS (took more than an hour) and it said all the tests have passed. The hard drive also has S.M.A.R.T., as far as I know, so it should've warned me...right?

What should I do now? Any input is appreciated.

Thanks,
Bo

---

### Post by damis648 on 2009-03-30
It sounds possible, certainly, however there could also be a problem with your BIOS or your motherboard. I cannot tell you much, however. Perhaps try removing the drive and booting a CD hard drive-less, see if that has any effect at all.

---

### Post by benerivo on 2009-03-30
Have you tried to boot from a linux usb image, or a vista rescue cd such as this [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by deusdies on 2009-03-30
Thanks for the fast replies!

damis, yes, I opened the laptop, got the drive out, and back in again. Didn't help.

benerive, no, not yet, but thanks! That's an awesome link, I'll try that too.

Right now I am burning Super Grub Disk loader. We'll see how that goes.

Thanks guys!

---

### Post by deusdies on 2009-03-30
Thanks everyone.

After doing some additional "Googling", I have fixed the issue.

The problem was a faulty RAM module. I have removed one 2GB RAM module, and the computer works just fine right now.

Thanks again!
Bo

---

