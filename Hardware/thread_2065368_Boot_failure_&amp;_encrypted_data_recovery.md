---
title: "Boot failure &amp; encrypted data recovery"
date: 2012-10-01
forum: Hardware
---

### Post by tomowen84 on 2012-10-01
Greetings felow Ubuntu users.

I have an Acer Aspire 1 D260 2DQkk about 20 months old.
The netbook was shipped with Windows 7 & Android partition. I added an Ubuntu 10.10 partition, used daily, never upgraded beyond this. Encryption of the hard drive was enabled and I know the password.
Default boot setings were as follows:
- Attempt to boot from USB, then 
- User selection of OS within 10 seconds, then
- Default to Ubuntu boot.

Recently it stopped booting: after power button pressed, hard drive LED flashes once and a single underscore (non-blinking) character on the top right of the screen, where it freezes. No BIOS screen of any sort displays if any of the F keys are pressed during or after the power button is pressed. There are no beeps.

I found similar symptoms and attempted this solution, but with no luck:
[http://www.qrpcw.com/2009/01/acer-aspire-one-bios-recovery.html](http://www.qrpcw.com/2009/01/acer-aspire-one-bios-recovery.html)

I removed and replaced the hard drive, the device behaviour is the same.
I tried to boot from a new Ubuntu 12.04 USB, behaviour is the same.

I have mounted old hard drive into an enclosure:
MAC:
- When connected to the wife's mac, it reports an empty USB device with a few GB free space (drive shipped was 160Gb)
- When attempting to unmount, mac report a three partion drive (which one do you want unmount?)
- I'm a total MAC noob, I was unable to identify the separate partitions

Windows 7:
- When connected to my work PC all three partions are shown, I can browse the windows file store ok, but:
- The Ubuntu partion is shown as "System Reserved"

I have two questions:

Conclusion: 
I assuming some sort of hardware failure, not the hard drive

Questions:
Can anyone suggest anything I could try to diagnose the problem with the netbook?
Can anyone suggest how I could recover my data from the hard drive? 
Please note, I'm reluctant to install an ubuntu partition on my work PC, although I could try having it boot from a USB drive, as a last resort. If so, is it necessary to boot Ubuntu 10.10?

Many thanks in advance for any responses.

Tom

---

### Post by ahallubuntu on 2012-10-01
It sounds like the motherboard on the netbook has some issue unrelated to the hard drive.

I don't think it's necessary to go back to Ubuntu 10.10 but yes, booting Ubuntu on another computer seems to be your best bet to be able to recover files from the encrypted partition.

In fact, you may be able to boot the drive itself (Ubuntu 10.10) in its enclosure on some other PC (probably not the Mac) normally.  Have you tried that?  I have done that a few times.  As long as you can boot from USB that may work.  If it does, you could then copy the files over to another external USB drive if you wish.

---

### Post by tomowen84 on 2012-10-04
> **ahallubuntu said:**
> 

In fact, you may be able to boot the drive itself (Ubuntu 10.10) in its enclosure on some other PC (probably not the Mac) normally.  Have you tried that?  I have done that a few times.  As long as you can boot from USB that may work.  If it does, you could then copy the files over to another external USB drive if you wish.

What a great idea! I shall try this and report back.
Thanks for taking the time to respond.

---

