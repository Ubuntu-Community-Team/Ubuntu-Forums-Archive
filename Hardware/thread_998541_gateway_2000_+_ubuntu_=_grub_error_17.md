---
title: "gateway 2000 + ubuntu = grub error 17"
date: 2008-11-30
forum: Hardware
---

### Post by srilyk on 2008-11-30
So, I tried installing the ubuntu essentials thing... whatever it's called for archaic hardware - on an old gateway 2000 laptop.

It started up fine and all that... well, about midway through the installation it hung, installing the same package for about 6 hours. The ol 3 finger salute didn't work, so I did a hard reboot... and "Grub error 17" came up.

That would be fine and dandy except now it won't boot from the CD-ROM at /all/

I'd try creating a bootable floppy and attempting to boot that way... but I have no other computers with a floppy.

So basically I'm stuck, because it won't boot any live CD (DSL, Puppy, Ubuntu - any of the CD versions I've stuck in there)

Any help would be great.

TIA

---

### Post by linuxisevolution on 2008-11-30
> **srilyk said:**
> So, I tried installing the ubuntu essentials thing... whatever it's called for archaic hardware - on an old gateway 2000 laptop.

It started up fine and all that... well, about midway through the installation it hung, installing the same package for about 6 hours. The ol 3 finger salute didn't work, so I did a hard reboot... and "Grub error 17" came up.

That would be fine and dandy except now it won't boot from the CD-ROM at /all/

I'd try creating a bootable floppy and attempting to boot that way... but I have no other computers with a floppy.

So basically I'm stuck, because it won't boot any live CD (DSL, Puppy, Ubuntu - any of the CD versions I've stuck in there)

Any help would be great.

TIA



I had the same problem with my gateway 2000. It got put into the basement for a year until my sister wanted a computer. I just reset the cmos after two failed attempts at installing Xubuntu. She now runs Xubuntu.. Try resetting it :)

Look on the manufacturers web page.. If you can, hit F10 or F9 during boot and see if anything that gives the cd rom boot option.

            -LIEvolution

---

### Post by srilyk on 2008-12-01
How do you reset the cmos? I haven't been able to find any documentation so far on the topic... neither F10 or F9 helped (though they did lock the thing up)

Edit:

Well that was good/sucked. I finally figured out how to reset the CMOS, and then the DSL linux CD I had in booted fine up to the startup. So I swapped to a puppy linux cd and that started booting... but then it got stuck in bootup. So I did a hard reset and now I'm back to square 1, except resetting the CMOS isn't helping anymore. :'( *tear*

---

### Post by linuxisevolution on 2009-01-01
> **srilyk said:**
> How do you reset the cmos? I haven't been able to find any documentation so far on the topic... neither F10 or F9 helped (though they did lock the thing up)

Edit:

Well that was good/sucked. I finally figured out how to reset the CMOS, and then the DSL linux CD I had in booted fine up to the startup. So I swapped to a puppy linux cd and that started booting... but then it got stuck in bootup. So I did a hard reset and now I'm back to square 1, except resetting the CMOS isn't helping anymore. :'( *tear*


Well the guys at Gateshit told me that my harddrive was bad. Try putting your harddrive in another linux box and run fsck /dev/sdb to see if that fixes the drive. You could also just format it. Maybe you should put your gateway in the basement for a year too lol. :D

---

