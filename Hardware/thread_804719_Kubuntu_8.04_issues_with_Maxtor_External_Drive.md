---
title: "Kubuntu 8.04 issues with Maxtor External Drive"
date: 2008-05-23
forum: Hardware
---

### Post by ringoShells on 2008-05-23
Before anyone gets mad that this has been covered before. i know. i tried much of what i saw....i've gotten nowhere.

I upgraded to 8.04, and my drive worked beautifully. Then suddenly today, nothing. I plugged it into a windows machine, and it loaded fine...so i have no idea what has gone wrong.

Does anyone have any advice on how i could get this going?

I apologise if i'm not giving much of a jumping off point for any potential advice...but i'm completely unsure what to do about the problem. I've tried poking around in fstab, forcing mounts, "safely removing" the dive from XP, and then plugging back into kubuntu. 

This is really driving me up the wall as all my files are on that drive.

Any help offered would be greatly appreciated.

---

### Post by ringoShells on 2008-05-23
Hmm...after a reboot it loads the drive, but i cannot access it simply because "permissions denied".

"chmod -R 777" on the drive ("OneTouch4") be the answer?

---

### Post by ringoShells on 2008-05-23
****SOLVED****

(seemingly...for now)

i used

```
pmount-hal /dev/sdb1
```

where "/dev/sdb1" is from fstab on the line

```
/dev/sdb1 /media/OneTouch4 auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0
```

now i seem to be able both read and write from the drive...so all is fixed. ....if only i knew why it broke to begin with!

....add this to the pile of potential answers to a USB HDD issue i guess.

---

### Post by ringoShells on 2008-05-24
i hate to bump this thread time and time again

...but i was wondering if anyone had any advice on automating that pmount-hal call, so i don't have to do it every time i connect the drive?

---

