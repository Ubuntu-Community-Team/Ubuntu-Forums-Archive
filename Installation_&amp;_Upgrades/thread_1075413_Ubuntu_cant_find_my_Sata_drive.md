---
title: "Ubuntu cant find my Sata drive"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by dips0502 on 2009-02-20
I am trying to install 8.10 i386 on my PC. It boots fine, but when i run the install wizard, it doesnt show my sata drive in the list. The sata drive is the one i would like to install it on. When I do fdisk -l
it shows:
Cannot open /dev/sda
Cannot open /dev/sdb

sda is my parallel ata drive and sdb is an external usb drive.

I am attaching my dmesg and lspci files. From what i can see in the lspci file the sata controller is recognized by ubuntu. I really cant understand the dmesg file, need some suggestion.........

---

### Post by Pumalite on 2009-02-20
Get in BIOS and see if you can make it 'AHCI'

---

### Post by caljohnsmith on 2009-02-20
When you run the fdisk command, you have to run it as root user with "sudo" for it to work, so how about trying:
```
sudo fdisk -lu
```
Does that show your SATA drive? If not, I would follow Pumalite's suggestion and try and enable "AHCI" for your SATA drive. Also, when you boot the Live CD, press F6 at the main menu to get extra boot options, and then add:
```
pci=nomsi
```
To the end of the boot parameters line. Then select "Try Ubuntu without making changes" and see if Ubuntu recognizes your SATA drive after that. Let us know how that goes.

---

### Post by dips0502 on 2009-02-20
thx guys...i can now see the sata drive...

sudo fdisk -lu, did not show it at first.

I enabled AHCI and nothing happened. Only after adding the pci=nomsi option did the sata drive show up. Enabled Sata back in the bios and with pci=nomsi option, it still shows...

But could you please explain what this option does ?

---

### Post by caljohnsmith on 2009-02-20
> **dips0502 said:**
> thx guys...i can now see the sata drive...

sudo fdisk -lu, did not show it at first.

I enabled AHCI and nothing happened. Only after adding the pci=nomsi option did the sata drive show up. Enabled Sata back in the bios and with pci=nomsi option, it still shows...

But could you please explain what this option does ?
So when you put the drive back in SATA mode instead of AHCI mode, but still used "pci=nomsi", you could still see the drive OK in Ubuntu? I just want to confirm because that's good info to know if you didn't have to use AHCI after all. And by the way, what that kernel parameter "pci=nomsi" does is disable "MSI", or Message Signaled Interrupts. If you want more info, you might want to read the Wikipedia page:

[http://en.wikipedia.org/wiki/Message_Signaled_Interrupts](http://en.wikipedia.org/wiki/Message_Signaled_Interrupts)

Anyway, I'm glad that Ubuntu can now see your SATA drive. :)

---

### Post by dips0502 on 2009-02-20
yes..thats right...i didnt hv to use AHCI ; only the extra pci=nomsi was all i needed...

---

