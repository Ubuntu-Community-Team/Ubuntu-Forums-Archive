---
title: "hard disk led not working propely"
date: 2010-08-13
forum: Hardware
---

### Post by tadaskr on 2010-08-13
Hello everyone. I'm using ubuntu about 2 weeks and today I notice problem that when i hear HDD working writing/reading LED of it is not on. I have toshiba satellite a300. Have any that problem too? What solution of this problem might be?
Thanks

---

### Post by varunendra on 2010-08-13
As far as I know, blinking of HDD-LED on accessing HDD is an OS-independent hardware function. So this should be a problem with your hardware, regardless of what OS you are using. But I may be wrong. This can be checked while booting. If the LED doesn't blink even during the boot-up (when the HDD is initially read) then it should be what I said.

Otherwise, are you sure the HDD is being read/written when you notice this? (the running of HDD doesn't necessarily mean that it is being read/written).

---

### Post by tadaskr on 2010-08-14
Well, my HDD is overheating, so if I look to led there is no reason why it should overheat, because hard disk not working a lot, but sometimes I hear HDD sound when it's reading or writing

---

### Post by varunendra on 2010-08-14
Ok, but does the LED blink while boot-up?

If it doesn't, then as I said before, there may be something wrong with your hardware. Adding to it, if the hard disk is overheating for no valid reason, then you should take it seriously as such a malfunctioning may cause damage to a good, working HDD.

If that makes any sense to you, I think you should consider the following:

First, you should make sure that it is not a fault on the OS side. For this I'd suggest to use a bootable CD with some HDD diagnostic tool (like [Hiren's Boot CD]("http://www.9down.com/Hiren-s-BootCD-10-6-352820/"), it also contains live XP that you may use as a completely different Live OS for the same purpose), and use that diagnostic tool to see if the HDD LED blinks during scanning. Then stop the scanning and leave the laptop idle for sometime (say, 15 min.) to make sure the HDD stops and doesn't over-heat as in ubuntu.

If all this goes as it should (LED blinking during scan; no led- no hdd running- no heating during idle session), then problem is in ubuntu, otherwise it is your hardware for sure! In that case, you should take it to a service center.

---

### Post by tadaskr on 2010-08-14
Ok, i let idling pc on 30 minutes on windows 7 where I don't notice that HDD working and LED not blinking and HDD cool down from 56 to 52

---

### Post by varunendra on 2010-08-15
:) :) :) :)

.... (smiling).....
.... because you still didn't tell clearly that 'was there any occasion during that whole exercise when the LED blinked?'

And...., if you think that ubuntu is making your HDD to run continuously (even during an idle session) causing the over-heat, then maybe we can try adjusting power options. Goto **System>Preferences>Power Management** and tick the **"Spin down the hard disks when possible" check-box**. For advance power options, you may need to install KDE desktop environment.

Oh.., 56 to 52 doesn't seem a **significant** difference to me (but am not an expert in that)!! ;)

---

### Post by tadaskr on 2010-08-15
In windows 7 there everything ok, I never notice that HDD led don't work propely, but it could be cooling problems in laptop, because i hear that over 50C is very bad for HDD. And one more question: When I check spin down hard disks when possible then My hdd will shut down?

---

### Post by varunendra on 2010-08-16
> **tadaskr said:**
> When I check spin down hard disks when possible then My hdd will shut down?

Yes, this is the expected effect of that option, but I can't say if it is guaranteed to work.

You may try hdparm command:
[http://ubuntuforums.org/showthread.php?t=179074](http://ubuntuforums.org/showthread.php?t=179074)
[http://ubuntuforums.org/showthread.php?t=227889](http://ubuntuforums.org/showthread.php?t=227889)
[http://ubuntuforums.org/showthread.php?t=939888](http://ubuntuforums.org/showthread.php?t=939888)


For the LED issue, I've got no idea. You may wish to try a different distro like Kubuntu, Xubuntu, or maybe Mint9.

---

