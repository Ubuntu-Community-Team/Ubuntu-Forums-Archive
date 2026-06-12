---
title: "KVM / remote X launch / EDID misdetection / randr issues on Karmic"
date: 2009-11-25
forum: Hardware
---

### Post by Church on 2009-11-25
I got CRT monitor connected to my ubuntu 9.10 i386 box with intel integrated video via KVM switch. I cannot login in gdm / start normally X, untill i locally switch off and on again to this box via KVM. Xorg seems lost all ways to force output/mode, and all previous ways/options in other distributions/XF86,Xorg versions seems ignored/deprecated. Tried whatever i could from my previous distributions/X11 versions experience/from googled out&mentioned here in forums, all to no avail.
Options "EnableRandR12" , "DPMS", "IgnoreEDID", "Enable", "PrefferedMode", specifying ModeLine, MergedFB options and all the rest - bye-bye.
When i'm not at work at that box, - i have to drive by car there and perform trick with kvm if i want to start X <grin>
From what it seems here/what i found out googling - if there are problems with EDID detection caused by kvm or display being switched off, there is no way to force output mode and launch X with current Xorg/intel driver versions. I'm guessing, that soon other distributions will move over to newer versions of those and i'll get same issues there aswell.

Maybe someone else has experienced something similar and can can advise me on my options?
 - Should i try to downgrade Xorg? intel driver version? Should i build myself? Should i disable randr support during custom X build?

