---
title: "Ununtu 18.0.4 can't find scanner"
date: 2018-06-05
forum: Hardware
---

### Post by stevecoh1 on 2018-06-05
The [Ubuntu Wiki Page]("https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected") seems to fit my situation, but a crucial piece of information is missing.

I have the epson2 backend enabled (my scanner is "Epson Perfection V300 photo" which is supported.

When I run the **sane-find-scanner** command though, I get this:
```

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8000 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x8008 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x138a/0x0017 at 003:006: Access denied (insufficient permissions)
could not open USB device 0x058f/0x9540 at 003:004: Access denied (insufficient permissions)
could not open USB device 0x0557/0x2213 at 003:012: Access denied (insufficient permissions)
could not open USB device 0x0557/0x8021 at 003:011: Access denied (insufficient permissions)
could not open USB device 0x0409/0x005a at 003:010: Access denied (insufficient permissions)
could not open USB device 0x04b8/0x0131 at 003:015: Access denied (insufficient permissions)
could not open USB device 0x04ca/0x7035 at 003:009: Access denied (insufficient permissions)
could not open USB device 0x8087/0x07dc at 003:008: Access denied (insufficient permissions)
could not open USB device 0x17ef/0x604d at 003:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Note the last paragraph:  running sane-find-scanner as root, does indeed find the scanner.

```
$ sudo sane-find-scanner
[sudo] password for scohen: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x138a, product=0x0017) at libusb:003:006
found USB scanner (vendor=0x04b8 [EPSON], product=0x0131 [EPSON Scanner]) at libusb:003:015
...
```

So it's apparently a permissions issue.  However it's not clear to me what to do to resolve that permissions issue.  Can someone tell me?

---

### Post by stevecoh1 on 2018-06-05
First of all, I asked this [same question]("https://askubuntu.com/questions/364163/how-to-solve-scanner-permissions-issues") five years ago, on Ubuntu 13.04.  D'Oh!  But the answer is different now. It seems to be a question of repositories.

I acquired the proprietary drivers and installed them through a script.  I did not notice that the installation did not succeed.  The following error messages occurred:

```
W: Skipping acquire of configured file 'multiverse/binary-amd64/Packages' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/binary-i386/Packages' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/i18n/Translation-en' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/i18n/Translation-en_US' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/Components-amd64.yml' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-48x48.tar' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/dep11/icons-64x64.tar' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'multiverse/cnf/Commands-amd64' as repository 'http://archive.canonical.com/ubuntu bionic InRelease' doesn't have the component 'multiverse' (component misspelt in sources.list?)
```

I'm not sure what to do about this.  There are several sources on the Net telling you how to set up your repositories in 18.04, for example[ this one]("https://itsfoss.com/things-to-do-after-installing-ubuntu-18-04/").  However, the suggestions made there don't seem to work for me.  This page tells me to go to the "Other Software" tab and click the "Canonical Partners" checkbox:

[IMG]https://4bds6hergc-flywheel.netdna-ssl.com/wp-content/uploads/2017/10/software-repository-ubuntu-17-10.jpeg[/IMG]

But my screen looks different from this and in any event I can't click on the Canonical Partners checkbox.
[ATTACH=CONFIG]279985[/ATTACH]
When I try to click it, the window goes faint and nothing happens.  It seems like this might be a bug in the Software application itself.  

Is there perhaps a way to enable this repository on the command line?  And if I do that would it resolve the errors above?

---

### Post by pqwoerituytrueiwoq on 2018-06-05
My guess is is is something in your sources.list left over from a upgrade
here is my /etc/apt/sources.list file, i did a clean install for 18.04
```
# deb cdrom:[Xubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

I think your issue can be fixed with a udev rule
This a utility i include with the software in my signature:
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2)

---

### Post by HereInOz on 2018-06-11
Try running Simple Scan from a terminal as root:  sudo simple-scan

Worked for me with my V370 scanner.

---

### Post by him610 on 2018-06-12
stevecoh1:

Did you consider running *scanimage -L* from the command line

---

### Post by austinzuffi on 2018-09-29
hi! same here. trying tough to get my V550 working. clean install of 18.04

sane-find-scanner gets access denied
sudo sane-find-scanner shows
```
found USB scanner (vendor=0x138a, product=0x0097) at libusb:001:002
found USB scanner (vendor=0x04b8 [EPSON], product=0x013b [EPSON Scanner]) at libusb:001:010
```
sudo scanimage -L shows "No scanners were identified"

my scanner uses epkowa backend
/etc/sane.d/epkowa.conf: ```
usb 0x04b8 0x013b
```
i have disabled conflicting epson && epson2 in dll.conf
```
#epson
#epson2
```

anyone know a way to test that the backend is linked correctly? the install script from epson created '/etc/sane.d/dll.d/iscan' which reads simply
```
# iscan -- enables the SANE backend(s) required
# Any changes to this file will be lost when upgrading iscan.

epkowa
```
all looks to be in the right place. hoping usb/scanner permission might improve my situation. also want to verify that the epkowa backend is being seen and linked by sane. any expertise is appreciated

---

### Post by trash1464 on 2018-09-30
I have the same problem with an Epson Perfection v600 Photo scanner. 
```

 sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8002 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 008:001: Access denied (insufficient permissions)

```

sane-find-scanner gets access denied
sudo sane-find-scanner shows

```
 sudo sane-find-scanner
[sudo] password for rich: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found USB scanner (vendor=0x04b8 [EPSON], product=0x013a [EPSON Scanner]) at libusb:003:016

```

Again it seems to be an issue with access permissions to USB ports or devices. Hoping someone has a way to set USB permissions. I have been working on this for days now.

---

### Post by austinzuffi on 2018-10-01
ubuntu manpage on sane-usb looks helpful, tho i haven't fully deciphered,> sane-find-scanner  doesn't  list  your  scanner?  Does it work as root? If yes, there is a        permission issue. See the **LIBUSB** section for details.[http://manpages.ubuntu.com/manpages/bionic/man5/sane-usb.5.html](http://manpages.ubuntu.com/manpages/bionic/man5/sane-usb.5.html)

---

### Post by deof on 2018-12-22
I found a way that works for me.

1) Update sources: 
sudo apt-get update

2) Install:libsane 1 (with synaptic)

3) Copy libsane-epkowa files to x86-64 libs:
sudo cp /usr/lib/sane/libsane-epkowa.* /usr/lib/x86_64-linux-gnu/sane/

4) Install your scanner driver ([http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX))

5) Edit /etc/udev/rules.d/79-udev-epson.rules: 
sudo nano /etc/udev/rules.d/79-udev-epson.rules

Add:
# chmod device EPSON group
ATTRS{manufacturer}=="EPSON", DRIVERS=="usb", SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="*", MODE="0777"

6) Reboot

Now I can check that sane-find-scanner it is work.

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 008:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 010:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 009:001: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0161 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc52b at 001:006: Access denied (insufficient permissions)
could not open USB device 0x056a/0x0084 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 001:004: Access denied (insufficient permissions)
found USB scanner (vendor=0x04b8 [EPSON], product=0x013a [EPSON Scanner]) at libusb:001:003
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc50e at 005:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 012:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 011:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.



You can see here [URL="https://askubuntu.com/questions/946198/device-driver-for-epson-v600-perfection/974626#974626"]https://askubuntu.com/questions/946198/device-driver-for-epson-v600-perfection/974626#974626





[/URL]

---

