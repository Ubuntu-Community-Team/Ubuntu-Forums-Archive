---
title: "error no such partion boot grub rescue"
date: 2011-07-13
forum: Hardware
---

### Post by JimmyFrix on 2011-07-13
Hello I'm trying to restore my laptop back to windows vista after completly wiping vista off and placing it with ubuntu. I've somehow seems to remove ubuntu but when I try restoring the laptop with the recovery cd I get an error, no such partion boot grub rescue when it's trying to format partions or something like that. I've been looking everwhere on how to fix this but everyone says go to the recovry tools from the recovery disc. The problem is the recovry disk I have is from acer and the only options I get is Restore system from factory default and exit, that's alll. When I try restore system from factory default t says this action will erase all existing data on Partion : .  I click okay and it begins to restore partion but when that is done I get the same error again. Anyone please help?

---

### Post by bennyroger on 2011-07-13
Are you sure the Disc you are using contain the whole backup or is it looking for a hidden recovery partition on the harddrive?

---

### Post by oldfred on 2011-07-13
A full recovery should restore the MBR also, but you still have a grub boot loader in the MBR which then  is missing the rest of the grub files it needs to boot.

You can restore a windows like boot loader with the Ubuntu liveCD, but if windows is not otherwise restored it will not work either.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.
[http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html)

---

