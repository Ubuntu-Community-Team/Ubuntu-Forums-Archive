---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by DemonEyes on 2009-04-26
my upgrade from 8.04 (or maybe 8.10 i forget) failed and now whenever i try to install anything i get the error message 

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

when i run sudo dpkg --configure -a i get 

Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-restricted-modules-2.6.28-11-generic (2.6.28-11.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
[COLOR="Red"]dpkg: subprocess post-installation script returned error exit status 1[/COLOR]


and if i try running sudo apt-get update just giving me the original error again

any suggestions?

---

### Post by koenbeek on 2009-04-26
One of your disk partitions is (almost) full

gzip: stdout: No space left on device

free up some space and try again

use df in a terminal to see which one is full (or use a disk usage analyzer)

---

### Post by DemonEyes on 2009-04-26
Ic well most of my drives are "almost full" but even then they all have between 10-70gigs of free space left except for my ubuntu user folder which only has 4 gigs which i would have thought would be enough for whatever it is trying to unzip

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdd2             18141512  12864680   4355284  75% /
tmpfs                  1028640         0   1028640   0% /lib/init/rw
varrun                 1028640       216   1028424   1% /var/run
varlock                1028640         0   1028640   0% /var/lock
udev                   1028640       156   1028484   1% /dev
tmpfs                  1028640       236   1028404   1% /dev/shm
lrm                    1028640      2380   1026260   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdd5                46633     44318         0 100% /boot
/dev/sdc1            312560608 280252720  32307888  90% /media/Vista
/dev/sdb1            488375968 413771436  74604532  85% /media/300
/dev/sda1             39079932  13635760  25444172  35% /media/Storage
/dev/sde1             31256640  22366352   8890288  72% /media/PATRIOT
tmpfs                  1028640      2760   1025880   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0                593018    593018         0 100% /media/cdrom0

is there any way to tell ubuntu where to upzip so it doesn't think there isn't enough space?

---

### Post by drs305 on 2009-04-26
Your /boot partition (sdd5) is full. You need to create some space in this partition. You can remove older kernels or look for other unneeded files in this partition.

You can check this guide for ways to free up disk space:
 [HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by DemonEyes on 2009-04-26
thanx i'll try that when i've got some free time.  Your quick responses are greatly appreciated

---

### Post by DemonEyes on 2009-04-26
i looked at the guide you linked but the problem is to remove the old kernels i would need to use synaptic which just gives me the dpkg error when i open it.  is there a method to manually remove the extra kernals?

i also tried sudo apt-get remove --purge to remove the kernals i wasn't using (not sure if this is the best way to go about this but figured id try it) that returned

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.28-11-generic

googled that and its got something to do with the repositories that i've got installed but i can't change that with the whole dpkg error anyway

---

### Post by DemonEyes on 2009-04-26
update manager told me to run sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.27-9-generic
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
5 not fully installed or removed.
After this operation, 2621kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137635 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-9-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-9-generic/volatile/': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.27-9-generic
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-9-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2009-04-27
One of the first things to do to start correcting the errors is to free up some space in your /boot folder.

You can try to make it larger. To do this, you would need to boot from a LiveCD, gparted or systemrescue CD and run *gparted* (or System, Administration, Partition Editor). To expand /boot you probably would have to shrink another partition, and then expand /boot. It would require several steps as the chance of having free space readily available adjacent to the /boot partition is not high.

Depending on what you have in your /boot folder, you might find some older files that you can delete. If possible, I would initially try to preserve both the -9 and -11 kernel files, since these are either the ones you have or are trying to install. Check which kernel you are currently running with:
```

uname -r

```

Then open a file browser with admin powers:
```
gksudo nautilus /boot
```

If you can find any vmlinuz, initrd, or config files that are earlier than -9 (or whatever kernel you are running) I would try to 1) preferably move it/them to another partition or 2) delete it/them. If you don't have an earlier version, to clear the error message you may have to delete the files of the kernel you are not using. Of course, if it's the -11 kernel files you won't be able to upgrade to that kernel until you have solved the space issue, but at least you will get dpkg/synaptic working again for other packages that don't have to write to the /boot partition.

---

### Post by Linux_Newbee on 2009-05-07
Hi, 
I'm getting this same Sudo dpkg thing as the person first writing, But unlike him/her I dont know how to Run the thing. how do you run Sudo Dpkg configure-a?
Thanks

---

### Post by overdrank on 2009-05-07
> **Linux_Newbee said:**
> Hi, 
I'm getting this same Sudo dpkg thing as the person first writing, But unlike him/her I dont know how to Run the thing. how do you run Sudo Dpkg configure-a?
Thanks

In the terminal located under applications, accessories you enter the command ```
sudo dpkg --configure -a
```  and then your password. DO not worry if your password is not shown as typing.

---

### Post by stephenoca on 2009-05-08
when i run sudo dpkg --configure -a i get
dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 1:
 newline in field name `#padding'
i got that error message after java 6 failed to install. 
can anyone help?
   Thanks

---

### Post by drs305 on 2009-05-09
> **stephenoca said:**
> when i run sudo dpkg --configure -a i get
dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 1:
 newline in field name `#padding'
i got that error message after java 6 failed to install. 
can anyone help?
   Thanks

I've waited to post in hopes you resolved your issue. If you haven't you could try to move (I prefer this to the more permanent delete) the file causing the error to see if you can regain use of dpkg. If it doesn't work, you can move the file back and restore things the way they were.
```

sudo mv /var/lib/dpkg/updates/0003 /$HOME/Desktop/0003
sudo apt-get update 

```
If you don't get any errors, you could try to install java again. If you still get error messages, put the file back where it was originally:
```

sudo mv /$HOME/Desktop/0003  /var/lib/dpkg/updates/0003

```

---

### Post by stephenoca on 2009-05-09
thanks drs305 it worked perfectly

---

### Post by drs305 on 2009-05-09
Glad it worked for you stephenoca. 

You now have a file owned by root on your Desktop. To delete it, you can open nautilus with gksudo and remove it using SHIFT-DELETE. If you just delete it the normal way it will move to ...Trash and won't really be gone from your computer (although it would be gone from your Desktop).

You might want to check out root's trash bin while you have it open. Delete any files with SHIFT-DEL or delete the entire "files" folder.
```
gksu nautilus $HOME/Desktop
gksu nautilus /root/.local/share/Trash/files
```

---

### Post by Linux_Newbee on 2009-05-10
Hey thanks bro, I really appreciate that. I used the Terminal and it worked great!
Maybe you can answer these two Q's I have aswell, 
What is the Terminal?   
and 
Why does certain media like videos work on Explorer but not Firefox? Ei. Uefa.com
Thanks man I really appreciate your help. 
LN

---

### Post by drs305 on 2009-05-11
> **Linux_Newbee said:**
> Hey thanks bro, I really appreciate that. I used the Terminal and it worked great!
Maybe you can answer these two Q's I have aswell, 
What is the Terminal?   
and 
Why does certain media like videos work on Explorer but not Firefox? Ei. Uefa.com
Thanks man I really appreciate your help. 
LN

The terminal is the non-graphical interface with your computer. Many things are much easier to do (and explain) via the terminal, which is why you often see solutions presented with terminal commands.

Here are a couple of links:
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

[http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal]("http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal")

Firefox uses different processes to handle events than does Explorer. How it handles things like multimedia are generally determined by what *plug-ins* you have in Firefox. Some of these must be added to Firefox to enable more than just basic browsing.

---

