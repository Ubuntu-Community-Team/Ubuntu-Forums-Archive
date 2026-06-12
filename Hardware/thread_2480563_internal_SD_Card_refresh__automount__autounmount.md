---
title: "internal SD Card refresh / automount / autounmount"
date: 2022-11-02
forum: Hardware
---

### Post by xaver88 on 2022-11-02
Hello
I'm new to Ubuntu
we use a NanoNeo Air with SDcard reader (on Board) and eMMC
the System is installed on the eMMC and the SD Card should be used as removable Media

If the SD Card is inserted at boot, it recoginzed as
mmcblk1      179:0    0 29.7G  0 disk
&#9492;&#9472;mmcblk1p1  179:1    0 29.7G  0 part /external/sd
and mounter as /external/sd

this works
but if I remove the card, the system did not recognise, that it's removed or if I put in an other one it also will not be recognized
How can I solve this problem
Target: everytime the card is removed, it should be automaticly unmounted and if it (or an other one) is back, it should be mounted with /extrernal/sd
/external is a folder on the eMMC
regard
Xaver

---

### Post by sudodus on 2022-11-02
Unfortunately it is the other way around: The card must be unmounted or 'ejected' before you unplug it. Otherwise there is a risk that it will get corrupted.

The problem is that the data, that you write to the drive is buffered in RAM, and will be written slowly (with low priority) to the drive by the system. If/when you unmount the drive or 'eject' it, the system will hurry up to flush the buffers and finish writing the data to the drive. You will get a notice that the process has finished, and after that you can unplug the drive without problems.

---

### Post by xaver88 on 2022-11-02
Thank you for the fast reply

if I unmount it, it stil is there with

mmcblk1      179:0    0 29.7G  0 disk
&#9492;&#9472;mmcblk1p1  179:1    0 29.7G  0 part


also after removing the card.

How to tell the OS, that the card is not there any more
if I insert the card again I can mount it
but if I use a different card, it's not possible to mount
also if there is no card at boot, the 
mmcblk1      179:0    0 29.7G  0 disk
&#9492;&#9472;mmcblk1p1  179:1    0 29.7G  0 part
is not be there after inserting the card

---

### Post by sudodus on 2022-11-02
After successful unmounting the drive is still there, but no longer mounted. You can see that the column for mountpoint is empty. Then it is possible to unplug the drive.

'Ejecting' the drive means both unmounting and turning it off, so that it is no longer seen (by lsblk and similar tools).

[hr][/hr]
Edit: If the drive is still seen after unplugging, something is wrong. Maybe the easiest way to fix it is to reboot the computer. It might also work to run the following commands (without reboot)
```

sync
sudo partprobe

```
Edit 2: It is also possible that the file system in the partition of the drive is corrupted. If this is the case you should

- try to copy any files that you want to keep to some other drive
- create a fresh partition table, partition and file system on the drive (alias format the drive).

---

