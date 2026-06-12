---
title: "SSD Raid 0 configuration in setup?"
date: 2015-03-01
forum: Hardware
---

### Post by warchild on 2015-03-01
I have 2x 250GB SSD drives and would like to configure them as RAID0 array. Checked the partition manager, no mention of raid... How do I do that?

---

### Post by tgalati4 on 2015-03-01
This is an old tutorial, but the basic steps are the same.  [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by warchild on 2015-03-01
> **tgalati4 said:**
> This is an old tutorial, but the basic steps are the same.  [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

The link you provided mentions of an "alternate install" which I cannot find. By the way, I'm looking to install Ubuntu Mate. Is there alternate install CD for Ubuntu Mate as well?

Edit: Nvm, I figured out that the Alternate Install means Ubuntu Server. So if I partition my drives with Ubuntu Server CD and then quit setup, install Ubuntu Mate, would it work?

---

### Post by tgalati4 on 2015-03-02
Yes, you can partition drives with any tool that you can load in a Live Session.  Once your drives are partitioned, you can then install MATE, although I believe the MATE installer has a manual partition step--Choose "Something Else" when asked about use the entire disk or "Something Else".  The Alternate installer is a text-based, console installer for low RAM or terminal-only installations--not sure if it is produced any more, since modern servers have on-board graphics.  

If your server has a USB port, then you can create a USB installer stick instead of using a CD.  The default Ubuntu distro no longer fits on a CD.  The alternate installer will fit on a CD, if you can find it.

---

### Post by oldfred on 2015-03-02
Most of the RAID drivers are not in Desktop installer.
Either server installer or minimal where you can add anything you want.

 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

