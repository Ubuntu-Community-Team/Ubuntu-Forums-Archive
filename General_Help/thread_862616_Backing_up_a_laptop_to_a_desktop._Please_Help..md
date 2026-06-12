---
title: "Backing up a laptop to a desktop. Please Help."
date: 2008-07-17
forum: General Help
---

### Post by shamusl on 2008-07-17
I have a sony vaio, and a custom built PC, I have the sony running a 7.10 live CD, and 8.04 on my desktop. Does anyone know how to mount the laptop's windows partition on my desktop so I can copy the files over? Is this even possible or is there a different way someone can help me?

---

### Post by scragar on 2008-07-17
```
cat /proc/partitions
```
look for something like: /dev/hda**#** or /dev/sda**#**

```
sudo mkdir /media/hd
sudo mount /dev/**s/h**da**#** /media/hd
```
your files will then be in /media/hd change the name as required.

---

### Post by shamusl on 2008-07-17
I'm trying to do this over a network. I think you read my original post wrong at first.

---

### Post by lswb on 2008-07-17
To simply copy files, here's what I would do. Install sshd on the laptop and sshfs on the desktop. Read the man page for sshfs, it lets you mount a remote system to a local directory name, making the files on the remote accesible (while connected) via the mountpoint, just like a locally mounted disk or partition. 

Actually, I believe that sshfs is not necessarily necessary, IIRC on the ubuntu gnome main menu/Places/Connect To Server, you can select ssh (or ftp) and get a nautilus view of the remote filesystem.

If you want an actual partition image rather than just a file copy, I believe it would be possible but I can't say exactly how without researching some.

---

