---
title: "Installer does not progress beyond installation options menu"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by badger_fruit on 2009-10-01
Sorry if that's a little vague but I see to be having an issue on any PC I've tried this 
with.

I'll boot a PC with the 9.04 install CD in the drive; it's recognised and I get the language selection menu.  I then select English (British) and I get the second, "Installation" menu (the one with "Install" "Try" "Boot local HDD" and so on).

Whichever option I select 9even boot from local HDD!), it just freezes the PC up totally and to reboot, I have to either hold down power button for x seconds, or switch power off at the wall.

If I remove the CD the system boots 100% fine (into Windows XP by the way).

I have tried:-

[LIST]
[*]Multiple copies of the install CD
[*]Multiple DVD/CD drives
[*]All the different options from that 2nd menu
[/LIST]
And yet, nothing works!
I have discovered that if I mount the ISO image using Daemon Tools in XP and then select "Install alongside Windows", it installs fine but I am loosing disk space and I want rid of windows, not to run alongside it!!

If I use this same ISO image but choose "install over windows" then I'm told to "simply reboot the pc with the cd in the drive", which then of course, gives me the problem above!!

Does anyone have any suggestions on how I can get it installed from the CD?!
Oh, I also tried putting in an Opensuse DVD, that installed just fine by putting in DVD, and booting the PC.

---

### Post by oldos2er on 2009-10-01
What are the hardware specs of this computer? Have you tried burning at a slow speed (4x or less); have you run MD5SUM on the disc? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by badger_fruit on 2009-10-01
> **oldos2er said:**
> What are the hardware specs of this computer? Have you tried burning at a slow speed (4x or less); have you run MD5SUM on the disc? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It's a Dell Poweredge SC430 - Dual Core 3GHZ P4, 1GB ram - don't ask me the mobo or ram types as it was a "hand-me-down".  I know it works well with other OSes such as XP, Fedora, Knoppix, FreeNAS and Suse as at one time or another, it's had all those installed to it.

The disk *was* ripped at 4x and the MD5 checked as well (burnt on K3B on Suse11.0 which checks the MD5 hash before burning).

The PC itself doesn't have a DVD drive (or CD drive for that matter) so I ripped the CD on a different computer then physically removed the drive, connecting it into the server.  I know the writer is good as I rip disks to and from it all the time, they are CD RWs or DVD RWs so I know the media is good as they're used for other distros and what nots.

I mean, it's working and with a quick tweek through Windows of the BOOT.INI, it always loads into Ubuntu but it'd be nice to know why the heck this darned OS is not installing how it should!

Oh and yes, I have tried to install on a spare, totally clean HDD I had kicking around but the exact same problem :(

---

### Post by badger_fruit on 2009-10-02
Sorry for the bump but anyone got ANY ideas at all?!

---

### Post by oldos2er on 2009-10-02
The only thing I can think to suggest is to try a CD-R instead of a CD-RW. This seems to work for some folks when nothing else does.

---

### Post by badger_fruit on 2009-10-04
> **oldos2er said:**
> The only thing I can think to suggest is to try a CD-R instead of a CD-RW. This seems to work for some folks when nothing else does.

Cool, I might give that a go but touching wood, all is working nicely as it is and you know the old saying ... if it ain't broke ... don't fix it!!

---

### Post by snag102 on 2009-10-04
Bump.
 
I've encountered the same problem trying to install on a lenovo g530.  Once I select an option (boot off live cd or install ubuntu or check disk etc.), it just hangs.  I have to power off and boot to windows vista.
 
Md5sum matches, and I've tried 4 different CD-Rs burned on 2 different machines :confused:
 
Any further ideas?  Is this a hardware problem by any chance?

---

### Post by badger_fruit on 2009-10-05
> **snag102 said:**
> Any further ideas?  Is this a hardware problem by any chance?

I can't see it being hardware, if I shove the CD in while running Windows then hit install alongside, it installs no problem - if it were hardware, surely even that would fail?!

---

### Post by snag102 on 2009-10-06
Agreed.

My problem just got resolved - Turned out it was a bad batch of CDRs.  For some reason vista told me the burn was ok, but when I tried on a mac I got repeated verification failures.  After going through 7-8 coasters, bought some new media and problem went away!

---

