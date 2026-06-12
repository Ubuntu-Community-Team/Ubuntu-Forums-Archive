---
title: "Grub 2 not getting updated"
date: 2017-09-20
forum: Hardware
---

### Post by selvarajarun1 on 2017-09-20
Hi,

Appreciate if anyone can take a look at the bootinfoscript output and let me know how I can determine which partition is the controlling partition. The bios shows two ubuntu entries and one of them is correct. The other is an older (or from one of the other installations) and i am trying to figure out which one is driving it. JUst looking to clean up all the grub cfg files is the distros and have a clean install. Any suggestions or alternative bootloaders are welcome.

Thanks,

Arun.

[https://paste.ubuntu.com/25577544/](https://paste.ubuntu.com/25577544/)

---

### Post by oldfred on 2017-09-20
Boot-Repair's report does not show the /EFI/ubuntu/grub.cfg file which is the actual file that controls which install boots. All flavors of Ubuntu (except Kubuntu) install to /EFI/ubuntu and use grub.cfg to chain to the full grub.cfg in the install. So last install is probably the one in control.

It looks like you have Windows installed, but do not have the Windows in the ESP - efi system partition, your sda1? You should have a /Microsoft folder. You would need Windows repair disk to fix that.

You may not be able to see the ESP from your installs. Ubuntu changed the mount of the efi partition in fstab, probably for security reasons. But to edit or repair ESP you have to mount it. I still change to defaults and Boot-Repair changes fstab entry to defaults so it can update entries.
Example:
 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    [COLOR=#ff0000]defaults[/COLOR]        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 

You should also be able to mount the ESP from live installer.
Then post this to see which partition is used as default boot. Note in mine I have another install of Ubuntu and commented out/edited back to my default install. I also have copies/backups of the entire ESP.

```
fred@Asusz97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

You can edit grub.cfg configfile in ESP to use any grub.cfg from any install you have. I have yet not found a way to have more than just /EFI/ubuntu as Ubuntu's grub internally is hard coded to find /EFI/ubuntu/grub.cfg. So even creating /EFI/xenial still booted the grub.cfg in /EFI/ubuntu. It seems Mint is using Ubuntu's grub as it also has same issue. But Debian is now using newer grub and does not seem to be hard coded, so I want to install it.

---

### Post by selvarajarun1 on 2017-09-20
> **oldfred said:**
> Boot-Repair's report does not show the /EFI/ubuntu/grub.cfg file which is the actual file that controls which install boots. All flavors of Ubuntu (except Kubuntu) install to /EFI/ubuntu and use grub.cfg to chain to the full grub.cfg in the install. So last install is probably the one in control.


It looks like you have Windows installed, but do not have the Windows in the ESP - efi system partition, your sda1? You should have a /Microsoft folder. You would need Windows repair disk to fix that.


You may not be able to see the ESP from your installs. Ubuntu changed the mount of the efi partition in fstab, probably for security reasons. But to edit or repair ESP you have to mount it. I still change to defaults and Boot-Repair changes fstab entry to defaults so it can update entries.
Example:
14.04 fstab entry defaults
UUID=FD76-E33D /boot/efi vfat defaults 0 1
16.04 fstab entry umask=0077
UUID=68CD-3368 /boot/efi vfat umask=0077 0 1 


You should also be able to mount the ESP from live installer.
Then post this to see which partition is used as default boot. Note in mine I have another install of Ubuntu and commented out/edited back to my default install. I also have copies/backups of the entire ESP.


```
fred@Asusz97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
#search.fs_uuid fabeeda1-ad36-4300-a7f8-73afba118f37 root hd1,gpt9 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```


You can edit grub.cfg configfile in ESP to use any grub.cfg from any install you have. I have yet not found a way to have more than just /EFI/ubuntu as Ubuntu's grub internally is hard coded to find /EFI/ubuntu/grub.cfg. So even creating /EFI/xenial still booted the grub.cfg in /EFI/ubuntu. It seems Mint is using Ubuntu's grub as it also has same issue. But Debian is now using newer grub and does not seem to be hard coded, so I want to install it.




Thanks Oldfred. Couple of things about the system. sda had windows 7 on it. This was on a system without an UEFI bios. When I upgraded the system I may not have installed from scratch. sde has Ubuntu, Kubutu, Gnome Ubuntu, Elementary and Mint (installed in that order). Windows 7 was updated to Windows 10 in place and for a while, all was well. I installed grub customizer on Ubuntu, Kubuntu and Mint and every now and then when Mint updated its kernel grub settings would get updated as well. I haven't had a chance to turn that off yet in Mint. 


Since everything was going so well, I decided that I needed to upgrade the hard drive and play around with trying to move all the partitions into the new drive. Also wanted to try LVM with all the extra storage. So I reinstalled windows 10 into the new SSD(sdd) and copied over all the / and /home partitions of the installations over to the SSD using gparted. (tried clonezilla and it did not seem to be that much easier). I learnt that "copying" in linux literally means that. And I had to go in and learn to change UUIDs and fstabs of all the partitions  to fix it. It was a lot of fun. My plan is to delete the windows from sda and all the linux installations on sde and keep sdd alone. The other two hard drives sdb/sdc were extra laptop hard drives but were not formatted clean so it has a windows boot partition on it.


When you said last install, does it matter if I copied the partitions over (I assume it shouldnt?). I'll run those commands as soon as get back home but if I was going to remove sda & sde I would have to install grub into sdd. Does it matter which copied partition I install grub from or should I do that from a Live CD? I guess once I figure out how to edit the grub.cfg file, I can choose which one to use.


The link in your signature was pretty useful and I've been reading up on rEFInd and it looks like it will work better than Grub when you have different distros. I might just do that on the sde drive to see how that turns out.


Arun.

---

### Post by oldfred on 2017-09-20
I have also wanted to try rEFInd, but have not gotten around to it. 
Grub will still be your boot loader, but UEFI, grub & rEFInd are boot managers or menus.

When you have multiple installs, it gets confusing. I regularly run Boot-Repair's report or bootinfoscript which is really the first part of the Boot-Repair report, just so I know what is where. I modify bootinfoscript to include my grub.cfg in the ESP, but not sure how in Boot-Repair.

Windows only boots in UEFI mode from gpt partitioned drives and only in BIOS boot mode from MBR drives. Ubuntu can boot in either UEFI or BIOS from gpt if correct partitions are on drive, and BIOS boot from MBR. A few have had Ubuntu on a MBR drive but sda was gpt were able to boot in UEFI mode thru sda's gpt into an install on sdb. Not recommended.
I suggest all drives should be gpt, and all drives have an ESP (even if not really used currently) and if you want or later may want BIOS boot include the bios_grub partition. I automatically use gpt and first two partitions are ESP & bios_grub. Neither need to be large, so I do same for larger flash drives also.

Grub in UEFI mode, only installs to the ESP - efi system partition on drive seen as sda. I manually copy back to ESP on install drive, more just as backup, but it would not directly boot on its own without an entry in UEFI. I do keep my 16.04LTS as main working install on sda & in sda's ESP, but have other installs of Ubuntu flavors or versions on both sda & sdb and have to reset grub.cfg in ESP on sda every time. Telling grub to install to sdb works with BIOS, but even though an UEFI install will say installing grub to sdb, it really will be in the ESP on sda.

---

