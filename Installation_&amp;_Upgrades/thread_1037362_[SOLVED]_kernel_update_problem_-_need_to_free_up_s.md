---
title: "[SOLVED] kernel update problem - need to free up some space on /boot"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by Egi_Power on 2009-01-11
A few days ago the updates included a new kernel: 2.6.24-23
I got an error message at the end of the update. See attached images.
I might be wrong, but i think the problem is my /boot partition is out of free space.
I would like to get some help on how to fix it.
I'm using 8.04 
Any more details required I will post just ask. (I'm not experienced, so go easy on me) :)
Any help would be appreciated.

Thank you in advance.

Egi_Power

P.s: The same update also gave error on my laptop. Very similar dependency problems.

---

### Post by whoop on 2009-01-11
I would wait it out for a bit. It could be that the repositories are not up to date (yet).
Problem could/should resolve itself.

The no space left on device could be a different problem... Are you getting this on your laptop too?
Most obviously your running out of space ;-) Maybe remove some old kernels. Leave at least two (latest, and working kernel before that).
Search for linux-image on synaptic and remove old kernels you don't use anymore (be sure to leave linux-image-generic)

---

### Post by avtolle on 2009-01-11
Get a terminal (Applications>Accessories>Terminal) and at the prompt, input ```
df -h
``` and see if /boot is full (or nearly full). You may cut and paste the results of the command in your next post (to copy in the terminal, use Shift+Ctrl+c).

---

### Post by Egi_Power on 2009-01-11
> **avtolle said:**
> Get a terminal (Applications>Accessories>Terminal) and at the prompt, input ```
df -h
``` and see if /boot is full (or nearly full). You may cut and paste the results of the command in your next post (to copy in the terminal, use Shift+Ctrl+c).

```
***@***-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.8G  3.4G  6.0G  36% /
varrun               1014M  112K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M   84K 1013M   1% /proc/bus/usb
udev                 1014M   84K 1013M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sda4              92M   80M  6.7M  93% /boot
/dev/sdb3             137G  124G  5.9G  96% /home
gvfs-fuse-daemon      9.8G  3.4G  6.0G  36% /home/***/.gvfs
/dev/sdc1             233G  178G   56G  77% /media/My Book
```

I'm also getting error when I try to remove old kernels as recommended by whoop. See attached image.



```
***@***-desktop:~$ uname -a
Linux ***-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
```

I'm using kernel 2.6.24-22. Is it safe to remove the following ones from synaptic?
- linux-image-2.6.24-21-386
- linux-image-2.6.24-21-generic
- linux-image-2.6.24-21-virtual

---

### Post by Egi_Power on 2009-01-12
I successfully freed up some space on the /boot partition and installed the new kernel, thanks to the advice I got from avtolle & whoop.

My problem now is the following:

After the kernel upgrade my nVidia drivers are gone in the new kernel.
At boot up between the splash screen and the login screen I got an option to set up the screen resolution, but can't set it higher than 800x600.

In 2.6.24-22 everything works as it should.

Any tips on how to fix it, how to get the nVidia driver?

Any help would be appreciated.

Egi_Power

---

### Post by Partyboi2 on 2009-01-12
Have you tried selecting the driver from System>Admin>Hardware Drivers, this will download and install the nvidia driver.

---

### Post by Egi_Power on 2009-01-12
There is nothing in Hardware Drivers.

Egi_Power

***EDIT:***

I managed to install the driver from nvidia.com. Now i can see the graphics driver in the Hardware Drivers.

But I still need to configure something to set the correct resolution.

Now in 2.6.24-22 the resolution is the same 800x600 as in 2.6.24-23.

Any further help would be appreciated.

---

### Post by Egi_Power on 2009-01-12
I will mark this thread as SOLVED, I managed to free some space and install the new kernel.

---

### Post by Partyboi2 on 2009-01-12
> **Egi_Power said:**
> There is nothing in Hardware Drivers.

Egi_Power

***EDIT:***

I managed to install the driver from nvidia.com. Now i can see the graphics driver in the Hardware Drivers.

But I still need to configure something to set the correct resolution.

Now in 2.6.24-22 the resolution is the same 800x600 as in 2.6.24-23.

Any further help would be appreciated.
Open a terminal and type
```
gksu nvidia-settings
``` then change the resolution to the correct one. If you don't have nvidia-settings installed you can install it by typing:
```
sudo apt-get install nvidia-settings
```

---

### Post by Egi_Power on 2009-01-12
> **Partyboi2 said:**
> Open a terminal and type
```
gksu nvidia-settings
``` then change the resolution to the correct one. 

I get an error message. See attached image.

When I run 

```
sudo nvidia-xconfig
``` 

i get:
```
***@***-desktop:~$ sudo nvidia-xconfig 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

***@***-desktop:~$ sudo nvidia-xconfig 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

The second time it looks it worked.

---

### Post by Partyboi2 on 2009-01-12
What happens when you run
```
sudo nvidia-xconfig
```
Also what graphics card are you using?

---

