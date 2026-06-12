---
title: "Multimedia Keys - Asus N53SV"
date: 2011-05-27
forum: Hardware
---

### Post by geudrik on 2011-05-27
I am unable to use the multimedia keys at the top of the keyboard in (K)Ubuntu.  I haven't been able to use keyboard layouts to solve this issue, either.

Anyone have any suggestions for me?  I have tried xev but xev doesn't even detect them being pressed.  I have also tried keytouch and that doesn't seem to help me any.  

Help? :-\

---

### Post by geudrik on 2011-05-27
I have done some further trouble shooting, and on the Asus website for drivers, in windows there is an ATKACPI driver that enables their use.  There are 4 buttons, mute, vol down, vol up and play/pause.  I have referenced [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting) but this seems to be gnome related.  I'm still somewhat new to things, so I'm hesitant on going about some of these suggestions.

Can anyone shed some light for me?

-Pat

---

### Post by geudrik on 2011-05-28
Bump :-\

---

### Post by Zorael on 2011-05-30
There is a kernel module named **asus_atk0110**; could that be the one? It doesn't have any real description, but googling atk0110 gives results like "Asus ATK 0110 Virtual Device ACPI Driver Driver". There is also a module named **asus-laptop**.

To see if either are loaded, run '**lsmod | grep asus**' in a terminal.
```
$ lsmod | grep asus
```
To manually load a module, run '**sudo modprobe *<module name>***'. Several modules can be supplied at the same time.
```
$ sudo modprobe asus_atk0110
#### test xev

$ sudo modprobe asus-laptop
#### test xev again
```
If either of these seem to fix the issue, you can add them as entries to your **/etc/modules** file to have them autoloaded upon boot.

Example (your entries may differ);
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
[b]asus_atk0110
asus-laptop[/b]
```

---

### Post by geudrik on 2011-05-31
Hey Zorael, Thanks for the tips.  When I lsmodded either of those, neither were loaded.  

```
sudo modprobe asus_atk0110
```
gives no results, but also does not get my buttons to work.

```
sudo modprobe asus-laptop
FATAL: Error inserting asus_laptop (/lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/asus-laptop.ko): No such device
```

Not sure what to do next :-s  Thoughts?


Followup: that module exists in the path given by the error.  Also, [http://comments.gmane.org/gmane.linux.acpi.acpi4asus.user/5987](http://comments.gmane.org/gmane.linux.acpi.acpi4asus.user/5987) but I am unsure how reputable this is, especially compiling the module from source :s

[http://git.iksaif.net/?p=acpi4asus-dkms.git;a=summary](http://git.iksaif.net/?p=acpi4asus-dkms.git;a=summary)
^ Git Link for the module, which is clearly in active development :)

---

### Post by Zorael on 2011-05-31
It looks like the kernel simply doesn't support the machine yet. You could try upgrading to the 2.6.39 kernel that's not in natty. Compiled and ready packages are available on the kernel-ppa PPA (**ppa:kernel-ppa/ppa**), and they nicely install next to your normal kernels.

```
$ sudo add-apt-repository ppa:kernel-ppa/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

Other than that, this warrants a real bug report. Head over to [Launchpad](http://launchpad.net/ubuntu) and file a bug [toward the **linux** package](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug). I couldn't find any existing bugs that fits what you're experiencing, but perhaps bug triagers will. Otherwise, it's a new bug!

Remember, unreported bugs can only be fixed by accident.

---

### Post by geudrik on 2011-05-31
I am like a blind man with a chainsaw...  Hmm..  Ideas? I have no idea what I'm doing. :-s

After running
```
git clone git://git.iksaif.net/acpi4asus-dkms.git
```


```
geudrik@geudrikmobile:~/mod/acpi4asus-dkms$ sudo make && make install
make -C drivers/platform/x86 default
make[1]: Entering directory `/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86 asus-wmi.ko eeepc-wmi.ko asus-nb-wmi.ko eeepc-laptop.ko asus-laptop.ko
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.o
/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.c: In function ‘asus_wmi_backlight_init’:
/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.c:1148:7: error: ‘struct backlight_properties’ has no member named ‘type’
/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.c:1148:15: error: ‘BACKLIGHT_PLATFORM’ undeclared (first use in this function)
/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.c:1148:15: note: each undeclared identifier is reported only once for each function it appears in
make[3]: *** [/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86/asus-wmi.o] Error 1
make[2]: *** [asus-wmi.ko] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/geudrik/mod/acpi4asus-dkms/drivers/platform/x86'
make: *** [default] Error 2
geudrik@geudrikmobile:~/mod/acpi4asus-dkms$ 

```

---

### Post by geudrik on 2011-05-31
This is weird, I clearly have internet connectivity...

```
geudrik@geudrikmobile:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  bind9-host dnsutils libbind9-60 libdns69 libisc62 libisccc60 libisccfg62 liblwres60 libpam-modules
  libpam-modules-bin libpam-runtime libpam0g linux-libc-dev phonon-backend-gstreamer xserver-common
  xserver-xorg-core
16 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 422 kB/4,269 kB of archives.
After this operation, 115 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libpam0g amd64 1.1.2-2ubuntu8.2
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main libpam0g amd64 1.1.2-2ubuntu8.2
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main libpam-modules-bin amd64 1.1.2-2ubuntu8.2
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main libpam-modules amd64 1.1.2-2ubuntu8.2
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main libpam-runtime all 1.1.2-2ubuntu8.2
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.2-2ubuntu8.2_amd64.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules-bin_1.1.2-2ubuntu8.2_amd64.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.2-2ubuntu8.2_amd64.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.2-2ubuntu8.2_all.deb  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by geudrik on 2011-05-31
Zorael - Thanks for the help.  I've created a bug report, and after a little researching on google, I have seen similar reports, but with older kernel releases.  Potentially unrelated to my model line, I'm not entirely sure. 

Thanks!

---

### Post by Yellow Pasque on 2011-05-31
I can't get the git source to build either. Will do more troubleshooting when I get home.

---

### Post by geudrik on 2011-05-31
Keep the thread updated if you would, I would love to find out what the issue is. I've been googling around and have yet to come up with anything thus far.

More Info: [http://lapsus.berlios.de/](http://lapsus.berlios.de/)
^ Requires asus-laptop module installed, and will NOT work using asus_acpi

Edit 2: [http://acpi4asus.sourceforge.net/](http://acpi4asus.sourceforge.net/)
I am seeing conflicting information here - asus-wmi-nb is not available as a kernel module for me. I have asus_acpi installed, but it clearly doesn't work.

---

