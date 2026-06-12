---
title: "s10-3 doesnt wake up after sleep ,found solution ,gksudo gedit /etc.., NOT working"
date: 2012-07-17
forum: Hardware
---

### Post by giantpow on 2012-07-17
hi and i am noob to linux , i read that wake up is a "common problem?"
they say the fix is to add a boot parameter intel.idle.max_cstate=0

i press e in the boot manager add the parameter and then i log in to lubuntu to make this permanent but if i enter gksudo gedit /etc/default/etc i enter my pass **nothing appears**:confused::confused::confused:

---

### Post by giantpow on 2012-07-17
I am glad to w8 for an answer because i really liked the lubuntu its snappy and clean.
The only problem is that it never wakes up...

---

### Post by steeldriver on 2012-07-17
I don't think there is any such file as /etc/default/etc -  if you try to edit a non-existant file it will just create a new empty file - did you mean **/etc/default/grub **maybe?

---

### Post by giantpow on 2012-07-17
> **steeldriver said:**
> I don't think there is any such file as /etc/default/etc -  if you try to edit a non-existant file it will just create a new empty file - did you mean **/etc/default/grub **maybe?
Yes nothing shows up

---

### Post by Toz on 2012-07-17
Do you have gedit installed? I believe the default text editor in lubuntu is leafpad, so therefore:
```
gksudo leafpad /etc/default/grub
```

BTW, you might also consider trying the **nohpet** kernel parameter if you are using kernel 3.x (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871891]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871891"))

---

### Post by giantpow on 2012-07-18
> **Toz said:**
> Do you have gedit installed? I believe the default text editor in lubuntu is leafpad, so therefore:
```
gksudo leafpad /etc/default/grub
```BTW, you might also consider trying the **nohpet** kernel parameter if you are using kernel 3.x (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871891))
```
gksudo leafpad /etc/default/grub
```
opens a notebook that is empty :confused:

---

### Post by giantpow on 2012-07-20
After realizing that leafpad doensnt really work i installed finally  gedit .
i enterred the parameters like this "quiet splash intel.idle.max_cstate=0 nohpet"
updated grub 
but still sleep is still not working :(

---

### Post by Toz on 2012-07-20
Try using **hpet=disable** instead ( with and without intel.idle.max_cstate=0 ).

---

### Post by giantpow on 2012-07-21
tried anything NOTHING, this problem is getting very annoying..... 
[https://wiki.archlinux.org/index.php/Lenovo_Ideapad_S10-3#Suspend_.26_Hibernate](https://wiki.archlinux.org/index.php/Lenovo_Ideapad_S10-3#Suspend_.26_Hibernate)
what is acpid

---

### Post by giantpow on 2012-07-21
so ok suggestion from arch linux worked and now i have sleep :popcorn:
but a new problem appeared  
 [http://ubuntuforums.org/showthread.php?p=10900038#post10900038](http://ubuntuforums.org/showthread.php?p=10900038#post10900038)
its funny how "ubuntu works out of the box"

---

### Post by Toz on 2012-07-21
> **giantpow said:**
> so ok suggestion from arch linux worked and now i have sleep :popcorn:
Glad to hear that sleep now works
> but a new problem appeared  
 [http://ubuntuforums.org/showthread.php?p=10900038#post10900038](http://ubuntuforums.org/showthread.php?p=10900038#post10900038)
its funny how "ubuntu works out of the box"
The link references language support. Perhaps it is best to mark this thread (sleep on an s10-3) as solved and create a new thread for this other issue.

---

### Post by wittyman37 on 2012-12-12
I struggled with this for months and months.  I have over 200 Lenovo S10-3 netbooks and I decided to go back to 10.04.4 Edubuntu and it works wonderfully.  Will this be addressed in the next LTS release?  12.04 works without issue on Lenovo S10e netbooks.

---

### Post by Toz on 2012-12-12
> **wittyman37 said:**
> I struggled with this for months and months.  I have over 200 Lenovo S10-3 netbooks and I decided to go back to 10.04.4 Edubuntu and it works wonderfully.  Will this be addressed in the next LTS release?  12.04 works without issue on Lenovo S10e netbooks.

Did you try the **nohpet** or **hpet=disable highres=off nohz=off** kernel parameters as referenced in post #9 and confirmed in post #10?

---

### Post by Biblioclasta on 2012-12-12
[B]
hpet=disable highres=off nohz=off

works for me
Thanks!
[/B]

---

