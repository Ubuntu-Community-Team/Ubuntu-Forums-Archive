---
title: "GRUB ERROR 17. will not boot! please help!"
date: 2009-08-29
forum: Hardware
---

### Post by knowndarkness on 2009-08-29
Hi. i recently purchased a ASUS EEEPC 1101HA. i think this is one of the newer models. but anyway. it HAD win xp on it. but i used a live usb to erase everything, and installed ubuntu netbook remix 9.04. 

after installing (everything else wiped out. win xp = gone), there was no internet. so i finally found a fix HERE: [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

i followed those directions. at the end of that blog post, i tried to follow [B]Setting the EFI partition for boot booster.

[/B]after entering in "sudo sfdisk --change-id /dev/sda 1 ef" in the terminal, i think i screwed up my whole entire netbook. as of right now, the only thing i can boot into is bios. but even when i try to load my live usb first before the hard drive, it still shows me the message. i cant seem to load ANYTHING! :'(

this is exactly what it shows me:
_______

GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 17

_______


if anyone could pleaseee help me. this netbook is new and i think i just killed it :((



EDIT / UPDATE: I FOUND OUT THAT I AM ABLE TO BOOT WITH A LIVE CD. but i can't boot with a usb.
I am wondering if i can fix this without having to reinstall the whole thing. at least now i KNOW that i CAN fix it. but i only will reinstall the whole thing as a last resort. can anyone help me?? maybe i can edit what i did wrong through this live cd. my live cd is NOT UNR. it is the desktop version of 9.04

---

### Post by cos85 on 2009-08-29
Hmm.. It's *very* strange that you can't boot from usb at all. Are you entirely sure the usb still works on other machines? 

I don't personally have an EEEPC, but here's a couple of things worth looking into:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good luck!

Cos

---

### Post by cos85 on 2009-08-29
I think the 9.04 LiveCD comes with gparted installed (under System>Administration>Partition editor), which (if memory serves) should have an option to repair the MBR.

Can you mount any drives, btw?

---

### Post by knowndarkness on 2009-08-29
my usb works fine. i made sure because i have two computers. my netbook that i somehow killed. and my desktop computer.

as of right now, i dont know why but it seems as though when i boot my live desktop cd ubuntu 9.04, its actually faster, less laggier, and better than UNR. 

quite honestly, i really don't see a difference between UNR and the desktop version. 

i made up my mind and i am going to reinstall ubuntu desktop version 9.04 on my netbook. 

thanks anyway. but this seems like a good idea to me. its less laggier. maybe its my system, but it works.

---

### Post by knowndarkness on 2009-08-29
> **cos85 said:**
> I think the 9.04 LiveCD comes with gparted installed (under System>Administration>Partition editor), which (if memory serves) should have an option to repair the MBR.

Can you mount any drives, btw?

i can mount drives. i can only mount from one usb port right now. (my external optical drive takes up 2 usb ports)

but thank god i bought an external optical drive :)

---

### Post by inkrypted on 2009-08-29
Make sure the USB drive is the first drive in the BIOS. If you intend to boot to it.

---

### Post by knowndarkness on 2009-08-29
> **inkrypted said:**
> Make sure the USB drive is the first drive in the BIOS. If you intend to boot to it.


yeah. i did. i put it as the first option. loaded it. wouldnt load my usb.

then i finally randomly out of no where, tried my ext op. drive. as first. and it worked. so im glad. thank you

---

### Post by Brightbelt on 2009-08-29
Hey, just my 2 cents. I found my HP Netbook to be super-finnicky and I had to try different methods for making a LiveUsb. Interestingly enough, I had best results when using Ubuntu's program for making a LiveUsb.

---

