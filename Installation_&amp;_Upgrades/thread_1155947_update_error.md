---
title: "update error"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Rambleon on 2009-05-11
Hi, I have tried to update my Ubuntu installation but get the following error message. Can you please provide a simple step by step instruction of what to do fro a complete novice to Ubuntu. thanks E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by pro003 on 2009-05-11
> **Rambleon said:**
> Hi, I have tried to update my Ubuntu installation but get the following error message. Can you please provide a simple step by step instruction of what to do fro a complete novice to Ubuntu. thanks E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


it's just like the error message said, run **dpkg --configure -a**
 in terminal, it should fix the problem... and type **sudo** before you entering such commands...

---

### Post by Partyboi2 on 2009-05-11
Hi, open a terminal (Applications>Accessories>Terminal) and type or paste
```
sudo dpkg --configure -a
```

---

### Post by Rambleon on 2009-05-11
thanks for the advice. I have run the command as directed but stop part way through with the message, 
gzip: stdout: no space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-generic
dpkg: subprocess post-installation script returned error exit status1
 
what next please ??

---

### Post by Partyboi2 on 2009-05-11
Can you open a terminal and post the output to
```
df -h
```

---

### Post by Rambleon on 2009-05-12
Hi Partyboi2
have entered the code to terminal as requested and the output is

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              31G  3.0G   27G  10% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   56K  379M   1% /dev
devshm                379M   12K  379M   1% /dev/shm
/dev/sda3              46M   40M  3.8M  92% /boot
/dev/sda1              22G   11G   11G  50% /media/sda1
/dev/sda2              22G  4.2G   18G  20% /media/sda2

---

### Post by Partyboi2 on 2009-05-12
You need to free up some room, open up Synaptic Package Manager and search for "linux-image" and remove all the ones you do not need except keep your current one and another one as a backup. Once you have made some room you can run
```
sudo dpkg --configure -a
```If you still do not have enough space you will need to increase the size of sda3

---

### Post by Rambleon on 2009-05-12
Hi Partyboi2,
 
would love to try your solution but synaptic package manager will only open as faded out with the original error message. ?

---

### Post by pro003 on 2009-05-12
you can free up some space by typing in terminal:

```

sudo aptitude autoremove
sudo aptitude clean
```

but can't tell you is it going to be enough...

---

### Post by Rambleon on 2009-05-13
hi Pro 003 
 
I have tried your suggestion. 
Running aptitude autoremove gives a list of actions and options but says " This aptitude does not have Super Cow Powers"
running aptitude clean has no effect on sda3 size. 
Any more suggestions gratefully received.

---

### Post by pro003 on 2009-05-13
```
sudo aptitude autoremove
``` 

> removes obsolete packages / installations

```
sudo apt-get clean
``` 

 > clears the cache 

... and both commands should give you some free space.

And if you have nerves to read this take a look how can you resize your ext3 partition without losing your data.

[http://ubuntuforums.org/showthread.php?t=105255](http://ubuntuforums.org/showthread.php?t=105255)

---

### Post by Rambleon on 2009-05-13
Hi pro003
 
as before autoremove dosnt seem to run. apt-get has no effect on the sda3 size so I guess its down to resizing the partition. Wish me luck

---

### Post by Kevbert on 2009-05-13
To clean out some image files go to Applications-Accessories-Terminal and type in the following:
```
uname -r
```
- this will give you the currently running linux kernel.
Next enter
```
cd /boot
ls -l
```
This will list all available kernels (which probably show up in your grub boot menu).
If you have any .bak files remove them with
```
sudo rm *.bak
```
**Be careful with this as if you enter the command wrong you may kill your operating system.**
Now you can remove some old kernels, but not the one displayed by uname -r with
```
sudo rm abi-2.6.24-22-generic
sudo rm config-2.6.24-22-generic
sudo rm initrd.img-2.6.24-22-generic
sudo rm System.map-2.6.24-22-generic
sudo rm vmlinuz-2.6.24-22-generic
```
If you've already removed some bak files you shouldn't need to remove any other old kernels by this method. The actual kernel number is just an old example.  If you need to remove an old kernel this way you'll need to edit your /boot/grub/menu.lst file. With just bak files removed you should be able to remove some old kernels with Synaptic (see previous posts) and this will automatically sort out your menu.lst file for you. It's best to keep the latest and the previous kernel (in case of problems).

---

### Post by Rambleon on 2009-05-14
thanks Kevbert, and all the rest of you. removed .bak fils as directed now only 59% on sda3 and working fine with out the need ot resize.

---

### Post by Kevbert on 2009-05-14
> **Rambleon said:**
> thanks Kevbert, and all the rest of you. removed .bak fils as directed now only 59% on sda3 and working fine with out the need ot resize.

It may still be worth removing any old kernels that you're unlikely to use via Synaptic. Just search for linux-image and completely remove the generic one's that are obsolete (but not the one you're using). ;)

---

