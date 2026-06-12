---
title: "Upgrade 2.6.28-15 Won't Install"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by lotusalive on 2009-08-18
Hi to All, It's 'UM' again !  (lol)

I'm lost with this, so maybe someone can direct me, since I don't even know what real question to ask...

sol@sol-desktop:~$ sudo apt-get upgrade
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-2.6.28-15-generic (2.6.28-15.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-generic:
 linux-restricted-modules-2.6.28-15-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-15-generic; however:
  Package linux-restricted-modules-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.15.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-15-generic (2.6.28-15.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-15-generic; however:
  Package linux-headers-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.28-15-generic
 linux-restricted-modules-2.6.28-15-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.28-15-generic
 linux-headers-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)
sol@sol-desktop:~$

---

### Post by zvacet on 2009-08-18
```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f instal
```

---

### Post by lotusalive on 2009-08-19
Thank you zvacet !

It's just not liking me too much:  Is it telling me it won't install without nvidia graphics card ? ?  (I tried to uninstall all programs that were for other graphics cards, since it made the machine unhappy and confused...)

sol@sol-desktop:~$ sudo dpkg --configure -a
[sudo] password for sol: 
Setting up linux-headers-2.6.28-15-generic (2.6.28-15.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-15-generic (2.6.28-15.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-15-generic; however:
  Package linux-headers-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-generic:
 linux-restricted-modules-2.6.28-15-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-15-generic; however:
  Package linux-restricted-modules-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.15.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.28-15-generic
 linux-image-2.6.28-15-generic
 linux-headers-generic
 linux-restricted-modules-2.6.28-15-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
sol@sol-desktop:~$ sudo apt-get -f instal
E: Invalid operation instal
sol@sol-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-15-generic (2.6.28-15.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-generic:
 linux-restricted-modules-2.6.28-15-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-15-generic; however:
  Package linux-restricted-modules-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.15.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-15-generic (2.6.28-15.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-15-generic; however:
  Package linux-headers-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.28-15-generic
 linux-restricted-modules-2.6.28-15-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.28-15-generic
 linux-headers-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)
sol@sol-desktop:~$ 

And / But, it asks me to Restart everytime it attempts this...

And, when I tried to install software with Synaptics, I got Error Msgs as well...

:confused::confused::confused:  In Preferences, Distribution, I had previously changed it from 'Highest Version' to 'Jaunty,' but when I went back to check it, it is STILL set at 'Highest Version' (I had thought it meant 'Highest Version' OF Jaunty...)  I'm afraid to change it back to Jaunty now, needing to understand what it means, and what to do at this point...

---

### Post by lotusalive on 2009-08-20
Can I change Preferences - Distritribution from "highest version" back to "Jaunty," or will it cause me troubles I can't fix ?

---

### Post by scolbeck on 2009-08-20
Check the free space on your /boot filesystem.  I had a similar problem that was due to no space left.

---

### Post by lotusalive on 2009-08-21
Thanks for answering me scolbeck.  There seems to be plenty of room in both root and home partitions.  I don't really know what you mean by checking /boot filesystem.  When I go to Places > Computer > Filesystem > Boot, this is what is there, if it will help determine why I can't Update :

[IMG]http://img508.imageshack.us/img508/7950/bootfilesystem.png[/IMG]

Thanks to all to check this.:confused:

---

### Post by lotusalive on 2009-08-21
Then, I went back into Synaptic > Preferences > Distribution, and 'Jaunty' was ticked instead of 'Highest Version,' opposite of what it was 12 hours ago, without me changing it...  Waiting for a Reply here to do so...  Why would that happen ? ? ?

And then here's the result of running Update Mgr again: 

E: linux-image-2.6.28-15-generic: subprocess post-installation script returned error exit status 2

E: linux-restricted-modules-2.6.28-15-generic: dependency problems - leaving unconfigured

E: linux-image-generic: dependency problems - leaving unconfigured

E: linux-restricted-modules-generic: dependency problems - leaving unconfigured

E: linux-generic: dependency problems - leaving unconfigured

E: linux-headers-2.6.28-15-generic: subprocess post-installation script returned error exit status 2

E: linux-headers-generic: dependency problems - leaving unconfigured

E: linux-restricted-modules: dependency problems - leaving unconfigured


I just don't understand any of this !  Am I talking to myself ? (lol)

---

