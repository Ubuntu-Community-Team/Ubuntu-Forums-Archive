---
title: "error after update"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-02-10
When I run the automatic updates, I always end up with following error:

Error processing
/var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb :
unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before
installing new version: Operation not permitted.

how can I cure that?
It happens on Kubuntu, Xubuntu and Ubuntu where ever I installed it, partition or wubi way, simple after the general updates done by the update manager from the net.

The error persisting and all updates end from now with this error.

---

### Post by aheckler on 2009-02-10
Post the output of "sudo apt-get update && sudo apt-get upgrade" please.

---

### Post by Kevbert on 2009-02-10
Do you have a large number of kernels installed ?  What is the terminal output of
```
cd /boot
ls -l
```

---

### Post by ottosykora on 2009-02-11
I just tried to install ubuntu, kubuntu and xubuntu.

In all versions, after installation there is a prompt to make update. 
OK, run the updater and at the end I am left with the above stated error message. 

Each time I start ubunto or any other ..buntu, I am again prompted to make update, this time only one update file seems to eed update, after short time I am getting again the same error message and the prompt for updating remains.
I did not do anything manually (I have no idea how to do it anyway), just installed and run the updater.
The same happends on all versions I manged to install, kubuntu 8.10, xubuntu 8.10, ubuntu 8.04

---

### Post by ottosykora on 2009-02-11
under kubuntu which is just on this machine:


after sudo apt-get upgrade:

----
os@ubuntu:~$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete sind zurückgehalten worden:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
Die folgenden Pakete werden aktualisiert:
  busybox-initramfs ca-certificates-java cpp-4.3 firefox firefox-3.0
  firefox-3.0-branding gcc-4.3 gcc-4.3-base ghostscript ghostscript-x ktorrent
  libc6 libc6-dev libc6-i686 libgcc1 libgomp1 libgs8 libldap-2.4-2 libpulse0
  libsqlite3-0 libstdc++6 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x linux-image-2.6.27-7-generic linux-libc-dev
  linux-restricted-modules-common nvidia-173-modaliases nvidia-96-modaliases
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ufw vim-common
  vim-tiny xserver-xorg-video-intel xulrunner-1.9
39 aktualisiert, 0 neu installiert, 0 zu entfernen und 4 nicht aktualisiert.
Es müssen noch 64.9MB von 88.3MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 28.7kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? 

---------------
after sudo apt-get update:

Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid Release.gpg
Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Translation-de
Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Translation-de
Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid Release
Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Packages
Ign cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Packages
Fehl cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/main Packages
  Bitte verwenden Sie apt-cdrom, um diese CD von APT erkennbar zu machen. apt-get update kann nicht dazu verwendet werden, neue CDs hinzuzufügen
Fehl cdrom://Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1) intrepid/restricted Packages
  Bitte verwenden Sie apt-cdrom, um diese CD von APT erkennbar zu machen. apt-get update kann nicht dazu verwendet werden, neue CDs hinzuzufügen
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid Release.gpg
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/main Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/restricted Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/universe Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/multiverse Translation-de
Hole:1 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/main Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/restricted Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/universe Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/multiverse Translation-de
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid Release
Hole:2 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates Release [51.2kB]
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/main Packages
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/restricted Packages
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/main Sources
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/restricted Sources
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/universe Packages
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/universe Sources
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/multiverse Packages
OK   [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid/multiverse Sources
Hole:3 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/main Packages [296kB]
Hole:4 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/restricted Packages [6843B]
Hole:5 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/main Sources [91.6kB]
Hole:6 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/restricted Sources [2016B]
Hole:7 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/universe Packages [61.1kB]
Hole:8 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/universe Sources [15.5kB]
Hole:9 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/multiverse Packages [5200B]
Hole:10 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) intrepid-updates/multiverse Sources [2366B]
Es wurden 532kB in 2s geholt (217kB/s)               
W: Konnte cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/dists/intrepid/main/binary-i386/Packages.gz nicht holen  Bitte verwenden Sie apt-cdrom, um diese CD von APT erkennbar zu machen. apt-get update kann nicht dazu verwendet werden, neue CDs hinzuzufügen

W: Konnte cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/dists/intrepid/restricted/binary-i386/Packages.gz nicht holen  Bitte verwenden Sie apt-cdrom, um diese CD von APT erkennbar zu machen. apt-get update kann nicht dazu verwendet werden, neue CDs hinzuzufügen

E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

---

### Post by ottosykora on 2009-02-11
after cd /boot, ls -l

---
os@ubuntu:~$ cd /boot
os@ubuntu:/boot$ ls -l
insgesamt 24304
-rwxr-xr-x 1 root root  507665 2008-10-24 09:29 abi-2.6.27-7-generic
-rwxr-xr-x 1 root root  507665 2008-11-21 00:46 abi-2.6.27-9-generic
-rwxr-xr-x 1 root root   91364 2008-10-24 09:29 config-2.6.27-7-generic
-rwxr-xr-x 1 root root   91364 2008-11-21 00:46 config-2.6.27-9-generic
drwxr-xr-x 2 root root   16384 2009-02-06 09:22 grub
-rwxr-xr-x 1 root root 8464677 2009-01-12 17:42 initrd.img-2.6.27-7-generic
-rwxr-xr-x 1 root root 8465914 2009-01-12 17:56 initrd.img-2.6.27-9-generic
-rwxr-xr-x 1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rwxr-xr-x 1 root root 1029585 2008-10-24 09:29 System.map-2.6.27-7-generic
-rwxr-xr-x 1 root root 1029585 2008-11-21 00:46 System.map-2.6.27-9-generic
-rwxr-xr-x 1 root root    1073 2008-10-24 09:31 vmcoreinfo-2.6.27-7-generic
-rwxr-xr-x 1 root root    1073 2008-11-21 00:48 vmcoreinfo-2.6.27-9-generic
-rwxr-xr-x 1 root root 2244272 2008-10-24 09:29 vmlinuz-2.6.27-7-generic
-rwxr-xr-x 1 root root 2244304 2008-11-21 00:46 vmlinuz-2.6.27-9-generic
os@ubuntu:/boot$ 



