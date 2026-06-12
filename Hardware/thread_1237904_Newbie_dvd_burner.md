---
title: "Newbie dvd burner"
date: 2009-08-11
forum: Hardware
---

### Post by majikhotline on 2009-08-11
Hello ubuntu country,
i installed 2 dvd burners, how can i mount them so the OS can use them and i can view videos

thx

---

### Post by sergiom99 on 2009-08-12
By dvd burners you mean DVD-RW optical drives, right?
Are they SATA, IDE, USB? Are they installed in your PC and detected by the OS?
Try typing this in a terminal
```
 $ sudo lshw -c disk 
```

They should appear there.
If they are Ok, when you put a DVD in, a menu appears asking what to do: ie Play DVD.

Or you can do it by hand and typing:
```
sudo mount /dev/dvd /media/dvd 
```
where '/dev/dvd' is your drive and '/media/dvd' is the mountpoint you want.

Once its mounted  open your player and make it open the directory where you mounted the DVD.

Good luck!

---

### Post by majikhotline on 2009-08-12
ok now only one dvd reader has appeared in the computer window and it reads it as a cdrom.....why.....still not reading the dvd

---

### Post by sergiom99 on 2009-08-12
Post model/maker of your drive to search for specific issues.

Also, post the output of the commands I told you before.

---

