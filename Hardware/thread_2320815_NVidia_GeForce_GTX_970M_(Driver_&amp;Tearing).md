---
title: "NVidia GeForce GTX 970M (Driver &amp;Tearing)"
date: 2016-04-17
forum: Hardware
---

### Post by anon24 on 2016-04-17
This last week, I did some serious searching on how to get the right driver for my video card. I ended up going to:

System Settings > Software and Updates> Additional Drivers

There, I found that Ubuntu "auto-detected" that there was an NVidia card. 

I went ahead and let it install whatever driver it suggested.

I selected: 352.63 (proprietary, tested)

I noticed that this is not the most current driver for this card.

OR IS IT (for Ubuntu, but not for other systems)?

Is there anyone that can confirm this?


I noticed lots of screen tearing both before and after I installed this driver.

It does the tearing during non-stressful activities.

Such as browsing this forum.

Any tips on getting rid of said tearing?

---

### Post by anon24 on 2016-04-19
Please, someone help me with this! I got the most up to date driver and that didn't make a difference.

---

### Post by oldfred on 2016-04-19
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
Note that too new of a drive can be an issue:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Always be sure to purge one driver before attempting to install another. Conflicts will create issues as proprietary driver install does not uninstall old driver completely. 
       
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx
# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.
# While you're at it upgrade libvdpau & nvidia-settings 
    
If another driver already installed:
#What is installed
dkms status 
sudo apt-get remove --purge nvidia-*

---

### Post by anon24 on 2016-04-20
dkms status
bbswitch, 0.7, 4.2.0-35-generic, x86_64: installed
nvidia-361, 361.42, 4.2.0-35-generic, x86_64: installed

When I look on the Nvidia website, it says that my card is supported for this driver.

Could you confirm this?


What does legacy refer to?

---

### Post by oldfred on 2016-04-20
For older nVidia cards, nVidia stops updating a driver and calls it legacy. It may occasionly get a security update, but no updates. 
Old card would not support features in new cards/chips & driver then does not have to work around for old cards.
Nvidia has several legacy drivers for different generations of cards. 

If newer card/chip newer driver should be correct, but did you see comments on ppa site with newest video drivers?

---

### Post by SeijiSensei on 2016-04-20
When, exactly, do you experience this tearing?  If you see it while watching videos, make sure you're using a player that supports "vdpau" like mplayer and mpv do.  If you install SMPlayer, you can use Options > Preferences > General > Video and choose the vdpau option there.

In Flash, open a video into full-screen view, then right-click on the image.  Check the "hardware acceleration" box if it is unchecked.

---

### Post by anon24 on 2016-04-20
~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - third-party non-free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GM204M [GeForce GTX 970M]
modalias : pci:v000010DEd000013D8sv00001462sd00001103bc03sc02i00
vendor   : NVIDIA Corporation
driver   : nvidia-352 - third-party free
driver   : nvidia-352-updates - third-party non-free
driver   : nvidia-361 - third-party free
driver   : nvidia-355 - third-party free
driver   : nvidia-358 - third-party free
driver   : nvidia-364 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

I tried to purge the drivers, but they keep showing up as if I haven't purged.



I experience the tearing during any and all activities. Though, it's worst when I try to play any games on Steam. There is no option to right click on Amazon Prime video or other streaming sites. What then?


Also, I noticed that something called bumblebee keeps being mention in reference to Nvidia and Ubuntu. Is that something that I need?

---

### Post by oldfred on 2016-04-20
This is just a list of available drivers:
ubuntu-drivers devices

To see what is installed:
#What is installed
dkms status 

If it comes back blank, then no proprietary driver installed.

---

### Post by anon24 on 2016-04-20
~$ dkms status
bbswitch, 0.7, 4.2.0-35-generic, x86_64: installed
nvidia-361, 361.42, 4.2.0-35-generic, x86_64: installed


I installed the new driver. I'm still getting severe tearing. How do I upgrade libvdpau?

---

### Post by oldfred on 2016-04-20
What version of Ubuntu?

