---
title: "Netbooting jaunty 9.04"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by caliston on 2009-05-05
I'm trying to install 9.04 on a laptop that has no CD, and can't boot from USB.  So I'm using the netbooting method.  I followed the instructions at [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
(I already had a PXE setup, so just tweaked that).

I tried using both netboot.tar.gz and 386/netboot.tar.gz in [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)
as my PXE images.

Ubuntu boots fine, and I select 'expert' installation.  debian-installer launches as you'd expect.

Previously I had put the ubuntu-9.04-desktop-i386.iso on both a USB flash stick, and burnt it to a DVD.  Both were connected to the laptop by USB.  I checked the sha1sum to ensure I'd downloaded the ISO correctly.

In the d-i console setup interface, I choose lots of the extra installer packages.  It goes away and downloads them.  I select 'Detect and mount CD-ROM'.  Go through the options, CD spins for a bit, and it prints the identifier of the CD (something like Jaunty 20090420-1).  But then there's an error of 'failed to read CD-ROM'.  If I press Alt-F4 and look at the console log, it's failing to find a package on the CD.  If I search for the .iso on the USB flash, I get the same result:

iso-scan: Found ISO ./ubuntu9.04.iso on /dev/sdb1
iso-scan: Detected ISO with 'jaunty' (jaunty) distribution
anna-install: Installing apt-mirror-setup
anna-install: Installing apt-cdrom-setup
anna[11547]: DEBUG: retrieving apt-cdrom-setup 1:0.37ubuntu11
cdrom-retriever: error: Unable to find 'pool/main/a/apt-setup/apt-cdrom-setup_0.37ubuntu11_all.udeb'
anna[11547]: WARNING **: package retrieval failed

And indeed, when mounted /cdrom/pool/main only contains directories b,d,f,g,i,l,m,n,o,p,s - no 'a' to be seen.

If I try 'Load installer components from CD' (or 'an installer ISO') I get some further errors:
cdrom-retreiver: warning: Unable to find main/debian-installer/binary-i386/Packages
cdrom-retreiver: warning: Unable to find main/debian-installer/binary-i386/Packages.gz
cdrom-retreiver: warning: Unable to find restricted/debian-installer/binary-i386/Packages
cdrom-retreiver: warning: Unable to find restricted/debian-installer/binary-i386/Packages.gz
...and again it's right, there's only /cdrom/dists/jaunty/[main|restricted]/binary-i386/[Packages.gz|Release]

I also tried the hd-image boot image, and wrote it onto a CompactFlash card which I used in a PCMCIA adaptor.  That booted OK, but there was no way I could tell it I had a CD drive - it would search all my hard drives, but I couldn't work out a way - even by poking around on the command line - to tell it just to use /dev/scd0.  When I put the ISO on a USB stick it found it, but had the same problems as above.

I tried putting mini.iso from the same place as I downloaded netboot.tar.gz - but I just get:
iso-scan: Found ISO ./mini.iso on /dev/sdb1
iso-scan: Not an Ubuntu ISO
and it ignores it (and indeed it just has a boot kernel on it - no dists/ or pool/ trees to be seen)

Since I have it booting, and I don't care where I install from, can I say 'just grab everything from the internet, don't bother about what you have on local drives'?  I'm not bothered if it ignores the ISO completely.


Any suggestions?  My guess would be that the new 'fast installation' system in jaunty has caused some old packages to be thrown out of the installer.  But the netboot image hasn't caught up.

I'd really rather not install Interpid then do an upgrade...

---

### Post by caliston on 2009-05-05
I got it to work, after quite a bit of faffing.  I discovered two understanding/documentation failures:

1. The 'desktop' CD doesn't work with the netboot installer.  You have to use the 'alternates' CD.  That got a lot further, then died with something about a package checksum failed on ttf indic fonts (I don't remember the exact package name).  It's very annoying that if there was an error, there's no way to force the installer to continue (I don't care about indic fonts).  So I had to try another way...

2. The installer asks if you want to load some extra installer packages.  What it doesn't say is that if you choose these you'll be forced to use them.  So if I load the 'search for CDs' option, it'll fail if it searches for CDs and doesn't find one.  It won't allow me to use any installation method.  If I don't tick the 'search for CDs' option, it'll download the packages from the net.  My mistake was to assume that I could fallback or use these two methods together (as apt allows - some packages on CD and the rest from the net).  It's strictly one or the other.

As I had to take a number of goes to get it right, I used apt-proxy on my server to cache the .debs locally.  Saved quite a bit of time and bandwidth.

So, anyway, having managed to tell it to install solely from the network, it worked.  

(Various other issues happened, including grub2 failing to spot my other partitions and me having to get my head around the non-obvious and undocumented new way it's configured, and me managing to get an encrypted filesystem on an encrypted block device because the installer didn't make clear the difference.  Sorted most of them now)

---

