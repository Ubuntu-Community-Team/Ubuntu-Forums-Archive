---
title: "Dual boot with Vista, cannot boot Ubuntu"
date: 2009-01-01
forum: Hardware
---

### Post by rusoman on 2009-01-01
Hi, I dual boot my Vista with Ubuntu v8.10. I follow the steps here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4") when I choose a bootloader, but when I try to boot my Ubuntu, this message came up:

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=8a9bf334-2c61-41d9-ad05-74e661 0a744b ro quiet splash

Error 17: File not found.


I can't access my Ubuntu. What should I do? Should I reinstall the OS? How?:(

---

### Post by logos34 on 2009-01-01
try using the symlinks in /:

Press 'e' on the highlighted ubuntu entry, 'e' again on the 'kernel' and 'initrd' lines and change to 

> kernel **/vmlinuz** root=UUID=8a9bf334-2c61-4...
initrd **/initrd.img** 

any luck?

---

### Post by rusoman on 2009-01-01
> **logos34 said:**
> try using the symlinks in /:

Press 'e' on the highlighted ubuntu entry, 'e' again on the 'kernel' and 'initrd' lines and change to 



any luck?

Ouch :cry:, I already format the partition where Ubuntu is placed. And I'm planning to install it again, can you give me instructions how to do it?:)

---

### Post by PatManOz on 2009-01-01
I have just been through this issue.
Because I know Windows very well and can usually rescue myself, I wanted to ensure that the PC booted to VISTA BY DEFAULT, and that Vista provided the option to continue (with Vista) or boot to Ubuntu if chosen.
IF
[INDENT]your PC currently boots to Ubuntu FIRST[/INDENT]
THEN
[INDENT]see [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)  for details of how to use Bootrec to restore default booting to Vista. Bootrec is available from the Vista install DVD, and I would rebuild BOTH the MBR and the Boot sector.[/INDENT]
END IF

Use Vista Disk Management to:
[INDENT]a) free up (say) 20 Gb on any drive.
b) In that free space create a 5 Gb partition (Ubuntu Swap Area).
c) a 15 Gb partition (Ubuntu Installation).
DO NOT FORMAT or assign a Drive Letter to either.
(Select partition sizes to suit YOUR needs).[/INDENT]
THEN

d) See [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) to download and install EasyBCD on Vista. This tool will enable you to manage the Windows BCD (Boot Configuration Data store) to select the OS (Vista [default] or Ubuntu).
e) See [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) for an EXCELLENT treatment of how to install Ubuntu. At step Three make a note of the Ubuntu 'names' for the two partitions you created. In my case they were (on drive D) /dev/sdb2 (5Gb swap) and /dev/sdb3 (15Gb Ubuntu)).  Use these at Step Six and you will be fine!!
f) Continue with that page, boot to Vista and use EasyBCD to create the (Vista) Boot Option for Ubuntu (Linux).
All the best - In Ubuntu an the New Year.

---

### Post by logos34 on 2009-01-01
> **rusoman said:**
> Ouch :cry:, I already format the partition where Ubuntu is placed. And I'm planning to install it again, can you give me instructions how to do it?:)

yep, little late if you formatted it already.

Try Patmanoz's suggestion (easyBCD, etc)

---

