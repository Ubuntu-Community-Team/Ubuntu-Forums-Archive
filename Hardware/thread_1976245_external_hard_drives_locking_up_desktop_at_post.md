---
title: "external hard drives locking up desktop at post"
date: 2012-05-08
forum: Hardware
---

### Post by jms1989 on 2012-05-08
Hello, my apologies if this is in the wrong place. I have an annoying and persistent issue with external hard drives. Somehow, when my external hard drives are connected and powered, it hangs the pc at the boot splash screen, the screen you see as the bios boots up and finds everything. It takes about a minute or so before it'll finally pass on to booting the main hard drive.

My solution so far is to just power down the drives before rebooting and heres the kicker. It boots fine with the drives powered and attached from a cold startup but not when you reboot. I don't understand this. For another kick in the rear, it seems to do this on another pc with a different drive.

My question is, what causes this? Is there a firmware or bios update I need to do it or am I just gonna have to power then down every time I reboot?

Some stats; 500gb wd mybook, 2tb wd mystudio, 1tb wd hdd. Asus P5QC mobo, 8 gigs of ram, 750gb wd internal hdd. I do have a pata/sata to usb adaptor that doesn't seem to be affected by this and occasionally, a usb flash drive will hang it. It also seems affected upon waking up from standby. Someone please shed some light on this.

Thanks

---

### Post by sudodus on 2012-05-08
> **jms1989 said:**
> Hello, my apologies if this is in the wrong place. I have an annoying and persistent issue with external hard drives. Somehow, when my external hard drives are connected and powered, it hangs the pc at the boot splash screen, the screen you see as the bios boots up and finds everything. It takes about a minute or so before it'll finally pass on to booting the main hard drive.

My solution so far is to just power down the drives before rebooting and heres the kicker. It boots fine with the drives powered and attached from a cold startup but not when you reboot. I don't understand this. For another kick in the rear, it seems to do this on another pc with a different drive.

My question is, what causes this? Is there a firmware or bios update I need to do it or am I just gonna have to power then down every time I reboot?

Some stats; 500gb wd mybook, 2tb wd mystudio, 1tb wd hdd. Asus P5QC mobo, 8 gigs of ram, 750gb wd internal hdd. I do have a pata/sata to usb adaptor that doesn't seem to be affected by this and occasionally, a usb flash drive will hang it. It also seems affected upon waking up from standby. Someone please shed some light on this.

Thanks
Cold booting and rebooting are similar, but not quite the same procedure.

Just a wild guess:

Maybe your bios is set to boot from USB before the internal HDD, so if you have a bootable USB drive, it would boot from it, and if you have a USB drive with data 'only' it will fail. It might not understand that it should try the internal drive, after it has failed booting from the USB drive.

If that is the problem, you should look for the key to enter the bios menu, and check/change the boot order. Usually there is information during one or two seconds about that key right after booting/rebooting.

---

### Post by jms1989 on 2012-05-17
Ok, I gave it a test. My internal hdd, which houses my linux install and home data, is set as the main boot device. I don't ever change it to boot the cd or flash drives, if I want them, I pull up my boot device window to 
bypass the usual boot order.

When I tested it, it would take quite some time before it'd move on with the external ones attached. It may have something to do with it needing to detect the connected devices on reboot... the external hdds are designed to spin down when no in use so when I go to reboot, they have to spin up with takes about 5-10 seconds.

This delay would freeze any other response as it waits for the hdds to spin up. Not even the numlock led would change, which I use to test if it's responding.

---

