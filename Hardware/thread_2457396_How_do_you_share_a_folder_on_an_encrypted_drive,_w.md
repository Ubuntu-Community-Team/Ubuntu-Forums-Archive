---
title: "How do you share a folder on an encrypted drive, with non-Linux clients?"
date: 2021-02-01
forum: Hardware
---

### Post by uacnt83982803 on 2021-02-01
Is this even possible?  I want to share an external drive so that a Windows PC can read/write files on it.  And I'd like to have my phone (Android) do the same, using Cx File Explorer.

But if the external drive must be encrypted; I can't have it sitting around with private files exposed.

What are my options here?  Thanks.

---

### Post by yancek on 2021-02-01
What filesystem type is the external drive?  If it is a Linux filesystem type, a default windows system will not be able to read much less write to it.  You willl need to install 3rd party software on windows which may work.  So what filesystem do you have on the external drive?  Are the windows systems on a LAN?

---

### Post by uacnt83982803 on 2021-02-01
External drive will be Ext4 with LUKS encryption.  Everything (Ubuntu PC with the external disk, Windows PC, and various Android devices) are all inside my LAN.

Maybe what I'll need to do is create 2 partitions on the external drive - one encrypted with LUKS, to hold private data that I don't wan to have at risk, and the other partition formatted with FAT where I'd put the cat photos (stuff that I don't care about whether anyone views it).

It sure would be nice to do this with a single encrypted partition, but I guess that's not possible?

---

### Post by CelticWarrior on 2021-02-01
It is possible with third-party software like Veracrypt.

---

### Post by uacnt83982803 on 2021-02-01
Yes, good point.  I already use Veracrypt to encrypt USB memory sticks.  So you're saying encrypt the entire drive, unlock it when I need access to it, and once unlocked I'll be able to share it with other clients (Windows and Android) on my LAN?

---

### Post by CelticWarrior on 2021-02-01
For network sharing it makes no difference. Once decrypted the file system system is the same as any other file system and when shared with Samba (required for Windows clients) the actual file system in the shared partition also doesn't matter.

I suggested Veracrypt because I thought you wanted to use an encrypted external drive both with Ubuntu and Windows. For that you need a cross-platform tool such as Veracrypt and the actual file system inside as NTFS. LUCKS + EXT4 works in Linux only.

---

### Post by uacnt83982803 on 2021-02-01
Yes, I do want it to be able to be used with both Ubuntu and Windows.  As far as Veracrypt, the way I use it currently is I unlock the memory stick, copy over what I need, then dismount it (thus locking it again) and remove it.

Are there any problems leaving a Veracrypt partition unlocked essentially continuously (which is what I think we're saying here)?  Does it automatically get locked if someone were to simply unplug the drive and walk away with it?  I assume so, but wanted to check. 

Also, is there a size limit to Veracrypt partitions?  I will be using a 2TB drive.

BTW thanks for your help on this, much appreciated.

---

### Post by CelticWarrior on 2021-02-01
> [COLOR=#000000]Are there any problems leaving a Veracrypt partition unlocked essentially continuously (which is what I think we're saying here)? [/COLOR]

No, it absolutely isn't what I'm saying here.

> [COLOR=#000000]Does it automatically get locked if someone were to simply unplug the drive and walk away with it? I assume so, but wanted to check.[/COLOR]
Yes, it's encrypted. The worse that can happen is corruption but as always and especially when dealing with encryption you must have backups.

> [COLOR=#000000]Also, is there a size limit to Veracrypt partitions? I will be using a 2TB drive.[/COLOR]

The size limit comes from the file system(s) inside, not from the software.

---

### Post by uacnt83982803 on 2021-02-01
What I really should be looking at, to do this right, is a NAS, correct?  That would give me access 24x7 from any device on my LAN, right?

---

