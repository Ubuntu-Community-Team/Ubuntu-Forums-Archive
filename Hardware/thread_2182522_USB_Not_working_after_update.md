---
title: "USB Not working after update"
date: 2013-10-21
forum: Hardware
---

### Post by Stephanie_Smith on 2013-10-21
Updated to the latest version of ubuntu, upon restart USB ports no longer work. This makes it impossible for me to use the internet at home because I need to plug my dongle into one of the ports but now i'm stuck using the wi fi. Further more i cant transfer files or open my usbs for school. If this isnt sorted by Wednesday my goose is cooked.


Also i have just notice my google 'history' 'file' 'tools' have all disappeared

---

### Post by sudodus on 2013-10-21
Welcome to the Ubuntu Forums :-)

Are you sure the USB are not working? Maybe it is 'only' the automatic mounting, that does not work for you. And in that case it is possible to fix it with some terminal window commands.

Please post the results of some commands that make us understand more about your system. Put them within code tags: Go into advanced (editing) mode, mark the text and click on the # icon at the top of the editing window or do it manually:

Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

Insert the USB drive(s) into your computer and run these commands (and post the output)

```
sudo parted -l
```
```
df
```
```
lsusb
```
```
 ls -l /media
```

---

### Post by Stephanie_Smith on 2013-10-21
code yeah i'm not really sure what your saying about putting it code)output(/code) but here goes nothing
(code)steph@stephlap:~$ parted-l
parted-l: command not found(/code)
(code)steph@stephlap:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      477534168 11797780 441455968   3% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1522860        4   1522856   1% /dev
tmpfs             306316     1148    305168   1% /run
none                5120        0      5120   0% /run/lock
none             1531568     1064   1530504   1% /run/shm
none              102400       48    102352   1% /run/user(/code)
(code)steph@stephlap:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub(/code)
(code)steph@stephlap:~$ ls-l/media
bash: ls-l/media: No such file or directory(/code)

Hope this is what you wanted but i'm pretty sure it's not registering them at all since i cant find them at all when they're plugged in on the computer

---

### Post by ajgreeny on 2013-10-21
> **Stephanie_Smith said:**
> code yeah i'm not really sure what your saying about putting it code)output(/code) but here goes nothing
```
steph@stephlap:~$ parted-l
parted-l: command not found
```
```
steph@stephlap:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      477534168 11797780 441455968   3% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1522860        4   1522856   1% /dev
tmpfs             306316     1148    305168   1% /run
none                5120        0      5120   0% /run/lock
none             1531568     1064   1530504   1% /run/shm
none              102400       48    102352   1% /run/user
```
```
steph@stephlap:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
steph@stephlap:~$ ls-l/media
bash: ls-l/media: No such file or directory
```

Hope this is what you wanted but i'm pretty sure it's not registering them at all since i cant find them at all when they're plugged in on the computer
You need to use square brackets [] as in the example from sudodus, not round brackets ().  I have added them to your output to see if it helps, however, I can not see any helpful output from the first few commands that did give some output.

The **sudo parted -l** command is missing a space before the **-l** and the **ls -l /media** command is missing a space needed before **/media**.

---

### Post by sudodus on 2013-10-22
Hi again Stephanie,

Please repeat the command

```
sudo parted -l
```

with a space before the minus according to *ajgreeny*. This command shows if the pendrive is recognized. It should be listed with a name and a list of partition(s).

The last command needs to be written like this (copy and paste is possible and better than rewriting and missing spaces).

```
ls -l /media
```

'ell ess space minus ell space slash media'

The list command is used with the long option '-l' with the parameter '/media' to list the files and directories in the directory **[FONT=courier new]/media[/FONT]**. This long list contains important information about the pemissions, that might need to be changed for automount to work.

---

