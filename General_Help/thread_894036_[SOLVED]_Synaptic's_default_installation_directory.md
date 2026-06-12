---
title: "[SOLVED] Synaptic's default installation directory"
date: 2008-08-18
forum: General Help
---

### Post by Elcid247 on 2008-08-18
is there a way to change the default directory where synaptic installs the packages it downloaded?

i cant seem to resize my root partition with Gparted or partition magic on windows or even when i boot with my ubuntu CD, so i need some space for future programs.

i want to be able to choose where the packages install like u could do in windows when u specify the installation directory.

---

### Post by the yawner on 2008-08-18
I dont think that's possible. Unlike Windows, application packages in GNU/Linux are installed over specific directories and not just one directory. But I did read that resizing the root partition is possible.

---

### Post by cdtech on 2008-08-18
If your afraid of running low on space, do to your package cache, a couple methods I use:

Go into "Synaptic Package Manager" go to the "Settings -> Preferences" 
go to the "files" tab and select "Delete downloaded packages after installation" this will clear the "apt cache" every time you apt-get install a program.

You can use an alias:
alias clean='sudo apt-get autoclean && sudo apt-get autoremove'

Or an easier method of the above would be to set it permanently within "/etc/apt/apt.conf.d/10periodic" by setting the interval of the update:
APT::Periodic::AutocleanInterval "1";

Hope this helps......

---

### Post by sameerds on 2008-08-18
> **Elcid247 said:**
> is there a way to change the default directory where synaptic installs the packages it downloaded?

There probably isn't a way to do this, and this practice should be strongly discouraged even if there is.

> **Elcid247 said:**
> i cant seem to resize my root partition with Gparted or partition magic on windows or even when i boot with my ubuntu CD, so i need some space for future programs.

You should follow up on this problem and figure out a good way to resize the root partition. There is another option which is a little more risky, and needs very careful planning. If you miss a step, you can lose your system.

This method uses the fact that all the packages install all there files in a directory called "/usr". What you can do is create a new partition, and use it for /usr. In order for this to work, you need to move all the existing files in the current /usr, to the new partition and then modify /etc/fstab to always mount this partition as /usr.

I am being deliberately vague about the details here, because this is a risky procedure, and I don't want to pretend that I can talk you through it over forum messages like this. The procedure definitely works and I have done it often enough. But you will need to get up to speed about the details.

> **Elcid247 said:**
> i want to be able to choose where the packages install like u could do in windows when u specify the installation directory.

This is one of the strong points of good package management systems like deb and rpm. Even if it were possible to change the default destination, it is most definitely not a good idea.

---

### Post by Elcid247 on 2008-08-19
@the yawner

i tried using Gparted, fdisk, partition magic on xp, my ubuntu's live CD, and searched google for alot of time, but found nothing tht would work...

@cdtech

well i managed to get arround tht by linking my /var/cache/apt/archives to a new folder in a separate partition. got it from the last post in this thread.

[http://ubuntuforums.org/showthread.php?t=671990](http://ubuntuforums.org/showthread.php?t=671990)


@sameerds

well could linking work like i did for the cache?

and um, i like taking risks, guess thts y im using ubuntu in the 1st place lol, i like messing arround with my comp ALOT! :D:D

but if ur afraid ur not gonna be able to guide me through it, and i understand tht u dont want to mis-guide me and i respect tht, but can u atleast give me some links or resources? thanx

---

### Post by cdtech on 2008-08-19
You can create a separate /var partition using the "gparted live cd" and mount the /var within the fstab file.

---

### Post by Elcid247 on 2008-08-19
> **cdtech said:**
> You can create a separate /var partition using the "gparted live cd" and mount the /var within the fstab file.

thnx, um what will the parameters of the fstab look like? (little new to it)

---

### Post by cdtech on 2008-08-19
**[COLOR="Blue"]NOTE::.[/COLOR]**
**This procedure must be ran using the "Live CD". In moving the /var directory it must be done on a non running system......**
[COLOR="Red"]**thanks to sameerds for pointing that out.**[/COLOR]

Create a folder to backup the contents of /var (just in case you need to fall back).
```
$ sudo mkdir /var1
```

Move the contents of /var to /var1
```
$ cd /var
$ sudo mv -R /var/* /var1
```

The command above will move your existing /var contents to the backup folder /var1.

Backup your /etc/fstab file so that if you have to you can roll back your changes.
```
$ sudo cp /etc/fstab /etc/fstab.bak
```

Using the "gparted live cd" create the partition for your new /var directory.

Edit /etc/fstab so that the /var directory points to the correct partition.
```
$ sudo pico /etc/fstab
```
add a line to mount the **new** /var partition:
```
**UUID=aed3efe3-53d1-4b88-9c36-c87678436f45** /var ext3 defaults 1 2
```
This is now the mount point for the new partition "/var".
(bold is the new partition block id)

Copy the contents of the /var1 directory to the newly created /var partition.
```
$ sudo cp -R /var1/* **/dev/sda?** (whatever the new partition is)
```

Reboot......

If and [COLOR="DarkRed"]**only if**[/COLOR] everything works and looks ok, just remove the /var and the /var1 directory from your "root /" partition.

---

### Post by sameerds on 2008-08-19
> **Elcid247 said:**
> well could linking work like i did for the cache?

Well, as a rule, symlinks "work", but the issues involved in moving /usr are bigger, since its the system directory itself. You can't move /usr in a running system, because for all practical purposes, /usr *is* the system. Moving /var/cache/apt/archives is easy because it not needed until your run a package manager.

Actually, the process that cdtech has posted for moving /var also requires that the system is not running. /var contains a lot of important files like locks and FIFOs that are used by active processes in the system.

> **Elcid247 said:**
> and um, i like taking risks, guess thts y im using ubuntu in the 1st place lol, i like messing arround with my comp ALOT! :D:D

More power to you, then! :)