I just want this box be able to start X with simple config - one specific mode, no matter what is detected/misdetected because of KVM, no matter if monitor is switched off or on.
Preferably without switching distributions. Preferably without connecting monitor directly. Preferably without keeping monitor always on. Preferably without buying ati or nvidia card to be able to use proprietary drivers with enforcable EDID stuff just because xorg/intel developers in current version for sake of user friendliness decided to deprecate/ignore options to set/force something. :( <irony>

---

### Post by Church on 2009-11-26
Downgraded intel driver to 2.6.3,
disabled KMS,
tweaked xorg.conf (as UXA is needed for dri2, but by default this driver uses EXA).

Now all works as i wanted to - even with kvm used, even with monitor switched off, X11&&gdm starts without problems.
```
wget "http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.3-0ubuntu9.3_i386.deb"
sudo dpkg -i xserver-xorg-video-intel_2.6.3-0ubuntu9.3_i386.deb
sudo nano /etc/xorg.conf # added Option "AccelMethod" "UXA" to device section
sudo nano /etc/default/grub # changed variable
# GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"
sudo update-grub2
```

---

### Post by flabdablet on 2010-02-16
Probably a little late to this party, but I just found some [[COLOR="Blue"]_instructions_[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Resolution%20with%20Intel%20graphics%20was%20correct%20in%20Intrepid%20or%20Jaunty%20%28with%20no%20xorg.conf%20configuration%29%20but%20is%20limited%20in%20Karmic") that let me force a resolution with up-to-date Karmic Intel drivers.

I have a flat panel (Acer AL1511) that apparently reports 640x350 as its preferred resolution instead of its native 1024x768. To stop the console framebuffer looking absolutely horrid on this panel, I uninstalled Grub 2, installed Grub, and added kernel options

nomodeset=1 [[COLOR="Blue"]_vga=791_[/COLOR]]("http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3")

to the **# kopt=** line and all the **kernel** lines in /boot/grub/menu.lst. To make the GUI default to the correct resolution, I used a root shell in Recovery mode to do

```
X -configure
mv xorg.conf.new /etc/X11/xorg.conf
vi /etc/X11/xorg.conf
```

and then replaced all of the generated "Display" subsections with

```
        SubSection "Display"
                Modes "1024x768"
        EndSubSection
```

I've submitted a [[COLOR="Blue"]_bug report for the AL1511_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522488") so that it will eventually get fixed with an update, but if you want to use current Intel drivers and still force resolutions for use with KVM switches and whatnot you might want to play with the above.

---

### Post by Church on 2010-05-10
Eek. It's ubuntu 10.04 and only vesa driver for me. To use intel most probably i'll have to give up my KVM switch. That seems simply stupid, as it _was_ possible to use this videocard and this kvm switch with for many years with many different distributions and XFree86/Xorg versions simply by forcing outputs on, and it's only @#$%*( new versions of intel driver that take only what their borked code autodetects and leaves me alongside those who power on PC with monitor switched off out in the cold.

It's wonderful when they (upstream intel-gfx developers) write autodetect code (which borks) for userfriendliness, and even more wonderful when they disable ways to force something to work without their buggy code.
I don't blame ubuntu, most probably all other distributions will see these same problems, when upgrade to new drivers which require kms/edid and other crap that fails to work.
Now i'm gonna search for painless ways to downgrade to intel driver 2.6.3 in 10.04 aswell. Wish me luck <sigh>

---

### Post by Church on 2010-05-10
Everything turned out even better then i initially thought. Finally [*googling*]("http://lists.freedesktop.org/archives/intel-gfx/2009-September/004048.html") turned out [*patch that*]("https://bugs.freedesktop.org/show_bug.cgi?id=14611") makes "Enable" option in monitor section to actually work, not ignored (makes custom modelines working even if no monitor detected as switched on). Option was there in manpage, but since 9.10 time it simply didn't work (before that i wasn't ubuntu user yet, and older Xorg versions in slackware(and probably older ubuntu versions) had no problems forcing output on via now deprecated options like IgnoreEDID/NoDDC and others). Guys on #xorg@irc.freenode told that patch is commited to upstream and probably will make it in xorg xserver 1.8 release. As for those who use intel driver now on ubuntu 10.04 and want for X11 to work with normal acceleration instead of vesa driver even if monitor is switched off during pc boot or with monitor misdetect caused by buggy KVM switch, here is what i did to patch xserver-core:

# I took patch itself from [*this bugreport's Comment #16*]("https://bugs.freedesktop.org/show_bug.cgi?id=14611")
# From [*this article*]("http://tero.tilus.net/rutinat/2009/11/20/ubuntu-karmic-koala-asus-eee-box-and-black-screen/") i took hints how to build in ubuntu custom patched package:
1) getting/installing/preparing sources and build dependancies:
```
sudo su -
mkdir ~/src && cd ~/src
apt-get install dpkg-dev
apt-get source xserver-xorg-core
apt-get build-dep xserver-xorg-core #              (*)
apt-get install devscripts          # contains dch (*)
```
* - here i saved in file list of which "The following NEW packages will be installed:", to later remove on as i don't need all those development packages&includes arround in normal usage.
2) downloaded patch mentioned above and enabled among patches to be aplied:
```
wget "https://bugs.freedesktop.org/attachment.cgi?id=25110" \
  -O xorg-server-1.7.6/debian/patches/201_force-output.patch
echo "201_force-output.patch" >> xorg-server-1.7.6/debian/patches/series
```
3) tagged build, built needed packages, installed them, cleaned up temporary build dir:
```
dch -i "bump version"
dch -l '~church' "tag this local"
dpkg-buildpackage -rfakeroot -uc -b
cd ..
dpkg -i xserver-xorg-core_1.7.6-2ubuntu8~church1_i386.deb \
  xserver-common_1.7.6-2ubuntu8~church1_all.deb
cd .. && rm -rf ~/src
```
4) Disabled KMS (kernel mode setting) in boot loader (grub2 here) config, and generated/tweaked Xorg config file to include generated with cvt resolution ([*from this article*]("https://wiki.ubuntu.com/X/Config/Resolution")):
a) changed boot parameters by adding "nomodeset" to GRUB_CMDLINE_LINUX_DEFAULT="quiet" variable, and rerun bootloader reconfiguration:
```
sudo nano -w /etc/default/grub
sudo /usr/sbin/update-grub2
```
b) generated modeline with cvt command:
```
cvt 1600 1200 75
[I]# 1600x1200 74.98 Hz (CVT 1.92M3) hsync: 94.09 kHz; pclk: 204.75 MHz
_Modeline "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync_[/I]
```
c) generated Xorg basic config, copied it in right place, and added modeline in this configfile:
```
sudo su -
Xorg -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf
nano -w /etc/X11/xorg.conf
```
```
[I]Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "ViewSonic"
        ModelName    "P810 21"
        _HorizSync    30.0 - 94.0_
        _VertRefresh  50.0 - 160.0_
_Option "Enable" "true"_
_Modeline "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync_
EndSection
...
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     24
_Modes "1600x1200_75.00"_
        EndSubSection
EndSection[/I]
```
5) You can 'lock' these particular versions from being upgraded with sudo apt-get upgrade or via regular updates applet via:
a) GUI:
eg. System/Administration/Synaptic Package Manager
Quick Search - xorg-core / select - xserver-xorg-core
Package>Lock Version (and same for xserver-common)
b) CLI (haven't tried this, hints from [*this link*]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")):
```
dpkg --list|egrep 'xorg-core|xserver-common' # to see installed versions
sudo su -
echo 'xserver-xorg-core hold'|dpkg --set-selections
```
6) removed newly installed build dependancies noted in step (1.):
```
dpkg -r all_the_packagenames separated_with_spaces
```

Now i'm using current intel driver from ubuntu 10.04 with forced mode and don't need to fight arround dependancy conflict when downgrading xorg-intel to 2.6.3 from ubuntu 9.3 as i had fixed that previously in ubuntu 9.10.

TODO: rtfm/try/play with mode/output forcing as boot param with actually using KMS with something from [*this*]("http://bbs.archlinux.org/viewtopic.php?pid=715630") or [*this*]("http://nouveau.freedesktop.org/wiki/KernelModeSetting") article ..

---

