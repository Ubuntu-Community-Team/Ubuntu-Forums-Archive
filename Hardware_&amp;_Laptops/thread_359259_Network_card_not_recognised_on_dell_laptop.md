---
title: "Network card not recognised on dell laptop"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by dizzy1234 on 2007-02-11
Hi,

I've got an old Dell Inspiron 2500 laptop upon which I have installed Ubuntu 6.10 (not sure what that one's called :). It doesn't appear to have recognised the existence of the onboard network card, or at least it's not showing up in system>admin>network settings and I can't find it listed in Sytem->Admin->Devices. It does appear to have found the phone modem which is part of the same device (by the look of it) without a problem.

I know I haven't given much information but I'm not sure what information is needed :( 

Any ideas?

Cheers
nick

---

### Post by IamAcoconut on 2007-02-12
iDid you try intalling yur winwdoV drivers via **ndiswrapper**

---

### Post by frisket on 2007-03-07
> **dizzy1234 said:**
> I've got an old Dell Inspiron 2500 laptop upon which I have installed Ubuntu 6.10 [...] It doesn't appear to have recognised the existence of the onboard network card

I have the identical problem. The laptop never used the network under Windows, so it was never installed, so there was never any trace of what it was, and the user no longer has docs or disks from the Windows install (originally ME, I think <gag,spit>).

The Dell web site is no use (entering the Tag number just says Inspiron 2500 and gives no details).

Is there any site out there which lists what actually went into these machines? (and yes, I have Googled all over for it without success).

///Peter

---

### Post by frisket on 2007-03-07
Turns out to be an Actiontec V.90/NIC MPCI Combo. 
I don't suppose anyone would like to hazard a guess at what driver might support this?

There *is* a Dell download for it (drivers for the NIC and the Modem): is there a shim that will let this work under Linux, or some way to suck the information out of it so it can be used?

///Peter

---

### Post by frisket on 2007-03-08
> **IamAcoconut said:**
> iDid you try intalling yur winwdoV drivers via **ndiswrapper**

I'm trying to do this. But ndiswrapper is for wireless and usb cards: it doesn't seem to have anything relevant to on-board cards like this one (Actiontec V.90/NIC MPCI Combo), and lspci doesn't show anything relating to a network card (or even the modem port).

Plus this is a new install on a machine which -- by definition -- doesn't have any connection to the outside world, so I have to do any needed system updates by copying .deb files to a memory stick...

///Peter

---

### Post by cylentz on 2007-11-14
Any luck with this?  I'm having the exact same issue.  Ubuntu recognises the actiontec modem, but I can't get it to see the NIC.

---

### Post by K.Mandla on 2007-11-14
I'll check my 8000 when I get home; I could swear that's the same as in mine and it uses the ee100pro module to activate the network line.

I'm not 100 percent sure that's right, but in the mean time you can check lsmod to see if that module is inserted ...

```
lsmod | grep e100
```
and insert it if it's not ...

```
sudo modprobe ee100pro
```
No guarantees, but it might suddenly kick in. Cross your fingers. ...[-o< And please keep in mind I'm doing this from memory (I'm at work), so it might be completely wrong.

---

