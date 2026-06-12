---
title: "hard drive space missing?"
date: 2008-08-01
forum: General Help
---

### Post by r0ot5 on 2008-08-01
Hi all, I have a problem that i'm not able to fix. Here the sitaution:

I'm currently running Ubuntu 7.04 Feisty Fawn, I have a 750GB Hard Drive. Now my problem....

When I check the total space use in /home I see 204GB but when I look at the space left I see 190GB, I don't understand why I just have 190GB when I only use 204GB of 750GB?!?

When you delete stuff from the Recycle Bin, I already tried all the cleaning techniques available on the forum but still no go!!! Is there anything i'm missing?


thx for you help, 


r0ot5

---

### Post by Elfy on 2008-08-01
Can you post the output of

```
df -h
```

---

### Post by r0ot5 on 2008-08-01
/dev/sda1             5,0G  2,5G  2,2G  53% /
varrun                497M  116K  496M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M   24K  496M   1% /dev
devshm                497M     0  497M   0% /dev/shm
/dev/sda2             683G  521G  128G  81% /home


I see that there is 521GB of stuff in home but when I look in this folder I only see 204GB???

---

### Post by Elfy on 2008-08-01
Check all trash folders - open nautilus as root and check both root and your user

```
gksudo nautilus
```

View hidden files

/home/.Trash-0
/home/*user*/.local/share/Trash


there is also the possibility that you have hidden files in your trash.

Also check your /home with baobab it will give you an idea of where space is being used

```
baobab
```

---

### Post by r0ot5 on 2008-08-01
can I just delete the file folder in Trash or I have to delete every files I find in the folder itself?

---

### Post by r0ot5 on 2008-08-01
thx forestpixie, everything works fine now, your the man, you saved my day, :)

---

### Post by Elfy on 2008-08-02
Glad I could help - if by any chance you come back perhaps you can mark thread solved and remember to do it in future :)

---

