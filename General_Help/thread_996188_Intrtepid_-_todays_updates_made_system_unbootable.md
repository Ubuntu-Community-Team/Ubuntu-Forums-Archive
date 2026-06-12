---
title: "Intrtepid - todays updates made system unbootable"
date: 2008-11-28
forum: General Help
---

### Post by tattrat on 2008-11-28
I opted to install all the update offered this morning by update manager. These included kernal upgrades. 

After the upgrades are applied the system will not boot (to either kernel); grub returns error 11, 

So I booted the system with live cd to discover that the update process has altered /boot/grub/menu.lst so that the line which previously read:
```
uuid     75208e07-98bf-4c69-84d2-53c98d80740c[CODE]
```[/CODE]

has been altered to:

```
root     75208e07-98bf-4c69-84d2-53c98d80740c[CODE]
```[/CODE]

Am I right in assuming that this is what is causing grub to fail?

If so I would appreciate if someone could tell me how to edit menu.lst, via booting from the live cd.

Thanks.

---

### Post by jakupl on 2008-11-28
> **tattrat said:**
> I opted to install all the update offered this morning by update manager. These included kernal upgrades. 

After the upgrades are applied the system will not boot (to either kernel); grub returns error 11, 

So I booted the system with live cd to discover that the update process has altered /boot/grub/menu.lst so that the line which previously read:
```
uuid     75208e07-98bf-4c69-84d2-53c98d80740c[CODE]
```[/CODE]

has been altered to:

```
root     75208e07-98bf-4c69-84d2-53c98d80740c[CODE]
```[/CODE]

Am I right in assuming that this is what is causing grub to fail?

If so I would appreciate if someone could tell me how to edit menu.lst, via booting from the live cd.

Thanks.

This might be a stupid question but... I generally like annoying people :)

Are you sure that it was your installation menu.lst, not the live session menu.lst?

---

### Post by drs305 on 2008-11-28
From the livecd desktop, open a terminal. To see your normal installation menu.lst, you will need to mount that partition first. You will have to know which partition your ubuntu installation is on and substitute it's designation (sdXX) in the mount command below:

```

sudo blkid
sudo mkdir /mnt/temp
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt/temp  # substitute your ubuntu installation's actual location, e.g. /dev/sda1
gksudo gedit /mnt/temp/boot/grub/menu.lst

```

---

### Post by tattrat on 2008-11-28
> **jakupl said:**
> This might be a stupid question but... I generally like annoying people :)

Are you sure that it was your installation menu.lst, not the live session menu.lst?

Of course I am sure - I mounted the filesystem and chrooted to it; I just don't know how to then edit it, with the right privelidges. 

I am not so partial to annoying people now you mention it.

Oh and it is a stupid question - the live cd does not have a menu.lst which refers to my hard disk - I was obviously checking to ensure that the value of uuid was correct, when I notice the format of the line was changed. In fact it doesn't even have  /boot/grub.

---

### Post by tattrat on 2008-11-28
Thank you drs305 for the sensible answer - I have now edited menu.lst to what it should be .

Surely this is a bug in the update process? - as I understand it the correct command in menu.lst if you are using UUIDs is 'uuid' and not 'root'. The update used 'root' with a UUID and altered the commands for my existing kernel also. I did not make any changes this was all done by the update process.

---

