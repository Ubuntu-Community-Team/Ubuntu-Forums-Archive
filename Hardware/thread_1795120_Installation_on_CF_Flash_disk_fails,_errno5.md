---
title: "Installation on CF Flash disk fails, errno5"
date: 2011-07-02
forum: Hardware
---

### Post by Afisamuleal on 2011-07-02
Greetings,

For some time now, I have been attempting to install linux on my 16 GB Kingston CF disk. I am using a cheap CF-sata adapter in my laptop.

However, every time I attempt to install an operating system (ubuntu, followed by arch linux, followed by mint), the install fails about 7/8 of the way through, usually with an errno 5 ```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```.

Following this, I ran sudo fsck -y /dev/sda1 , which produced too many errors to be reasonable, samples of which often take the following types of forms (however in multitude):


```
Inode 156427 ref count is 2, should be 1.  Fix? yes

Unattached inode 156428
Connect to /lost+found? yes
```

```
Inode 16144 was part of the orphaned inode list.  FIXED.
Inode 9567 has a bad extended attribute block 56569.  Clear? yes

Inode 9567, i_blocks is 2097153, should be 0.  Fix? yes
```

```
Entry '..' in /???/#263360 (263360) has deleted/unused inode 11.  Clear? yes
```

```
Setting filetype for entry '..' in ??? (262446) to 2.
Directory inode 262449, block #0, offset 0: directory corrupted
Salvage? yes

Missing '.' in directory inode 262449.
Fix? yes
```


Eventually the errors become fixed. However they reappear when I try to install the operating system again. However, I am completely unable to install any operating system on the CF drive.

I am not sure if there is a remedy for this; I am not sure what is wrong. I would appreciate any help you can give!

---

