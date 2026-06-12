---
title: "Removing Hard Drive"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by bman on 2006-04-23
](*,) I have been using 2 Drives, 1 (Windows XP Pro) 2 (Ubuntu)

don't want to use the drive with Ubuntu, newer drive coming, I removed it from the computer and started the computer, comes up with black screen saying grub error 12

What is that, how can I fix this?

---

### Post by FLeiXiuS on 2006-04-24
Boot up your Windows CD and load the 'Recovery Console'.  From there initiate the following commands.
```

fixboot
fixmbr

```

That oughta do it for you.

What happens is, grub is installed to the 'Master Boot Record' which is where your system looks for bootable devices.  If grub has been removed, where does the system go?  No where, it fauls at the error you received. 

Your telling windows that "Hey, I need you to tell the MBR that your the primary boot device!"  Afterwards, voila..all is said and done!

---

