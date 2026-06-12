---
title: "Best configuration for two SSDs (RAID or no?)"
date: 2015-04-13
forum: Hardware
---

### Post by James_Spinella on 2015-04-13
Hey all,

I have a Mac Mini server on OS X and for more or less obvious reasons, I'd like to move to Ubuntu Server. The server itself doesn't do much, DHCP, DNS, website hosting is the main purpose but who knows what it'll be doing a year from now. My frustration comes from the fact that OS X server is rarely up-to-date (Apache, etc.), and does not use the latest standards (TLS 1.0 are you serious???). I'd also prefer the administration model of command-line Ubuntu Server.

The Mac Mini has two 240GB SSDs, and I'm not sure how to best configure them. My thinking is to use RAID0 to essentially have one "drive", since SSDs are quite reliable (drive would be backed up to external HDD). I know for the absolutely MOST redundancy, RAID1 is the way to go, but I feel it would be moot for SSDs.

The other option I'm heavily considering is just installing Ubuntu on one SSD and using the other as specific storage, perhaps for local backups, perhaps for user data or website files.

I'm very open to and would appreciate your suggestions.

---

### Post by oldfred on 2015-04-13
I do not have server with RAID.

But RAID is not for redundancy but availability or uptime.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array. And with SSD, you should not need speed.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)



But if you have good backups to another server/drive then you should be ok, with whatever you decide.
 [http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by weatherman2 on 2015-04-13
I agree with Fred - don't bother with RAID0.

Whether you need a mirror (e.g. RAID1) depends on what your intended use of the server will be.  A RAID mirror gives you redundancy in case one device fails - then your chances of losing data are much reduced. This is really most important with a heavy-use server with a lot of users, constantly accessing data.  If you won't have a high-use server, it's probably pointless to have a RAID mirror.  You'd do better by making regular, reliable backups.  Remember, a RAID mirror doesn't protect against file system corruption or accidental erasure.  (And if any Windows machines can access the server, data is vulnerable to malware corruption.)  That's where backups are much more important than a RAID mirror.

---

### Post by James_Spinella on 2015-04-14
Thanks for the replies.

Given SSDs reliability and speed, at least with RAID0 I get one 480GB SSD vs. two 240GB SSDs, and if it's all getting backed up anyway, that's the one that makes the most sense to me.

---

