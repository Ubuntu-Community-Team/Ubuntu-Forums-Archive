---
title: "ubuntu hangs on boot. &quot;acpi = off&quot; &quot;noapic&quot; and &quot;nolapic&quot;"
date: 2008-07-16
forum: Hardware
---

### Post by villageillness on 2008-07-16
:)............

---

### Post by chicken101 on 2008-07-16
In the grub menu you can edit the entries to run these special parameters.
I found a blog [here]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html") which explains this process. Don't forget to back up these files first!

---

### Post by Rocket2DMn on 2008-07-17
You will want to add those options to /boot/grub/menu.list where it says "# defoptions" and "# altoptions"
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Do the edit, save and close, then run
```
sudo update-grub
```

---

### Post by villageillness on 2008-07-17
:).........

---

### Post by Rocket2DMn on 2008-07-17
You can't edit the menu.lst file until you are in Ubuntu.  It can be done from the LiveCD, but there isn't much point if it won't boot with the options entered manually in GRUB are not working.  Are you sure you are adding them in the right place from GRUB?  It should look similar to
```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=30fcb748-ad1e-4228-af2f-951e8e7b56df ro splash quiet acpi=off noapic nolapic
```
Note that there is no space between acpi, =, and off.  If you delete the "quiet" part you can see where it is hanging during the boot sequence.

---

### Post by villageillness on 2008-07-17
:)>..........

---

### Post by Rocket2DMn on 2008-07-17
You should make sure to add them to "# defoptions" and "# altoptions" like I said earlier because if an update comes around for GRUB or a new kernel is added, menu.lst will be regenerated and won't save the options you tagged on to the end of the kernel lines.

---