> **Elcid247 said:**
> but if ur afraid ur not gonna be able to guide me through it, and i understand tht u dont want to mis-guide me and i respect tht, but can u atleast give me some links or resources? thanx


Too lazy to search for a proper HOWTO on this! So let me make my own ;)
All this also applies to /var; if you move /var, you can remove the symlink you are using and instead put archives back where it's supposed to be.

**_[COLOR="DarkRed"]WARNING:[/COLOR]_**
[LIST=1]
[*]The following steps may not be complete.
[*]I am just making this as I go along, I havn't actually tested it out right now. The procedure is of course, known to work.
[*]There might be unexpected issues with the commands used.
[*]The procedure is potentially dangerous to your entire system.
[/LIST]

First of all, you need a CD to boot from, since you can't touch a working system. Once you have booted from the CD, create a new partition to be used for /usr. Mount it with some temporary name ... I don't know how modern fancy GUIs do it, I just create a directory for this:

```
sudo mkdir /mnt/new_usr
sudo mount /dev/whatever-id /mnt/new_usr
```

I am not sure about whether you need sudo when booted into the LiveCD ... it probably doesn't log you in as root, and so you would need sudo.

Now assume your HDD root partition is mounted at /mnt/oldroot. Move the contents of /usr to the new partition

```
sudo cp -a /mnt/oldroot/usr/* /mnt/new_usr
```

Note that we actually copied the contents, not delete them. The files still occupy all the space in your root partition, but we will delete them only after testing and making sure that the system works correctly. The new partition will be mounted *over* the /usr directory, so the old contents will remain invisible.

Find the UUID of the new partition, so that we can put it in fstab.

```
$ sudo vol_id --uuid /dev/whatever-id
bb512692-1ea0-45df-b84a-173d368dec4c
```

Now edit the file /mnt/oldroot/etc/fstab to add an entry for the new partition. Note that I have just copied the line in my fstab, that refers to the root partition. I have not attempted to ensure whether the options used for root are applicable for usr.

```
UUID=bb512692-1ea0-45df-b84a-173d368dec4c  /usr  ext3  relatime,errors=remount-ro  0  1
```

Now you are ready to go. Reboot, and see if everything works. If it does, reboot from the CD again, and delete the contents of the old /usr directory, which should be visible as /mnt/oldroot/usr, but not the directory itself. Do be careful with the "rm -rf"

```
sudo rm -rf /mnt/oldroot/usr/*
```

---

### Post by sameerds on 2008-08-19
> **cdtech said:**
> Create a folder to backup the contents of /var (just in case you need to fall back).
```
$ sudo mkdir /var1
```

Move the contents of /var to /var1
```
$ cd /var
$ sudo mv -R /var/* /var1
```

The command above will move your existing /var contents to the backup folder /var1.



I don't think this can be done safely on a running system.

---

### Post by cdtech on 2008-08-19
You are so correct.......

I've updated to include using the "live cd" to perform the operation.

**Thanks..**

---

