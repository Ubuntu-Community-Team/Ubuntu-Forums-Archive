---
title: "hdparm setting after resume from suspend"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by teachop on 2007-06-10
In my hdparm.conf file is the following to prevent constant hard disk clicking:

command_line {
	hdparm -B254 /dev/sda
}

This works on reset, but the setting becomes 128 after suspend / resume, and the drive clicking returns (which I think is constant park / unpark but I am not sure of that).

Can someone help as to where this setting belongs so it will still apply after suspend / resume?

I have an Acer Aspire 3100 with Feisty....

---

### Post by neptho on 2007-06-10
If you want different settings, create a file in /etc/acpi/resume.d, such as 40-shutupdisk.sh:

```
#! /bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
/etc/init.d/hdparm start
```

Make sure you remember to chown root:root, and chmod 755..

---

### Post by teachop on 2007-06-10
That worked for me, thank you.

---

### Post by scotc on 2008-03-21
I have the same issue  - resume brings back the clicking.

I don't understand what you mean by this

> Make sure you remember to chown root:root, and chmod 755..

---

### Post by bkraptor on 2008-03-28
he means that, given the file name 40-shutupdisk.sh you should run these commands:
$ chown root:root 40-shutupdisk.sh
$ chmod 755 40-shutupdisk.sh

---

### Post by ethanay on 2008-05-02
hah!  I have tried everything to stop the load/unload bug after resume from suspend/hibernate.  Nothing has worked for this exact same reason.  I will try this script...keeping fingers crossed.

edit:  no dice...dangit. :(

---

### Post by ianbear on 2008-05-20
Two things:  first, make sure you added the entry to /etc/hdparm.conf as stated above.

Second: at some point in the past hdparm was moved from init into udev so /etc/init.d/hdparm no longer exists.  I think /lib/udev/hdparm should work in its place.  Change your 40-shutupdisk.sh to look like 
```

#! /bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
/lib/udev/hdparm
```

and see if that helps.

---