### Post by xaver88 on 2022-11-02
turning off is not possible, because the reader is on the pcb of the NanoPi Neo Air
after sync and sudo partprobe I have only
mmcblk1      179:0    0 29.7G  0 disk
at lsblk
inserted an other card and also use sync and sudo partprobe I didn't get back the
[COLOR=#000000]&#9492;&#9472;mmcblk1p1 179:1 0 29.7G 0 part
so how to tell the system to refresh it?

Also reboot the Nano is no option[/COLOR]

---

### Post by xaver88 on 2022-11-02
> **sudodus said:**
> 

Edit 2: It is also possible that the file system in the partition of the drive is corrupted. If this is the case you should

- try to copy any files that you want to keep to some other drive
- create a fresh partition table, partition and file system on the drive (alias format the drive).

I need the card outside and the Nano should work with a new one for logging some datas
The card is not corrupted (at the moment)

---

### Post by sudodus on 2022-11-02
It would help me (and others who can help you) if you download the [system-info script](https://github.com/UbuntuForums/system-info/), run it and let it upload the output to a pastebin. Then put a link to the pastebin into a reply here. The output contains data about the computer hardware and operating  system.

---

### Post by xaver88 on 2022-11-02
have nopastebin installed

but that the system-ino.txt

Starting the Ubuntu Forums 'system-info' Report: 2022-11-02  20:50:45 CET (+0100)
	Part of the Ama-gi Project
	Version: 02.00-03, Script Date: 2022.10.29


---------------------------------------------------------------
Main Complaint: test
Problem Description:  sd not found
---------- General Computer Specifications:


  --- Computer/CPU Information from '/proc/cpuinfo' --- 
ARMv7 Processor rev 5 (v7l)


------------------ SMBIOS Information from '/sys/class/dmi/id/' 
No SMBIOS information found


Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
	This would check / have checked if SecureBoot was enabled or not, 
	and checks if the system BIOS was UEFI or Lagacy only BIOS, 
	but package mokutil was not installed. If you would like to check
	this information, please install 'mokutil' and rerun script.


---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:            491          46         312           2         132         422
Swap:           511           0         511


---------- Swap Information:
  --- Info from 'fstab'
/mnt/512MB.swap    none    swap    sw    0    0


  --- Info from '/proc/swaps'
Filename				Type		Size	Used	Priority
/mnt/512MB.swap                         file		524284	0	-2


  --- System Swapiness Settings
Valid swappiness settings are from 10 - 60 . 
Current setting in '/proc/sys/vm/swappiness': 60 
Current configuration setting in '/etc/sysctl.conf file: 




---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]


  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS


  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000


For more detailed wireless information, get and run the script at [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) 


  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: NanoPi-NEO-Air-51




---------- Storage Controller Information From 'lspci':
No storage controller found. Check in 'lsusb' section.
May be USB or SD storage.


---------- File system specs from 'df -h':
Filesystem     Type     Size  Used Avail Use% Mounted on
overlay        overlay  6.1G  674M  5.4G  11% /
/dev/mmcblk0p1 vfat      40M   12M   29M  30% /boot
/dev/mmcblk1p1 vfat      30G   15M   30G   1% /kdts/sd


---------- Disk/Partition Information From 'fdisk':
Disk /dev/mmcblk1: 29.7 GiB, 31914983424 bytes, 62333952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device         Boot Start      End  Sectors  Size Id Type
/dev/mmcblk1p1 *     8192 62333951 62325760 29.7G  c W95 FAT32 (LBA)


Disk /dev/mmcblk0: 7.3 GiB, 7818182656 bytes, 15269888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x35da405b


Device         Boot   Start      End  Sectors  Size Id Type
/dev/mmcblk0p1        49152   131071    81920   40M 83 Linux
/dev/mmcblk0p2       131072  2516991  2385920  1.1G 83 Linux
/dev/mmcblk0p3      2516992 15269887 12752896  6.1G 83 Linux


Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


---------- Disk/Partition Information From 'lsblk':
NAME          SIZE FSTYPE LABEL    MOUNTPOINT MODEL
mmcblk1      29.7G                            
|_mmcblk1p1  29.7G vfat            /kdts/sd   
mmcblk0boot0    4M                            
mmcblk0boot1    4M                            
mmcblk0       7.3G                            
|_mmcblk0p2   1.1G ext4   rootfs              
|_mmcblk0p3   6.1G ext4   userdata            
|_mmcblk0p1    40M vfat   BOOT     /boot      
   ------- 'lsblk' information continued ...
NAME         HOTPLUG PARTUUID                             UUID
mmcblk1            1                                      
|_mmcblk1p1        1                                      829F-FF2E
mmcblk0boot0       1                                      
mmcblk0boot1       1                                      
mmcblk0            1                                      
|_mmcblk0p2        1 35da405b-02                          ff313567-e9f1-5a5d-9895-3ba130b4a864
|_mmcblk0p3        1 35da405b-03                          269e9152-5cb6-035b-9c34-e1ed87cca310
|_mmcblk0p1        1 35da405b-01                          555E-7B30


---------- Mount Details of '/etc/fstab':
/dev/mmcblk0p1    /boot vfat defaults 0 0
/mnt/512MB.swap    none    swap    sw    0    0


---------- Current Mount Details of 'mount':
/dev/mmcblk0p1 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro)
/dev/mmcblk1p1 on /kdts/sd type vfat (rw,relatime,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro)


For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair) 


