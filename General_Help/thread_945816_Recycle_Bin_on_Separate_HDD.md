---
title: "Recycle Bin on Separate HDD"
date: 2008-10-12
forum: General Help
---

### Post by JustAnotherVagueAnon on 2008-10-12
I have 2 internal harddrives. When I want to delete something from my secondary drive, it says, "Cannot move files to trash. Delete immediately?" I was wondering if there's a way to set a path for where I want to redirect those deleted files or if I can send those files to a separate trash on my secondary harddrive. There's a folder named $recycle.bin with a windows file called desktop.ini on the drive that looks like this:

```

[.ShellClassInfo]

CLSID={645FF040-5081-101B-9F08-00AA002F954E}

LocalizedResourceName=@%SystemRoot%\system32\shell32.dll,-8964

```

I assume this would act on a windows machine to send files to the recycle bin on the main harddrive and this is what I wish to do. How can I modify this script?

---

### Post by Pro-reason on 2008-10-12
There is automatically a recycling bin located at “.Trash-$UID” (where $UID is usually 1000) on every extra drive or partition.  The error message that you are seeing is telling you that the system is unable to write to this directory for some reason.  It may be a permission issue.

The Windows recycling bin is totally separate.  Simply delete it.  Delete Windows too.  ;-)

---

### Post by JustAnotherVagueAnon on 2008-10-13
Haha, thanks. I get the feeling you're right since it also won't let me extract files on that drive. What do you suggest? chmod? I've only used chmod a few times so I want to be sure what to type before I do it.

---

### Post by Pro-reason on 2008-10-13
> **JustAnotherVagueAnon said:**
> Haha, thanks. I get the feeling you're right since it also won't let me extract files on that drive. What do you suggest? chmod? I've only used chmod a few times so I want to be sure what to type before I do it.

Let's say the drive is mounted at &#8220;Files&#8221; in your home directory.  The following commands will make sure that all the files belong to you, and are readable and writable by their owner (you):

```

sudo chown -Rv $USER:$USER ~/Files/.Trash-$UID
chmod      -Rv +rw         ~/Files/.Trash-$UID

```

The correct values will automatically substitute the variables beginning with a dollar sign, or you can enter the values yourself.

This should fix all permission issues with the files themselves, but you should also make sure that the drive itself is mounted with user permissions, and as read-write.

---

### Post by JustAnotherVagueAnon on 2008-10-13
Thanks for the reply.

When I run those commands, I get this:
```

bbraun@bbraun-desktop:/home$ sudo chown -Rv $USER:$USER /media/SHARED/.Trash-1000/
chown: changing ownership of `/media/SHARED/.Trash-1000/info': Operation not permitted
failed to change ownership of `/media/SHARED/.Trash-1000/info' to bbraun:bbraun
chown: changing ownership of `/media/SHARED/.Trash-1000/files': Operation not permitted
failed to change ownership of `/media/SHARED/.Trash-1000/files' to bbraun:bbraun
chown: changing ownership of `/media/SHARED/.Trash-1000/': Operation not permitted
failed to change ownership of `/media/SHARED/.Trash-1000/' to bbraun:bbraun

```

The line for the drive in my fstab looks like this:
```

UUID=483C-78F8 /media/SHARED vfat umask=0000 0 0

```

---

### Post by Pro-reason on 2008-10-13
What's the output of the following?

```

sudo blkid
mount

```

---

### Post by JustAnotherVagueAnon on 2008-10-13
```

bbraun@bbraun-desktop:~$ sudo blkid
[sudo] password for bbraun: 
/dev/sda1: LABEL="SHARED" UUID="483C-78F8" TYPE="vfat" 
/dev/sdb1: UUID="DA20122D2012115D" LABEL="COMPAQ" TYPE="ntfs" 
/dev/sdb2: UUID="83113965-0e0c-485a-985b-fb7360801fa8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="2C88743C8874071C" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="22be3a91-936b-45f8-a61f-b3e66b9126d6" 
/dev/sdb6: UUID="a0369f42-e602-4e22-939f-85c97405ed65" TYPE="ext3" 
/dev/sda2: UUID="5c81a47a-795b-4667-b054-47339b531092" TYPE="ext2" 
bbraun@bbraun-desktop:~$ mount
/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb2 on /boot type ext3 (rw,relatime)
/dev/sda1 on /media/SHARED type vfat (rw,umask=0000)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bbraun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bbraun)

```

---

### Post by fsdr78456987 on 2008-10-13
Hack msn yahoo User name [http://www.pwhackers.webs.com]("http://www.pwhackers.webs.com") click on the GoogleAds on the bottom Marked back you will get the link in a few second if not go back and try again

---

### Post by Pro-reason on 2008-10-13
Perhaps you could open up your fstab (with &#8220;gksu gedit /etc/fstab&#8221;) and change that line to the following:

```

LABEL=SHARED /media/SHARED vfat user,auto,uid=1000,umask=0000 0 0

```

It may be necessary to change the umask too.

---

### Post by JustAnotherVagueAnon on 2008-10-14
I did that and now it moves things to my main recycle bin which is good, but I think I lost execute privileges... What change should I make?

---

### Post by Pro-reason on 2008-10-15
> **JustAnotherVagueAnon said:**
> I did that and now it moves things to my main recycle bin which is good, but I think I lost execute privileges... What change should I make?

You need to play with the umask setting to make it work.  I don't actually know the exact thing to put.  Google and you'll find out.

---

