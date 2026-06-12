---
title: "Weird Upgrade Problem"
date: 2008-10-15
forum: General Help
---

### Post by Austin17 on 2008-10-15
Hey all, before I go ahead with what I'm planning to do I want to run this by you guys here and get your input.

Windows had some updates earlier today, and after installing them I rebooted. Upon rebooting and selecting the Windows option in Grub the Windows splash screen flashes for a second and then reboots. I've tried booting into safe mode and "Last Known Good Configuration" unsuccessfully.

I've booted into Ubuntu and Googled my problem, and found this page:
[http://www.techsupportforum.com/microsoft-support/windows-xp-support/162137-resolved-windows-won-t-boot-after-update.html]("http://www.techsupportforum.com/microsoft-support/windows-xp-support/162137-resolved-windows-won-t-boot-after-update.html")

It looks like someone had a very similar experience over a year ago and was able to fix it with a Repair Install. So my concern is, if I do a repair install should I be worried about my MBR with a Windows Repair install? Because if possible I would like to avoid unplugging my hard drive with linux because it is in a rather awkward place to get to. Thanks for the help! :-)

---

### Post by logos34 on 2008-10-15
If Grub is on the MBR of the Windows drive, then I believe doing a repair install will overwrite it, but I could be wrong.  But no big deal since you can easily restore grub from the ubuntu live cd or Super Grub Disk. (see links my sig).

good luck

---

### Post by Austin17 on 2008-10-15
Thanks for the help. One more thing, if I do unplug my hard drive with Grub and Ubuntu on it, do I have to worry about anything?

---

### Post by Austin17 on 2008-10-16
I'm sorry about the double post, but also if I just disable the hard drive with Ubuntu/GRUB on it in BIOS, should I have to worry about Windows overwriting my MBR with a repair install?

---

### Post by logos34 on 2008-10-16
> **Austin17 said:**
> I'm sorry about the double post, but also if I just disable the hard drive with Ubuntu/GRUB on it in BIOS, should I have to worry about Windows overwriting my MBR with a repair install?

Oh, so grub is on the ubuntu drive.  I guessed the other way.  In that case, to do a repair install you first have to make the windows drive the boot drive in the Bios--it won't install any other way.  Then windows will safely write the bootloader to the mbr of that drive and not the ubuntu drive in second position.  But disable the latter like you said--hopefully that will provide double insurance.

---

### Post by Austin17 on 2008-10-16
> **logos34 said:**
> Oh, so grub is on the ubuntu drive.  I guessed the other way.  In that case, to do a repair install you first have to make the windows drive the boot drive in the Bios--it won't install any other way.  Then windows will safely write the bootloader to the mbr of that drive and not the ubuntu drive in second position.  But disable the latter like you said--hopefully that will provide double insurance.

Thank you very much, I will probably do it within the next few days and post my results. Thanks again for the help so far!

---

### Post by Austin17 on 2008-10-18
Ok, sorry for the double post. Just wanted to post to say that this was solved. A repair install did not work so I had to reformat my Windows partition. It did mess up Grub, but I was able to easily restore it with one of the tutorials. Thanks!

---