---------- USB Information from 'lsusb -t -v':
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=musb-hdrc/1p, 480M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=ohci-platform/1p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-platform/1p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-platform/1p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ehci-platform/1p, 480M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ehci-platform/1p, 480M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-platform/1p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-platform/1p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-platform/1p, 480M


---------- Video Details from 'lspci':
No formal GPU found. Check in other places for a framebuffer.


   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Desktop is: <Not Populated> 
The Current Desktop Session is: <Not Populated> 
The Current Session Type is: <No Graphics Session Type Loaded> 
The Current Display Manager is: <Not Configured>
The Current Desktop Theme: Is not set, this is Console Based.
The Current Virtual TTY's being used are:
	TTY#	Used By
	tty1	login
	ttyS0	login
	tty1	bash
	ttyS0	bash
	ttyS0	system-info
	ttyS0	system-info
	ttyS0	sed
	ttyS0	system-info
	ttyS0	ps
	ttyS0	awk


---------- Sound Device Information From 'lspci':
No sound devices found. Also check in 'lsusb' section.


For more detailed audio information, get and run the script at: [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) 


---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':


Sources List:
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) xenial main restricted universe multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) xenial-security main restricted universe multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) xenial-updates main restricted universe multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) xenial-backports main restricted universe multiverse


Sources List from SourcesD:


---------- KeyMap and Locale Information from from various sources:
   --- Keymap Info from 'setxkbmap' ----
# KEYBOARD CONFIGURATION FILE


# Consult the keyboard(5) manual page.


XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""


BACKSPACE="guess"


   --- Locale Info from 'localectl' ----
   System Locale: LANG=en_US.UTF-8
       VC Keymap: n/a
      X11 Layout: us
       X11 Model: pc105


---------- Other Details from 'Various':
The current kernel version is:       4.14.111 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 16.04.2 LTS 


Estimated Installation Date:         1970-01-01 
Original Installation Media: Cannot determine which ISO this was installed from (yet). 
The Installer Log Directory does not exist. 
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'


   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-16.04, Kernel Version: 4.15.0.142.137


   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-16.04 was not detected. Please check 
kernel version to verify range


   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).


   --- User Installed Package List:
