---
title: "Install onDell PowerEdge 830 Dual Pentium?"
date: 2010-09-09
forum: Hardware
---

### Post by EchoBeach on 2010-09-09
Hi
I've been 'given' a Dell PowerEdge 830 Dual Pentium Server.
It's currently running Windows Server 2003, but I'd like to reconfigure it to Linux.
Will I be able to install 10.04 and have it work OK.
What other information is required to give a better idea?
Thanks
Echo

---

### Post by Fafler on 2010-09-09
The onboard graphics might be very slow, depending on your model, if you are going to using for desktop as well. Other than that, they work great.

If it has hardware RAID, you might want to compare performance with Linux software RAID on the same controllers, as software RAID in some cases is significantly faster.

---

### Post by EchoBeach on 2010-09-10
Thanks Fafler.
I would like to use it as a web server, and also possibly as a desktop with Windows XP in a VirtualBox session.
The CPU is a Pentium D Dual Core.  Can you suggest which flavour of 10.4 I should use?
Echo

---

### Post by Fafler on 2010-09-10
Just the stock desktop version. The main difference is the default window manager and as a new user with a powerful machine like yours, you're better off with the default Gnome.

If you have more than 4 gb, you should either get the 64 bit version or the 32 bit version with a PAE enabled kernel, otherwise most people use the 32 bit version.

[http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.iso.torrent)
or
[http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent)

---

### Post by EchoBeach on 2010-09-11
I've now installed 10.4 and it seems to be working OK so far.
I went for the amd64 desktop.

---

### Post by EchoBeach on 2010-09-25
Fafler
Returning to your earlier comment.
> **Fafler said:**
> The onboard graphics might be very slow, depending on your model, if you are going to using for desktop as well. Other than that, they work great.
Would this explain that fact that when I played [Enigma]("http://www.nongnu.org/enigma/") last night, the screen kept going black for a few seconds?

> **Fafler said:**
> If it has hardware RAID, you might want to compare performance with Linux software RAID on the same controllers, as software RAID in some cases is significantly faster.
I had a look inside and there is one SCSI HDD in a casing with room for four HDD.  RAID 0!

Thanks
Echo

---

