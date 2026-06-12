---
title: "HP scan to computer functionality"
date: 2012-02-16
forum: Hardware
---

### Post by artshark on 2012-02-16
Heys guys. I am on a 11.10. I have my HP 3050a set up and it works very very very well. I've always been of the opinion HP printers are actually easier to set up on an ubuntu machine than a pc, but alas, thats for a different time.
I'd like to use the scan to computer feature. This allows a scan to be initiated from the printer, NOT from the computer; this is beneficial as my computer and printer are not near one another. I checked in HPLIP and i can't find this check box. It exists on the pc software and works
Thanks
Art

---

### Post by mendhak on 2012-03-24
Did you ever find an answer to this? I've got the same set-up as you, everything's working fine.  But I can't get the scan-to-computer feature working in Ubuntu.  It works in Windows 7 as it was part of the installer.  I suspect this may have to do with the LIPS driver software, perhaps it is a feature not implemented?

---

### Post by Another Monkey on 2012-03-26
I too am looking for this information, but from what I can tell it simply will not work with any GNU/Linux.

This is [HP's fact sheet]("http://hplipopensource.com/hplip-web/models/officejet/officejet_6500_e710n-z.html") for the printer I have.  As you can see it says "Scan to PC: Yes" so you'd think that it'd work.  But you will also see it refers to note three.

Note 3 says:> Scan supported means that PC initiated scan using a SANE compatible software application is supported over parallel, USB, or network (depending on I/O connection). Information on digital sending products is covered in note 9, below.
So they are defining "Scan to PC: Yes" as meaning the PC can start the scan and have the information sent to it.  That is sharp practice if you ask me.

Note 9 says:> Device supports digital sending, not standard scanning protocols. See this KB article for more info. and the [KB article]("http://hplipopensource.com/node/302") is useless as it doesn't even discuss the same printer (in fact, the KB article implies that scan-to-pc should work in the expected manner).

At the bottom of the KB article is a link to "[Configure Digital Printing]("http://hplipopensource.com/node/334")" that suggest using the web interface to configure a shared folder that the printer can dump the scans to.  It's just a shame that the web interface doesn't actually expose any such functionality (there is a web scan, right-click on the image to save).

I have installed the 3.11.5 HPLIP drivers from the [HPLIP PPA]("https://launchpad.net/~hplip-isv/+archive/ppa"), I am wondering about installing 3.12 [directly from HP]("http://hplipopensource.com/hplip-web/gethplip.html") but am worried that I won't be able to remove them easily if I have problems.  Hmm...just noticed that they provide support via Launchpad Answers.  They say "Scan to PC" does work for some printers, but then reference the above KB article which doesn't explain anything.

"Scan to PC" works with Windows 7 and OS X, so surely it must be possible with a GNU/Linux like Ubuntu.  Has anyone gotten it to work and if so, how?

---

### Post by Another Monkey on 2012-03-27
I have re-read this [KB article]("http://hplipopensource.com/node/302") and I think it is saying that "Scan to PC" does not work with GNU/Linux.

Looking at [this list]("http://hplipopensource.com/hplip-web/supported_devices/combined.html"), some printers (such as the [HP LaserJet m3035 Multifunction Printer]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_m3035_mfp.html")) have "DS" in the "Scan to PC" column meaning that they can scan to PC.  Ones that just list "Yes" ***cannot*** scan to PC!

This means the printers that can scan to PC are all LaserJets and a couple of DesignJets.  All the OfficeJets, Photosmarts and other A-I-O printer cannot do it.

I have half a mind to return the printer and demand a full refund under false advertising.  Why list "Yes" for something the printer cannot do?  The 6500 can't even scan to a network folder!  :(

To answer artshark and mendhak: The HP 3050a does not support scan to PC.

---

### Post by Acknud on 2012-03-28
I fixed it but I am not sure how.  I did a complete reinstall of Ubuntu and low and behold, it started working.  I must have initially reinstalled the software 20 times without effect.  I guess the system just needed cleaning up.  It works like a dream now.

---

### Post by artshark on 2012-03-28
> **Acknud said:**
> I fixed it but I am not sure how.  I did a complete reinstall of Ubuntu and low and behold, it started working.  I must have initially reinstalled the software 20 times without effect.  I guess the system just needed cleaning up.  It works like a dream now.
including scan to computer? if so, where is the check box?

---

### Post by Another Monkey on 2012-03-29
> **Acknud said:**
> I fixed it but I am not sure how.  I did a complete reinstall of Ubuntu and low and behold, it started working.  I must have initially reinstalled the software 20 times without effect.  I guess the system just needed cleaning up.  It works like a dream now.

Just so I understand - you can press "Scan" on the printer and scan to an Ubuntu PC?  HPLIP team tell me that this is not supported.

Can you please explain what you did to get printer-initiated scanning working?

---

### Post by Another Monkey on 2012-03-29
> **artshark said:**
> including scan to computer? if so, where is the check box?

I think acknud is referring to their problems in [this thread]("http://ubuntuforums.org/showthread.php?t=1924822").

They probably picked up a newer version of HPLIP that now recognises the printer.  Until they come back and say otherwise, assume that scan-to-pc does not work.

---

