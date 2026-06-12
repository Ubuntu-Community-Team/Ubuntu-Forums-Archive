---
title: "LSHW Help"
date: 2015-01-16
forum: Hardware
---

### Post by bigpappajohn1984 on 2015-01-16
I just formatted a drive using
```

sudo mkfs.ext3 /dev/sda
```

Now I rebooted, and when I try to runn
```

sudo lshw -C disk -short
```

The drive is not listed.  It skips it in the drive letter assignmets.  This is what I see...
/dev/sda disk 120GB Axiom Signature
/dev/cdrom disk DVD+RW DS
/dev/sdc disk 640GB FreeAgent GoFlex

---

### Post by Bucky Ball on 2015-01-16
That command shows the whole drive, not the partitions on it, i.e. the one you just formatted. ;)

You could have a look in Gparted, if you have it, and see what that shows or try 'df -l' in a terminal.

---

### Post by bigpappajohn1984 on 2015-01-16
trying to run ```
df -l
``` still does not return my drive...grrr!!!!

The worst part of it is I had just copied a raw image from a failing drive over to this one, and now I can't see that drive at all!


I am running the Ubuntu-Rescue Remix from a bootable .iso so g-parted is not an option :(

---

### Post by bigpappajohn1984 on 2015-01-16
> **Bucky Ball said:**
> You could have a look in Gparted, if you have it

I know the disk doesn't have gparted, but I believe it has parted if you could provide assistance with using that.

---

### Post by Bucky Ball on 2015-01-16
I don't use parted in the terminal myself but [this]("http://manpages.ubuntu.com/manpages/lucid/man8/parted.8.html") may help. If you type into the terminal:

```
man parted 
```

... you'll get the same info as on that link.

> **bigpappajohn1984 said:**
> trying to run ```
df -l
``` still does not return my drive...grrr!!!!

Just to be clear, you are looking for a partition and not a drive? You found the drive sda fine, but you can't format that, as it is a drive, not a partition. You can't format a 'drive' but you can format the partitions on it. I'm imagining that your code:

```
sudo mkfs.ext3 /dev/sda
```

Should be pointing to a partition, i.e.

```
sudo mkfs.ext3 /dev/sdax
```

Where 'x' is the partition, for instance, sda5.

---

### Post by bigpappajohn1984 on 2015-01-16
> **Bucky Ball said:**
> I don't use parted in the terminal myself but [this]("http://manpages.ubuntu.com/manpages/lucid/man8/parted.8.html") may help. If you type into the terminal:

```
man parted 
```

... you'll get the same info as on that link.



Just to be clear, you are looking for a partition and not a drive? You found the drive sda fine, but you can't format that, as it is a drive, not a partition. You can't format a 'drive' but you can format the partitions on it. I'm imagining that your code:

```
sudo mkfs.ext3 /dev/sda
```

Should be pointing to a partition, i.e.

```
sudo mkfs.ext3 /dev/sdax
```

Where 'x' is the partition, for instance, sda5.

Yep - my issue seems to be exactly as you suspected...
```
sudo mkfs.ext3 /dev/sdax
```

Thank you!!

---

### Post by Bucky Ball on 2015-01-16
Glad to help. I should have twigged from the get go! Working now?

---

