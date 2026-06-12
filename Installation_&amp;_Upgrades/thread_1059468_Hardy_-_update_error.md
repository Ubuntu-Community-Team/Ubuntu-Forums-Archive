---
title: "Hardy - update error"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by mattman85 on 2009-02-03
I just tried running the most recent security updates in 8.04, and I am not sure if they went through properly.

I saw that I had critical updates, and I ran the Update Manager.  I saw that there was an update to the kernel but I'm not sure if it went through successfully.  I didn't have the option to choose the newest kernel (usually, my **/boot/grub/menu.lst** would change to show all of the kernels listed in /boot.  However, when I restarted the computer, I was shown the grub list that I created a couple of weeks ago.

Also, now I'm getting this error message when I try to run the Update Manager:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Does anyone know how to check what all recent updates were applied?  Or what the above error is, and how to fix it? And can anyone tell me what the latest kernel should be?  Right now, I'm using kernel 2.6.24-23-generic and I don't know if that is the latest, or the next-to-most recent...  A lot of questions, but any help is greatly appreciated!

Thanks, all!

---

### Post by mattman85 on 2009-02-05
I have the latest kernel.  my mind was playing tricks on me, and I thought I saw 24 at the end of the kernel version, but it must have been 2.6.24-23.  However, I still can't figure out my issue with the error message..  and there isn't anything in /etc/apt/sources.list that looks like what the error message is saying, so I'm out of ideas..

---

### Post by lucaspr on 2009-02-05
Maybe this will help you solve the errors!

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Your errors are about gpg keys. They are usually very easy to import but a google on your key didn't give any hits!

And since I updated two server yesterday.. with kernel 2.6.24-23-generic I think it is the most recent one for 8.04!

---

### Post by forger on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by xmzx on 2009-03-01
> **forger said:**
> [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

You're a lifesaver.  Thank you.  :D

---

