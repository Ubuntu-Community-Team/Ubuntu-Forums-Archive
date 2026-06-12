---
title: "fresh install with encrypted home partition"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by w00ly on 2009-10-29
Hi all. When I setup ubuntu the first time I selected "encrypt home partition" but didnt mess with it further...i dont believe the unwrap command worked properly after installing. So now I'm trying to do a fresh install but on the live cd my home directory doesnt mount. When I try to mount it it says ecryptfs isnt setup properly. How do I do a fresh install and keep my home partition intact and mounted properly?

edit: Solved. Noticed there was also a symlink in the home directory from .Private to /var/lib/ecryptfs so I put my backup copy of that back in place, logged out and back in and it mounted!

---

### Post by apterix on 2009-10-29
**I have the same problem!**

1) Before
I used 9.10 RC and had:
/
/swap
/home (encrypted)

2) I decided to format / and swap
I installed the 9.10 final, formatted / and /swap, and mounted /home

3) When I started my new installation, I get many errors:
OS doesn't recognized my /home
Probably because it's encrypted, but the OS doesn't ask anything.

4) Fine, I can't decrypt my /home

5) I reinstalled my 9.10 ubuntu and used other partition to /home
Now I have:
/
/swap
/home
And /dev/sda3, my OLD HOME.

I need to recovery my partition SDA3 (OLD HOME), but I can't decrypt it.

I installed the cryptsetup and ecryptfs-tools and saw many tutorials, but I can't recovery my partition.

When I mount it, I see:
Access Your Private Data
README.txt

cat README.txt:

```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
```

But any information help me.

When I click two times in "Access Your Private Data", one window open and close automatically.

Help me! I have (or had) more 300gB files in SDA3.

---

### Post by cwbar_1 on 2009-10-29
Check this out.
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by apterix on 2009-10-29
apterix@apterix-pc:/$ mount /dev/sda3 /files
apterix@apterix-pc:/$ sudo mount -t ecryptfs /files/apterix/.Private /files/apterix/Private
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: n
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=5f517565259a1973
**Error mounting eCryptfs: [-2] No such file or directory**
Check your system logs; visit <http://launchpad.net/ecryptfs>

[COLOR=Red]**update:**[/COLOR]
new tutorial: [http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

apterix@apterix-pc:~$ sudo modprobe dm-crypt
apterix@apterix-pc:~$ sudo cryptsetup luksOpen /dev/hda3 crypt1
[B]Command failed: Can not access device

[COLOR=Red]update2:[/COLOR]
[/B]apterix@apterix-pc:~$ sudo mount /dev/sda3 /files/
apterix@apterix-pc:~$ cd /files/
apterix@apterix-pc:/files$ ls
apterix  lost+found
apterix@apterix-pc:/files$ cd apterix/
[B]apterix@apterix-pc:/files/apterix$ ls
Access-Your-Private-Data.desktop  README.txt
apterix@apterix-pc:/files/apterix$ cat Access-Your-Private-Data.desktop [/B]
[Desktop Entry]
Name=Access Your Private Data
GenericName=Access Your Private Data
Exec=/usr/bin/ecryptfs-mount-private
Terminal=true
Type=Application
Categories=System;Security;
**apterix@apterix-pc:/files/apterix$ cat README.txt **
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
apterix@apterix-pc:/files/apterix$

---

### Post by w00ly on 2009-10-29
> **cwbar_1 said:**
> Check this out.
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
The link says
> 
One downside of encryption is that using a separate /home partition is more difficult and there are as of yet no automated tools on the installation CD (alternate or desktop) to automatically preserve and configure your Ecryptfs encrypted /home directories.
 I advise you back up your data, install, then restore your data.
But I dont have another 500gb hd to backup everything (and it would take a while). Is there no way to set it up automatically?

---

### Post by w00ly on 2009-10-29
bump

---

### Post by apterix on 2009-10-30
**SOLVED:**

1) i re-installed UBUNTU 9.10
And select:
/sda1 to /
/sda2 to/swap
/sda3 to /home (my OLD HOME)

2) In the installation, I select "ask password t login and secure partition".
I had to use DESKTOP INSTALL, because ALTERNATE INSTALL doesn't help with this.

3) The system was re-installed and when I logged in the system, my OLD HOME (SDA3) back. :KS
:popcorn::p

---

### Post by w00ly on 2009-10-30
> **apterix said:**
> **SOLVED:**

1) i re-installed UBUNTU 9.10
And select:
/sda1 to /
/sda2 to/swap
/sda3 to /home (my OLD HOME)

2) In the installation, I select "ask password t login and secure partition".
I had to use DESKTOP INSTALL, because ALTERNATE INSTALL doesn't help with this.

3) The system was re-installed and when I logged in the system, my OLD HOME (SDA3) back. :KS
:popcorn::p
ah very nice. I set the partition to mount as home but I didnt see anything about asking for a password which was when I backed out

---

### Post by apterix on 2009-10-30
Pay attention in the last option when you see window when you put username, password etc. Only desktop installation, not alternate cd.

---

### Post by w00ly on 2009-10-30
I have the desktop installation, so just to be sure: this option comes *before* the step where it asks you to verify that everything is correct because it's about to format/erase, correct?
You also seem to know more than me about ecryptfs because when I run ecryptfs-mount-private it says ecryptfs isnt setup properly. So do you know what I have to run in 9.04 so that it is setup properly and can later be accessed by 9.10 and/or it's livecd?

---

### Post by w00ly on 2009-10-30
bump for info on how to get ecryptfs setup right so that when the installer asks for user/pass it'll mount properly and work

---

### Post by w00ly on 2009-10-30
bump again
please help someone i have no idea what i'm doing with the encryption and I dont want to lose all my data :\

---

### Post by w00ly on 2009-10-31
GRR i knew it was a bad idea to try to continue with this but my impatience got the better of me. Installed 9.10, mounted the previous partition as /home, selected "password required to decrypt and mount" in the installer, set the username and password to what they were before and continued. Now of course for whatever reason this didnt work and just as I feared, the home directory has the .desktop file and the readme.txt and is unwritable, rendering the desktop useless FFFFFFUUUUUUUUUUUUUU- 
PLEASE SOMEONE HELP ME!!!!!!!!!!!!!!! I need to be able to use my computer!!!!

---

### Post by w00ly on 2009-10-31
bump

---

### Post by apterix on 2009-10-31
When your Ubuntu start, it say any error?

---