Again, I did no manual installations or updates, all done by the updater alone.

But the updater is still prompting me again and again that importanat updates are avaiable.
Is there at least a way to disable the automatic update prompting so this does not permanently disturbs every few minutes?

---

### Post by ottosykora on 2009-02-11
now the updater did again run and this is what remained on the screen after that. I have no clue what this is about, but it is all the time the same. Ubuntu 8.04 on other machine and Xubuntu as well, all give the same when the updater is finaly run.

----

Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --unpack, /var/cache/apt/archives/libc6-i686_2.8~20080505-0ubuntu9_i386.deb, /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_i386.deb, /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb, /var/cache/apt/archives/linux-restricted-modules-common_2.6.27-11.16_all.deb, /var/cache/apt/archives/linux-restricted-modules-2.6.27-11-generic_2.6.27-11.16_i386.deb, /var/cache/apt/archives/openjdk-6-jre-lib_6b12-0ubuntu6.1_all.deb, /var/cache/apt/archives/ca-certificates-java_20080712ubuntu4_all.deb, /var/cache/apt/archives/openjdk-6-jre-headless_6b12-0ubuntu6.1_i386.deb, /var/cache/apt/archives/openjdk-6-jre_6b12-0ubuntu6.1_i386.deb, /var/cache/apt/archives/busybox-initramfs_1-0x1.afff4bfb9fcc4p-1491.10.2-1ubuntu7_i386.deb, /var/cache/apt/archives/libldap-2.4-2_2.4.11-0ubuntu6.1_i386.deb, /var/cache/apt/archives/libsqlite3-0_3.5.9-3ubuntu1_i386.deb, /var/cache/apt/archives/vim-tiny_1-0x1.afff4bfb9fcc4p-1497.1.314-3ubuntu3.1_i386.deb, /var/cache/apt/archives/vim-common_1-0x1.afff4bfb9fcc4p-1497.1.314-3ubuntu3.1_i386.deb, /var/cache/apt/archives/ufw_0.23.3_all.deb, /var/cache/apt/archives/firefox-3.0-branding_3.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb, /var/cache/apt/archives/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb, /var/cache/apt/archives/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb, /var/cache/apt/archives/firefox_3.0.6+nobinonly-0ubuntu0.8.10.1_all.deb, /var/cache/apt/archives/ghostscript_8.63.dfsg.1-0ubuntu6.2_i386.deb, /var/cache/apt/archives/libgs8_8.63.dfsg.1-0ubuntu6.2_i386.deb, /var/cache/apt/archives/ghostscript-x_8.63.dfsg.1-0ubuntu6.2_i386.deb, /var/cache/apt/archives/ktorrent_3.1.2+dfsg.1-0ubuntu2.1_i386.deb, /var/cache/apt/archives/libpulse0_0.9.10-2ubuntu9.3_i386.deb, /var/cache/apt/archives/libxine1_1.1.15-0ubuntu3.1_i386.deb, /var/cache/apt/archives/libxine1-x_1.1.15-0ubuntu3.1_i386.deb, /var/cache/apt/archives/libxine1-console_1.1.15-0ubuntu3.1_i386.deb, /var/cache/apt/archives/libxine1-misc-plugins_1.1.15-0ubuntu3.1_i386.deb, /var/cache/apt/archives/libxine1-bin_1.1.15-0ubuntu3.1_i386.deb, /var/cache/apt/archives/linux-generic_2.6.27.11.14_i386.deb, /var/cache/apt/archives/linux-image-generic_2.6.27.11.14_i386.deb, /var/cache/apt/archives/linux-restricted-modules-generic_2.6.27.11.14_i386.deb, /var/cache/apt/archives/linux-headers-2.6.27-11_2.6.27-11.27_all.deb, /var/cache/apt/archives/linux-headers-2.6.27-11-generic_2.6.27-11.27_i386.deb, /var/cache/apt/archives/linux-headers-generic_2.6.27.11.14_i386.deb, /var/cache/apt/archives/nvidia-173-modaliases_173.14.12-1-0ubuntu5.1_i386.deb, /var/cache/apt/archives/nvidia-96-modaliases_96.43.09-0ubuntu1.1_i386.deb, /var/cache/apt/archives/xserver-xorg-video-intel_2-0x1.afff4bfb9fcc4p-1492.4.1-1ubuntu10.3_i386.deb ], 
    Sup-process returned error code 1, 
    Error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb : unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted.

---

### Post by ottosykora on 2009-02-11
now the last disaster:
after those above updates did run as the updater insisted, I was not able to start the Kubuntu any more. Kernell panic was what I read at the end.

OK tried to hit ESC and went to the menu where something like kernel 9 was written, This time it did start, but nothing works any more properly, firefox just flashes and closes again... simply system seems to be completely broken by those updates.

Is there no way to get rid of all those updates and leave the system running as it is?

The updater insists stil on updates all the time, but when run, the result is:

Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --unpack, /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb ], 
    Sup-process returned error code 1, 
    Error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb : unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted.

---

### Post by ottosykora on 2009-02-11
Furthermore:

the last update did change the language of the installation into default english, the original was installed german. Not a real problem for me, but might bes erious for many other people.

Pls help me somehow to solve this update issue, since it seems to be common to all flavours. Installed the ubuntu 8.04 in czech language, it insited on an update of some 150 or so files and since then still updates are anounced , but can not be done since all ends with an error.

---

