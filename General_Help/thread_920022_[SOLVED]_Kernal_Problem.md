---
title: "[SOLVED] Kernal Problem?"
date: 2008-09-14
forum: General Help
---

### Post by kemadruma on 2008-09-14
When i boot with "ubuntu 8.04-2.5.19-kernal - generic"  --> My sound and Wifi drivers are not loaded.


But when i press "ESC" and boot with "ubuntu 8.04-2.5.16-kernal - generic"  --> My sound and Wifi works fine.


Wat could b the prob and wats the solution? because my default boot selection is the kernel 2.6.19 hence normailly it doesnt load drivers.

---

### Post by iaculallad on 2008-09-14
Best solution for you is to make "ubuntu 8.04-2.5.16-kernal - generic" your default boot kernel as long as it does not pose any hardware problem when using this kernel. Edit your /boot/grub/menu.lst file and change the **default** key value to point to "ubuntu 8.04-2.5.16-kernal - generic" kernel.

EDIT:

**TO EDIT YOUR GRUB MENU.LST FILE**

Open /boot/grub/menu.lst for editing:

```
gksudo gedit /boot/grub/menu.lst
```

Find this line and change the default value to point to the value of your desired kernel.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]**default         0**[/COLOR]
```

Sample values using my current menu.lst file will be:

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic		[COLOR="Red"]<----- 0[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)		[COLOR="Red"]<----- 1[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic		[COLOR="Red"]<----- 2[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)		[COLOR="Red"]<----- 3[/COLOR]
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=16d722ac-565b-4d2d-9c6e-317b1ac253ff ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+		[COLOR="Red"]<----- 4[/COLOR]
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I want to boot on "Ubuntu 7.10, kernel 2.6.22-14-generic" as default, I would change the value of default to 2 instead of 0.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         **[COLOR="Red"]2[/COLOR]**
```

After you had changed it, Save and close. And while on your terminal, reboot.

```
sudo shutdown -r now
```

---

### Post by kemadruma on 2008-09-15
Well thanks, I implemented the above solution, But i would like to know the reason of this as earlier my drivers was working on 'kernel 2.6.19' and suddenly they stopped, thatswhy i tried the other kernel.

---

### Post by FuturePilot on 2008-09-15
You might want to check that "ubuntu-linux-modules-generic" and "ubuntu-restricted-modules-generic" are installed.

---

### Post by iaculallad on 2008-09-15
> **kemadruma said:**
> Well thanks, I implemented the above solution, But i would like to know the reason of this as earlier my drivers was working on 'kernel 2.6.19' and suddenly they stopped, thatswhy i tried the other kernel.

I don't know quite well the reason why you're drivers (as I don't know you're hardware specs) are not working with 2.6.19, a wild guess would be incompatibility or simply a hardware issue with the latest kernel build.

---

### Post by kemadruma on 2008-09-15
when i run
```

sudo apt-get install linux-generic linux-restricted-modules-generic

```

it gives me error
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

when i run 
```

dpkg --configure -a

```

it says
```

dpkg: requested operation requires superuser privilege

```

when i login afer logout as "root" it says
```

SuperAdmin can not login from here.

```


Wat to do??

---

### Post by iaculallad on 2008-09-15
> **kemadruma said:**
> when i run
```

sudo apt-get install linux-generic linux-restricted-modules-generic

```

it gives me error
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

when i run 
```

dpkg --configure -a

```

it says
```

dpkg: requested operation requires superuser privilege

```

when i login afer logout as "root" it says
```

SuperAdmin can not login from here.

```


Wat to do??

You should insert 'sudo' before the command "dpkg --configure -a". so:

```
sudo dpkg --configure -a
```

As for the root account, it is disabled by default in Ubuntu so you can't login using root.

---

### Post by swudee on 2008-09-15
Hi

Did you forget to sudo it?

sudo dpkg --configure -a

---

### Post by kemadruma on 2008-09-15
No,
```
sudo dpkg --configure -a
```

says
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0049' near line 1:
 newline in field name `#padding'
```

---

### Post by kemadruma on 2008-09-24
i m waiting for reply........................................................

---

### Post by kemadruma on 2008-09-26
Ok i got the solution myslef,
i changed to super user \su and deleted the file from updates folder
then sudo dpkg --configure -a

and problem solved..

---

### Post by kemadruma on 2008-09-26
Ok i got the solution myslef,
i changed to super user \su and deleted the file from updates folder
then sudo dpkg --configure -a

and problem solved..

---

