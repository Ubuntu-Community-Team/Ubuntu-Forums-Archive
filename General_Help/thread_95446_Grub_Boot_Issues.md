---
title: "Grub Boot Issues"
date: 2005-11-26
forum: General Help
---

### Post by dwessell on 2005-11-26
Hello all.

Oh what a tangled web we weave :)

So I was having some issues with ATI drivers for Ubuntu.. And I managed to make a big ole mess of it.. So I thought hey.. Let's just delete Ubuntu and start all over.. That sounds like fun..

So I booted into Windows XP (Dual boot), deleted everything but the Windows partition.. Felt pretty happy.. Rebooted.. And oh no.. Grub error 22... :) I had imagined that grub was on one of the linux partitions, and deleting everything would just have the machine booting into Windows again... Obviously I made a mistake in judgement somewhere.

Both Windows and gparted (Ubuntu live CD) show there only being the one NTFS partition... Can anyone offer advice to get rid of Grub, so that I'm just booting into Windows again.. Then I can reinstall Ubuntu for more playtime?

Thanks
David

---

### Post by qbproger on 2005-11-26
you apparently have a windows computer at home other than the one with ubuntu.  Make a MSDOS boot disk.  there is a command to re-write the windows boot loader.  I'm not 100% sure what it is.

[http://www.cs.princeton.edu/~jrc/windows/winnt/dualboot.html](http://www.cs.princeton.edu/~jrc/windows/winnt/dualboot.html)

i think it's here.

---

### Post by Irony on 2005-11-26
*Boot from XP installation disc > press any key on prompt to boot from CD > after some time options appear, press R for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

Note it may take some time before you get to the R for recovery console.

Or;

Boot from the install ubuntu CD and at the prompt typed;

*boot: rescue*

Go to a  mount point;

*dev/disc/disc0/part1*

type;

*grub-install /dev/hda*

After being returned to the prompt, do;

[I]#umount /dev/hda5
#reboot[/I]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot (when you see the BIOS name, CPU, and RAM), it will open. If you can't seem to get it open naturally, enter the BIOS setup and change the boot sequence to bypass the CD, boot normally, login, and eject the CD. Try not to use the pin or hard-reset.

---

### Post by Kevinator on 2005-11-26
If you can boot from a windows boot disk you can probably do

fdisk /mbr

to restore the master boot record to the Windows default. You might also be able to restore the MBR from the Windows recovery console if you boot from your Windows CD.

I suppose you could also just boot from your Ubuntu installation CD and begin the installation. The Windows partition should be detected, just make sure you don't accidentally format it. When Grub is installed it should create an entry for Windows. This might be the easiest option.

---

### Post by lcg on 2005-11-26
[QUOTE=dwessell]So I booted into Windows XP (Dual boot), deleted everything but the Windows partition.. Felt pretty happy.. Rebooted.. And oh no.. Grub error 22... :) I had imagined that grub was on one of the linux partitions, and deleting everything would just have the machine booting into Windows again... Obviously I made a mistake in judgement somewhere.[/QUOTE]
Well, GRUB itself is located in the master boot record. Unfortunately for you, it reads its configuration from /boot/grub/menu.lst, which is (and in your case, was) on your Ubuntu root partition.

[QUOTE=dwessell]Both Windows and gparted (Ubuntu live CD) show there only being the one NTFS partition... Can anyone offer advice to get rid of Grub, so that I'm just booting into Windows again.. Then I can reinstall Ubuntu for more playtime?[/QUOTE]
You can use a Windows XP CD, boot from it and start the recovery console. (Or was it called repair console? Doesn't really matter, you should recognize it when you see it.) After entering your administrator password, you can execute commands to restore your Windows. The command that should fix your problem is 'fixmbr' (without quotes).
However, be advised that a friend of mine lost his partition table when he restored his MBR with this procedure. This has never created any problems for me, though. YMMV.

HTH,
Lars

---

### Post by lcg on 2005-11-26
[QUOTE=Irony]
*grub-install /dev/hda*
[/QUOTE]
I don't think that this will help. After all, it's not Grub that is missing, but rather its config file, which is gone with the Ubuntu partition.

But after reading the original post again, I think it would be sufficient to install Ubuntu again. If I understand correctly, that was dwessel's intention anyway, and it would give him back a working configuration for Grub (and therefore a working Grub).

Lars

---

### Post by dwessell on 2005-11-27
Well that did it!! Reinstalling Ubuntu fixed the grub issue!! Thanks for all the help!! Now back to the 'how to install my video drivers' post :-)

Thanks
David

[QUOTE=lcg]I don't think that this will help. After all, it's not Grub that is missing, but rather its config file, which is gone with the Ubuntu partition.

But after reading the original post again, I think it would be sufficient to install Ubuntu again. If I understand correctly, that was dwessel's intention anyway, and it would give him back a working configuration for Grub (and therefore a working Grub).

Lars[/QUOTE]

---

