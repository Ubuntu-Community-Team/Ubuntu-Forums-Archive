---
title: "Mysterious start up problems, and my computer cannot stand"
date: 2008-10-05
forum: General Help
---

### Post by PostersandGuitar on 2008-10-05
After a long, complicated installation of Ubuntu Studio, when attempting to load into Ubuntu Studio, it will often take ages with white area moving around the Ubuntu Studio logo, and then dump me into a busybox command line. It will also sometimes display a bunch of text I don't understand before entering into Ubuntu Studio.

I have two hard drives, an IDE and a SATA. Linux is on the IDE, Windows is on the SATA.

Also, my computer i currently laying on it's side. When I stand it up, I get GRUB error 17, or a read error, and I have to unplug, and replug the IDE cable several times, and reset the order of hard drives in the BIOS, and lay it on it's side before it will work again. The ribbon cable being very close to a power supply cable also appeared to cause error 17, or a read error. Electrical interference?

---

### Post by Zill on 2008-10-05
Your PC sounds quite sick!  If you can't identify the dodgy hardware then the most cost-effective solution may be to replace the complete system.

---

### Post by taladan on 2008-10-05
It sounds to me like you may have a faulty IDE drive.  Assuming you're not experiencing any issues with the SATA drive when using it, it's possible that the armature controller in your drive has gone bad.  My first step would be to image off the drive when it's in a running state (partimage or Partimage Is Not Ghost [http://windowsdream.com]("http://windowsdream.com") will help you with this) and pull it over on a safe known-good drive.  Replace the drive **and** the cable with a known-good IDE hard drive (or add another sata drive in if you have an extra port), or resize the windows partition on the sata drive and drop your image to it.  I see hard drives go bad all the time so it's not an uncommon or unlikely experience.  The good news is that you can get relatively largish hard drives on the cheap now, unlike a decade ago where every megabyte was pricey.  

hope this helps,

Tal

---

### Post by oldsoundguy on 2008-10-05
If you are using any external USB drive, unplug it or turn it off.  I have a serious boot issue if I have my external Sony dual layer burner plugged in.  I turn it off and then turn it back on once the boot up is complete.

---

### Post by PostersandGuitar on 2008-10-05
Could the hard drive being unsecured and lying on the edge of the case be causing this? The computer does work fine when it's lying on it's side.

---

### Post by MaxIBoy on 2008-10-05
Do you know how the hard drive itself is oriented within the case? Is it flat when the computer is standing up? Is it vertically bolted to the inside of the front panel?

---

### Post by taladan on 2008-10-05
it could (being unsecured) cause problems if the drive has shifted around during operation and caused impact force within the drive unit itself - has it been dropped? Kicked over?  Nudged hard?  Something like that could cause internal damage to the drive itself - which is why they're usually securely mounted within the system case.  You could try securing the drive into the case itself and see if that would help, but if the drive has been damaged already by one of these things, continuing to use it without imaging the drive could lead to a loss of data on the drive itself.  

Primary rule - the more data you have that you can't lose, the more likely it's going to be that your hard drive is going to fail if you don't have it backed up.

Tal

---

### Post by PostersandGuitar on 2008-10-05
I think I'll secure the drive.

---

