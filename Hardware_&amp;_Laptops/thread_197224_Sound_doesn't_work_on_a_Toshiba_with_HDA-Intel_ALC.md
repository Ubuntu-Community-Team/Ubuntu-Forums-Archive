---
title: "Sound doesn't work on a Toshiba with HDA-Intel ALC260 codec"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by er-ku on 2006-06-15
Hi,
This is a new thread deriving from [http://ubuntuforums.org/showthread.php?t=76019](http://ubuntuforums.org/showthread.php?t=76019) (same problem on Acer notebooks).

The problem is simple: you cannot hear any sound if you're using a Toshiba which uses Realtek's ALC260 Intel HDA codec for sound.

Here, We'll be trying to find a working solution for this.

The problem is not on my computer, so this first entry in the thread looks a littlee weird. :)

---

### Post by JLCarneiro on 2006-06-18
[QUOTE=er-ku][...]
The problem is simple: you cannot hear any sound if you're using a Toshiba which uses Realtek's ALC260 Intel HDA codec for sound.

Here, We'll be trying to find a working solution for this.
[...][/QUOTE]
Well, I'm not very experienced with GNU/Linux. So, probably this info is not that useful. Anyway, a friend of mine told me about this site, that gives vendor information (in a friendly way):
[http://kmuto.jp/debian/hcl/index.cgi]("http://kmuto.jp/debian/hcl/index.cgi")
You only have to paste your [FONT="Courier New"]lspci -n[/FONT] output there.

This is what I got:[HTML]
PCI ID    Works?   Vendor              Device                                                                 Driver
80862668  Yes      Intel Corporation   82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller   snd-hda-intel[/HTML]

---

### Post by er-ku on 2006-08-04
Okay, so the solution to this problem should be simple - using the 'test' model, that ALSA 1.0.11 provides. Here are the instructions on how to compile the required ALSA 1.0.11 drivers for Dapper:

[LIST=1]
[*] Download the alsa-source package from Edgy from any of the mirrors listed at [alsa-source download page](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fa%2Falsa-driver%2Falsa-source_1.0.11-3ubuntu1_all.deb&md5sum=9efe70b4a38fc8b6ef750744903856c4&arch=all&type=main);
[*] **NOTE: from here on, you'll be working in a terminal window.** Install the downloaded file like this:
```
$ sudo dpkg -i /path/to/alsa-source_1.0.11-3ubuntu1_all.deb
```
[*] add yourself to the group 'src' (this isn't necessary, but that's mysetup:
```
$ sudo adduser $(whoami) src
```
then log out and log back in;
[*] Install the packages that are needed for compilation. You probably have most of them already:
```
$ sudo apt-get install linux-headers-$(uname -r) kernel-package make gcc dpkg-dev debhelper debconf-utils debconf bzip2
```
[*] extract the ALSA driver sources:
```
$ cd /usr/src
$ tar -jxvf alsa-driver.tar.bz2
```
[*] Edit the alsa-source configuration file to define which drivers to compile.
```
$ sudo gedit /etc/alsa/alsa-source.conf
```
In our case, we will tell ALSA to only compile the snd-hda-intel module by setting ALSA_CARDS="hda-intel". "test" module (which we need) will be enabled by setting ALSA_DEBUG="y".
Save the file
[*] copy the Linux kernel headers to a place where you can write to their directory:
```
$ cp -rpL linux-headers-$(uname -r) /tmp
$ ln -s asm /tmp/linux-headers-$(uname -r)/include/asm-i386

```
[*] Compile the drivers:
```
$ cd /usr/src/modules/alsa-driver
$ fakeroot debian/rules binary_modules KSRC=/tmp/linux-headers-$(uname -r) KVERS=$(uname -r)
```
[*] Remove the temporary kernel source directory:
```
$ rm -Rf /tmp/linux-headers-$(uname -r)
```
[*] Install the newly-compiled drivers:
```
$ sudo dpkg -i /usr/src/modules/alsa-modules-$(uname -r)*.deb
```
[*] Create/edit /etc/modprobe.d/snd-hda-intel.modprobe file by adding to it a line telling the module to use the 'test' model:
```
$ sudo -s
# echo "options snd-hda-intel model=acer" >> /etc/modprobe.d/snd-hda-intel.modprobe
# exit
```
[*] restart ALSA (by rebooting your computer, for example).
[/LIST]

Now you should be having the 'test' model loaded, and you should be able to tweak most of the controls of the ALC260 chipset.

Let me know if you have any problems or success with this HOWTO. ;)

---

