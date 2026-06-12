---
title: "Is there any way to move my ibex install to another computer?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by josephellengar on 2009-02-12
I've got a heavily personalized ibex install on my pavilion dv6000 and I recently bought a more up-to-date version of the pavilion.  I regularly backup my pavilion with clonezilla, and I was wondering if I could just move the install over to the new pavilion by uploading the clonezilla image to it.  I'm just concerned about what might happen with mounting disks and whatnot if I did that.  Is this possible?  Thanks.  Any help would be greatly appreciated.

---

### Post by lemming465 on 2009-02-14
I think it's possible, yes.  You might run into some boot and driver issues.  If you have good Linux troubleshooting skills these can be overcome.

As an alternative, you could do a fresh install, run *dpkg --get-selections* on the old machine, *dpkg --set-selections* on the new one followed by apt-get upgrade; and copy over your home directory and the contents of /usr/local, maybe with rsync.  That would get you most of the way there too, and would avoid the boot & driver issues.

If you can describe what "heavily personalized" means in terms of ubuntu packages, 3rd party source, modified configuration files, and user settings, we might be able to offer you more targeted alternatives.

---

### Post by oldsoundguy on 2009-02-14
or you could clone the entire drive with something like EZGig (works in Linux).

---

### Post by josephellengar on 2009-02-14
> **oldsoundguy said:**
> or you could clone the entire drive with something like EZGig (works in Linux).

Yeah, that's what I was asking.  I normally use clonezilla, but I'm concerned about what would happen if I moved it like that.

---

### Post by cosine352 on 2009-02-14
remastersys is a good option. I have done it several time. 

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by josephellengar on 2009-02-14
> **lemming465 said:**
> I think it's possible, yes.  You might run into some boot and driver issues.  If you have good Linux troubleshooting skills these can be overcome.

As an alternative, you could do a fresh install, run *dpkg --get-selections* on the old machine, *dpkg --set-selections* on the new one followed by apt-get upgrade; and copy over your home directory and the contents of /usr/local, maybe with rsync.  That would get you most of the way there too, and would avoid the boot & driver issues.

If you can describe what "heavily personalized" means in terms of ubuntu packages, 3rd party source, modified configuration files, and user settings, we might be able to offer you more targeted alternatives.

Heavily personalized meaning:
- Office 2003 set up to work with everything in wine
- Firefox with all of the passwords that I can never remember, and all of the other things- you know
- all of my themes/whatever
- various packages that I have installed
Could most of this be overcome just with moving my home directory?  I'd really like to move everything at once, just because there's all sorts of other things, even root scripts that I have set up and whatnot.

---

### Post by oldsoundguy on 2009-02-14
thing is about cloning .. if it does not work on the new machine, the old one is STILL working!
IF that happens, time for plan B (whatever that may be)

---

