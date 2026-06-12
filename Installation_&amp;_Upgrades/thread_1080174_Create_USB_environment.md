---
title: "Create USB environment"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by phil101 on 2009-02-25
Hello all you wonderful ubuntu people - I wonder if you might be able to apply your collective experience and knowledge to advise me on the best way to address a particular issue I'm having.

I am an ubuntu user of about a year and finding it an excellent OS - I've not booted into Windows for about 6 months and living quite happily without Mr Gates et al.

I use Ubuntu on the desktop, but have recently been investigating Xubuntu on a USB key as a 'system on any PC' kind of thing - I have successfully installed xubuntu (8.10) on a USB key and customised it in a number of ways, including creating a custom usplash, desktop, applications and preferences.  This is good, but what I'd like is a way of cloning this so I can store it and retrieve at a later basis.

I've taken a couple of approaches:

1.  Create a direct copy of the USB key using dd:

sudo dd if=/dev/sdb1 of=epk4.iso

This produces an ISO, but when I write it to a CD it doesn't boot - presumably because it doesn't have any of the ISOLINUX stuff.


2.  Create ISO using mkisofs:

sudo mkisofs -D -o myiso.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table /media/disk/

/media/disk is my USB key.  I think this should work and has the benefit that it's an ISO and not modifiable - I only need it read-only.  But this fails with 'can't find directory for boot.cat' - I'm not sure whether these are a absolute file paths (and need to be in the directory you are running the command from) other whether they are just identifiers for the mkisofs command.

My feeling is that if I can just produce a bootable ISO of this environment I can store that and use it to create the bootable cd at any time.


3.  I've also investigated the Ubuntu Customisation Kit (UCK) - which has a bunch of scripts which will unpack an existing LiveCD, allow you to modify the filesystem and then repack it into an iso.  Following the scripts here ([http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/api.html](http://uck.svn.sourceforge.net/viewvc/uck/trunk/uck/docs/html/api.html)) I have done the following:

Get UCK (Ubuntu customisation kit) and the xubuntu live cd iso file.

Make a 'livecdtemp' directory somewhere there is a free 5Gb and a 'remaster' directory under that.  Then go to the livecdtemp directory and run the command:
	sudo uck-remaster-unpack-iso [path to]/xubuntu-8.10-desktop-i386.iso remaster/

This unpacks the ISO into the remaster directory - note that you now have a remaster-iso directory under remaster.  Now run the command:
	sudo uck-remaster-unpack-rootfs remaster/

This unpacks the root filesystem which is compressed using SquashFS.  Now there is a remaster-root directory under 'remaster'.  Rename this directory remaster-root-old and create a new directory called remaster-root.  Into this new directory copy the backed up filesystem of the keyosk and make sure the permissions are the same.  Now run the command:
	sudo uck-remaster-pack-rootfs remaster/

But then I get:

Updating files lists...                                                                
chroot: cannot run command `dpkg-query': Exec format error                             
Cannot update filesystem.manifest, error=126  


So, after all that I still don't have a repeatable version of this environment that i can store and recreate at the drop of a hat.

Any advice or recommendations on doing it another way would be very much appreciated.  FYI - I have considered just using G4L or Acronis to make a copy of the whole drive and recreate, but I'm particularly interested in it being a bootable ISO with a squashed file system (SquashFS) - as I can then get the image size down from 1.9Gb to about 800Mb, and the ISO burning tools don't require a boot cd to create a copy.

Thanks
Phil

---

