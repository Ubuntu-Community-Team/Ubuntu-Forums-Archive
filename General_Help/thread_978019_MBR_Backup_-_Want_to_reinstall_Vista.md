---
title: "MBR Backup - Want to reinstall Vista"
date: 2008-11-10
forum: General Help
---

### Post by Amivit on 2008-11-10
Once I had only Vista installed on my HD.
Then I installed Ubuntu and now Ubuntu manages my dual boot with (I think it is called) grub.
I wish to reinstall Vista but am afraid that it will ruin my dual boot. How do I reinstall Vista and afterwards get everything back to normal so I can dual boot once again?
Thanks in advance! :)

---

### Post by TeXtonyx on 2008-11-10
Well, you don't have to reinstall Ubuntu, you just have to reinstall
grub. You are right that reinstalling Vista will overwrite the MBR
which currently has been written to by grub. It isn't just the MBR,
because grub will scan the drive and add an entry to menu.lst, which
is the grub boot menu options. 

I like to keep the dual booting OS's separate. If the Ubuntu partition
gets damaged or you want to get rid of it, then grub when it's 
installed to the MBR will no longer support booting because it has
support files on the Ubuntu partition. So Vista won't boot because
there is no grub menu to select it. You have to fix the MBR for
Vista to boot standalone again. So I use a different approach:

"If he chooses the default on installing grub to the MBR, and he
'wishes to get rid of Ubuntu in the future', then he will no
longer be able to boot Vista. I think the OP will consider this
to be affecting Vista. He can fix that with the Vista install cd,
but some people don't get those issued, instead they get OEM
recovery disks which don't permit executing the bootrec command.

The OP can avoid this by installing grub to the MBR in Step 7, 
Advanced, by choosing the /boot partition from the drop down 
menu. There is a program, Easybcd, for Vista, which puts Ubuntu 
on the boot menu. Then if he removes Ubuntu, there is no PITA 
situation. And if Vista has a problem, the OP can still boot 
Ubuntu with the Super Grub Disk."

Since you have to reinstall grub, you can reinstall grub to the
/boot partition, rather than the MBR, now. Then dl and use Easybcd.

---

### Post by bodhi.zazen on 2008-11-10
Naw, you do not need any of that. Grub is easy to restore.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by TeXtonyx on 2008-11-10
[http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)

You will want to verify where your Ubuntu grub files are located.
sudo fdisk -l
This will report all your partitions, and you're interested in the
one which is Linux type 83 ext3. This helps you know what to do.

Now to install grub. Since you've reinstalled Vista which wrote to
the MBR, you'll need Super Grub Disk (very handy) or your Ubuntu
live cd. After Ubuntu loads, open a terminal and type 
sudo fdisk -l 
and note the relevant information.

Next, sudo grub , then at the grub prompt >,
	
grub> find /boot/grub/stage1

This tells you where your grub stage1 files are located.

grub> root (hd0,?) use the information provided by the find command

If fdisk reported your ext3 83 partition on, sda5 for instance,
in grubspeak, that is (hd0,4) The 4 is the partition number,
which is one less that sda5, where 5 is the partition number.
That's how it works. sda4 for instance is grub (hd0,3)

Now the last important step, choose the MBR or the boot partition.

grub> setup (hd0) installs grub to the MBR like you are used to.

This way install grub to the Ubuntu boot partition.
grub> setup (hd0,?) this is the same information as the root 
(hd0,?) for instance root (hd0,4) would use setup (hd0,4)

grub> setup (hd),?) use the correct grub partition number

grub> quit

Then you would need to download free Easybcd and add Ubuntu 
to the Vista bootloader menu, under Linux. Keep in mind what
your setup (hd0,?) information was that you used. You don't
want to choose your Linux swap partition. 

I like being able to boot both OS from either grub or Vista/bcd
bootloaders. Both OS are now standalone with Ubuntu available
for boot by using the Super Grub Disk. If Ubuntu fails, Vista 
still works. I'm a believer in an ounce of prevention is worth
a pound of cure. If Ubuntu/grub fails, this preventive method
eliminates panic; and if you delete Ubuntu, restoring Vista MBR.

---

