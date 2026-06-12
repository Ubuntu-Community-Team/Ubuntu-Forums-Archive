---
title: "Broadcom WIFI help"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-06-28
I installed ndiswrapper 1.1 as instructed in a forum here. I got 2 errors but I still continued installing the driver. When I type ndiswrapper -l
I get bcmwl5 and it says hardware present.
But when I give 
modprobe ndiswrapper
Im getting
FATAL : Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel drivers/net/ndiswrapper/ndiswrapper.ko) : Operation not permitted.

Wat should I do? Plz help. ](*,)

---

### Post by acascianelli on 2005-06-28
try running 'ndiswrapper -m' then do a 'modprobe ndiswrapper'

---

### Post by mail2sona938 on 2005-06-28
ndiswrapper -m works. It says it is already present or something like that.

---

### Post by acascianelli on 2005-06-28
try 'insmod ndiswrapper'

---

### Post by mail2sona938 on 2005-06-29
it says 
ndiswrapper not found : No such file or directory
Should I do it in some specific directory?? Thnx for the help so far...Keep helping..

---

### Post by acascianelli on 2005-06-29
I just noticed that youve installed NDISWrapper 1.1, I think that might be the problem because I was told that newer versions require kernel patching and such.

Whats the problem with the version that is in the repository?  Where did you get instructions on installing version 1.1, I've been having a few problems with crashing during boot up and I've been wanting to upgrade to a newer version but haven't found any good instructions.

---

### Post by mail2sona938 on 2005-06-30
do u mean that I shouldnt have installed NDISwrapper and that ubuntu comes packaged with ndiswrapper?? How to use the ndiswrapper that coms with ubuntu after I reinstall ubuntu???

---

### Post by acascianelli on 2005-06-30
You should try removing the version you installed, and install the version from the repository.  Its a little old, but it should work none the less.

---

### Post by mail2sona938 on 2005-06-30
Thanks so much...I was successful in installing the driver for my wifi. Now I have to download the GUI applet that manages connection..Keep in touch...

---

### Post by mail2sona938 on 2005-06-30
Thanks a lot dude....Ive got it finally....now Im online with my ubuntu system... :)

---

### Post by acascianelli on 2005-06-30
[QUOTE=mail2sona938]Thanks a lot dude....Ive got it finally....now Im online with my ubuntu system... :)[/QUOTE]
 ;) no problemo

---

