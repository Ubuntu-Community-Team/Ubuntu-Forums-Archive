---
title: "Ubuntu dies after ati-drivers install"
date: 2009-06-08
forum: Hardware
---

### Post by goshanecr on 2009-06-08
Hi all!
I'm install Ubuntu 9.04 x86 on **Dell lattitude D531**. All work fine, but 3D is slow. This laptop have ATI X1200 videocard. I'm install throught *Install/Remove software* ati-drivers. After restart, system got black screen with some color noise. 
I try to load in safe mode, and see /etc/X11/xorg.conf there are only some lines like
```
<device>
    configured device
</device>
.....
``` 
not fglrx, or radeonhd.. 
I try to cp /etc/X11/xorg.conf.safe (with vesa driver) to /etc/X11/xorg.conf it not help. Also i try chanhe vesa to radeon, radeonhd or fglrx this not work.
How i can solve problem?

---

### Post by goshanecr on 2009-06-09
I found on this forum, that older ATI cards like X1200 not supported by proprietary ati-drivers, so how i can revert to default video settings?
In ubuntu /etc/X11/xorg.conf contains something strange lines like configured device and i don't know how properly setup video. Help!!!

---

### Post by blackSP on 2009-06-09
Check the ATI card compatibility list. With a newer card the Catalyst 9.5 drivers run great!

---

### Post by goshanecr on 2009-06-09
As i write in previous post, X1200 - isn't a newer card [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English") <-- here AMD/ATI tells that for X1250 and all products < HD2000 Catalyst 9.3 must be used. But i'm install driver throught ubuntu package management utility, and now system not start in graphics mode. So i need first just answer how i can resolve this issue. Maybe uninstall ati-drivers and change video settings to correct... I can boot only in safe mode.

---

### Post by goshanecr on 2009-06-09
Is this problem so hard that nobody can tell how solve it? Ubuntu - is most user friendly distro... just one click and your system unrecoverable dead?

---

### Post by ZZCheetahZZ on 2009-06-13
same problem here..  i'm a newbie to linux and don't know how to remove the ATI drivers and revert back to default through the safe mode with networking..

---

### Post by gradinaruvasile on 2009-06-13
Boot with the recovery option, select root prompt from the list (its a bit lower)
type

apt-get remove --purge fglrx*

dpkg-reconfigure -phigh xserver-xorg

ctrl-d
resume boot

---

### Post by sadaka on 2009-06-14
I am not sure, but info I have tells that older cards will not work with Janty, since it uses Xorg 1.6, which is not supported by older ATI drivers. Newb myself, though =]

---

### Post by goshanecr on 2009-06-16
> **gradinaruvasile said:**
> Boot with the recovery option, select root prompt from the list (its a bit lower)
type

apt-get remove --purge fglrx*

dpkg-reconfigure -phigh xserver-xorg

ctrl-d
resume boot

Thank's!! This helps me without any problem :)
Maybe you can tell me and others how install ati-drivers version of which supports older cards in Ubuntu 9.04
I think that just download binary driver package from ati site and install it is not best idea.. all software as it possible must be installed throught package manager.. But if exists not official method, i'm and other users i think will be happy read how-to :)

---

### Post by nghalion on 2009-06-24
9.0ello Everyone,

The same happened to me (Ubuntu 9.04 wont start after installing ati packages) and i tried to do what was told here but when i get to the part where i have to put 
"apt-get remove --purge fglrx*
dpkg-reconfigure -phigh xserver-xorg"

I get errors saying xserver-xorg not installed and the operation fails. I'm sorry if i'm confusing but I'm a newbie and didn't get the exact phrases of the error messeges. I'll do that if that helps.

Thanks in advance.
cheers

---

### Post by sadaka on 2009-06-29
I guess, in your case X is missing its configuration files. I know that there is a command smth similar to "blah-blah --reconfigure" to rewrite your conf files to defaults. Can't recall it now, though.

---

### Post by Odemia on 2009-06-29
> **nghalion said:**
> I get errors saying xserver-xorg not installed and the operation fails. I'm sorry if i'm confusing but I'm a newbie and didn't get the exact phrases of the error messeges. I'll do that if that helps.

The first thing to find out is if xserver actually did get removed.
```
aptitude show xserver-xorg
```
If you don't see "State: installed" you will need to install it again.
```
apt-get install xserver-xorg
```
If xserver-xorg is listed as "installed" and dpkg-reconfigure says it is not, try:
```
dpkg-reconfigure -phigh --force xserver-xorg
```
To force debconf to configure X11.
As a last resort make sure /etc/X11 didn't somehow get deleted
```
ls /etc | grep X11
```

Regarding running ATI cards with acceleration I would suggest using Ubuntu 8.04.  It is a LTS (Long Term Support) release.  The Linux community is transitioning to xserver 1.6, and Ubuntu chose to move fairly early with 9.04.  The current fglrx driver sounds a bit like a work in prgress, not sure when ATI will have it's next revision of fglrx out or what graphics cards might be included.  There are a few posts around like [http://ubuntuforums.org/showthread.php?t=1175385](http://ubuntuforums.org/showthread.php?t=1175385) for patching the xserver to work better with fglrx but I haven't seen anything for getting older cards working with fglrx and xserver 1.6.

---

### Post by ssri on 2009-06-29
read my post that tells you how to reconfigure to the opensource radeon drivers for your ati card:

[http://ubuntuforums.org/showpost.php?p=7509489&postcount=13](http://ubuntuforums.org/showpost.php?p=7509489&postcount=13)

---

