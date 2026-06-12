---
title: "[SOLVED] Problems i've been having recently."
date: 2008-08-28
forum: General Help
---

### Post by dragos240 on 2008-08-28
Well, it's gotten to the point where a lot of things have been blocked off for some strange reason. I can't let it keep going like this. Here are some things i'd like cleared up:

1.. When i go to log off now, i will click the red button in the corner, both panels will disappear, top and bottom, and the only way i can log off is CTRL + ALT +BACKSPACE.

2. I cant copy anything to my desktop anymore, it will say that i dont have anymore space. Which i don't believe is true considering after it displayed its message i moved all the items on my desktop to another folder. I also deleted some things. Nothing happened.

3. Sometimes my internet (Linksys) will be working and then it will be blocked and say Unknown.


I have no idea why any of this has been happening. Help!

---

### Post by Elfy on 2008-08-28
Well running out of space can cause some odd things so let's try and clear that up first - run this from aterminal

```
df -h
```

---

### Post by dragos240 on 2008-08-28
> **forestpixie said:**
> Well running out of space can cause some odd things so let's try and clear that up first - run this from aterminal

```
df -h
```

Well here are the results i got:

```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      6.5G  6.2G     0 100% /
varrun                506M  120K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   52K  505M   1% /dev
devshm                506M   36K  505M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M  124K  900K  13% /tmp
gvfs-fuse-daemon      6.5G  6.2G     0 100% /home/name/.gvfs
/dev/sda1             6.1G  4.9G  1.2G  81% /media/disk
/host/ubuntu/disks/new.disk
                       15G  3.7G   11G  27% /media/extra
```

---

### Post by Elfy on 2008-08-28
It is full - /> host/ubuntu/disks/root.disk
                      6.5G  6.2G     0 100% /

You can probable gain some room by ```
sudo apt-get clean
``` which will remove downloaded packages, or the other option is to resize the partition.

Of course before you do that ensure that trash is empty - do Ctrl+H to view hidden files as well, maybe check roots trash as well.

---

### Post by dragos240 on 2008-08-28
> **forestpixie said:**
> It is full - /

You can probable gain some room by ```
sudo apt-get clean
``` which will remove downloaded packages, or the other option is to resize the partition.

Of course before you do that ensure that trash is empty - do Ctrl+H to view hidden files as well, maybe check roots trash as well.
Thankfully everything works now, except for the panels when i try to log off.

---

### Post by davenxt on 2008-08-28
[ Mesothelioma Lawyer ](http://www.mesotheliomalawyerattorney.com)

---

### Post by Elfy on 2008-08-28
ASsuming that they don't come back on next login, try these in a terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Run each seperately it should restore your panels

---

### Post by dragos240 on 2008-08-29
> **forestpixie said:**
> ASsuming that they don't come back on next login, try these in a terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Run each seperately it should restore your panels

It's fixed. :) Solved.

---