acl
adduser
adwaita-icon-theme
alsa-base
alsa-utils
apt
at-spi2-core
base-files
base-passwd
bash
bc
binutils
bluetooth
bluez
bsdutils
busybox
busybox-initramfs
bzip2
ca-certificates
colord
colord-data
console-setup
console-setup-linux
coreutils
cpio
cpp
cpp-5
crda
cron
dash
dbus
dbus-x11
dconf-gsettings-backend
dconf-service
debconf
debianutils
device-tree-compiler
dh-python
diffutils
distro-info-data
dmsetup
dns-root-data
dnsmasq
dnsmasq-base
dpkg
e2fslibs
e2fsprogs
exfat-fuse
exfat-utils
figlet
file
findutils
fontconfig
fontconfig-config
fonts-dejavu-core
ftp
fuse
g++
g++-5
gawk
gcc
gcc-5
gcc-5-base
gcc-6-base
gcr
gir1.2-glib-2.0
git
git-man
glib-networking
glib-networking-common
glib-networking-services
gnome-keyring
gnupg
gpgv
grep
gsettings-desktop-schemas
gzip
hddtemp
hicolor-icon-theme
hostapd
hostname
htop
humanity-icon-theme
i2c-tools
ifupdown
indicator-application
init
init-system-helpers
initramfs-tools
initramfs-tools-bin
initramfs-tools-core
initscripts
insserv
iperf3
iproute2
iptables
iputils-arping
iputils-ping
isc-dhcp-client
isc-dhcp-common
iso-codes
iw
kbd
keyboard-configuration
klibc-utils
kmod
krb5-locales
language-pack-en
language-pack-en-base
less
libacl1
libapparmor1
libappindicator3-1
libapt-inst2.0
libapt-pkg5.0
libasan2
libasn1-8-heimdal
libasound2
libasound2-data
libassuan0
libatk-bridge2.0-0
libatk1.0-0
libatk1.0-data
libatm1
libatomic1
libatspi2.0-0
libattr1
libaudit-common
libaudit1
libavahi-client3
libavahi-common-data
libavahi-common3
libbfb0
libblkid1
libbluetooth3
libboost-filesystem1.58.0
libboost-system1.58.0
libbsd0
libbz2-1.0
libc-bin
libc-dev-bin
libc6
libc6-dev
libcaca0
libcairo-gobject2
libcairo2
libcap-ng0
libcap2
libcap2-bin
libcc1-0
libcolord2
libcolorhug2
libcomerr2
libcroco3
libcryptsetup4
libcups2
libcurl3-gnutls
libdatrie1
libdb5.3
libdbus-1-3
libdbus-glib-1-2
libdbusmenu-glib4
libdbusmenu-gtk3-4
libdconf1
libdebconfclient0
libdevmapper1.02.1
libdns-export162
libdpkg-perl
libdrm-amdgpu1
libdrm-freedreno1
libdrm-nouveau2
libdrm-radeon1
libdrm2
libedit2
libegl1-mesa
libelf1
libepoxy0
liberror-perl
libexif12
libexpat1
libexpat1-dev
libfdisk1
libffi6
libfftw3-double3
libfile-fcntllock-perl
libfontconfig1
libfreetype6
libfribidi0
libfuse2
libgbm1
libgcc-5-dev
libgcc1
libgck-1-0
libgcr-3-common
libgcr-base-3-1
libgcr-ui-3-1
libgcrypt20
libgd3
libgdbm3
libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-common
libgirepository-1.0-1
libgl1-mesa-dri
libglib2.0-0
libglib2.0-data
libgmp10
libgnutls-openssl27
libgnutls30
libgomp1
libgpg-error0
libgphoto2-6
libgphoto2-l10n
libgphoto2-port12
libgpm2
libgraphite2-3
libgssapi-krb5-2
libgssapi3-heimdal
libgtk-3-0
libgtk-3-bin
libgtk-3-common
libgudev-1.0-0
libgusb2
libharfbuzz0b
libhcrypto4-heimdal
libheimbase1-heimdal
libheimntlm0-heimdal
libhogweed4
libhx509-5-heimdal
libicu55
libidn11
libieee1284-3
libindicator3-7
libiperf0
libisc-export160
libisl15
libiw30
libjbig0
libjpeg-turbo8
libjpeg-turbo8-dev
libjpeg8
libjson-glib-1.0-0
libjson-glib-1.0-common
libk5crypto3
libkeyutils1
libklibc
libkmod2
libkrb5-26-heimdal
libkrb5-3
libkrb5support0
liblcms2-2
libldap-2.4-2
libllvm3.8
liblocale-gettext-perl
libltdl7
liblz4-1
liblzma5
libmagic1
libmbim-glib4
libmbim-proxy
libmirclient9
libmircommon5
libmirprotobuf3
libmm-glib0
libmnl0
libmount1
libmpc3
libmpdec2
libmpfr4
libmulticobex1
libncurses5
libncursesw5
libndp0
libnetfilter-conntrack3
libnettle6
libnewt0.52
libnfnetlink0
libnl-3-200
libnl-genl-3-200
libnl-route-3-200
libnm0
libnma-common
libnma0
libnotify4
libobexftp0
libopenobex2
libopts25
libp11-kit-gnome-keyring
libp11-kit0
libpam-gnome-keyring
libpam-modules
libpam-modules-bin
libpam-runtime
libpam-systemd
libpam0g
libpango-1.0-0
libpangocairo-1.0-0
libpangoft2-1.0-0
libpcap0.8
libpcre3
libpcsclite1
libperl5.22
libpipeline1
libpixman-1-0
libpng12-0
libpolkit-agent-1-0
libpolkit-backend-1-0
libpolkit-gobject-1-0
libpopt0
libprocps4
libprotobuf-lite9v5
libproxy1v5
libpython-dev
libpython-stdlib
libpython2.7
libpython2.7-dev
libpython2.7-minimal
libpython2.7-stdlib
libpython3-stdlib
libpython3.5
libpython3.5-minimal
libpython3.5-stdlib
libqmi-glib1
libqmi-proxy
libreadline6
librest-0.7-0
libroken18-heimdal
librsvg2-2
librsvg2-common
librtmp1
libsamplerate0
libsane
libsane-common
libsasl2-2
libsasl2-modules
libsasl2-modules-db
libseccomp2
libsecret-1-0
libsecret-common
libselinux1
libsemanage-common
libsemanage1
libsepol1
libsigsegv2
libslang2
libsmartcols1
libsoup-gnome2.4-1
libsoup2.4-1
libsqlite3-0
libss2
libssl1.0.0
libstdc++-5-dev
libstdc++6
libsystemd0
libtasn1-6
libthai-data
libthai0
libtiff5
libtinfo5
libtxc-dxtn-s2tc0
libubsan0
libudev1
libusb-0.1-4
libusb-1.0-0
libustr-1.0-1
libuuid1
libvpx3
libwayland-client0
libwayland-cursor0
libwayland-egl1-mesa
libwayland-server0
libwind0-heimdal
libwrap0
libx11-6
libx11-data
libx11-xcb1
libxau6
libxcb-dri2-0
libxcb-dri3-0
libxcb-present0
libxcb-render0
libxcb-shm0
libxcb-sync1
libxcb-xfixes0
libxcb1
libxcomposite1
libxcursor1
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxi6
libxinerama1
libxkbcommon0
libxml2
libxmuu1
libxpm4
libxrandr2
libxrender1
libxshmfence1
libxtables11
libxtst6
linux-base
linux-libc-dev
linux-sound-base
locales
login
lsb-base
lsb-release
make
makedev
manpages
manpages-dev
mawk
mime-support
mobile-broadband-provider-info
modemmanager
mount
multiarch-support
nano
ncurses-base
ncurses-bin
ncurses-term
net-tools
netbase
network-manager
network-manager-gnome
network-manager-pptp
notification-daemon
ntp
obexftp
openobex-apps
openssh-client
openssh-server
openssh-sftp-server
openssl
p11-kit
p11-kit-modules
passwd
patch
perl
perl-base
perl-modules-5.22
pinentry-gnome3
policykit-1
policykit-1-gnome
ppp
pptp-linux
procps
psmisc
python
python-apt-common
python-dev
python-gi
python-gobject
python-gobject-2
python-minimal
python-pil
python-pip
python-serial
python-smbus
python2.7
python2.7-dev
python2.7-minimal
python3
python3-apt
python3-chardet
python3-distupgrade
python3-minimal
python3-pkg-resources
python3-requests
python3-six
python3-update-manager
python3-urllib3
python3.5
python3.5-minimal
read-edid
readline-common
rename
rfkill
rsync
sed
sensible-utils
sgml-base
shared-mime-info
ssh-import-id
sudo
systemd
systemd-sysv
sysv-rc
sysvinit-utils
tar
tcpd
time
toilet
toilet-fonts
tzdata
u-boot-tools
ubuntu-keyring
ubuntu-mono
ubuntu-release-upgrader-core
ucf
udev
udhcpc
udhcpd
update-manager-core
update-motd
usb-modeswitch
usb-modeswitch-data
usbutils
ussp-push
util-linux
vim
vim-common
vim-runtime
wget
whiptail
wireless-regdb
wireless-tools
wpasupplicant
x11-common
xauth
xdg-user-dirs
xkb-data
xml-core
xz-utils
zlib1g


   --- Installed Snap Package List:
