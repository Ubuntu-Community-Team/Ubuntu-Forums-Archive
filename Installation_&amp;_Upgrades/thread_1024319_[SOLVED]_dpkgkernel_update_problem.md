---
title: "[SOLVED] dpkg/kernel update problem"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by stattostatto on 2008-12-28
I've searched for a result to this problem everywhere and can't find it. I'm using Hardy as this prevents me from upgrading.

I recently ran out of space on my /boot folder and just figured out how to clean the /boot/.Trash0 folder to free up some space.

However, this meant that linux-image-2.6.24-22-rt and linux-image-2.6.24-22-generic didn't install properly (I think).

As a result, I've had some troubles on this machine recently. For instance, I need to GRUB menu boot into linux-image-2.6.24-21-generic whenever I want to use my machine.

Another problem is with updates - I updated yesterday with few problems, but now dpkg seems to be broken with no way to fix it.

This is the output from the terminal:
ubuntu@dell:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-22-rt (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-rt (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
dpkg: subprocess post-installation script returned error exit status 1
ubuntu@dell:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy Release.gpg
Ign [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy/pirate Translation-en_US
Hit [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Fetched 1B in 5s (0B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@dell:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

It's the infinite loop from hell :(

`/boot/initrd.img-2.6.24-22-rt.new' existed as a 7.5Mb file, but was completely worthless in Nautilus - it said the file had been recently moved or deleted. I can't uninstall/reinstall it because apt-get is broken.

Please help. Thanks!

---

### Post by taurus on 2008-12-28
Not sure if other have already told you but it's not a good idea to mix one release with another in /etc/apt/sources.list.  

You are running hardy but you have some feisty's repos in there.

```

Hit http://packages.medibuntu.org feisty Release.gpg 

Ign http://packages.medibuntu.org feisty/free Translation-en_US 

Ign http://packages.medibuntu.org feisty/non-free Translation-en_US 

Hit http://packages.medibuntu.org feisty Release
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://packages.medibuntu.org feisty/non-free Packages 

```

---

### Post by albinootje on 2008-12-28
> **stattostatto said:**
> 
I recently ran out of space on my /boot folder and just figured out how to clean the /boot/.Trash0 folder to free up some space.

However, this meant that linux-image-2.6.24-22-rt and linux-image-2.6.24-22-generic didn't install properly (I think).


Can you post the output of the following :
```

df -h
ls -la /boot/
dpkg -l|grep linux-image
dpkg -l|grep modules|grep linux

```

---

### Post by stattostatto on 2008-12-29
I do know about the not mixing repo's, there are no gutsy's in there for instance but I guess I forgot to take out the feisty's.

Here you go. Thank you very much:

```
ubuntu@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             104G   62G   38G  63% /
varrun               1009M  140K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   72K 1009M   1% /dev
devshm               1009M  168K 1009M   1% /dev/shm
/dev/sda3             193M   99M   85M  54% /boot
tmpfs                1009M   39M  971M   4% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      104G   62G   38G  63% /home/ubuntu/.gvfs
ubuntu@dell:~$ ls -la /boot/
ls: cannot access /boot/config-2.6.24-22-generic: No such file or directory
ls: cannot access /boot/initrd.img-2.6.24-22-rt: No such file or directory
ls: cannot access /boot/initrd.img-2.6.24-22-rt.bak: No such file or directory
total 80826
drwxr-xr-x  5 root root    3072 2008-12-28 19:51 .
drwxr-xr-x 21 root root    1024 2008-12-28 17:34 ..
-rw-r--r--  1 root root  422667 2008-08-20 21:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-21 20:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 15:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root     512 2008-10-11 08:45 boot.0810
-rw-r--r--  1 root root  308326 2008-10-11 08:44 coffee.bmp
-rw-r--r--  1 root root   80049 2008-08-20 21:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   85837 2008-08-20 21:58 config-2.6.24-19-rt
-rw-r--r--  1 root root   80062 2008-10-21 20:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   85862 2008-10-21 20:24 config-2.6.24-21-rt
-?????????  ? ?    ?          ?                ? config-2.6.24-22-generic
-rw-r--r--  1 root root   85862 2008-11-24 16:01 config-2.6.24-22-rt
lrwxrwxrwx  1 root root      15 2008-10-11 08:44 debian.bmp -> /boot/sarge.bmp
-rw-r--r--  1 root root  153720 2008-10-11 08:44 debianlilo.bmp
drwxr-xr-x  2 root root    1024 2008-12-28 19:36 grub
-rw-r--r--  1 root root 7874561 2008-08-27 07:19 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7854428 2008-08-27 07:20 initrd.img-2.6.24-19-rt
-rw-r--r--  1 root root 7876949 2008-11-07 21:34 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7876931 2008-11-07 21:33 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7854279 2008-11-07 21:33 initrd.img-2.6.24-21-rt
-rw-r--r--  1 root root 7854237 2008-11-07 21:33 initrd.img-2.6.24-21-rt.bak
-rw-r--r--  1 root root 7875265 2008-11-30 20:53 initrd.img-2.6.24-22-generic
-?????????  ? ?    ?          ?                ? initrd.img-2.6.24-22-rt
-?????????  ? ?    ?          ?                ? initrd.img-2.6.24-22-rt.bak
-rw-r--r--  1 root root 7852206 2008-12-28 19:57 initrd.img-2.6.24-22-rt.new
drwx------  2 root root   12288 2007-10-09 13:07 lost+found
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rwxrwxrwx  1 root root   23662 2008-10-11 08:44 sarge.bmp
-rw-r--r--  1 root root   24116 2008-10-11 08:44 sid.bmp
-rw-r--r--  1 root root  905170 2008-08-20 21:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  928302 2008-08-20 21:58 System.map-2.6.24-19-rt
-rw-r--r--  1 root root  905617 2008-10-21 20:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  928723 2008-10-21 20:24 System.map-2.6.24-21-rt
-rw-r--r--  1 root root  905617 2008-11-24 15:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  928723 2008-11-24 16:01 System.map-2.6.24-22-rt
drwx------  2 root root    1024 2008-12-28 19:48 .Trash-0
-rw-r--r--  1 root root 1921464 2008-08-20 21:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1960312 2008-08-20 21:58 vmlinuz-2.6.24-19-rt
-rw-r--r--  1 root root 1920760 2008-10-21 20:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1960792 2008-10-21 20:24 vmlinuz-2.6.24-21-rt
-rw-r--r--  1 root root 1921176 2008-11-24 15:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1960984 2008-11-24 16:01 vmlinuz-2.6.24-22-rt
ubuntu@dell:~$ dpkg -l|grep linux-image
rc  linux-image-2.6.20-16-generic              2.6.20-16.32                           Linux kernel image for version 2.6.20 on x86/x86_64
ii  linux-image-2.6.22-14-generic              2.6.22-14.52                           Linux kernel image for version 2.6.22 on x86/x86_64
rc  linux-image-2.6.24-16-generic              2.6.24-16.30                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-16-rt                   2.6.24-16.30                           Linux kernel image for version 2.6.24 on Ingo Molnar's
rc  linux-image-2.6.24-17-generic              2.6.24-17.31                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-17-rt                   2.6.24-17.31                           Linux kernel image for version 2.6.24 on Ingo Molnar's
rc  linux-image-2.6.24-18-generic              2.6.24-18.32                           Linux kernel image for version 2.6.24 on x86/x86_64
rc  linux-image-2.6.24-18-rt                   2.6.24-18.32                           Linux kernel image for version 2.6.24 on Ingo Molnar's
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                           Linux kernel image for version 2.6.24 on x86/x86_64
ii  linux-image-2.6.24-19-rt                   2.6.24-19.41                           Linux kernel image for version 2.6.24 on Ingo Molnar's
ii  linux-image-2.6.24-21-generic              2.6.24-21.43                           Linux kernel image for version 2.6.24 on x86/x86_64
ii  linux-image-2.6.24-21-rt                   2.6.24-21.43                           Linux kernel image for version 2.6.24 on Ingo Molnar's
ii  linux-image-2.6.24-22-generic              2.6.24-22.45                           Linux kernel image for version 2.6.24 on x86/x86_64
iF  linux-image-2.6.24-22-rt                   2.6.24-22.45                           Linux kernel image for version 2.6.24 on Ingo Molnar's
ii  linux-image-generic                        2.6.24.22.24                           Generic Linux kernel image
ii  linux-image-rt                             2.6.24.22.24                           Real time Linux kernel image
ubuntu@dell:~$ dpkg -l|grep modules|grep linux
rc  linux-backports-modules-2.6.20-16-generic  2.6.20-16.11                           Ubuntu supplied Linux modules for version 2.6.20 on x8
rc  linux-backports-modules-2.6.22-14-generic  2.6.22-14.10                           Ubuntu supplied Linux modules for version 2.6.22 on x8
rc  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29                         Non-free Linux 2.6.20 modules on x86/x86_64
rc  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.10                         Non-free Linux 2.6.22 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-16-rt      2.6.24.12-16.34                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-17-generic 2.6.24.12-17.36                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-17-rt      2.6.24.12-17.36                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-generic 2.6.24.13-18.41                        Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-18-rt      2.6.24.13-18.41                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-19-rt      2.6.24.13-19.45                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-21-rt      2.6.24.14-21.51                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-22-generic 2.6.24.14-22.53                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-22-rt      2.6.24.14-22.53                        Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.14-22.53                        Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.22.24                           Restricted Linux modules for generic kernels
ii  linux-restricted-modules-rt                2.6.24.22.24                           Restricted Linux modules for rt kernels
rc  linux-ubuntu-modules-2.6.22-14-generic     2.6.22-14.37                           Ubuntu supplied Linux modules for version 2.6.22 on x8
rc  linux-ubuntu-modules-2.6.24-16-generic     2.6.24-16.23                           Ubuntu supplied Linux modules for version 2.6.24 on x8
rc  linux-ubuntu-modules-2.6.24-16-rt          2.6.24-16.23                           Ubuntu supplied Linux modules for version 2.6.24 on x8
rc  linux-ubuntu-modules-2.6.24-17-generic     2.6.24-17.25                           Ubuntu supplied Linux modules for version 2.6.24 on x8
rc  linux-ubuntu-modules-2.6.24-17-rt          2.6.24-17.25                           Ubuntu supplied Linux modules for version 2.6.24 on x8
rc  linux-ubuntu-modules-2.6.24-18-generic     2.6.24-18.26                           Ubuntu supplied Linux modules for version 2.6.24 on x8
rc  linux-ubuntu-modules-2.6.24-18-rt          2.6.24-18.26                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.28                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-19-rt          2.6.24-19.28                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-21-generic     2.6.24-21.33                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-21-rt          2.6.24-21.33                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-22-generic     2.6.24-22.35                           Ubuntu supplied Linux modules for version 2.6.24 on x8
ii  linux-ubuntu-modules-2.6.24-22-rt          2.6.24-22.35                           Ubuntu supplied Linux modules for version 2.6.24 on x8

```

---

### Post by albinootje on 2008-12-29
> **stattostatto said:**
> 
/dev/sda3             193M   99M   85M  54% /boot
--- cut ---
ls: cannot access /boot/config-2.6.24-22-generic: No such file or directory
ls: cannot access /boot/initrd.img-2.6.24-22-rt: No such file or directory
ls: cannot access /boot/initrd.img-2.6.24-22-rt.bak: No such file or directory
[/CODE]

Okay, you have quite some space in /boot now, can you do the following :
```

cd /boot
sudo rm config-2.6.24-22-generic
sudo touch config-2.6.24-22-generic
sudo rm initrd.img-2.6.24-22-rt
sudo touch initrd.img-2.6.24-22-rt
sudo rm initrd.img-2.6.24-22-rt.bak
sudo touch initrd.img-2.6.24-22-rt.bak
sudo dpkg --configure -a

```
And post any errors.

---

### Post by stattostatto on 2008-12-29
I did make a typo in there, apologies

```
ubuntu@dell:~$ cd /boot
ubuntu@dell:/boot$ sudo rm config-2.6.24-22-generic
[sudo] password for ubuntu: 
rm: cannot remove `config-2.6.24-22-generic': No such file or directory
ubuntu@dell:/boot$ sudo touch config-2.6.24-22-generic
touch: cannot touch `config-2.6.24-22-generic': No such file or directory
ubuntu@dell:/boot$ sudo rm initrd.img-2.6.24-22-rt
rm: cannot remove `initrd.img-2.6.24-22-rt': No such file or directory
ubuntu@dell:/boot$ sudo touch initrd.img-2.6.24-22-ty
ubuntu@dell:/boot$ sudo touch initrd.img-2.6.24-22-rt
touch: cannot touch `initrd.img-2.6.24-22-rt': No such file or directory
ubuntu@dell:/boot$ sudo rm initrd.img-2.6.24-22-rt.bak
rm: cannot remove `initrd.img-2.6.24-22-rt.bak': No such file or directory
ubuntu@dell:/boot$ sudo touch initrd.img-2.6.24-22-rt.bak
touch: cannot touch `initrd.img-2.6.24-22-rt.bak': No such file or directory
ubuntu@dell:/boot$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-22-rt (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-rt (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
dpkg: subprocess post-installation script returned error exit status 1
ubuntu@dell:/boot$ 

```

---

### Post by albinootje on 2008-12-29
Okay, thanks.
Weird that you cannot create those files with "touch".
Can you post the output of the following :

```

mount
uname -a
cat /boot/grub/menu.lst
sudo touch /boot/initrd.img-2.6.24-22-rt.new
sudo dpkg --configure -a
sudo apt-get install --reinstall linux-image-2.6.24-22-rt

```

---

### Post by stattostatto on 2008-12-29
This is becoming almost funny at this point. Thank you again for your continual help.

```
ubuntu@dell:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda3 on /boot type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@dell:~$ uname -a
Linux dell 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
ubuntu@dell:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
initrd		/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single
initrd		/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
initrd		/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single
initrd		/initrd.img-2.6.24-21-rt

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
initrd		/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-rt root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single
initrd		/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

ubuntu@dell:~$ sudo touch /boot/initrd.img-2.6.24-22-rt.new
[sudo] password for ubuntu: 
ubuntu@dell:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-22-rt (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-rt (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
dpkg: subprocess post-installation script returned error exit status 1
ubuntu@dell:~$ sudo apt-get install --reinstall linux-image-2.6.24-22-rt
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ubuntu@dell:~$ 

```

---

### Post by albinootje on 2008-12-29
> **stattostatto said:**
> This is becoming almost funny at this point. Thank you again for your continual help.

:) No problem.

So you're using kernel 2.6.24-21-generic right now.
Can you please try the following :

```

sudo dpkg -P --force-all linux-image-2.6.24-22-rt linux-image-2.6.24-22-generic linux-image-2.6.24-21-rt linux-image-2.6.24-19-rt linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-22-rt linux-restricted-modules-2.6.24-22-generic linux-restricted-modules-2.6.24-21-rt linux-restricted-modules-2.6.24-19-rt linux-restricted-modules-2.6.24-19-generic

```
Hopefully that'll work right away.

---

### Post by stattostatto on 2008-12-29
```
ubuntu@dell:~$ sudo dpkg -P --force-all linux-image-2.6.24-22-rt linux-image-2.6.24-22-generic linux-image-2.6.24-21-rt linux-image-2.6.24-19-rt linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-22-rt linux-restricted-modules-2.6.24-22-generic linux-restricted-modules-2.6.24-21-rt linux-restricted-modules-2.6.24-19-rt linux-restricted-modules-2.6.24-19-generic
[sudo] password for ubuntu: 
(Reading database ... 314266 files and directories currently installed.)
Removing linux-restricted-modules-2.6.24-21-rt ...
Purging configuration files for linux-restricted-modules-2.6.24-21-rt ...
Removing linux-restricted-modules-2.6.24-19-rt ...
Purging configuration files for linux-restricted-modules-2.6.24-19-rt ...
Removing linux-restricted-modules-2.6.24-19-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-19-generic ...
dpkg: linux-image-2.6.24-22-generic: dependency problems, but removing anyway as you request:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic.
 linux-image-generic depends on linux-image-2.6.24-22-generic.
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic.
Removing linux-image-2.6.24-22-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-22-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-22-generic': Directory not empty
dpkg: linux-image-2.6.24-21-rt: dependency problems, but removing anyway as you request:
 linux-ubuntu-modules-2.6.24-21-rt depends on linux-image-2.6.24-21-rt.
Removing linux-image-2.6.24-21-rt ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-21-rt ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-21-rt': Directory not empty
dpkg: linux-image-2.6.24-19-rt: dependency problems, but removing anyway as you request:
 linux-ubuntu-modules-2.6.24-19-rt depends on linux-image-2.6.24-19-rt.
Removing linux-image-2.6.24-19-rt ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-19-rt ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-19-rt': Directory not empty
dpkg: linux-image-2.6.24-19-generic: dependency problems, but removing anyway as you request:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic.
Removing linux-image-2.6.24-19-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.24-19-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-19-generic': Directory not empty
dpkg: linux-restricted-modules-2.6.24-22-rt: dependency problems, but removing anyway as you request:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.24-22-rt.
Removing linux-restricted-modules-2.6.24-22-rt ...
Purging configuration files for linux-restricted-modules-2.6.24-22-rt ...
dpkg: linux-restricted-modules-2.6.24-22-generic: dependency problems, but removing anyway as you request:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic.
Removing linux-restricted-modules-2.6.24-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-22-generic': No such file or directory
Purging configuration files for linux-restricted-modules-2.6.24-22-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-22-generic': No such file or directory
dpkg: linux-image-2.6.24-22-rt: dependency problems, but removing anyway as you request:
 linux-ubuntu-modules-2.6.24-22-rt depends on linux-image-2.6.24-22-rt.
 linux-image-rt depends on linux-image-2.6.24-22-rt.
Removing linux-image-2.6.24-22-rt ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-22-rt ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-22-rt': Directory not empty
ubuntu@dell:~$ 

```

Noticed update manager lit up with a big bad "dependency problem" sign... am running it right now.

---

### Post by stattostatto on 2008-12-29
Update manager popped this out:

```
E: /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb: unable to install new version of `./boot/config-2.6.24-22-generic'

```

---

### Post by albinootje on 2008-12-29
> **stattostatto said:**
> 
Noticed update manager lit up with a big bad "dependency problem" sign... am running it right now.

Okay.
After this, can you run :
```

sudo dpkg --configure -a
sudo apt-get -f install

```
And post any errors ?

---

### Post by stattostatto on 2008-12-29
```
ubuntu@dell:~$ sudo dpkg --configure -a
[sudo] password for ubuntu: 
Setting up linux-image-2.6.24-22-rt (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-rt:
 linux-restricted-modules-2.6.24-22-rt depends on linux-image-2.6.24-22-rt; however:
  Package linux-image-2.6.24-22-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-rt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-rt
 linux-image-generic
 linux-restricted-modules-2.6.24-22-generic
 linux-restricted-modules-2.6.24-22-rt
ubuntu@dell:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.24-22-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-22-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/18.4MB of archives.
After this operation, 61.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 311271 files and directories currently installed.)
Unpacking linux-image-2.6.24-22-generic (from .../linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb (--unpack):
 unable to install new version of `./boot/config-2.6.24-22-generic': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@dell:~$ 

```

Well... we're getting closer I think!?

---

### Post by albinootje on 2008-12-29
> **stattostatto said:**
>  Well... we're getting closer I think!?

What I don't understand is that
```

sudo touch /boot/linux-image-some-example-name

```
gave errors :(

I've even tested it here (with sudo) to be sure.

The touch command should create a file when the file does not exist.
And if the file exists, then it should only update the timestamp on that file and nothing else.

---

### Post by albinootje on 2008-12-29
Do you want to continue trying to resolve this problem, or is backing up properly, and doing a fresh install a valid option for you ?

---

### Post by stattostatto on 2008-12-29
Well I think those files are broken somehow.

I don't really want to reinstall. I've had this setup for 14 months now and this was the first big problem. Apt-get works now and I got into synaptic package manager again (finally) so that issue has been resolved :D

Unfortunately, I have three broken packages - linux-image-generic, linux-restricted-modules-2.6.24-22-generic, linux-ubuntu-modules-2.6.24-22-generic - and I'm not sure how to fix them :(.

---

### Post by stattostatto on 2008-12-29
I am also getting an Error: Brokencount > 0 error.

---

### Post by albinootje on 2008-12-29
> **stattostatto said:**
> Well I think those files are broken somehow.

I don't really want to reinstall. I've had this setup for 14 months now and this was the first big problem. Apt-get works now and I got into synaptic package manager again (finally) so that issue has been resolved :D

Unfortunately, I have three broken packages - linux-image-generic, linux-restricted-modules-2.6.24-22-generic, linux-ubuntu-modules-2.6.24-22-generic - and I'm not sure how to fix them :(.

We can look at that later today, I need to catch some sleep.

Au revoir :)

---

### Post by stattostatto on 2008-12-30
Cheers, Thanks

---

### Post by albinootje on 2008-12-30
Can you do the following :
```

sudo su -
mkdir /boot
touch /boot/initrd.img-2.6.24-22-rt.new
touch /boot/config-2.6.24-22-generic
exit
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -f install

```

And post any errors.Thanks.

---

### Post by stattostatto on 2008-12-30
Still the 'touch' problem. Probably due to the fact the permissions are -?????????

```
ubuntu@dell:~$ sudo su -
[sudo] password for ubuntu: 
root@dell:~# mkdir /boot
mkdir: cannot create directory `/boot': File exists
root@dell:~# touch /boot/initrd.img-2.6.24-22-rt.new
root@dell:~# touch /boot/config-2.6.24-22-generic
touch: cannot touch `/boot/config-2.6.24-22-generic': No such file or directory
root@dell:~# exit
logout
ubuntu@dell:~$ sudo apt-get update
Hit http://repository.cinnamonpirate.com hardy Release.gpg
Ign http://repository.cinnamonpirate.com hardy/pirate Translation-en_US
Hit http://repository.cinnamonpirate.com hardy Release                         
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://repository.cinnamonpirate.com hardy/pirate Packages                 
Hit http://wine.budgetdedicated.com hardy Release                              
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://repository.cinnamonpirate.com hardy/pirate Packages                 
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://packages.medibuntu.org feisty Release.gpg                           
Ign http://packages.medibuntu.org feisty/free Translation-en_US                
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US            
Hit http://packages.medibuntu.org feisty Release                               
Hit http://packages.medibuntu.org feisty/free Packages                         
Hit http://packages.medibuntu.org feisty/non-free Packages                     
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US   
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://archive.ubuntu.com hardy-updates Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US   
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg          
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release                      
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release               
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://archive.ubuntu.com hardy-updates/restricted Packages     
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://us.archive.ubuntu.com hardy/restricted Packages          
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Fetched 1B in 46s (0B/s)
Reading package lists... Done
ubuntu@dell:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-22-rt (2.6.24-22.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-22-rt
mv: cannot move `/boot/initrd.img-2.6.24-22-rt.new' to `/boot/initrd.img-2.6.24-22-rt': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-22-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not installed.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic:
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however:
  Package linux-image-2.6.24-22-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-rt:
 linux-restricted-modules-2.6.24-22-rt depends on linux-image-2.6.24-22-rt; however:
  Package linux-image-2.6.24-22-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-22-rt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-22-rt
 linux-image-generic
 linux-restricted-modules-2.6.24-22-generic
 linux-restricted-modules-2.6.24-22-rt
ubuntu@dell:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.24-22-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-22-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/18.4MB of archives.
After this operation, 61.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 311271 files and directories currently installed.)
Unpacking linux-image-2.6.24-22-generic (from .../linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb (--unpack):
 unable to install new version of `./boot/config-2.6.24-22-generic': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config-2.6.24-22-generic: No such file or directory
Found kernel: /vmlinuz-2.6.24-22-rt
Found kernel: /vmlinuz-2.6.24-21-rt
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-19-rt
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@dell:~$ 

```

---

### Post by albinootje on 2008-12-30
> **stattostatto said:**
> Still the 'touch' problem.
```

root@dell:~# touch /boot/initrd.img-2.6.24-22-rt.new
root@dell:~# touch /boot/config-2.6.24-22-generic
touch: cannot touch `/boot/config-2.6.24-22-generic': No such file or directory

```


Very strange, now one touch command works, the other doesn't.

This is on my machine :

# touch /boot/initrd.img-2.6.24-22-rt.new
# ls -la /boot/initrd.img-2.6.24-22-rt.new 
-rw-r--r-- 1 root root 0 2008-12-31 00:20 /boot/initrd.img-2.6.24-22-rt.new

You have enough disk space in / according to your df -h output.
/boot is not a separate partition on your machine.
I didn't see any unusual mount options for your / partitions, although I might have to check again to be sure.

Do you have an Ubuntu Live CD ?
Can you boot with that and then mount your / partition from your hard disk, and then do the following, assuming that in this example your / partition of your hard disk is mounted with mountpoint /media/disk-1 :
```

sudo touch /media/disk-1/boot/initrd.img-2.6.24-22-rt.new
sudo touch /media/disk-1/boot/config-2.6.24-22-generic

```

When that does not give an error, please boot again from your working kernel without the Live CD, and perform again the following :
```

sudo dpkg --configure -a
sudo apt-get -f install

```
Please post any errors.

---

### Post by stattostatto on 2008-12-30
FYI boot is a separate partition on my computer, sda3 where the rest of the hard drive is sda6. Will try this - my live CD is Intrepid but I don't think that should cause a problem. Thanks!

---

### Post by albinootje on 2008-12-30
> **stattostatto said:**
> FYI boot is a separate partition on my computer, sda3 where the rest of the hard drive is sda6. 

Hmmm,okay,sorry,got that mixed up somehow.

can you show the output of :
```

cat /etc/fstab
mount

```
again, please ? thanks.

>  Will try this - my live CD is Intrepid but I don't think that should cause a problem.
That's fine.

---

### Post by stattostatto on 2008-12-30
'ere you go, thanks again:

```
ubuntu@dell:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa39ea06-74e5-4a91-b0bb-423155a3454e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d42cc688-e83c-474e-b677-c392dc03a10c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=cfcbd857-0e6d-4767-b855-49a7ba35361f  /boot ext3 defaults 0 0
ubuntu@dell:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda3 on /boot type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@dell:~$ 

```

---

### Post by albinootje on 2008-12-30
> **stattostatto said:**
> 
UUID=cfcbd857-0e6d-4767-b855-49a7ba35361f  /boot ext3 defaults 0 0
-- cut --
/dev/sda3 on /boot type ext3 (rw)
[/CODE]

Okay, thanks, looks good.
Can you do this :
```

sudo umount /boot
sudo fsck -y /dev/sda3
sudo mount -a

```
And then continue with commands under the live cd as proposed ?

---

### Post by stattostatto on 2008-12-30
Just for kicks I ran fsck on sda3. It fixed some errors. I then tried touching the files even though I hadn't restarted with the Live CD, and they "touched" without an error message! So I ran: 
sudo dpkg --configure -a 
sudo apt-get update

and now I have 0 broken packages and it appears the kernel installed successfully.

I am going to restart my computer now, if it goes well I'll [SOLVED] this thread and graciously thank you!

---

### Post by stattostatto on 2008-12-30
My Ubuntu is healthy again! Thank you very much.

---

### Post by albinootje on 2008-12-31
> **stattostatto said:**
> My Ubuntu is healthy again! Thank you very much.

Great! Glad it's fixed :)

---

