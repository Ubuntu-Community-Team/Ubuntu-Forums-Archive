---
title: "Fujitsu Amilo M7440G with Ubuntu 12.04"
date: 2012-05-02
forum: Hardware
---

### Post by aswhad on 2012-05-02
HOWTO
Just some data to get a laptop Fujitsu Amilo M7440G with Ubuntu 12.04 to work.
First problem is **the fan** that keeps running on boot;
In /etc/rc.local you put thes lines;
```
echo 1 | sudo tee /sys/class/thermal/cooling_device1/cur_state ;
echo 0 | sudo tee /sys/class/thermal/cooling_device1/cur_state ;
```

Second to get **wifi** working;
go to [http://fsam7440.sourceforge.net/down.html]("http://fsam7440.sourceforge.net/down.html") and download [Fsam7440 v0.4 Source Code]("http://sourceforge.net/projects/fsam7440/files/fsam7440/fsam7440-0.4/fsam7440-0.4.tar.bz2/download")
extract
```
tar -xjvf fsam7440-0.4.tar.bz2 
```
Next for it to compile without errors you need to edit 3 lines in the fsam7440.c file (in your ~/fsam7440-0.4 directory)...
*Or simply use the attachment, it is already edited and just needs to be compiled/installed*.
So back in the terminal enter:

```
gedit ~/fsam7440-0.4/fsam7440.c 
```

When gedit opens, find the line:
```
#include <linux/autoconf.h>
```
and change it to:
```
# include <generated/autoconf.h>
```

Now you need to change the 2 instances of &proc_root to NULL

so find the Line:
```
remove_proc_en try(DRV_NAME, &proc_root);
```
and change it to:
```
remove_proc_en try(DRV_NAME, NULL);
```

and the line:
```
dir_base = create_proc_en try(DRV_NAME, S_IFDIR, &proc_root);
```
and change it to:
```
dir_base = create_proc_en try(DRV_NAME, S_IFDIR, NULL);
```

Save the fsam7440.c file.

To compile/install the driver... back in the terminal, enter:

```
cd ~/fsam7440-0.4
make
sudo make install 
```

Now to test it works... still in the terminal, enter:
```
sudo modprobe fsam7440 
```

Add the line:
```
fsam7440
```
to your /etc/modules file.

thank you brainwash [LINK]("http://ubuntuforums.org/showthread.php?t=1968639&page=2")

and also [ Mark Greaves LINK]("http://linuxforums.org.uk/ubuntu/how-to-install-amilo-fsam7440-rf-kill-switchs-driver-in-ubuntu/?PHPSESSID=b4bb8af5881a042b20a43fb747e3cddf")

---

