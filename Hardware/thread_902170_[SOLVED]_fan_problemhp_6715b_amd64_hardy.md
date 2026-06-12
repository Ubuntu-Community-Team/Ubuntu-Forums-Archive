---
title: "[SOLVED] fan problem:hp 6715b amd64 hardy"
date: 2008-08-27
forum: Hardware
---

### Post by 6715b_user on 2008-08-27
Recently I got a new HP 6715b Notebook and installed the 64 Bit version of Ubuntu (Hardy) right away.

Most things work, but the fan is driving me crazy. The fan is pretty loud and is running way too often. The fan runs maybe for two minutes, then goes off for a short period of time then it starts back up again. On, Off, On, Off, On, Off....forever! All of that happens without putting any demand on the cpu! Its really annoying.

I tried fancontrol, but I think fancontrol is not working with my notebook. Is there any other option two control the fan? What mechanism triggers the fan to start, and how can I control it? Should I maybe switch to the 32 bit version of Ubuntu or an older version? Or maybe another Linux distribution.

Please help, I cant use Ubuntu like that!

---

### Post by 6715b_user on 2008-08-27
To add some more information:

The cpu temperature goes up to 45 degrees C and the the fan kicks in until the cpu is down at 40 degrees C. Then the cpu goes up to 45 again and the cpu kicks in... and all of this without any cpu load! Is it normal that the cpu would heat up without anything to do really?

---

### Post by sergiom99 on 2008-08-27
I have a DV6646us with Kubuntu Hardy 32bits and didnt notice it.
I will pay more attention and post back if I notice anything.

Good luck.

---

### Post by 6715b_user on 2008-08-28
I'm sure, nobody cares, but I found a solution!!! After hours and hours of searching the web, reading countless threads and installing about five different linux distros I was ready to give up (already ordered a cooling pad!). But then I tried a last google search in german language instead of english, and voilà I found it. It really is a miracle, I must have been so frustrated that GOD himself had pity with me and put that report there... 

The processor kicked in with 40% at 45 degrees C. Now I was able to change that to 10%, and thats almost inaudible! And it is really not complicated to do

[http://www2.informatik.hu-berlin.de/~jbirkhol/hp6715/index.html](http://www2.informatik.hu-berlin.de/~jbirkhol/hp6715/index.html)
Unfortunately it is in german, but it has something to do with /proc/acpi/dsdt ...even if you dont understand german you should be capable of doing it..

---

