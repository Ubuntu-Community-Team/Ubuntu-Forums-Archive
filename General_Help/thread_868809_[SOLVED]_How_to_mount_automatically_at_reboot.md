---
title: "[SOLVED] How to mount automatically at reboot?"
date: 2008-07-24
forum: General Help
---

### Post by Vadi on 2008-07-24
I need to do the following:


> sudo mount -t vboxsf -o uid=vadi Systems /home/vadi/share
sudo mount -t vboxsf -o uid=vadi Programs /home/vadi/share2


At every bootup. Is it possible to automate this?

---

### Post by Potatoj316 on 2008-07-24
Yes, you can edit your fstab to control what mounts when you boot.  Im not sure how to do this though but im sure if you ask google nicely it will tell you.

---

### Post by Vivaldi Gloria on 2008-07-24
> **Vadi said:**
> ... Is it possible to automate this?

I'm not sure how you can add that to fstab (google "vboxsf fstab") but you can add it to

```
/etc/rc.local
```

as follows:

```
mount -t vboxsf -o uid=vadi Systems /home/vadi/share&
mount -t vboxsf -o uid=vadi Programs /home/vadi/share2 &
exit 0
```

Now it'll mount automatically.

---

### Post by Vadi on 2008-07-24
That's what I found out on the virtualbox forums too, thanks

---

### Post by Vivaldi Gloria on 2008-07-24
> **Vadi said:**
> That's what I found out on the virtualbox forums too, thanks

You're welcome mate.

---

### Post by wurzelkp on 2008-07-25
So what you're saying is that I need to get VirtualBox as well? Then  just type the commands shown into the comand line and reboot?

---

### Post by Vadi on 2008-07-25
wurzelkp, I think your issue is a different one. Please start another thread and give us a link to look at.

---

### Post by wurzelkp on 2008-07-25
Sorry Vadi, it's just that my question seemed rather similar in nature.  You'll have have to forgive me as I'm very new.  Here is a link to my question: 
[http://ubuntuforums.org/showthread.php?t=869404]("http://ubuntuforums.org/showthread.php?t=869404")
Thanks

---

### Post by Vadi on 2008-07-25
That's okay, and I replied there. Our questions are very much different too ;)

---

