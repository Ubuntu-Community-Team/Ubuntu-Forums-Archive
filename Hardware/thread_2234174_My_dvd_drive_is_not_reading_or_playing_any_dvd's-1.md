---
title: "My dvd drive is not reading or playing any dvd's-14.04"
date: 2014-07-13
forum: Hardware
---

### Post by tears of the river on 2014-07-13
I have a lenovo B570e and I freshly installed ubuntu 14.04 on it. However Even after adding the dvd repositories the dvd's arent getting read. I have checked the same dvd's on other laptops with windows and they are playing just fine.

I do believe that the dvd drive is recognised as when I execute:
```
eject
```
in the terminal it works perfectly fine.

Any help would be really appreciated and thanks in advanced

---

### Post by yancek on 2014-07-13
What is on the DVD?  If you are referring to video on dvd, the post below should help.  If you have done that already, more specifics on what happens and what you mean my 'in the terminal it works fine?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by tears of the river on 2014-07-14
What I mean is that when I try to run a dvd containing some software or any burned dvd that would be automatically played or recognized in windows (E.g. A DVD containing Microsoft Office Software or Ubuntu DVD) does not get recognized and does not run in Ubuntu. I have installed restricted formats so I know that it is not the issue. However at the same time I know that the dvd-Drive is recognized by Ubuntu because the Eject command from terminal is running perfectly. 

That's what I am confused at as to what is the exact problem when my Drive is recognized but it is not running anything. Also I have booted Live Ubuntu Disk on it before so I know that the problem is not that the dvd Drive doesn't work.

---

### Post by yancek on 2014-07-14
Microsoft Office software won't run on Ubuntu.  Not really sure what you are trying to do with that or with an Ubuntu DVD.  A DVD is usually shown in an icon in the left panel and clicking it will open it in a file manager.  You should also be able to access if by changing to the /media directory.  Here it will likely show with a uuid number and you can go to /media to see what is there, then insert the DVD and you should see a new uuid.

---

