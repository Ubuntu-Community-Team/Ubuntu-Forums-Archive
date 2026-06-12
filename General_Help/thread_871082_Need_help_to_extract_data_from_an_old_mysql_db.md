---
title: "Need help to extract data from an old mysql db"
date: 2008-07-26
forum: General Help
---

### Post by LilYoda on 2008-07-26
Here is my problem

My server was getting old, so I ripped the drives out, installed a new root drive, a software RAID 5 array for storage, etc.

But before I ripped the drives out, I forgot to do a dump of the mysql db ](*,). The drive is now in a USB case that's a pain to open, my new server is all finished, so I'm trying to avoid having to get the original drive out of its USB case to boot the old system just to make the sql dump.  I can mount the USB drive on the new system, but I read that I'm not supposed to copy files to copy a mysql db.

I tried the following paths, but I failed at all of them, so if you could help me out, I'd appreciate it a lot
1) boot on the USB drive through the BIOS. Just plain doesn't work
2) boot on the USB drive through fancy grub commands. Didn't manage to make it work, no idea how to do this
3) boot on the USB drive with a debian install CD. Doesn't work
4) tried mysqldump, mysqlmport, mysqlhotcopy commands, but I don't understand how they work, and the manpage doesn't seem very clear to me

Do you have suggestions? Could it be possible to boot that drive in a VMware machine?

---

### Post by hyper_ch on 2008-07-26
well, copying the binary databases often leads to damaged databases... so it's much more recommended to mysqldump them for backup.

However you can try to just copy them back. Normally the database is a folder (=database name) and contains for each table a .frm, .MYD and .MYI file.

Therefore copy the whole folder to /var/lib/mysql/ and then apply
```

sudo chmod 0755 /var/lib/mysql/TABLE
sudo chmod 0660 /var/lib/mysql/TABLE/*
sudo chown -R mysql.mysql /var/lib/mysql/TABLE

```
that shold set proper permissions and ownership.

Then you should be able to use it - if the binaries did not get damaged. You'd still need to create a user that can access it then.

---

