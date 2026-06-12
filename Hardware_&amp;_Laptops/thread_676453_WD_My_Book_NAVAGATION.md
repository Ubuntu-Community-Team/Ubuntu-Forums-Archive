---
title: "WD My Book NAVAGATION"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by xfearxnxloathing on 2008-01-23
my external harddrive, WD: My Book shows up and is functional the only problem i'm having is that i am trying to backup/ghost my complete gutsy/compizfusion install onto it but i dont even know the path to navigate to through the terminal.  i've been reading several tuts on how this is done and have been able to write to this drive.  just now i read this: [https://bugs.launchpad.net/ubuntu/+bug/108980](https://bugs.launchpad.net/ubuntu/+bug/108980), is this true?!  if so, then why all these tuts on backing-up installs/files/folders to ext. hd's...?  when i try to navigate throught the terminal as in the picture below i get that message so i think it's cause i dont have permission but it seems i do, do i?  did i type the right directory in the terminal?

```
cd /blah/blahblah
```

i've tried ```
cd /dev/sda1 : cd /dev/My Book : cd /media/My Book : cd /My Book
```

it's a Western Digital: My Book 500gig and is again, fully functional.  please help!

:confused:

[IMG]http://i23.photobucket.com/albums/b366/ecko7two90/Screenshot-1.png[/IMG]

---

### Post by xfearxnxloathing on 2008-01-24
bump

---

### Post by xfearxnxloathing on 2008-01-24
hey bro, why dont you try putting "\" before the spaces in the terminal or else it wont recognize.  

```
cd /media/My\ Book
```


[SOLVED]

---

