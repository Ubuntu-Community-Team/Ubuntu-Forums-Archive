---
title: "Boot problems 9.10"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by ibates on 2009-11-07
I have recently installed Unbuntu 9.10 on a Win XP Pro SP3 machine on a separate HDD.

Upon bootup via the GRUB menu I get the pervasive dialogue box that one or more of my HDD are failing.  It turns out that Ubuntu thinks there are a many bad sectors on the disc.  (There weren't on either Windows or Ubuntu 9.04).

No problem, purchase new HDD, as recommended by the Ubuntu dialogue, but can't go anywhere because the GRUB loader finds no disk.

OK, so I will fix the MBR.   But; no I won't.  The GRUB menu does not offer me the option to boot from my Windows CD.

So now I am stuck.  I can't boot up to Ubuntu; I can't fix the MBR;  I can't boot up from any CD; and unless I resinstall the faulty HDD (which according to Ubuntu is failing), I can't even boot up on Windows.

I tried Ubuntu a few months ago and had to give it away because it simply became too complicated.  And now it is starting off the same way again.  Is it just me?  Or is Ubuntu still a "works in progress"?

Perhaps someone can enlighten me how I can go about fixing the MBR for a start, and then perhaps how to get Ubuntu 9.10 installed on a new HDD which probably has no bad sectors - yet!

---

### Post by freackout on 2009-11-07
> **ibates said:**
> I have recently installed Unbuntu 9.10 on a Win XP Pro SP3 machine on a separate HDD.

Upon bootup via the GRUB menu I get the pervasive dialogue box that one or more of my HDD are failing.  It turns out that Ubuntu thinks there are a many bad sectors on the disc.  (There weren't on either Windows or Ubuntu 9.04).

No problem, purchase new HDD, as recommended by the Ubuntu dialogue, but can't go anywhere because the GRUB loader finds no disk.

OK, so I will fix the MBR.   But; no I won't.  The GRUB menu does not offer me the option to boot from my Windows CD.

So now I am stuck.  I can't boot up to Ubuntu; I can't fix the MBR;  I can't boot up from any CD; and unless I resinstall the faulty HDD (which according to Ubuntu is failing), I can't even boot up on Windows.

I tried Ubuntu a few months ago and had to give it away because it simply became too complicated.  And now it is starting off the same way again.  Is it just me?  Or is Ubuntu still a "works in progress"?

Perhaps someone can enlighten me how I can go about fixing the MBR for a start, and then perhaps how to get Ubuntu 9.10 installed on a new HDD which probably has no bad sectors - yet!
try downloading or getting a copy of pmagic 4.5 (free) option supergrub it may help also its very handy disk to have.
its also available for usb stck version too, works over a network also. or cd.iso
though there will be other available fixes using another live distro ect.

Grub is NOT supposed to allow you to boot from cd ect THAT is hardware not OS, YOUR  option is available from the BIOS ie press one of the following while booting like del, f1,f5, or more commonly F8 this will alow you to change the boot order. not grub ok. THEN if you want to change the OS boot order use grub or supergrub on the cd.

---

### Post by ibates on 2009-11-07
Thanks for that.

I did forget to add in my original post that since this problem developed, any attempt (even via the BIOS options) to boot from a CD are totally ignored.  I end up back at the GRUB loader failed prompt.

To clarify the situation, BIOS is set up for CD as the first boot option.

Even going to the BIOS BOOT menu F8 and selecting CD, still results in ending up at the GRUB failed screen with no attempt to boot from the CD.

What now?

---

### Post by ibates on 2009-11-08
Final update.

Purchased a new disk, reinstalled 9.10 on that disk from the ISO CD (which was able to boot), wiped the old (failing disk), rebooted and heh presto!   All fixed.

But; the "failing disk" message still remains because the "failing disk" is still operating in the computer as a blank but formatted NFTS disk.

9.10 Disk analyser examines each and every HDD in the system, regardless of the operating system under which it is formatted.

But 9.10 seems to be operating perfectly.

Thanks for help.

---

### Post by omegamormegil on 2009-11-08
I'd suggest not doing anything too important on the drive unless you have backups.  The new disk utility in Karmic is checking signals from your hard drive that indicate how healthy the drive is, and you are being bothered because something is amiss.  It will check any drive on your computer. 

For more information, you can check out the S.M.A.R.T. Hard Disk Monitoring Utility here:  [http://sourceforge.net/apps/trac/smartmontools/wiki#testinghelp](http://sourceforge.net/apps/trac/smartmontools/wiki#testinghelp)

If you don't care, and don't want to be bothered anymore, you can stop it from automatically checking the health of your drives by unchecking "Disk Notifications" in System > Preferences > Startup Applications.

---

### Post by dansi on 2009-11-09
Make another partition on your hard drive start the live disk of ubuntu and install it onto the new parttion make sure the grub installs it should be similar to the 9.4 method
============================
[Self Certification Mortgage UK](http://www.self-cert-mortgage-centre.co.uk/self-certification-mortgage-uk.html)
[Start a home based business](http://www.nitroblueprint.com)

---

