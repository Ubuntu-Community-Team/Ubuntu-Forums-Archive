---
title: "mounting a new HDD"
date: 2008-11-24
forum: General Help
---

### Post by hirohitosan on 2008-11-24
Sorry for this basic question.
I just added a new Ext2 HDD and I don't know how to mount it.
And how can I mount it at startup

Thanks :confused:

---

### Post by decard_pain on 2008-11-24
go into gparted and see if it's there in the drive list.
you may need to install gparted
sudo apt-get install gparted

you can mount it from inside gparted 
but it should auto mount by default 
so just see it the drive is detected  because this could be a slave master problem

---

### Post by hirohitosan on 2008-11-24
well I don't have gparted. I installed server edition so I don't have X server. I need a command line

---

### Post by decard_pain on 2008-11-24
ok it will be something like this

sudo mount -t /dev/sdb1 /media/disk2
(you may need to make a directory called /media/disk2)

this command may not be correct as i don't mount by command line very oftern
i'll look into this a little further just wait 10 -15 min

---

### Post by decard_pain on 2008-11-24
[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)

look here you should fund the right one half way down the page

---

