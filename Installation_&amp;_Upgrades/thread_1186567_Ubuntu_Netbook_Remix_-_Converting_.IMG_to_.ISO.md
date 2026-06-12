---
title: "Ubuntu Netbook Remix - Converting .IMG to .ISO"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Kevlar-Source on 2009-06-13
My fellow users,

I noticed that many people have questions and requests regarding UNR install in a standard PC or in any ssytem but through a CD/DVD instead of USB pen.

After some research, i found a post in a different forum, teaching users how to do it.

I did it, tested it and was successful. Hoping to make some people life easier, allow me to share that info with you all.

[SIZE="4"][COLOR="DarkRed"]**[Begin Of Procedure]**[/COLOR][/SIZE]

**Download the UNR image**

**Place it on your desktop**

**Create a directory to be your ISO root**
[COLOR="Blue"]mkdir unr[/COLOR]

**Create a directory to mount the ubuntu image**
[COLOR="Blue"]mkdir realunr[/COLOR]

**Mount the netbook image**
[COLOR="Blue"]sudo mount -o loop -t vfat ubuntu-9.04-netbook-remix-i386.img realunr/[/COLOR]

**Navigate to the realunr folder and set the option [COLOR="Blue"]show all files[/COLOR] on**

**Copy the files from [COLOR="Blue"]realunr/[/COLOR] to [COLOR="Blue"]unr/[/COLOR] [make sure the [COLOR="Blue"].disk[/COLOR] directory copies, it will apparently not load without it]**

**Rename the folder**
[COLOR="Blue"]syslinux[/COLOR] to [COLOR="Blue"]isolinux[/COLOR]

**Rename the file**
[COLOR="Blue"]isolinux/syslinux.cfg[/COLOR] to [COLOR="Blue"]isolinux/isolinux.cfg[/COLOR]

**Build the ISO file**
[COLOR="Blue"]mkisofs -o ubuntu-9.04-netbook-remix-i386.iso -r -J -l -V "Ubuntu-Netbook-Remix 9.04 i386" -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table unr/[/COLOR]

**Enjoy your brand new Ubuntu Netbook Remix ISO file :)**

**Burn it to a DVD [notice it's size]**

**Do whatever you like with it**

[SIZE="4"][COLOR="DarkRed"]**[End Of Procedure]**[/COLOR][/SIZE]

---

### Post by aysiu on 2009-06-13
If you don't mind getting Ubuntu 8.04 instead of 9.04, you can get an .iso directly:
[http://oem-images.canonical.com/unr/unr-1.0.1.iso](http://oem-images.canonical.com/unr/unr-1.0.1.iso)

---

### Post by Kevlar-Source on 2009-06-14
> **aysiu said:**
> If you don't mind getting Ubuntu 8.04 instead of 9.04, you can get an .iso directly:
[http://oem-images.canonical.com/unr/unr-1.0.1.iso](http://oem-images.canonical.com/unr/unr-1.0.1.iso)

Yes... But, as you mention, in a pre-packed ISO you only have 8.04 available... Not even 8.10... or 9.04...

I wonder why do they only pack LTS...

Cheers.

---

### Post by cardinalx on 2009-09-27
I went through the procedure you outlined above and created an iso which works - thank you! I think quite a few people want to have access to the iso and it seems a bit odd that it isn't provided in a simple manner.
 
Clearly the iso file is extremely similar to the img and it would be a waste of bandwidth to provide an iso as well. However, I think it would be very useful if the guys providing the img also provided an xdelta patch to create the iso, then we could avoid having to go through the above procedure.
 
Having an xdelta patch would mean that we have consistent MD5 sums on the ISO since if I create an iso using your procedure, I suspect the md5 probably won't match the md5 of the someone else creates due to timestamps or whatever. Also the above procedure gives one slight error relating to a file that gets corrupted (a German openoffice dictionary of some sort) - not a problem for me luckily but a concern for next time - will future img files give more errors if this technique is used? 
 
So why not provide an xdelta patch file alongside the img file!
Just for fun I created an xdelta file myself and it comes out at only 115KB!
Providing this file would save all of us a lot of time.
 
The patch can be created by using the following command:
 
$ xdelta delta ubuntu-9.04-netbook-remix-i386.img \
ubuntu-9.04-netbook-remix-i386.iso \
ubuntu-iso-patch
 
This command can be used to create the iso from an img file and patch file:
 
$ xdelta patch ubuntu-iso-patch \
ubuntu-9.04-netbook-remix-i386.img \
ubuntu-9.04-netbook-remix-i386.iso
 
As a bonus for windows users, a windows version of xdelta can be found here: [http://evanjones.ca/software/xdelta.exe](http://evanjones.ca/software/xdelta.exe)
 
If you have any influence with the powers that be.....
 
Hal

---

### Post by cardinalx on 2009-09-27
> **cardinalx said:**
> I went through the procedure you outlined above and created an iso which works - thank you! I think quite a few people want to have access to the iso and it seems a bit odd that it isn't provided in a simple manner.
 
Clearly the iso file is extremely similar to the img and it would be a waste of bandwidth to provide an iso as well. However, I think it would be very useful if the guys providing the img also provided an xdelta patch to create the iso, then we could avoid having to go through the above procedure.
 
Having an xdelta patch would mean that we have consistent MD5 sums on the ISO since if I create an iso using your procedure, I suspect the md5 probably won't match the md5 of the someone else creates due to timestamps or whatever. Also the above procedure gives one slight error relating to a file that gets corrupted (a German openoffice dictionary of some sort) - not a problem for me luckily but a concern for next time - will future img files give more errors if this technique is used? 
 
So why not provide an xdelta patch file alongside the img file!
Just for fun I created an xdelta file myself and it comes out at only 115KB!
Providing this file would save all of us a lot of time.
 
The patch can be created by using the following command:
 
$ xdelta delta ubuntu-9.04-netbook-remix-i386.img \
ubuntu-9.04-netbook-remix-i386.iso \
ubuntu-iso-patch
 
This command can be used to create the iso from an img file and patch file:
 
$ xdelta patch ubuntu-iso-patch \
ubuntu-9.04-netbook-remix-i386.img \
ubuntu-9.04-netbook-remix-i386.iso
 
As a bonus for windows users, a windows version of xdelta can be found here: [http://evanjones.ca/software/xdelta.exe](http://evanjones.ca/software/xdelta.exe)
 
If you have any influence with the powers that be.....
 
Hal
 
For anyone who would like to try my suggested simple method of creating an iso from the img file, I have attached the file 'ubuntu-iso-patch.zip'.
Just extract the file 'ubuntu-iso-patch', put it in the same directory as your downloaded 'ubuntu-9.04-netbook-remix-i386.img' file, then issue the 'xdelta patch ...' command as shown above or if you prefer the windows version of xdelta, make sure its a one-liner:
**xdelta patch   ubuntu-iso-patch   ubuntu-9.04-netbook-remix-i386.img   ubuntu-9.04-netbook-remix-i386.iso**
 
Hal
```
 
The MD5sums are: 
9f8835bec3777e07d21d0b4144250755 *ubuntu-iso-patch
86945e9eb0eefd694726b50ff7883c96 *ubuntu-9.04-netbook-remix-i386.iso
(note my previous comments about consistent MD5 sums)

```

---

