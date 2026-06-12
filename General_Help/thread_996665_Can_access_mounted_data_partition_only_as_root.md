---
title: "Can access mounted data partition only as root"
date: 2008-11-29
forum: General Help
---

### Post by korami on 2008-11-29
Hi there,

A few days ago I had to reinstall Ubuntu Intrepid because of an error I couldn't solve. Now I'm stick with the following issue:

I have an ext3 data partition which I used to mount with fstab under myhome/mydir. This has been working for a couple of years already. Since the reinstall though, I can see the files under /mydir only as root, but not as regular user. That is, with "gksudo nautilus" I can see the contents, but as regular user, the directory is empty. 

Also, when I try to create a new directory under /mydir, I receive the following error: "Error creating directory: Permission denied".

fstab line for the partition in question reads as follows:
```
# /dev/sda6
UUID=d775cc10-eb81-49e0-8687-19b55fd31e16  /home/korami/mydir  ext3  relatime,noexec  0  2
```
Have tryed with several other options...

*ls-l *for my home directory gives the following output:
```
total 188
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Desktop
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Documents
lrwxrwxrwx  1 korami korami     26 2008-11-27 22:18 Examples -> /usr/share/example-content
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Music
**drw-rw-rw- 10 korami korami   4096 2008-11-28 22:47 mydir**
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Pictures
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Public
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Templates
drwxr-xr-x  2 korami korami   4096 2008-11-27 23:08 Videos

```

One more thing that might worth mentioning it, is that when I access in nautilus the /mydir directory as regular user, in the button/based location bar, /mydir turns into "54.8 GB media". This isn't the case with "gksudo nautilus" though.

I didn't find any similar issue through the posts. Can anyone help please?

---

### Post by nic2 on 2008-11-29
According to file permissions you cannot execute the directory named 'mydir' - change the file permissions to enable you to execute this directory.

---

### Post by korami on 2008-11-29
Done that, but when mounting, the execute option is overwritten...

However, even without the rights to execute binaries, I guess I should still be able to read/write in the folder...?

---

### Post by vanadium on 2008-11-29
THe execute permissions are not overwritten during mounting. First make sure (with "ls -l") that you actually changed the permissions for mydir to "execute".

---

### Post by korami on 2008-11-29
This is the output of "ls -l" when partition not mounted:
```
drwxr-xr-x 2 korami korami   4096 2008-11-27 21:32 mydir
```

After mounting:
```
drw-rw-rw- 10 korami korami   4096 2008-11-28 22:47 mydir
```

So I guess the mount does that, based on the options in fstab.

But again, even without execution possibility, I still should see those folders/files under /mydir, right?

---

### Post by louieb on 2008-11-29
Try changing /etc/fstab to use the default options. 
```

# /dev/sda6
UUID=d775cc10-eb81-49e0-8687-19b55fd31e16  /home/korami/mydir  ext3  [COLOR=Red]defaults[/COLOR]   0  2
```

The execute option when on a directory is what allows you to list the file and folders in it.   
```
chmod 777 /home/korami/mydir
```

Thats how I normally set up a data partition.  This will allow any user to list the files and folders. They can create files and folders. 

Buy the way I also mount it on /meda/stuff and let root own it. That way a user can create files and folders inside the directory and have control over who can read and write their files. But can't accidentally change permissions on the mounted folder itself.

:confused:Hope this makes sense.

---

### Post by nic2 on 2008-11-29
noexec in field 4 of the fstab entry prevents you from executing binaries that are on that partition - try deleting this _or_ follow the suggestion made by louieb.

---

### Post by korami on 2008-11-29
Thanks louieb, that did work. Thanks also to vanadium and nic2.

What I've been keeping on doing is to make the mydir folder executable when data partition was unmounted. Now I've done that with the partition mounted and it worked.

Now I only have 2 more small questions:
1. In the button-based location bar, /mydir turns into "54.8 GB media". Is there a way to change that?
2. I want to also mount the data partition under my wife's home partition (/home/thewife/mydir). Is it ok to mount the same partition under 2 different mount points at the same time (via fstab)?

---

### Post by vanadium on 2008-11-29
So it was indeed the exec option: I should have seen it as well. You can only "traverse" directories when they have the executable bit set.

> 1. In the button-based location bar, /mydir turns into "54.8 GB media". Is there a way to change that?
Strange that a partition mounted through /etc/fstab behaves like this. Does this behaviour continue after a reboot? Anyway, changing the volume label of the drive to "mydir" will have nautilus use "mydir" as well. See [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) for how to label parititions.
> 
2. I want to also mount the data partition under my wife's home partition (/home/thewife/mydir). Is it ok to mount the same partition under 2 different mount points at the same time (via fstab)?
You should be working with symbolic links rather than with mounts.

Instead of mounting under your home directory, mount under /mnt instead. Then create a symbolic link to it in your home directory and one in the home directory of your wife.

* Make a new directory /mnt/mydir with a nautilus with root permissions ("gksu nautilus") or a command "sudo mkdir /mnt/mydir"

* Change the line in /etc/fstab to reflect the new mount point

```

# /dev/sda6
UUID=d775cc10-eb81-49e0-8687-19b55fd31e16  /mnt/mydir  ext3  defaults  0  2

```

* Make the new /etc/fstab active

```

sudo mount -a

```

Now, you can create links to the partition. With nautilus, you do this by pressing Ctrl+Shift and dragging the /mnt/mydir directory to your home directory. Do this the same for your wife. You will need to adjust permissions so that both you and your wife can use the same storage space.

If you want separate storage for you and for your wife, first create, as riit user, two directories, say "myself" and "mywife". Change the owner of the directories to yourself and your wife, respectively. Then create a symbilic link to "myself" in your home directory and a symbolic link to "mwywife" in your wife's home (the latter she must do herself or you must do it as root).

As a general note: in linux, it is good practice to mount exclusively under /mnt (if you do not want an icon on your desktop) or under /media (which will cause the volume to appear as an icon on your desktop). All the rest you can arrange with links. THe user does not need to know about mount points. He navigates wherever he is allowed to through links in his home directory.

---

### Post by korami on 2008-11-29
Thanks vanadium for the answers.

Re my first question, I did several boots, with the same results.

However, your advise regarding mounting under /mnt did solve the issue. The "54.8 GB media" label also disappeared. Also another issue I had was solved: following an advise from another forum, I changed the .profile filed from both users so that when creating files/folders, also the group receives the read-write (instead of the default read only) permissions; however this didn't work before, it is however working now.

So cheers for the answers.

---