I am using Ubuntu 16.04  with an older nVidia card and just the open source driver.
Link above to ppa shows older versions of libvdpau for older distributions.

libvdpau (1.1.1-3ubuntu1) xenial; urgency=medium

Do not know if that would be an issue or not.

---

### Post by anon24 on 2016-04-20
I am using 15.10

Do I have to "build something" for libvdpau? All I found on that page for ppa was "source code". 

How do I install something like this? Is there an easier way to do it? 

Could the libvdpau upgrade be the reason for the tearing?

---

### Post by mc4man on 2016-04-20
Most m cards are optimus & if so &  using the nvidia drivers then there is no vsync. So there will be tearing, generally everywhere.
This is when using the default method of thru nvidia-prime. It's possible that bumblebee isn't affected as such, no clue as never used.

(- there is a simple workaround for this in 14.04, not so simple in 15.10/16.04

---

### Post by anon24 on 2016-04-20
I'm not even sure what bumblebee is. I am a beginner when it comes to Ubuntu. 

Am I using the wrong driver? Is that what you're saying?

Any suggestions?

---

### Post by anon24 on 2016-04-20
Ok, so, I updgraded libvdpau and also my Nvidia driver. I am still getting tearing. 

I noticed when I switched to Intel for power saving, I didn't get any tearing when I played Half-Life Source. 

As soon as I switched to Nvidia for performance mode, the tearing returned.

I've seen some posts about Triple Buffering?

Is that something that might help?

---

### Post by anon24 on 2016-04-21
$ cd $DEV_HOME
$ git clone git://anongit.freedesktop.org/vdpau/libvdpau
$ cd libvdpau/
[COLOR=#ff0000]$ ./autogen.sh --prefix=$NVD[/COLOR]
$ make
$ make install

As soon as I got to the autogen command, I was met with this error:

~/libvdpau$ ./autogen.sh --prefix=$NVD
./autogen.sh: 9: ./autogen.sh: autoreconf: not found

---

### Post by SeijiSensei on 2016-04-22
Try running "sudo apt-get install build-essential autoconf".  Also you'll need to run "make install" as "sudo make install" since the script will be writing into privileged directories.

---

### Post by anon24 on 2016-04-22
Ok, I did that and it seemed to install something. Make install did not work. What do I do next?

machinicsnobbery@Computatron:~$ sudo make install
make: *** No rule to make target 'install'.  Stop.
machinicsnobbery@Computatron:~$ cd $DEV_HOME
machinicsnobbery@Computatron:~$ git clone git://anongit.freedesktop.org/vdpau/libvdpau
fatal: destination path 'libvdpau' already exists and is not an empty directory.
machinicsnobbery@Computatron:~$ cd libvdpau
machinicsnobbery@Computatron:~/libvdpau$ sudo make
make: *** No targets specified and no makefile found.  Stop.
machinicsnobbery@Computatron:~/libvdpau$ sudo make install
make: *** No rule to make target 'install'.  Stop.

---

### Post by anon24 on 2016-04-24
Sooooooo, does anyone have any ideas on this?

---

### Post by anon24 on 2016-04-26
I hate to keep bumping this, but it's really frustrating. I've done my own searching and nothing that I've tried works. Would someone please help me shed some light on this?

---

### Post by oldfred on 2016-04-27
Did you see this:
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes) 

> LLVM-3.8 enables AVX512 on all 6th generation Intel Core CPUs  ("Skylake") when it should be enabled only on server CPU's. This causes  the user session to fail to start when Mesa llvmpipe driver is used.  This should happen only when the system has a separate GPU which isn't  natively supported by open source drivers. 



Work around is to install updates when installing.

       xenial: invalid opcode when using llvmpipe 
[https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156](https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156)

---

### Post by anon24 on 2016-04-27
Are you saying that I need to reinstall Ubuntu? Ubuntu is working fine. 

It  boots up with both Intel and Nvidia. It's just that when I boot with  Nvidia, the battery lasts for about two seconds unplugged and there is  major tearing.

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-mono cli-common gnome-icon-theme libdbus-glib1.0-cil
  libdbus-glib2.0-cil libdbus1.0-cil libdbus2.0-cil libgconf2.0-cil
  libgdata2.1-cil libgdiplus libgif7 libgkeyfile1.0-cil libglib2.0-cil
  libgtk-sharp-beans-cil libgtk2.0-cil libgudev1.0-cil
  libjavascriptcoregtk-1.0-0 libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib4.5-cil libmono-data-tds4.0-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-data4.0-cil
  libmono-system-drawing4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-numerics4.0-cil libmono-system-runtime-serialization4.0-cil
  libmono-system-security4.0-cil libmono-system-servicemodel-internals0.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libnewtonsoft-json5.0-cil libnotify0.4-cil libtaglib2.1-cil
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwnck-common libwnck22
  mono-4.0-gac mono-gac mono-runtime mono-runtime-common mono-runtime-sgen
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  firefox firefox-locale-en gir1.2-soup-2.4 language-selector-common
  language-selector-gnome liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libsoup-gnome2.4-1 libsoup2.4-1 oxideqt-codecs
  python3-distupgrade thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 110 MB of archives.
After this operation, 6,312 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 language-selector-gnome all 0.165.1 [18.7 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 language-selector-common all 0.165.1 [214 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-release-upgrader-gtk all 1:16.04.14 [9,322 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-release-upgrader-core all 1:16.04.14 [29.2 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-distupgrade all 1:16.04.14 [104 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox amd64 46.0+build5-0ubuntu0.16.04.2 [45.0 MB]
Get:7  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64  firefox-locale-en amd64 46.0+build5-0ubuntu0.16.04.2 [595 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libsoup2.4-1 amd64 2.52.2-1ubuntu0.1 [269 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libsoup-gnome2.4-1 amd64 2.52.2-1ubuntu0.1 [4,982 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gir1.2-soup-2.4 amd64 2.52.2-1ubuntu0.1 [24.7 kB]
Get:11  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64  thunderbird-locale-en amd64 1:38.7.2+build1-0ubuntu0.16.04.1 [350 kB]
Get:12  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64  thunderbird amd64 1:38.7.2+build1-0ubuntu0.16.04.1 [33.3 MB]
Get:13  [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64  thunderbird-gnome-support amd64 1:38.7.2+build1-0ubuntu0.16.04.1 [8,538  B]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main  amd64 thunderbird-locale-en-us all 1:38.7.2+build1-0ubuntu0.16.04.1  [10.1 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqt-qmlplugin amd64 1.14.7-0ubuntu1 [167 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqtquick0 amd64 1.14.7-0ubuntu1 [262 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqtcore0 amd64 1.14.7-0ubuntu1 [28.7 MB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 oxideqt-codecs amd64 1.14.7-0ubuntu1 [541 kB]
Fetched 110 MB in 1min 17s (1,418 kB/s)                                        
(Reading database ... 184321 files and directories currently installed.)
Preparing to unpack .../language-selector-gnome_0.165.1_all.deb ...
Unpacking language-selector-gnome (0.165.1) over (0.165) ...
Preparing to unpack .../language-selector-common_0.165.1_all.deb ...
Unpacking language-selector-common (0.165.1) over (0.165) ...
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a16.04.14_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:16.04.14) over (1:16.04.12) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a16.04.14_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:16.04.14) over (1:16.04.12) ...
Preparing to unpack .../python3-distupgrade_1%3a16.04.14_all.deb ...
Unpacking python3-distupgrade (1:16.04.14) over (1:16.04.12) ...
Preparing to unpack .../firefox_46.0+build5-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox (46.0+build5-0ubuntu0.16.04.2) over (45.0.2+build1-0ubuntu1) ...
Preparing to unpack .../firefox-locale-en_46.0+build5-0ubuntu0.16.04.2_amd64.deb ...
Unpacking firefox-locale-en (46.0+build5-0ubuntu0.16.04.2) over (45.0.2+build1-0ubuntu1) ...
Preparing to unpack .../libsoup2.4-1_2.52.2-1ubuntu0.1_amd64.deb ...
Unpacking libsoup2.4-1:amd64 (2.52.2-1ubuntu0.1) over (2.52.2-1) ...
Preparing to unpack .../libsoup-gnome2.4-1_2.52.2-1ubuntu0.1_amd64.deb ...
Unpacking libsoup-gnome2.4-1:amd64 (2.52.2-1ubuntu0.1) over (2.52.2-1) ...
Preparing to unpack .../gir1.2-soup-2.4_2.52.2-1ubuntu0.1_amd64.deb ...
Unpacking gir1.2-soup-2.4 (2.52.2-1ubuntu0.1) over (2.52.2-1) ...
Preparing to unpack .../thunderbird-locale-en_1%3a38.7.2+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../thunderbird_1%3a38.7.2+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.7.2+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.7.2+build1-0ubuntu0.16.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.14.7-0ubuntu1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.14.7-0ubuntu1) over (1.13.6-0ubuntu1) ...
Preparing to unpack .../liboxideqtquick0_1.14.7-0ubuntu1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.14.7-0ubuntu1) over (1.13.6-0ubuntu1) ...
Preparing to unpack .../liboxideqtcore0_1.14.7-0ubuntu1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.14.7-0ubuntu1) over (1.13.6-0ubuntu1) ...
Preparing to unpack .../oxideqt-codecs_1.14.7-0ubuntu1_amd64.deb ...
Unpacking oxideqt-codecs:amd64 (1.14.7-0ubuntu1) over (1.13.6-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up language-selector-common (0.165.1) ...
Setting up language-selector-gnome (0.165.1) ...
Setting up python3-distupgrade (1:16.04.14) ...
Setting up ubuntu-release-upgrader-core (1:16.04.14) ...
Setting up ubuntu-release-upgrader-gtk (1:16.04.14) ...
Setting up firefox (46.0+build5-0ubuntu0.16.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (46.0+build5-0ubuntu0.16.04.2) ...
Setting up libsoup2.4-1:amd64 (2.52.2-1ubuntu0.1) ...
Setting up libsoup-gnome2.4-1:amd64 (2.52.2-1ubuntu0.1) ...
Setting up gir1.2-soup-2.4 (2.52.2-1ubuntu0.1) ...
Setting up thunderbird (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-gnome-support (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en-us (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up oxideqt-codecs:amd64 (1.14.7-0ubuntu1) ...
Setting up liboxideqtcore0:amd64 (1.14.7-0ubuntu1) ...
Setting up liboxideqtquick0:amd64 (1.14.7-0ubuntu1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.14.7-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```

---

### Post by oldfred on 2016-04-27
Please use code tags on any long or terminal output.
Easy to add code tags with forum's advanced editor and the # icon.

If you have done updates then it should have run all the downloads required. So reinstall not required.

---

### Post by anon24 on 2016-04-28
[INDENT][B]This was posted on Nvidia forums today about the tearing issue:
[/B]

*"*_snizzo said_:'Yes  please. Having no VSync and playing on linux simply means having the  card to overheat like hell. My pc shut down suddenly because of  temperature too high.

I'd say without vsync my gpu is at risk of being fried.'[COLOR=#006400]

[/COLOR][/INDENT]
[I][COLOR=#006400]
_fratti said_: 'Indeed, the lack of blocking vsync can cause serious bugs such as Qt's  render loop running way too fast for animated GUI elements, which also  means excessive heating of the hardware.'[/COLOR]

[/I]


_dirkfunk said_: 'Any word on when there will be a fix for the terrible tearing a lot of us are seeing with Optimus in Ubuntu 16.04?'[I]

[COLOR=#006400]
_fratti said_: 'When the Xorg patches get merged, released, and then backported by your  Ubuntu package maintainer. 

The latter may never happen at all, so worst  case you'll be waiting until the next Ubuntu release.

Nvidia themselves can't tell you when any of those things happen, since it depends entirely on Xorg and Ubuntu.[/COLOR]'"[/I]

---

### Post by anon24 on 2016-05-01
Has anyone heard anything about this? Supposedly, Nvidia is saying that this tearing issue is entirely due to something on Ubuntu's side of things.

---

### Post by Jack Harper on 2016-05-01
I have an Asus Rog laptop with that graphics card and I dont have tearing, driver is 361.42, desktop and playing videos works fine, tested a Steam game as well and did not notice tearing, I dont have onboard graphics enabled though, can you disable your onboard graphics in BIOS?

---

### Post by anon24 on 2016-05-02
I'm not sure how to go about that. My BIOS has been all weird since I updated to 16.04. It isn't an option in the Grub2 menu anymore. How would I go about disabling Intel?

Also, has anyone been using Bumblebee with 16.04 or anything that allows use of the dual system?

---

### Post by Jack Harper on 2016-05-03
> **anon24 said:**
> I'm not sure how to go about that. My BIOS has been all weird since I updated to 16.04. It isn't an option in the Grub2 menu anymore. How would I go about disabling Intel?

Also, has anyone been using Bumblebee with 16.04 or anything that allows use of the dual system?

Most systems have F2 or F10 as keys used for entering BIOS (repeatedly press when you reboot). Not all versions of BIOS support disabling onboard graphics though, I was lucky that in my case manufacturer disabled it so I didnt have to use Bumblebee, if you cant disable onboard graphics you will likely need Bumblebee:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Should be easy to install. You said you updated to 16.04 LTS, maybe you should also try doing a clean installation, upgrades sometimes dont go perfectly. I have a clean installation of 16.04 LTS with latest driver from the repository which is 361.42 and I dont have tearing. Do you use two monitors perhaps?

---

### Post by anon24 on 2016-05-07
Would my issue maybe be fixed by using the "Do not use this device option" as depicted?

edit: This did not fix the issue, the same tearing happens.

If the tearing was being caused by Intel and Nvidia being utilized at the same time, then what is the point of the "Performance" or "Power Saving" modes in XSettings?

I thought that this selected one or the other?

Bumblebee caused my system to not be able to boot into Ubuntu, so I'm not trying that again unless there is evidence that it works.

Any other ideas about this? I'd really like to get this solved. 

It's a real thorn in my side, being a gamer and all.

---

### Post by oldfred on 2016-05-07
Perhaps these issues, (grasping at straws)

 [http://askubuntu.com/questions/752743/ubuntu-16-04-skylake-6th-generation-screen-flickering](http://askubuntu.com/questions/752743/ubuntu-16-04-skylake-6th-generation-screen-flickering)
16.04 Intel Skylake (6th gen) CPU and an NVIDIA GPU bug & work around
[https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156](https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156)

---

### Post by anon24 on 2016-05-07
I'm pretty sure that neither of those is the issue. My issue is clearly tearing and not random flickering. I don't see any random lines just pop up on the screen when I have an idle desktop. It only happens when there is movement occurring such as: scrolling, gaming, watching videos.

The second issue mentioned, they say, "When you encounter this bug, Unity/Compiz will fail to start..." And I'm using Ubuntu right now, so that's not the issue either.

---

### Post by anon24 on 2016-05-11
A little more detailed info on my laptop:

 MSI GS70 2QE Stealth Pro
Processor: Intel Core i7-4710HQ
Graphics: Nvidia GM204 [GeForce GTX 970M]
Driver Version: 361.42

I really like Ubuntu and I want to keep using it... 
But this issue is such a deal breaker.
It's pretty much the only thing that makes me want to have a Windows partition.
As of now, I only have Ubuntu installed. I'm considering going back to Windows. :/


Please, there has to be someone out there who knows what's going on with this!

---

### Post by anon24 on 2016-05-13
This is from a thread on the Nvidia forum titled:
Vsync issue Nvidia Prime (UX32VD with GT620 M)
-------------------------------------------------------------------------
[B]_frMage said_: So what's going on with these patches, guys? It seems from other threads like everyone got the new driver up and   running, while I miserably failed to do so and even fail to understand   the current state of affairs with prime and linux. Is the fix in the   main distros now? Does it work? How can I download and install it   properly? What do I have to do

_fratti said_: Hi, the current situation is like this:
[/B]
[LIST]
[*]** The kernel-side patches are merged and released in kernel 4.5.** 
[*]** The Xorg-server patches have not yet been merged** 
[*]** The fixes on the nvidia binary driver have not yet been released, as far as I'm aware ** 
[/LIST]
[B]Since bullet point 3 is a proprietary driver, even if you were to apply  the patches to Xorg yourself, you'd not be able to try it out. We're  essentially just waiting for the Xorg patches to be mainlined.

As for mainstream distros, the thing to look out for so far is whether  they ship at least kernel 4.5. We'll know which Xorg version you need  once the patches get merged.

_dbelyakin said_: Unfortunately, there are no one who reviews this patches.. Give it some time. Getting patches merged can take a bit.[/B]
-------------------------------------------------------------------------
So, I feel like I've kind of been brushed off about this issue on the Nvidia forum. There has to be something else that can be done, right? Is there anyone that can describe what is going on in layman's terms? I explained my situation in detail and they seem to think that this "patch" will fix my issue.

---

### Post by anon24 on 2016-05-16
Hello, hello, hello... Is anyone out there, out there, out there?

---

### Post by mc4man on 2016-05-16
> **anon24 said:**
> Hello, hello, hello... Is anyone out there, out there, out there?
As I said before tearing on mobile nvidia  optimus setups can be removed in 14.04 very easily.  (that's 14.04.1/2/3 images,  14.04.4 image is more difficult, ie. same as 16.04, which while it can be done, see screen, I think the Intel drivers are better, particularly for accelerated video playback

Figure at least another 6 months on the prime patches ..

---

### Post by anon24 on 2016-05-17
Thanks for the response, I really appreciate it. I've decided to just reinstall Windows on my system. MSI sells recovery USB drives for $35, which is pretty fair. I figure, I'll reinstall Windows, then do a dual boot and use Ubuntu primarily for web browsing.

---

### Post by Donnylink on 2016-05-23
[FONT=arial]Hello, 

I have read through your posts on this forum and I am too suffering from screen tearing. I was wondering weather you could answer a few questions first.

1) does your machine use optimus/intel and nvidia?

My laptop only has nvidia and not intel and I do not suffer from tearing with compositing enabled. There is also a handy line for people with just nvidia cards that eliminates tearing without using compositing, yet it can give some performance issues with games, some latency issues. 

[/FONT][FONT=arial]You then need to add the following line to the "Screen" section of the opened Xorg configuration file:
[/FONT]
[FONT=arial] [/FONT][FONT=arial]Option  "metamodes" "nvidia-auto-select +0+0 { ForceCompositionPipeline = On }"

If you do use optimus graphics, there are a few ways to not get tearing, you could just install the proprietary drivers, you can then switch graphics chips in nvidia-settings. [/FONT]
Please let me know if you request any help as I am not giving up just yet. I am looking for a solution for mobile G-sync for example which I can't seem to solve yet, still waiting for an answer off nvidia. I have sent them my nvidia log file which they requested. 

Let me know if any of these options work for you. If not, we could maybe look for another solution?

---

### Post by anon24 on 2016-08-27
I'm bringing this thread back to life. I uninstalled ubuntu for a while and went back to a single boot of Windows 10 because this issue was so annoying. 

As soon as I saw this, I reinstalled ubuntu. I'm hoping that this issue is finally fixed and that I can say goodbye to Windows for the most part.

I'm wondering if someone can help me make sense the conclusions that Nvidia representative agoins came to. Did they fix the Vsync / tearing issues or not?

[https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/8](https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/8)

[https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1](https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/1)

OR... Have any of you tried this new Nvidia beta? Does it work?

---

### Post by zer010 on 2016-08-29
Since this is the newest Optimus thread I found, I guess I can ask here.  I have an HP dv6 with an i3 and a 650M.  I used to use bumblebee back on 14.04 around the time of 14.04 till perhaps 15.10(?).  It worked fine for the most part, but since I upgraded with a clean install, as I always do, I went through the motions of setting up everything as I had before and after a reboot, I was met with a black screen for a login. I had tried to follow whatever guide I could find to solve the problem, but the only thing that seemed to work was ditching any nvidia drivers and just settling for the integrated Intel. In fact, it's what I'm still doing to this day because I really don't feel like going through all that again, even reinstalling several times.  

So, after a lengthy blogpost, my questions are this: Has anything changed regarding Optimus since 16.04? Is there any definitive guides on how to install Prime or bumble bee?  In recent users' experience, what works better?  

Since I'll be moving from kubuntu 16.04 to xubuntu 16.04 (unrelated), I'm willing to check out a few things for some help as I plan on reinstalling anyways.

---

### Post by anon24 on 2016-08-29
> **zer010 said:**
> So, after a lengthy blogpost, my questions are this: Has anything changed regarding Optimus since 16.04? Is there any definitive guides on how to install Prime or bumble bee?  In recent users' experience, what works better?

Prime simply doesn't work with 16.04 *yet* is the short answer. I have tried Bumblebee on both 15.10 and 16.04 and I got the black screen as well. I asked on the Nvidia forum because pretty much no one is responding on here about this subject. What the Nvidia representative said was this:

"**It requires an X server that hasn't been released yet, making it  difficult to get set up for the time being. You need an X server built  from Git commit 2a79be9, and Linux kernel 4.5. When Xorg 1.19 releases,  it should start going out to distributions and will be much easier to  set up. The issue with lack of synchronization wasn't just an issue in the NVIDIA driver, but also the X server and kernel.**" 

Here is the conversation if you want to chime in:
[https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/8](https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/8)

Basically until Xorg releases 1.19, we're out of luck... And they don't have a release date posted as of yet. Unless another user on here has any other information that I am unaware of about that "difficult set up" that the Nvidia representative is talking about.

---

### Post by zer010 on 2016-09-03
How did it all go so backwards since 15.04 I wonder?  I know bumblebee has had some development since then, but it just seems that it's too far behind or that resources (not enough apparently) have been pooled into Prime.  This whole situation stinks. I'm glad Nvidia is at least trying to help out where they can, but unfortunately, there is a whole generation of machines out there that are effectively crippled using linux.  I.. I guess the only thing for someone like me to do is wait or get a new machine (more waiting).

Thanks for the reply, anon.

---

### Post by anon24 on 2016-09-03
Aw man, I'm sure sorry. I feel your pain. I've wanted to completely migrate to Ubuntu and ditch Windows entirely. This completely keeps
 me from doing that.

I agree that it is great to see that NVIDIA is putting such effort into this. Our frustrations are heard somewhere at least.

I know that it's going to be a while, a few months at least, but I'm hopeful that NVIDIA and Xorg will get this sorted out. When I first put this thread up people in the community here did try pretty hard to help me. It all gives me hope, I love the open source community because of this kind of support.

I used to have a MacBook Pro and there are still threads that I wrote from years ago on Apple forums that went unanswered. Worry not, there is still hope!

---

### Post by sudodus on 2016-09-05
I have good news for you. Bucky Ball, one of our moderators, is running nvidia 970 successfully with an Ubuntu 16.04 LTS based system. See the following link:

[Re: Ubuntu 14.04 LTS installation stuck (on loading dots)](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433)

I guess it should work well to start from the Ubuntu 16.04.1 LTS iso file. If you have some incompatible hardware in the motherboard, for example built in graphics (the stuff that needs bumblebee), maybe it is possible to turn that off.

---

### Post by zer010 on 2016-09-07
You're absolutely right about how helpful the linux community, and more specifically, the ubuntu community really is.  I'm sure it'll work out eventually. As these optimus cards start to decline in marketshare, I'm sure nvidia will be more willing to let loose some more info. If it's gonna be a legacy card, the last thing they need is bad legacy. lol

---

