---
title: "Random Logouts in 9.10"
date: 2009-12-02
forum: Hardware
---

### Post by mbrowning2000 on 2009-12-02
Hi Guys,

I recently installed 9.10 on a Presario sr1103wm, and it will log me out randomly while I'm using Firefox. I also have an issue with my mouse cursor not coming up when I log in, but i found that when i open Terminal and type anything my cursor shows.I think these two problems are related, but I have no idea on what it could be. If anyone thinks they can help it will be greatly appreciated. 

Here is some Basic info:

Intel Celeron 2.5ghz cpu
512 mb RAM
Intel 845g Chipset

Im still a somewhat beginner, so I dont know all of the commands to type in Terminal :confused:

---

### Post by mbrowning2000 on 2009-12-02
UPDATE: The Problem also happens when I try to change my wallpaper, Im thinking its a Graphics Driver issue

---

### Post by Daltonn0810 on 2009-12-02
system > administration > hardware drivers 

paste whats in there or install the [recommended] drivers

---

### Post by mbrowning2000 on 2009-12-02
ok, I did that and it Searched for drivers, but came back with nothing.

I have heard that Intel Integrated Graphics chips don't have proprietary drivers for Ubuntu.

---

### Post by Daltonn0810 on 2009-12-02
> **mbrowning2000 said:**
> ok, I did that and it Searched for drivers, but came back with nothing.

I have heard that Intel Integrated Graphics chips don't have proprietary drivers for Ubuntu.


i have a nvidia driver and it didn't  show up until i fully updated

system > administration > update manager 

or
goto system > prefrences > appearance and click on visual effects and make sure its set to none


just pray its not a graphics card problem and just a bad install

---

### Post by mbrowning2000 on 2009-12-02
Update manager says I'm up to date. Im gonna assume its a bad install and redo it and post back once its done.

---

### Post by mbrowning2000 on 2009-12-02
OK I reinstalled, and I figured something out. The cursor disappears when I up the resolution to 1280x1024(5:4), and i think thats whats causing the random logout. Is there any way to let me be able to use that resolution without the crashes?

---

### Post by Daltonn0810 on 2009-12-02
> **mbrowning2000 said:**
> OK I reinstalled, and I figured something out. The cursor disappears when I up the resolution to 1280x1024(5:4), and i think thats whats causing the random logout. Is there any way to let me be able to use that resolution without the crashes?



a graphics card driver maybe ...............

---

### Post by mbrowning2000 on 2009-12-02
I just reverted to Jaunty, because that was the last version that was installed on this PC where I had minimal problems. I will check after i get it updated to see if it fixed my graphics issue.

---

### Post by mbrowning2000 on 2009-12-03
OK, I have got Jaunty Running and Updated. It Fixed my Problem, so I guess ill have to stick with Jaunty until......Whenever. Thanks for Trying to Help Daltonn I really appreciate the attempt. :D

---