Snap is not installed


   --- Installed Flatpak Package List:
Flatpak is not installed


Currently logged in User(s):
NAME     LINE         TIME         COMMENT
pi       ttyS0        Nov  2 20:49
pi       tty1         Nov  2 20:49


The User running this script was: pi
uid=1000(pi)
gid=1000(pi)
groups=1000(pi),27(sudo),44(video),101(input)


The 'system-info' script was booted from a Live Image Environment (LIE).


The 'system-info' script seems to be running locally


The Linux Kernel Command Line use to boot was: 
console=ttyS0,115200 earlyprintk root=/dev/mmcblk0p2 rootfstype=ext4 rw rootwait fsck.repair=yes panic=10 fbcon=map:0  data=/dev/mmcblk0p3 snd-soc-core.pmdown_time=3600000


---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    gsettings
    mokutil
    curl
    pastebinit
    nc


*** End Of Report ***

---

### Post by sudodus on 2022-11-02
```

The current kernel version is: 4.14.111
--- Operating System Release Description --- 
[COLOR="#FF0000"]The current release description is: Ubuntu 16.04.2 LTS  # this version of Ubuntu has passed end of life and receives no updates, not even security updates[/COLOR]
 
 ---------- File system specs from 'df -h':
Filesystem Type Size Used Avail Use% Mounted on
[COLOR="#FF0000"]overlay overlay 6.1G 674M 5.4G 11% /  # it seems you are running a (persistent?) live system[/COLOR]
/dev/mmcblk0p1 vfat 40M 12M 29M 30% /boot
[COLOR="#FF0000"]/dev/mmcblk1p1 vfat 30G 15M 30G 1% /kdts/sd  # it is still mounted according to df[/COLOR]

---------- Disk/Partition Information From 'lsblk':
NAME SIZE FSTYPE LABEL MOUNTPOINT MODEL
mmcblk1 29.7G
[COLOR="#FF0000"]|_mmcblk1p1 29.7G vfat /kdts/sd  # it is still mounted according to lsblk [/COLOR]
mmcblk0boot0 4M
mmcblk0boot1 4M
mmcblk0 7.3G
|_mmcblk0p2 1.1G ext4 rootfs
|_mmcblk0p3 6.1G ext4 userdata
|_mmcblk0p1 40M vfat BOOT /boot 

---------- Mount Details of '/etc/fstab':
/dev/mmcblk0p1 /boot vfat defaults 0 0
/mnt/512MB.swap none swap sw 0 0


---------- Current Mount Details of 'mount':
/dev/mmcblk0p1 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,io charset=ascii,shortname=mixed,utf8,errors=remount-ro)
[COLOR="#FF0000"]/dev/mmcblk1p1 on /kdts/sd type vfat (rw,relatime,gid=100,fmask=0002,dmask=0002,allow_u time=0020,codepage=437,iocharset=ascii,shortname=m ixed,utf8,errors=remount-ro)
[/COLOR]
The Linux Kernel Command Line use to boot was:
console=ttyS0,115200 earlyprintk root=/dev/mmcblk0p2 rootfstype=ext4 rw rootwait fsck.repair=yes panic=10 fbcon=map:0 data=/dev/mmcblk0p3 snd-soc-core.pmdown_time=3600000

```

