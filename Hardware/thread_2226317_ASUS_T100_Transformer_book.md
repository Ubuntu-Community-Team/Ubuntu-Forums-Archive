---
title: "ASUS T100 Transformer book"
date: 2014-05-26
forum: Hardware
---

### Post by dead2 on 2014-05-26
Okay so, currently I have to factory reset my ASUS T100 because I apparently messed up windows(and i did not make a recovery USB before my Ubuntu installation, so now I can't even boot back into windows) That's fine, I learn by trial and error.. I will quickly mention that I am BRAND spankin new to Linux, so i appologize for my n00bness.

After I factory reset, I have a few questions for someone with experience with this.

So, I would like to be able to boot to Windows or Ubuntu and have both OS' operational.
I have a 64GB ASUS T100, I installed ubuntu on /dev/mmcblk0p5 which I had read was a recovery drive. I guess I should not have installed on that partition.
I'm booting Linux from a USB drive and doing full install after GRUB loader, and all of that is fine.. I am very resourceful and the internet answers most questions I have to get this going on my own.
However, Before I do anything else, I must figure out which partition to install onto and how.
What partition should I choose? Should I make a new one? if so, should I create a blank partition in windows before I install? do i reformat to ext4?

After I installed ubuntu(full) onto /dev/mmcblk0p5 I tried to boot into Ubuntu and was unsuccessful due to improper file locations(that's fine i'll work that out later.)
but when I tried to just reboot into windows i got "Attempting repair" then "Diagnosing PC" then "unable to fix problems"

Thanks in advanced

---

### Post by ajgreeny on 2014-05-26
Which versions of Windows and Ubuntu are you asking about?

If this is all about Win8 you may need to read and follow everything in [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") as there are many changes that are required because of that change to UEFI instead of legacy BIOS in most new machines.

---

### Post by dead2 on 2014-05-28
im on windows 8 and i've been following jfwells tutorial and others on how to install ubuntu. I shrunk the windows partition, leaving me with 16GB free space, i used 14 of it for a straight "/" install, no separate partitions for home or boot as that just complicated things for me. i used 2GBs for a swap.

I currently have it installed but I am unable to boot to the ubuntu partition (only the live USB bootable) and using the commands:
"linux (hd1,gpt6)/boot/vmlinuz-3.13.xxxx root=/dev/mmcblk0p6 video=VGA-1:1368x768e reboot=pci,force"
"initrd (hd1,gpt6)/boot/initrd-3.13.xxxx"
"boot"

i get booted into a loop of (i forget the exact output) but it's a bunch of errors saying not found and retry block read only etc
"timed out sending r/w cmd command" or something over and over. I can't get the wifi to work on the live USB boot or i would create a bootia32.efi into my boot/efi/EFI/ubuntu or whatever the directory is. i dont know if this is the only thing stopping me from booting, and i dont know how to get to the directory from windows if thats possible.

if i could get the wifi working i imagine i could just get boot-repair and go that route.

---

