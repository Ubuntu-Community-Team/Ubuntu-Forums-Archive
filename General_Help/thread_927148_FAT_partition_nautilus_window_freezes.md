---
title: "FAT partition nautilus window freezes"
date: 2008-09-22
forum: General Help
---

### Post by merry_meerkat on 2008-09-22
I dual boot and apart from the linux partitions I have a NTFS and a FAT partition. I use the FAT partition for all kinds of files to access from either OS.

Since recently, whenever I go to "Places" and then "24.1 GB Media" (that's the FAT partition), the window freezes after a couple of seconds (see attached screenshot). I have to force kill it, and when I do so, every time the panel reloads and my home folder opens in a window afterwards. Accessing the partition again just leads to the same problem.

During the freeze everything else is working fine. I just cannot open any nautilus window and I cannot click on any icon on the desktop.
Other applications that need to access the FAT partition can do so during the freeze (incl write access) without problem.

Anybody, please help!

---

### Post by stickmangumby on 2008-09-22
To determine whether it's something to do with Nautilus, or to do with the partition, try accessing the partition using the command line.

Open the Terminal, and type the following at the prompt:

```

cd /media/disk
ls -l

```

This will change directories to your FAT32 partition, and then try to list files that are in it. If this works, you can do the following to copy files from it:

```

cp my_fat32_filename /home/my_username/Desktop
cp -r my_fat32_directory /home/my_username/Desktop

```

Obviously, you need to replace my_fat32_filename and my_username with the actual file that you want to copy, and your username.

---

### Post by merry_meerkat on 2008-09-22
Thanks!
I have tried the commands that you suggests, All worked fine. The partition seems to be mounted and working properly. As I had pointed out before, other applications manage to read from and write to it without problem.

Before trying this, I uninstalled the two most recently installed applications (dropbox and conduit) and restarted the computer. Now the whole problem I have reported seems to have vanished.

I'll try re-installing them one by one to find out if indeed there is a problem with one of them and then file a bug there.

Thanks again.

---

