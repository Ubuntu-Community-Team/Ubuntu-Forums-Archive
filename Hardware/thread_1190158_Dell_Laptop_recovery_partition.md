---
title: "Dell Laptop recovery partition"
date: 2009-06-17
forum: Hardware
---

### Post by xixpsychoxix on 2009-06-17
I have an older Dell inspiron 600m that i got originally with windows xp. I recently (just a few days ago) installed Ubuntu 9.04 on it. This computer came with a recovery partition and a utility partition on it and i had the partition tool save those two in case i wanted to go back to my windows setup. For some reason in the GRUB menu i can access the utilities partition but not the recovery partition. if it helps any, the recovery partition is FAT32 and the other is FAT16. Can anyone tell me why the recovery partition is inaccessible and how to access it?

---

### Post by recluce on 2009-06-17
> **xixpsychoxix said:**
> I have an older Dell inspiron 600m that i got originally with windows xp. I recently (just a few days ago) installed Ubuntu 9.04 on it. This computer came with a recovery partition and a utility partition on it and i had the partition tool save those two in case i wanted to go back to my windows setup. For some reason in the GRUB menu i can access the utilities partition but not the recovery partition. if it helps any, the recovery partition is FAT32 and the other is FAT16. Can anyone tell me why the recovery partition is inaccessible and how to access it?

Check if this works for you (it worked for my otherwise inaccessible Dell Diagnostics partition)

Find out the partition number of your recovery partition as seen by grub. In my case, it is (hd0,0).

In grub's boot screen, press C to enter the console, you will see the grub> prompt.

Enter "root (hdx,y)" (where x,y are the numbers you found for your recovery partition)

Enter "chainloader +1"

Enter "boot"

This should hopefully start your recovery partition, if the OS on it is chainloaded.

---

### Post by xixpsychoxix on 2009-06-17
the problem is that i can't see the partition with grub so im not exactly sure how to figure out which number it is. How do i figure that out cuz its not listed on grub's menu?

---

### Post by uncreative.ca on 2009-10-26
[FONT=Verdana]I've got a Dell Precision M4400 and ran into the same problem. I could run the diagnostics from the BIOS by pressing F12, but when they would complete it would return to the GRUB menu instead of booting the diagnostic partition.

Thanks recluce for the help! I've only got one HD in there listed as sda1, with the Dell partition being the first thing on the drive. This worked for me from the GRUB command line:[/FONT]

[INDENT][FONT=Courier New]root (hd0,0)[/FONT]
[FONT=Courier New]chainloader +1[/FONT]
[FONT=Courier New]boot[/FONT]
[/INDENT][FONT=Courier New][FONT=Verdana]
[/FONT][FONT=Verdana]Cheers,
uncreative[/FONT]
[/FONT]&#9660;
&#9650;

---