Try to unmount the partition **[FONT=Courier New]/dev/mmcblk1p1[/FONT]**

```

sudo umount /dev/mmcblk1p1
# and if necessary from the mountpoint
sudo umount /kdts/sd

```

Check with
```

df -h
lsblk -f

```

and if necessary
```

sudo partprobe
df -h
lsblk -f

```

**If problems, show what warnings or error message you get when trying to unmount.**

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by xaver88 on 2022-11-02
unmounting is no problem
the problem is to get the card recognized, if it is changed or not inserted during the boot up

---

### Post by sudodus on 2022-11-02
So it is not automounting when not inserted during boot. Then try to mount it manually

```

sudo mkdir -p /kdts/sd
sudo mount /dev/mmcblk1p1 /kdts/sd

```

If problems, show what warnings or error message you get when trying to unmount.

[hr][/hr]
Edit: If the card is not recognized (for example by lsblk) 5 seconds after inserting, there is a real problem. I would reboot and check if there is some (temporary?) problem due for some previous action or incident. If you cannot reboot, I'm sorry, but I have not more ideas.

***Let us hope that someone else will chip in and help you with some fresh ideas.***

---

### Post by xaver88 on 2022-11-02
after booting without inserted card:
```

pi@NanoPi-NEO-Air-51:~$ sudo mkdir -p /kdts/sd
pi@NanoPi-NEO-Air-51:~$ sudo mount /dev/mmcblk1p1 /kdts/sd
mount: special device /dev/mmcblk1p1 does not exist

```

in my opinion the system does not (yet) know the SD Card at this moment
also "lsblk" didn't show mmcblk1...

so I think a need some "command" to tell the system to "look" for the card

---

### Post by sudodus on 2022-11-02
I think you are right. My only tip is using 
```

sudo partprobe

```
(or reboot ...)

---

### Post by xaver88 on 2022-11-02
reboot is working but not possible, because the litte Nano is a datalogger 
I tried sudo partprobe, but no success

