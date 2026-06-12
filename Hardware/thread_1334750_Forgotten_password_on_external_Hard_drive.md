---
title: "Forgotten password on external Hard drive"
date: 2009-11-22
forum: Hardware
---

### Post by sg42 on 2009-11-22
I have a WD Mybook essential, 1TB which I was using with a Windows system a while ago. I forgot the password used to access the data, and tried plugging it into my Ubuntu machine to see if I can get at the data.

Interestingly, only a part of the external HD (~500 MB) shows up, and that too as /dev/scd2, and I am unable to write into this. 

I was just wondering if there is a way to access the data. Any help is much appreciated.

Cheers.

SG.

---

### Post by ram2500 on 2009-11-22
Does the drive have special software that password-protects the drive? Can you at least read the contents of the drive? 

I'm guessing sudo chown -R /dev/scd2 will be successful...

---

### Post by sg42 on 2009-11-22
It looks like the drive has some software, and no, I cannot read the entire contents of the drive - only about 500MB that seems to contain some sort of autorun.exe type files that windows uses.

---

### Post by sg42 on 2009-11-22
chown -R says that scd2 is a read-only file system, and is unable to change the ownership permissions.

---

