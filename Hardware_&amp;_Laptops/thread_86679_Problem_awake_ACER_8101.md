---
title: "Problem awake ACER 8101"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by quai_k8 on 2005-11-06
Hi all .. I got a ACER 8101 and Breezy !!

I don't wanna play with this computer that's why i've not installed
the ATI drivers ... 

My computer knows how to sleep but not how to awake itself
when it awakes .. it automaticaly shut down after I entered my password !!

any idea to fix it ??? 

THX in advance

---

### Post by Teroedni on 2005-11-06
write
cat /proc/acpi/info

and post the information here

You probably have to get a newer acpi.
If anybody else knows how to fix this go ahead;)

If not i guess i just have to search a little bit more

---

### Post by Teroedni on 2005-11-06
also i found a script that may work


[http://csd.informatik.uni-oldenburg.de/~eagle/acpid.html](http://csd.informatik.uni-oldenburg.de/~eagle/acpid.html)


direct download
[http://csd.informatik.uni-oldenburg.de/~eagle/acpid/my.acpid-conf.tar.gz](http://csd.informatik.uni-oldenburg.de/~eagle/acpid/my.acpid-conf.tar.gz)


tell me if it works

---

### Post by quai_k8 on 2005-11-06
Thx for ur answers ^^

> quaik8@KQ8:~$ cat /proc/acpi/info
version:                 20050729


I'm trying the script yo posted ... rezults :

- 1st sleep/awake = black screen (never awake ^^)
- 2nd sleep/awake = OK
- 3rd sleep/awake = OK
- 4th sleep/awake = OK
- 5th sleep/awake = black screen

It's better but not perfect ^^

I continue to search !

---

