---
title: "Auto mount extra HD on boot?"
date: 2010-03-24
forum: Hardware
---

### Post by johnuk on 2010-03-24
Aloha! ;)

9.10 Karmic Koala

Have a spare 200gb drive so stuck it in alongside my primary

It wants my sudo pass to mount it each reboot

Can I have it auto mount without the sudo each time? Store the sudo for the mount I mean.

Thanks for your time!
John

---

### Post by vanadium on 2010-03-24
Maunt the drive automatically with system startup by including it in the configuration file /etc/fstab.

---

### Post by moi on 2010-03-24
> **vanadium said:**
> Maunt the drive automatically with system startup by including it in the configuration file /etc/fstab.

and this sort of thing is why linux is not spreading to the masses.  any system changes are difficult to manage and before you rabid fanboys pounce, most people do not want to have to edit anything just to auto-mount a drive, they are not going to spend the time to learn linux nor are they going to hire someone to do it for them.

---

### Post by johnuk on 2010-03-25
Thanks Vanadium, I was going to say it earlier but I haven't got round to working out precisely what I need to add to fstab. 

Moi is correct, but then, I also didn't make out that I needed any extra help in my original post.

To be fair, a quick google search has pulled up a bunch of pages about automounting drive - which I should have searched for first.

---

### Post by rhy7s on 2010-03-25
Was one of those pages [here]("http://ubuntuforums.org/showpost.php?p=5470813&postcount=1")?

---

### Post by johnuk on 2010-03-25
No, but thanks for the link! ;)

---

### Post by johnuk on 2010-03-25
I tried following this [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

The only mistake I can think of is that I used a lowercase j for John in my username to set up the permissions, when it's John under users and groups - my name that is, my login is john

On restarting, I got a bunch of logical partition errors and then the disk entirely disappeared from the GUI

Cut the line out of fstab, errors disappeared, disk reappears in GUI

---

### Post by Morbius1 on 2010-03-25
Why not post the output of the following command:

Open **Terminal**
Type **sudo blkid -c /dev/null**

---

### Post by johnuk on 2010-03-25
/dev/sda1: UUID="9e60a79b-a0c5-4059-bf6d-dff9101f2636" TYPE="ext4" <----- main disc
/dev/sda5: UUID="baa2cd21-c15e-4619-8d19-0de3477df105" TYPE="swap" <----- main disc
/dev/sdb1: UUID="0953fd04-ca7a-4ec7-bfca-0fd0ace628bb" TYPE="ext2" <----- this is the spare 200gb drive

The UUID and type are both what I used in fstab on my first attempt.

Could someone explain the ext# file systems. I know what FAT / NTFS & swap are about, but why does Linux have these ext# (extension, I understand that, not the number) and is there any logic behind the number assigned or difference in the actual file system? For example, could I have two drives or partitions with the same ext#?

Thanks for the help amigos

---

### Post by vanadium on 2010-03-26
* Create a mount point for the drive
```
sudo mkdir /mnt/sdb1
```
* open the file /etc/fstab for editing with root permissions
```

gksudo gedit /etc/fstab

```
(or: sudo nano /etc/fstab if you want to edit using nano)
* Add a line for your sdb1. First field is the drive, references by its UUID, second field = mount point, third field is file system, fourth field is options, fifth field is no more used (leave it 0) 6th field specifies checking or not (make it 2 - in second order after the system drives)
```

UUID="0953fd04-ca7a-4ec7-bfca-0fd0ace628bb" /mnt/sdb1 ext2 defaults 0 2

```
Save the file and exit

* perform the mount. There should not be any output from the following command. Otherwise, there is an error.
```

sudo mount -a

```

If no error, the drive is mounted and can be found in /mnt/sdb1.

* By default, only root can write to /mnt/sdb1 (the root partition of the drive. If you want to change that, you can use nautilus with root permissions: "gksudo nautilus". With right-click, properties, you can change permissions of the /mnt/sdb1 if needed. Existing directories will keep their permissions. 

ext2, ext3 and ext4 are different versions of the ext filing system of linux. ext4 is the most recent version, which has become the default for the latest Ubuntu.

---

### Post by johnuk on 2010-03-26
Thanks again for the detailed reply Vanadium, I'll give it a go in a few minutes and report back.

Two ext# questions.

Why continue offering the older versions, is it just compatibility or are there some benefits to the previous versions?

Also, is it worth me reformatting the spare drive in any particular ext# file system other than ext2? I'm basically only using the drive for storage of videos and music, so maximizing that would be my goal; similar to choosing between fat 16/32 based on access speed versus disk usage I guess.

---

### Post by vanadium on 2010-03-26
It is compatibility, but also features can be a point. ext2 has no journaling. Drawback is that is is less robust against errors such as power failures, but advantage is that it is faster and requires less writes to the medium. The latter is of interest for flash drives, which have only limited read write cycles.

Worth reformatting a drive for data storage? The condition of a partition needs to be checked from time to time to verify the integrity of the data structures. A journaled file system such as ext3 and ext4 has the advantage that a quick check can be done: only the journal is checked. A lengthy, in-dept analysis is only needed now and then. With ext2, a check always involves a lengthy check. So it is easy to check an ext3 drive regularly, while doing that for an ext2 drive is secure but tedious.

I think the extra convenience and the extra security are worthwhile to use ext3 or ext4 even for home use. ext4 is rather new, but tested. The only reason not to use it would be compatibility, I guess. For an internal drive that is used on a single system, compatibility is not the issue.

---

