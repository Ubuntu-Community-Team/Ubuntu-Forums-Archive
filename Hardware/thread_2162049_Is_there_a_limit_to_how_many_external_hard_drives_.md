---
title: "Is there a limit to how many external hard drives I can connect"
date: 2013-07-12
forum: Hardware
---

### Post by Singtoh on 2013-07-12
Hello All,

I am having a strange problem with some external hard drives. The drives are fine it's just that I cannot connect them to the computer all at the same time?? I am using Ubuntu 13.04 64bit on a thinkpad laptop. I am trying to connect a 500gig WD SATA hard drive, a 120gig SATA WD hard drive and a 250gig IDE WD hard drive all external. I thought it might be an IDE, SATA thing causing the problem but I can connect the 500gig SATA and the 250gig IDE and there is no problem but when I try to connect the third 120gig hard drive the little lite on the drive just pulses and does not connect?? When I disconnect one of the other drives and re-connect the 3rd drive it connects no problem?? This happens with any combination I try and all ends with the same result, cannot connect a third external hard drive?? I have had this issue for a long time. I had the issue with Ubuntu 12.10 and 12.04 as well but can't recall if other Ubuntu's had the issue or not?? Am I missing something here?? Is there something I need to add to fstab or other place?? They all automount whenever I connect them seperately?? Any ideas, this is strange to me?? Thanks in advance for any help and pointers.

Cheers,

Singtoh

---

### Post by blackened on 2013-07-12
Are these 2.5" or 3.5" drives? Are they externally powered or do they draw their power via the USB port?

My guess is that they're all 2.5" USB-powered drives, in which case they're probably overloading the USB circuit. Try plugging them into an externally-powered USB hub.

---

### Post by Singtoh on 2013-07-12
> **blackened said:**
> Are these 2.5" or 3.5" drives? Are they externally powered or do they draw their power via the USB port?

My guess is that they're all 2.5" USB-powered drives, in which case they're probably overloading the USB circuit. Try plugging them into an externally-powered USB hub.

Hello blackened,

Thanks for the reply. Yes, I forgot to mention that bit. Actually the 500gig Western Digital has it's own power and it is a 3.5" drive and the other two are USB powered 2.5" drives. I also have all drives connected to a powered USB hub and I have checked the power going to the hub and it is 5.5 to 6 volts. I have tried everything I can think of but am failing miserably to connect three drives at the same time?? Thanks blackened, any other suggestions I could try??

Cheers,

Singtoh

---

### Post by CharlesA on 2013-07-12
Try connecting 1 USB powered drive and the 3.5" powered drive at the same time and see if it works.

I don't think 5V will be enough to power 2 usb powered drives.

---

### Post by Singtoh on 2013-07-12
> **CharlesA said:**
> Try connecting 1 USB powered drive and the 3.5" powered drive at the same time and see if it works.

I don't think 5V will be enough to power 2 usb powered drives.

Hello CharlesA,

Yes, write now I have the SATA 500gig powered drive and the 250gig IDE drive connected and there is no problem, but when I try to connect the third drive, the third drive just sits there and pulses and then I disconnect the IDE drive and re-connect the third drive and it connects no problem. A question for you?? Do you think I could up the voltage on the powered hub by a volt or two without damage?? I have one of those multi-volt power supplies that I can change the voltage on? Thanks CharlesA.

Cheers,

Singtoh

---

### Post by CharlesA on 2013-07-12
I wouldn't recommend increasing the voltage as you might fry the hub. If you have a space USB port, you could hook one drive up to that and then use the hub for the other two.

Also: Some 2.5" drives have an external power connector that you can use, so that might be an option if your drive supports it.

---

### Post by tgalati4 on 2013-07-12
Some IDE/SATA controllers have a limit of 2 SATA drives if an IDE drive is connected.  I've seen desktop BIOS with an option to turn off IDE and that will allow up to 6 SATA, but with IDE, only 2 SATA.  The thinkpad chipset might have a similar restriction.  It could also be a power/current problem as others have suggested.

---

### Post by Singtoh on 2013-07-12
> **CharlesA said:**
> I wouldn't recommend increasing the voltage as you might fry the hub. If you have a space USB port, you could hook one drive up to that and then use the hub for the other two.

Also: Some 2.5" drives have an external power connector that you can use, so that might be an option if your drive supports it.

Hello CharlesA,

I just plugged all the drives into the powered hub and it seems to work that way. I have never thought of doing it this way because the 500gig drive has it's own power and I thought that was enough but apparently not. I was running with the 500gig in a seperate usb port on the laptop and the others on in the powered hub and that didn't play nicely. Now they are all in the powered hub and it seems ok. Sorry for wasting your time everybody, I guess I should have tried them all in the powered hub before posting, just never thought of it:redface: 

Cheers,

Singtoh

---

### Post by CharlesA on 2013-07-12
Glad you got it working. I don't think I would have thought to try that. :)

---

