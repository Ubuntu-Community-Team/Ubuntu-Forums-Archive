---
title: "Files suddenly disappearing"
date: 2008-09-01
forum: General Help
---

### Post by pundip on 2008-09-01
A couple of days ago all the files on my desktop vanished. The folders remained but the some of the files in there vanished and some remained. Ctrl+H does not show anything neither does reboot. I have seen this happen before it to secondary  drive in a windows environment but it happened across the drive and was a hardware failure of the drive. Here only my desktop files seem to be effected. Files in  the home dir and other places seem unaffected so i dont think it is a hardware issue.  Other people have reported that files in their entire home directory vanish and reappear but for me they haven’t come back and its only my desktop files. One of the files was very important I would appreciate any help in figuring this one out. They system suffered some kind of crash I think I had to force a virtualised instance of widows under Virtualbox to close when I saw my desktop missing the files.  Ps I am using Hardy

---

### Post by sayakb on 2008-09-01
The files on the desktop are nothing but those inside ~/Desktop (/home/username/Desktop). If your files inside the home folder remain unaffected, the files on the Desktop should too. Volumes (drives) disappear when unmounted and reappear on mounting. Check whether you have the files in the ~/Desktop folder.

---

### Post by pundip on 2008-09-01
LinuxIsInnovation thanks for your reply. I did have a look in /home/maneesh/Desktop as you suggested and the files are not there. Its as if files have been randomly eaten very similar to a that of a coroupt FAT or a dying drive but this issue is not drive wide only the Desktop folder is effected. I am not really sure what to do. Is there a linux util that can be used to surface scan a drive just to rule out hardware issue with the drive?

---

### Post by joenix on 2008-09-01
Hello Pundip,

Drive corruption seems very unlikely if the problem is restricted to one folder. If you want to check it anyway, fsck is the program you need. The problem is your drive can not be in use while you are using it.
You can type the following in the terminal to force fsck on your next reboot, before it is mounted:
```
sudo touch /forcefsck
```
Or you can boot from a live cd and run fsck from there.

Did you perhaps change the language of your GUI interface recently? This can change the location of your desktop directory and make you end up with an empty desktop.
If not, can you try to search your home directory for a file you're certain was there before?
Also, could you type the following in a terminal and post the output:
```
cat ~/.config/user-dirs.dirs
```

---

### Post by pundip on 2008-09-02
Joenix here is output of cat ~/.config/user-dirs.dirs

```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
maneesh@deepthought:~$ 

```

The odd thing is that not all files are gone. All the files not in folders are gone and only some of the files in the folders are gone.

---

### Post by joenix on 2008-09-02
The users-dir.dirs file looks ok, your desktop files should be in Desktop under your home dir.

If fsck turns up empty, you can have a look at your system log files under /var/log and see if you can spot some dramatic errors. Specifically in /var/log/messages, which contains kernel messages.

In any case, backup any important files before you might loose them.

---

