---
title: "Encyrption programs for Ubuntu?"
date: 2008-10-08
forum: General Help
---

### Post by Aero-Z on 2008-10-08
Hello,

I have Ubuntu Server edition and I'd like to encrypt the hard drive. Is it possible? Which software? How?

Thanks

---

### Post by justleen on 2008-10-08
have a look at [http://www.truecrypt.org/](http://www.truecrypt.org/)
or  [http://luks.endorphin.org/](http://luks.endorphin.org/)
(I found  it much easier to install with encrypted LVM's from scratch, if you need to encrypt the whole drive - including /boot, otherwise this is very good option)

---

### Post by Aero-Z on 2008-10-08
> **justleen said:**
> have a look at [http://www.truecrypt.org/](http://www.truecrypt.org/)

(I found  it much easier to install with encrypted LVM's from scratch, if you need to encrypt the whole drive - including /boot, otherwise this is very good option)
Yea, I know that encrypting when installing OS would be easy but I need to encrypt already running system.

---

### Post by justleen on 2008-10-08
hyper_ch has a tutor here: [http://ubuntuforums.org/showthread.php?t=404346](http://ubuntuforums.org/showthread.php?t=404346)

---

### Post by vanadium on 2008-10-08
Another option that allows to create encrypted directories is encfs. I believe this is being incorporated in the upcoming Intrepid.

If you want to encrypt single files, then gpgp is an option.

---

### Post by hyper_ch on 2008-10-08
just:

that howto is old :) the alternate and server cd include now directly encryption upon installation.

[http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691)

and as you say it's a server you may also want to have a look here:

[http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)

---

### Post by Aero-Z on 2008-10-08
The thing is that I need to encrypt already running system. No clean installations and stuff.

---

