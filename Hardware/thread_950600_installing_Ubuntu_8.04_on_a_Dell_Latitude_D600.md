---
title: "installing Ubuntu 8.04 on a Dell Latitude D600"
date: 2008-10-17
forum: Hardware
---

### Post by Ken53 on 2008-10-17
In the process of installing Ubuntu on a Dell Latitude D600, I encountered two problems:
[LIST=1]
[*]a disk partitioning error that resulted in loss of available space
[*]failure of wireless to work
[/LIST]
With help from the Dell Linux listserv, the problems were solved, and at the suggestion of one of the list members, I am posting here to make what I learned more accessible to the Ubuntu commmunity.

**System Information**

[LIST]    
[*]Dell Latitude D600
[*]Intel Pentium 1.4 GHz processor
[*]512 MB RAM
[*]80 GB HD
[*]Dell TrueMobile 1300 WLAN Mini-PCI Card using the Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
[*]Windows XP Pro OS
[/LIST]
**Summary of the Installation**
[LIST]
[*]Connected the D600 to the internet via a wired connection.
[*]Started installation from an Ubuntu 8.04 CD to install dual-boot with XP. 
[*]For partitioning, I selected Guided partitioning with 50% XP (~37GB) and 50% Ubuntu (~37 GB).
[*]During partitioning, I got the error
> Failed to create a file system: The ext3 file system creation in partition #5 of SCSI (0,0,0)(sda) failed.

[*]Clicked OK and the "Prepare disk space" installation step automatically repeated. This time, I chose 30% XP (11.0 GB) and 70% Ubuntu (25.8 GB). Note that the combined partitions are about half the ~74GB space originally available. See the resolution, below.
[*]Installation proceeded without further errors.
[*]After installation, all seemed well except that wireless did not work. I found the following in the Syslog (System > Administration > System Log > syslog):
[LIST]
[*]Oct  6 13:01:54 Ken53-D600 firmware_helper[7484]: main: error loading '/lib/firmware/b43legacy/ucode4.fw' for device '/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/ssb0:0/firmware/ssb0:0' with driver '(unknown)'
[*]Oct  6 13:01:54 Ken53-D600 kernel: [ 1105.887652] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[*]Oct  6 13:01:54 Ken53-D600 kernel: [ 1105.887663] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[*]Oct  6 13:01:56 Ken53-D600 NetworkManager: <WARN> nm_device_802_11_wireless_scan(): (wlan0): could not trigger wireless scan: Network is down
[/LIST]
[/LIST]
**Partition Problem Resolutio**n

To recover the lost disk space, I used the following procedure.
[LIST=1]
[*]Restart and boot from live CD.
[*]Run Gparted (System > Administration > Disk Partitioning). See [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/).
[*]Find the bad partition. In my case, it was a ~36GB partition of "unknown" file system type.
[*]Change the file system type of that partition to ext3.
[/LIST]
Upon rebooting the installed system, I found a new volume corresponding  to the lost space. It's a messy set of partitions but it works and and  I'll clean that up when I understand partitions and partitioning better.

**Wireless Problem Resolution**

For this, I found the following references helpful, if not essential:
[LIST=1]
[*]Linux Wireless b43 and b43legacy page: [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)
[*]Christopher's 8.04 + Broadcom Wireless page [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)
[/LIST]
I used the following procedure:
[LIST=1]
[*]Get a wired connection to the internet.
[*]Open a Terminal.
[*]Create a directory, say 'Wireless' and go there.
```

mkdir Wireless
cd Wireless

```
[*]Get and install the build essentials package to build the firmware extractor, b43-fwcutter [reference 2]
```

sudo apt-get install build-essential

```
[*]Get and build the b43-fwcutter [1]
```

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

```
[*]Download the driver and extract the firmware [1, 2 (with modifications)]. If necessary, change FIRMWARE_INSTALL_DIR to thedirectory where the firmware should go.
```

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
sudo ./b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o

```
[*]Reboot.
[/LIST]
After this procedure, wireless worked and Ubuntu is running well now. A few issues remain, but I'm working on those. I have a usable system and I'm using it for my work.

I hope that the summary helps someone. The Linux community has certainly been a blessing to me!

---

### Post by baosheng on 2008-10-17
This is great. Thanks Ken.

---

