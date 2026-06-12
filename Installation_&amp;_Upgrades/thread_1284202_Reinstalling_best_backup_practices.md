---
title: "Reinstalling: best backup practices?"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by ternarybit on 2009-10-06
I almost cringe asking a question for fear of duping, so I apologize if this has been answered n-million times.

I am running Jaunty amd64 on ext4, which started as a linux playground but has evolved into a full-time web development environment. ext4 has given me plenty of headaches and so I want to back everything up and start over on ext3.

I store most files on a separate ntfs partition so windoze can access it, but I'm very interested in preserving my many downloaded apps & custom settings. I have read that backing up /home should work, but is this where *everything* resides? I've also read that programs hide in /opt or /usr/sbin or something else. Would I be better off just starting from scratch? Thank you!

P.S. Since I'm going to all this trouble, would it be best to start a new md raid1 disk? how should I partition it? Thanks again!

---

### Post by friv_livs on 2009-10-06
As long as you are going to use the same 64 bit installer, you may be able to backup your full system to a tarball on an external HDD.
If you do go this route, you will have to copy the UUID from the new install to /etc/fstab and /boot/grub/menu.lst before restarting computer.

Only thing you may have to worry about is journaling on ext4 vs. no journaling on Ext3, I have no idea if journaling works it's way into the filesystem.

/home, /usr/sbin, and /opt contain different parts of each app, depending on what app it is.

/home usually contains user settings and links for all the programs
/opt generally contains open office operating files
/usr/sbin generally contains launchers and config files

I cannot answer the raid1 question. But if you do end up repartitioning the drive, just back up your /home directory.

---

### Post by ternarybit on 2009-10-06
> **friv_livs said:**
> As long as you are going to use the same 64 bit installer, you may be able to backup your full system to a tarball on an external HDD.
If you do go this route, you will have to copy the UUID from the new install to /etc/fstab and /boot/grub/menu.lst before restarting computer.

Only thing you may have to worry about is journaling on ext4 vs. no journaling on Ext3, I have no idea if journaling works it's way into the filesystem.

/home, /usr/sbin, and /opt contain different parts of each app, depending on what app it is.

/home usually contains user settings and links for all the programs
/opt generally contains open office operating files
/usr/sbin generally contains launchers and config files

I cannot answer the raid1 question. But if you do end up repartitioning the drive, just back up your /home directory.

Thank you for your reply. I have read that I could tarball the whole / and reinstall. What is the proper command to do this while preserving permissions, etc?

Also thank you for the bit about UUID. I will be sure to copy those.

---

### Post by drs305 on 2009-10-06
You can create a list of your installed apps via Synaptic: File, Save Markings. Make sure you tick the "Save full state, not only changes". Save the file somewhere you don't plan on formatting. 

On the new install, you can return to Synaptic and use the File, Read Markings to restore all the apps that were registered with Synaptic on the first install (provided you have the same repositories enabled).

---

### Post by ternarybit on 2009-10-06
> **drs305 said:**
> You can create a list of your installed apps via Synaptic: File, Save Markings. Make sure you tick the "Save full state, not only changes". Save the file somewhere you don't plan on formatting. 

On the new install, you can return to Synaptic and use the File, Read Markings to restore all the apps that were registered with Synaptic on the first install (provided you have the same repositories enabled).

Will this work for all packages installed by apt-get or just ones installed with the Synaptic Package Manager?

---

### Post by drs305 on 2009-10-06
> **ternarybit said:**
> Will this work for all packages installed by apt-get or just ones installed with the Synaptic Package Manager?

When the feature first came out I played extensively with it to determine the answer. Each time I compared the APT and Synaptic lists they were off by less than a dozen packages, out of about 1500. I didn't make the effort to determine why there was a difference. But the general answer is that they both appear to use the APT information.

---

### Post by ternarybit on 2009-10-06
> **drs305 said:**
> When the feature first came out I played extensively with it to determine the answer. Each time I compared the APT and Synaptic lists they were off by less than a dozen packages, out of about 1500. I didn't make the effort to determine why there was a difference. But the general answer is that they both appear to use the APT information.

Excellent. It sounds like my best bet is backing up /home, exporting the Synaptic list and then reinstalling fresh.

Since I do not have another ext partition, I will have to tarball the /home dir. Can someone help me with the proper command to do this? Thank you very much in advance.

---

### Post by friv_livs on 2009-10-06
To tar ball /home, run the following command:

```
cd /media/"your-back-up directory"
tar cvpzf "name".tar.gz --exclude=/home/"username"/"what files you don't want backed up in home" /home/"username"
```
replacing what's in parentheses with what's indicated. 
Repeat the --exclude=/home/"username"/"directory" for each directory in home you don't want backed up.

---

