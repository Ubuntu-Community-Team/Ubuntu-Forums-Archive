---
title: "Upgrade 9.04--&gt;9.10 Suggestion Request"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by larry on 2009-10-29
Dear All,
I am currently running Ubuntu 9.04 on my laptop. I would like to upgrade to 9.10 via apt-get and terminal.
I have a few questions
(1) See my source list at the end of this post. Should I simply change jaunty to karmic and run apt-get update followed by apt-get dist-upgrade?
Also: will karmic backports be available immediately?
(2)I read something about the switch from ext3 to ext4 as the Ubuntu  filesystem in 9.10, is it anything I should worry about?
(3) When installing Ubuntu 9.04, I chose to encrypt my home directory. Does it make any difference for the dist upgrade I have in mind?

Many thanks!

larry


$ more /etc/apt/sources.list

##JAUNTY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty main restricted

##JAUNTY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

##JAUNTY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted

##JAUNTY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted

##JAUNTY COMMUNITY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty universe multiverse

##JAUNTY COMMUNITY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates universe multiverse

##JAUNTY COMMUNITY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed universe multiverse

##JAUNTY COMMUNITY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe multiverse


##JAUNTY BACKPORTS
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

##MEDIBUNTU
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

##CANONICAL
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner

---

### Post by lemming465 on 2009-10-30
The recommended upgrade is *sudo update-manager -d*; it will do a better job than apt-get dist-upgrade, and will take care of the jaunty->karmic APT conversion for you.  I'm not sure if you can run it in an entirely non-GUI mode.  Debian folks would suggest *sudo aptitude full-upgrade* rather than apt-get.

I haven't tried your upgrade-the-encrypted-home directory scenario, but see no reason why it shouldn't work just fine.  As with any upgrade, prudence suggests a backup first, and be doublly sure you have exported and archived your ecryptfs recovery keys off-host as part of that backup.

---

### Post by larry on 2009-10-30
> **lemming465 said:**
>  As with any upgrade, prudence suggests a backup first, and be doublly sure you have exported and archived your ecryptfs recovery keys off-host as part of that backup.

Thanks a lot for your suggestions.
I am a bit ignorant --encryption just sounded good to me-- so: where do I find the my ecryptfs recovery keys?
Cheers

larry

---

### Post by DocEsq on 2009-10-30
It is my understanding that with an upgrade to 9.10 you retain the ext3 file system.  It is when you do a fresh install of 9.10 that you get as default ext4.

As to the encryption, I am not sure whether you get this while you are upgrading or if you have to wait until the upgrade is complete.  If the later, I would wait a while before implementing the encryption to make sure that 9.10 works they way you want as you may not be able to revert back.

Also, always back up before doing any type of upgrade.

Good luck

DocEsq

---

### Post by slakkie on 2009-10-30
> **lemming465 said:**
> The recommended upgrade is *sudo update-manager -d*; it will do a better job than apt-get dist-upgrade, and will take care of the jaunty->karmic APT conversion for you.  I'm not sure if you can run it in an entirely non-GUI mode.  Debian folks would suggest *sudo aptitude full-upgrade* rather than apt-get.

I haven't tried your upgrade-the-encrypted-home directory scenario, but see no reason why it shouldn't work just fine.  As with any upgrade, prudence suggests a backup first, and be doublly sure you have exported and archived your ecryptfs recovery keys off-host as part of that backup.

The -d is not the recommended way of upgrading. You just told him how to upgrade to a development release! Please see the link in my sig.

---

### Post by lemming465 on 2009-11-01
Abject apologies and thanks for the correction; I'll do a better job of reading the man pages and spelunking for existing man pages next time, I promise.  The point I was trying to make is that Ubuntu prefers to use the "update-manager" infrastructure to do upgrades, rather than the obsolescent "apt-get dist-upgrade" (Debian is apparently moving toward "aptitude full-upgrade"?)

---

### Post by lemming465 on 2009-11-01
> where do I find the my ecryptfs recovery keys
Use *ecryptfs-unwrap-passphrase* and copy the result off the computer (e.g. to a USB fob or using pen & paper).  The result is typically 32 hexadecimal (base 16) characters, i.e. 128 bits of key material.  Protect it as well as you protect your login password, because it can be used to decrypt your home directory without logging in as you.  

This is good for disaster recovery (not that we are expecting an upgrade disaster, we're just taking a prudent precaution), but represents a slight security risk.  If you happen to use PGP or S/MIME based file encryption on some other system you could use that to protect the "unwrapped passphrase" by re-encrypting it yourself.  But just keeping good physical control of the USB fob or scrap of paper with the unencrypted form is probably secure enough for most people.

---

### Post by larry on 2009-11-05
> **lemming465 said:**
> Use *ecryptfs-unwrap-passphrase* and copy the result off the computer (e.g. to a USB fob or using pen & paper).  The result is typically 32 hexadecimal (base 16) characters, i.e. 128 bits of key material.  Protect it as well as you protect your login password, because it can be used to decrypt your home directory without logging in as you.  

This is good for disaster recovery (not that we are expecting an upgrade disaster, we're just taking a prudent precaution), but represents a slight security risk.  If you happen to use PGP or S/MIME based file encryption on some other system you could use that to protect the "unwrapped passphrase" by re-encrypting it yourself.  But just keeping good physical control of the USB fob or scrap of paper with the unencrypted form is probably secure enough for most people.

Hi,
This is what I did

$ ecryptfs-wrap-passphrase encryption
Passphrase to wrap: 
Wrapping passphrase: 
Warning: Using default salt value (undefined in ~/.ecryptfsrc)

and then saved the encryption file on my usb stick.
Is that it?
Cheers

larry

---

### Post by lemming465 on 2009-11-13
No, your procedure is for generating a new wrapping key and then feeding it by hand into a brand new ecryptfs setup.  In order to be able to recover your existing home directory files, you need the key it's already using.  Run```
ecryptfs-**un**wrap-passphrase
```

---

