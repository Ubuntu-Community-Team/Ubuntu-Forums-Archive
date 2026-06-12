---
title: "two Hardware issue with Ubuntu Please Help"
date: 2010-07-02
forum: Hardware
---

### Post by PsychoNix on 2010-07-02
Hello guys 
 basically i have two questions 
The First One :

My sound Card Not working right to much distortion and not clear sound 
My Card Is : Creative Sound Bluster Live 5.1

Second Question : 

How can i make my Hard-discs Mounted After Every time i restart " they already there but i cant keep the icons on the desktop"  they are appear when i open them but after restart they disappear Note: I dont Use Fstab to mount them they automatic mounted

Any help with that plz 

Sorry about my English

thank you

---

### Post by SaintDanBert on 2010-07-02
Are your file systems listed in /etc/fstab?  If so, and they mount then go away for some reason, that is one sort of problem.

If they are not in fstab at all, that is another sort of problem.

Open a terminal window and try the following and post the results:
```

user@host:/path/ $ sudo fdisk /dev/sda

```
[i]NOTE -- The above assumes that you have one reasonably new HDD.
An older HDD might be **/dev/hda**[/i].

And
```

user@host:/path/ $ sudo  mount
... a list appears ...

```

The first list will tell you about whichever partitions are on your drive.

The second list will tell you about whichever partitions are currently mounted.

Now inspect your /etc/fstab armed with this information. What is part of your hardware but missing from fstab?  missing from the mount list?
These answers might help you solve your own problem. Someone will be here when you post the answers and your own analysis.

~~~ 0;-Dan

---

