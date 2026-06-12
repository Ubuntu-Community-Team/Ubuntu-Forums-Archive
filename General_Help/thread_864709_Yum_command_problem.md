---
title: "Yum command problem"
date: 2008-07-19
forum: General Help
---

### Post by fsloke on 2008-07-19
For example I run this c ommand:

yum search gcc

Then I have a list of related gcc repositor installer

then I choose...

yum install gcc.i386

then a warning prompt out:
[root@localhost ~]# yum search gcc
Loading "installonlyn" plugin
Existing lock /var/run/yum.pid: another copy is running. Aborting.

Why?

Last time I also using this command to install the gcc but at that time my pc go problem suddenly stop function( cursor cannot move and key board no functioning). Then I restart.... At that time the yum install no complete yet...

How to delete the /var/run/yum.pid... since there is no user using it....

thank

---

### Post by ilovelinux33467 on 2008-07-19
If you are using ubuntu, use apt-get instead

---

### Post by wannadumpwindows on 2008-07-19
It looks like you might have had another instance of "yum" running. Looks like you can only run one at a time, just like synaptic or add/remove programs.

Close the first one, then run it again, and you should be all set.

---

### Post by fsloke on 2008-07-19
> **wannadumpwindows said:**
> It looks like you might have had another instance of "yum" running. Looks like you can only run one at a time, just like synaptic or add/remove programs.

Close the first one, then run it again, and you should be all set.

There is no other pid is running... 

the pid is cause by last time problme... reboot OS

:(

---

### Post by wannadumpwindows on 2008-07-20
> **fsloke said:**
> There is no other pid is running... 

the pid is cause by last time problme... reboot OS

:(

What OS are you running?

---

