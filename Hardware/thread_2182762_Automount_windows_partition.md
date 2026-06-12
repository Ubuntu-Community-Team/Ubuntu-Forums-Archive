---
title: "Automount windows partition"
date: 2013-10-22
forum: Hardware
---

### Post by rob20 on 2013-10-22
Hi all

I am running Ubuntu 13.04

I have a windows drive in the machine. It is accessible from the file manager under ubuntu, but when I create network shares on the drive they are lost after a reboot.
The drive pops up in /etc/mtab
I think I need to put the drive in /etc/fstab so it is automatically mounted on boot rather than mounted when first accessed. I think this will mean the shares "stick" and do not need to be created on every reboot. I may be wrong......

In etc/mtab the drive is listed as below.
/dev/sda1 /media/rob/New\040Volume2 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

What would I need to put in to fstab to auto mount this drive on boot. I have tried copying the above line to the fstab file but this produces an error on boot and the drive is not accessible.

Thanks for any help you can offer.

Rob

---

### Post by ian-weisser on 2013-10-22
What is the exact boot error?

---

### Post by rob20 on 2013-10-22
Hi Ian.

The message on the boot screen was "An error occurred while mounting /media/rob/New Volume2"

Whe I tried to access the drive from the file manager I got :-
Error mounting system-managed device /dev/sda1: Command-line `mount "/media/rob/New Volume2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is using the command found in mtab, pasted into fstab.

Could not find much in the syslog but then I don't really know what I'm looking for.

Thanks

Rob

---

### Post by drmrgd on 2013-10-22
The way that I usually do it is as follows:

First I like to use the UUID of all drives in fstab in order to prevent any issues down the road with partitioning.  To get that, you can run:

```

sudo blkid

```

So, for one of my NTFS drives, I get this:

```

/dev/sde1: LABEL="Windows Drive" UUID="9E68AD6368AD3B43" TYPE="ntfs"

```

Now, I add an entry to fstab (I usually like to backup the current fstab to something like fstab.bak in case I really hose something):

```

# Windows Drive Mount 
UUID=9E68AD6368AD3B43   /media/Windows\040Drive       ntfs    defaults        0       0

```

In this entry, there are a couple things to note:


[LIST=1]
[*]I'm using the UUID as the drive identifier rather than something like /dev/sde.
[*]Since there's a space in the drive label, I need to add the '\040' octal code to the entry.  Adding a space or anything like that will cause an error, and you need to use the octal escape code for a space in the name.
[*]For me all the default parameters are good enough, and I don't need to worry about setting permission masks or anything like that.
[/LIST]

Now that I have my fstab entry, I head over to /media, and create a directory for the drive to mount to:

```

sudo mkdir /media/Windows\ Drive && sudo chown $USER:$USER /media/Windows\ Drive

```

That code will create the new directory in /media that we referenced in the fstab entry, and change the ownership to your user name.  By default, the directory will have root privileges and unless you chown it, you won't have rw access.

That's about it.  Now when you reboot, your NTFS drive will mount to the mountpoint you specified in fstab and you should be able to access it all the time.  Hope that helps.  Post back if you still have questions.

---

### Post by rob20 on 2013-10-23
Sir, you are a hero.

I stepped though your instructions and now have a windows drive mounted on boot.

The reason for this was so network shares stuck between boots.
After following your instructions I was unable to make shares, but Ubuntu told me how to fix this.
By adding :-
```
usershare owner only = false

```
to the samba config file "/etc/samba/smb.conf" I was again able to create shares by right clicking and following the menu prompts, and these share "stuck" between reboots.

Thanks very much for all your help.

Rob

---