is there any way to tell the system to reload the driver (or something else which is done during boot to recogize the SD)

---

### Post by sudodus on 2022-11-03
***Let us hope that someone with new ideas will chip in and help you :-P***

[hr][/hr]
The only remaining thing that I can suggest is to ***replace the old operating system with a current version of Ubuntu***, and hope that it will manage to identify the drive after unmounting and unplugging and replugging and then mount the partition on it again.

---

### Post by TheFu on 2022-11-08
The output posted seems to be from the lsblk command, which is helpful, but it reports devices by default, not mounts.
There are a number of ways to see what is mounted and what isn't.  I typically use 'df -Th' to see mounted storage ... with some -x options to filter out a bunch of crap.

Some desktops come setup to automatically mount new storage. That almost always uses sub-optimal mount options, so I disable it on all my systems, plus, the power to mount is the power to destroy, so being very careful is prudent.  If you disable the file manager and udev to prevent gvfs from mounting foreign storage without specific user action, then it won't automatically be remouted once the umount/eject is run.  I'll leave the research for why allowing storage to magically mount on any computer is a terrible idea, regardless of OS.  Of course, there are people who disagree for some reason.  I won't guess why.

BTW, on Unix/Linux systems "automount" usually means to use the automountd daemon which requires an admin to configure. On Linux, we use 'autofs' as the method to safely, automate mounts with full mount option control.  This is very different than the inferior gvfs method that Gnome DEs use.  The gvfs team really should have used existing mount tools, but decided against it long ago, probably due to their goal of having GTK+ cross platform with Windows and MacOS and perhaps some phone devices.  gvfs has been a problem at least that long for many file systems.  I think some fixed got into the code that addressed some issues along the way.

Ah ... you are only the EOL 16.04 release.  You get all the issues with gvfs. Congratulations.  Running EOL OSes on any network isn't a good idea. If you don't have ESM, I'd stop and move to a supported LTS release for the hardware.  Probably 20.04 or 22.04 and make plans to upgrade to a new LTS every 3-4 yrs.  That's the usual cadence for Ubuntu LTS migrations. The server has 5 yrs of support for the core packages.

BTW, thanks for saying the hardware. I didn't recognize it immediately, but had an idea it was an SBC.  Those act different in some ways due to the hardware differences than the x86-64 that we deal with constantly around here. I've don't use other storage on my ARM SBCs. They pull data over the network as needed. Locally, the storage holds the OS and configs to access and process remote data.  I think on SBCs, the default install assumes an SD card, so it doesn't write logs to the storage. This is to minimize the writing which would wear out the SD storage much faster.  You can change the setting in the /etc/systemd/journald.conf file so it writes to storage.  Be certain to turn that off once you have enough logs to solve this.

Helpful storage aliases:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

Also, devices change based on the order they are seen. This is why using either the UUID or a manually configured LABEL on the file system is much preferred.  Those won't change between boots.  There are lots of other methods that can be used to find aliases for a specific device.  Take a look in /dev/disk/by-* for all the options.  Down there are symbolic links to the correct device name for that specific boot.  for example, 
```
$ ll /dev/disk/by-label/
total 0
drwxr-xr-x 2 root root  80 Oct 29 11:06 ./
drwxr-xr-x 7 root root 140 Oct 29 11:06 ../
lrwxrwxrwx 1 root root  10 Nov  5 00:02 home -> ../../dm-2
lrwxrwxrwx 1 root root  10 Nov  5 00:02 root -> ../../dm-0
```

dm-0 and dm-2 devices can change between boots, but  /dev/disk/by-label/root and   /dev/disk/by-label/home will not.

---

### Post by xaver88 on 2023-01-21
> **sudodus said:**
> I think you are right. My only tip is using 
```

sudo partprobe

```
(or reboot ...)


with partprobe i get the message

Error: Partition(s) 1 on /dev/mmcblk1 have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

Any other way without reboot?

---

### Post by sudodus on 2023-01-21
I think reboot is the easiest and most reliable solution.

The alternative is to stop the processes that use the partition and clean up things, but if things are corrupted, it might be difficult. Of course, you can always unplug the card even if it is not unmounted, and *hope* that things will work well afterwards.

---

