---
title: "How can I confirm a hard drive is going bad?"
date: 2008-07-09
forum: Hardware
---

### Post by curiousnoob on 2008-07-09
I set up a dual boot machine for my parents using Hardy Heron and XP.  A week after setting this up neither would work.  I have resurrected Linux using fsck -y /dev/sdax 
Windows needs to be reinstalled due to a missing system file which is no real problem but I am concerned that since data was corrupted on two different partitions that it might mean that the HDD is going bad.  
Is there any type of diagnostic program or test that can confirm whether this was a freak accident or a physical problem with the HDD?

---

### Post by phidia on 2008-07-09
Install [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") I believe that's in the repos too.

---

### Post by tamoneya on 2008-07-09
the best way to check a harddrives integrity is to go to the manufactures website and download a diagnostic tool.  Typically they will have some sort of ISO which you can burn and then boot from.  It is often a dos environment that then loads the diagnostic and checks for errors.

The other way is to listen for nasty clicking noises.

---

### Post by Vivaldi Gloria on 2008-07-09
tamoneya idea is very good. Look for vendor's site for programs.

Also look if your disk reports any errors. First enable smart if there is an option for it in the bios. Then install

```
sudo apt-get install smartmontools
```

Now

```
sudo smartctl -H /dev/sda
```

checks the health of the disk /dev/sda if it has smart capability. See

```
man smartctl
```

for more info.

There is also the testdisk program for scanning and repairing disk partitions but I have not used it. Install it and see

```
man testdisk
```

for more about it.

---

