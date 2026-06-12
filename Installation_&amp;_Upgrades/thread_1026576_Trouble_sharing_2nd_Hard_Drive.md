---
title: "Trouble sharing 2nd Hard Drive"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Bennett2005 on 2008-12-31
Hi gang,

I'm currently dual-booting with XP and Ubuntu.  I recently added a second hard drive with the intention of using it to access and share files on both the XP and Ubuntu side (so it's NTFS format).

I've been trying to get this set up by using the partition editor in the Ubuntu install program.  I have the second hard disk partitioned into one ext3 partition for my home directory, and a substantially larger chunk partitioned as an NTFS section for my music, pictures, various plans for global domination, etc.  The original hard drive is just partitioned for the XP system, Ubuntu system, and swap area.

The problem I'm having involves setting up that NTFS partition to share files over my network.  When I change the sharing options to share the directory I get an error message stating "Unable to share drive."  Adding the extra line in the samba.conf to allow all users doesn't fix it.

I've run the program NTFS Config to try to fix the problem, and that DOES allow me to share the files, so I'm assuming it's a mount issue.  The only problem here is when I run NTFS Config I can't boot into Windows anymore.  I get an error message when I select the Windows XP boot from the Grub list.

Is there a better method to setting something like this up?  I'm about to throw in the towel and just format the entire drive as ext3; but I'd really like to be able to use and share the same files when in Windows so it doesn't affect my network setup.

Any advice would be huge.  Thanks a bunch.

---

### Post by albinootje on 2008-12-31
Can you post the output of :
```

mount
cat /etc/fstab

```
And the [share] part of your /etc/samba/smb.conf and the current permissions set on the share.

---

### Post by Bennett2005 on 2009-01-01
Thanks for the interest in helping me out, Albinootje.  I really appreciate it.

I seem to have fixed the problem just by trying another distro.  I installed Linux Mint 6 to try it out; it must be a little more pre-configured for sharing because I was able to set everything up very easily.

Going to give Mint a try, but at least I know it's just a settings issue now and not a hardware configuration problem.

Thanks again.

---

### Post by albinootje on 2009-01-01
> **Bennett2005 said:**
>  I seem to have fixed the problem just by trying another distro.  I installed Linux Mint 6 to try it out; it must be a little more pre-configured for sharing because I was able to set everything up very easily.

Going to give Mint a try, but at least I know it's just a settings issue now and not a hardware configuration problem.


By coincidence I was testing Linux Mint for the first time (and also tried Slackware 12.x), and I noticed a generic "sharing options" somewhere in the settings/administration part, which Ubuntu doesn't seem to have.

I'm glad to hear you solved it.

---

