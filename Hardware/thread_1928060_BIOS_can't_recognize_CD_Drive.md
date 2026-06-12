---
title: "BIOS can't recognize CD Drive"
date: 2012-02-19
forum: Hardware
---

### Post by milos989 on 2012-02-19
Hello,

I recently made a clean Ubuntu start in my life and after removing the last ntfs partition and installing Ubuntu 11.10 64bit from a usb stick I inserted a disc into the drive but nothing happens. CD spins but nautilus doesnt show any new drive.

I had ubuntu installed before this installation and cd worked just fine. With the new installation i changed my ntfs partition into ext4 and moved swap from extended to primary, could that be the problem?

When i enter bios, under ide master (where should be CD Drive) says not recognized, so i suppose it has little to do with my OS. Does anyone have any ideas?

Thanks :)

---

### Post by 2F4U on 2012-02-19
If the BIOS doesn't recognize the CD drive, Ubuntu can't access it. Maybe the cable is loose or the drive is broken?

---

### Post by milos989 on 2012-02-19
hmm maybe.. But its funny how it happened just after OS installation, so i figured there might be something wrong with the software. 

I will disassemble the laptop if i must, but if you guys can think of something software-wise i can check first, i would be thankful. cheers

---

### Post by 2F4U on 2012-02-19
If you think that there is a problem with Ubuntu, you could try to boot into a liveCD. If the BIOS recognizes the drive, it should offer you the option to boot from it. I guess it doesn't really matter which kind of liveCD you attempt to boot, any you have available should be fine.

---

### Post by milos989 on 2012-02-19
I did as you said, but nothing happens, it just boots into normal ubuntu. In bios boot manager, i cant set to but from cd, just hdd, usb and network. Does that mean it's definitely something wrong with hardware? When i put in a cd, i hear it spinning inside. Maybe that cable got unplugged as you suggested?

---

### Post by ahallubuntu on 2012-02-19
Laptop CD drives generally plug in without a "cable."  They are often very easy to remove - one or two screws on the bottom of the laptop and perhaps a release latch. I would try popping out the CD drive and putting it back.  They DO fail sometimes as well and may not be that expensive to replace.  Depends on make/model of laptop.

---

### Post by grahammechanical on 2012-02-19
You may find that with the BIOS set to boot from USB it might remove the option to boot from CD drive and also the other way around. I do not know.

I did find on my system that I could not set a BIOS to boot from USB when it was set to boot from floppy drive. So, it is just something to check. 

Regards.

---

