---
title: "TRUECRYPT and I need help"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by JobeJahova on 2009-10-20
So, I used Fedora 10 for a while and have a 480Gb partition that uses ext4 truecrypt. It is my /home for Fedora 10. I want to switch to Ubuntu but Ubuntu doesn't seem to like the ext4 truecrypt volume.

I've read like 3-4 different How-to's on getting truecrypt to work. One method allowed me to access the truecrypt partition from command line, but not nautilus or anything, and it's a real round-about way of doing things.

I need native Truecrypt support! I tried installing the binary truecrypt package, but the installer is bugged out or something. Here's a screenshot.

btw, it's /dev/sda3 that I need mounted. Eventually, I need it to mount as my /home in Ubuntu.


Attached is a screenshot of the Install button grey-ed out. I tried to download the binary truecrypt package for Ubuntu because truecrypt in not in the repositories. HALP! :confused:

---

### Post by JobeJahova on 2009-10-20
The ext4 truecrypt partition still works when I boot into Fedora 10. It just doesn't work in Ubuntu. Anyone know why or what I need to do?

---

### Post by JobeJahova on 2009-10-21
I am still desprate for help on this.

This is the how-to guide I tried that didn't work:
[http://ubuntuforums.org/showthread.php?t=149561](http://ubuntuforums.org/showthread.php?t=149561)

I downloaded the tar.gz installed for ubuntu from this site:
[http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

It contains a binary file that starts up the ubuntu software installer. According to the instructions, I should just click "Install Package", but for whatever reason, the button that says "Install Package" is grey-ed out. I click it but it doesn't do anything. It's disabled or something.

Someone, please lend me a hand. **Is there any other way I can install this package file?** I'd even try de-packaging it and reading the scripts to manually copy the files in their respective places if I have to.

---

### Post by cbtengr on 2009-10-21
Which version of Ubuntu are you using.  There are two Ubuntu downloads available - x86 & x64(64bit).  I'm on 9.04 and the Ubuntu - x86.deb installed on my system with no problems.  It now is listed in Synaptic post install.  I'm also using it on 8.10 using the same installer.

---

### Post by sgosnell on 2009-10-21
You have to extract the .gz file to a directory.  Then either open a terminal there and type "sudo ./filename", where filename is the name of the binary executable, or open Nautilus and right-click on it and select Run in Terminal.  That executable program gives you the choice of extracting a .deb or .rpm file, and you should select .deb for Ubuntu.  When that extracts, install it with gdebi.  It's a roundabout way of doing it, but that's the way the Truecrypt developers did it, and it's not the fault of Ubuntu or Linux.

---

### Post by JobeJahova on 2009-10-21
I'm on 32-bit Ubuntu 9.04

> **sgosnell said:**
> You have to extract the .gz file to a directory.  Then either open a terminal there and type "sudo ./filename", where filename is the name of the binary executable, or open Nautilus and right-click on it and select Run in Terminal.  That executable program gives you the choice of extracting a .deb or .rpm file, and you should select .deb for Ubuntu.  When that extracts, install it with gdebi.  It's a roundabout way of doing it, but that's the way the Truecrypt developers did it, and it's not the fault of Ubuntu or Linux.

Yes. I did this. I extracted the tar.gz file like I normally would. I then tried several methods of installation. Here's what I have tried:
-> double-click the icon
-> right-click the icon and "open with" "sh"
-> used the console and ran the command "sudo ./truecrypt-6.2a-setup-ubuntu-x86"
-> used the console and ran the command "sudo sh ./truecrypt-6.2a-setup-ubuntu-x86"

All of these methods had the exact same result. The legacy dialog opened and I clicked "Install Treucrypt" button. Then the Software Installer application opened with the "Install Package" button grey-ed out where I can't click it.

Today I made a small discovery.
```

joe@blackwater:/tmp$ gdebi ./truecry*
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
**Breaks exisiting package 'gdecrypt' dependency truecrypt (< 5)**

joe@blackwater:/tmp$ 


```

So... give me a few minutes to remove the gdecrypt package and try again.

---

### Post by JobeJahova on 2009-10-21
:guitar: :popcorn: :guitar: :popcorn: :guitar: :popcorn: :guitar:

```

joe@blackwater:/tmp$ sudo gdebi ./truecry*
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


TrueCrypt
 TrueCrypt is a software system for establishing and maintaining an
 on-the-fly-encrypted volume (data storage device). On-the-fly encryption
 means that data are automatically encrypted or decrypted right before they
 are loaded or saved, without any user intervention. No data stored on an
 encrypted volume can be read (decrypted) without using the correct
 password/keyfile(s) or correct encryption keys. Entire file system is
 encrypted (e.g., file names, folder names, contents of every file,
 free space, meta data, etc).
Do you want to install the software package? [y/N]:y
Selecting previously deselected package truecrypt.
(Reading database ... 176376 files and directories currently installed.)
Unpacking truecrypt (from ./truecrypt_6.2a-0_i386.deb) ...
Setting up truecrypt (6.2a-0) ...


joe@blackwater:/tmp$ 


```

I removed that decrypt package (or whatever it was called) and now I was able to install Truecrypt! wooo time to celebrate!

---

### Post by JobeJahova on 2009-10-21
Still can't mount that partition. What do I do now?

```
joe@blackwater:~$ ls /media
cdrom  cdrom0  ext4  floppy  floppy0
joe@blackwater:~$ sudo mount /dev/sda3 /media/ext4
[sudo] password for joe: 
mount: unknown filesystem type 'crypto_LUKS'
joe@blackwater:~$ 

```

---

### Post by sgosnell on 2009-10-22
What version of Ubuntu do you have installed?  9.04 is the first version to use ext4, and if you have a previous version it won't recognize it, just as Fedora 9 wouldn't.

I've also never tried to mount a truecrypt volume that way.  I've always done it through truecrypt, and let truecrypt take care of the mounting.  Have you tried that?

---

### Post by JobeJahova on 2009-10-24
> **sgosnell said:**
> What version of Ubuntu do you have installed?  9.04 is the first version to use ext4, and if you have a previous version it won't recognize it, just as Fedora 9 wouldn't.

I've also never tried to mount a truecrypt volume that way.  I've always done it through truecrypt, and let truecrypt take care of the mounting.  Have you tried that?

ubuntu 9.04

I'm not sure how to mount through truecrypt. I need this to be a /home partition, just like it is in Fedora 10.

---

### Post by sgosnell on 2009-10-25
Truecrypt is not really designed to mount a full partition, and I've never tried that.  Reading the fine manual might give you more insight into how to do what you want.  You're going to have to input a password somewhere to mount a truecrypt drive, and you don't seem to be doing that in the example you gave.  If you can mount a drive without a password, then what is the use of having it encrypted?

---

### Post by JobeJahova on 2009-10-26
> **sgosnell said:**
> Truecrypt is not really designed to mount a full partition, and I've never tried that.  Reading the fine manual might give you more insight into how to do what you want.  You're going to have to input a password somewhere to mount a truecrypt drive, and you don't seem to be doing that in the example you gave.  If you can mount a drive without a password, then what is the use of having it encrypted?

In fedora, I enter the password while the system boots. I'm not implying that there is no password entered.

---

### Post by sgosnell on 2009-10-26
How are you running Truecrypt during boot on Fedora?  You can set Ubuntu to run programs at boot, through System/Preference/Startup Applications, but I've never tried that.  In Karmic, you can encrypt the /home partition through the kernel, without having to run a separate program, and I think that is going to be a better way to go.

If you want to continue with Truecrypt, try reading [this thread](http://ubuntuforums.org/showthread.php?t=761530), which is a how-to for dual-booting an encrypted volume.  Even if you don't plan to dual-boot, it should help you with mounting the Truecrypt volume.

---

### Post by krimzonstarr on 2009-10-27
This may be naive, but I have an idea for your issue as I have been playing with Truecrypt on XP and Ubuntu for years. Try unencrypting your /home in Fedora and setting Ubuntu to use it also as your /home. Then, once booted in to either distro, use Truecrypt's encrypt filesystem function to encrypt the entire partition. That way, you can boot in to either distro and then mount it through Truecrypt. That would give you functional encryption with the ability to use it through either distro.

I am certain there is a more elegant solution, probably many. Hopefully, better linux pro's can elaborate ;)

---

### Post by JobeJahova on 2009-10-27
> **sgosnell said:**
> How are you running Truecrypt during boot on Fedora?  You can set Ubuntu to run programs at boot, through System/Preference/Startup Applications, but I've never tried that.  In Karmic, you can encrypt the /home partition through the kernel, without having to run a separate program, and I think that is going to be a better way to go.

If you want to continue with Truecrypt, try reading [this thread](http://ubuntuforums.org/showthread.php?t=761530), which is a how-to for dual-booting an encrypted volume.  Even if you don't plan to dual-boot, it should help you with mounting the Truecrypt volume.

Fedora 10 automatically set up the LUKS encrypted partition for me. I didn't do anything special to it. When I installed Fedora 10, I just clicked to make it ext4 and encrypt the partition. Basically, if the Truecrypt application is running on boot (Fedora) then I don't know about it. When it boots, it asks for a password to the /home and continues on like normal.

So, there is a way to un-encrypt the entire /home volume? I'd do that if it's an option. Basically, I need the files on it!

---

### Post by JobeJahova on 2009-10-27
OK. Using some hints from this:
[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

I was able to mount the partition and access the files from GUI.

:popcorn:

This is progress.

Thanks for all the help so far. It has given me a better understanding of this software. Now one step closer.

---

### Post by krimzonstarr on 2009-10-27
> **sgosnell said:**
> How are you running Truecrypt during boot on Fedora?  You can set Ubuntu to run programs at boot, through System/Preference/Startup Applications, but I've never tried that.  In Karmic, you can encrypt the /home partition through the kernel, without having to run a separate program, and I think that is going to be a better way to go.

Ok, I think I got the idea now. He isn't using a Truecrypt volume, rather it is an Ubuntu install attempting to use it's kernel encryption to mount a /home that was encrypted with Fedora's kernel encryption. Perhaps a Fedora Live CD to unencrypt and mount the partition, and remove the encryption then? I am not familiar with Fedora, so I would suggest looking to see if they offer any support for this issue.

Truecrypt is useful for filesystem encryption through it's own program, or creating cabinet-like files that are mountable encrypted filesystems.

---

