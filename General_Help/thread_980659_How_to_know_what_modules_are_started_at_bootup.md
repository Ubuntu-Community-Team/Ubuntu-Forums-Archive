---
title: "How to know what modules are started at bootup ?"
date: 2008-11-13
forum: General Help
---

### Post by sreejithemk on 2008-11-13
Hi,

I'm using Ubuntu for a while and now sticking with 8.04. But the problem I'm facing is that the time required to boot completely into the GNOME desktop is 75 seconds (When the Hard disk stops spinning). I'm using a Core 2 Duo machine with 1GB RAM. But its too slow in boot and GNOME starts very slowly after GDM login. After that applications works perfectly.

I assume this is due to starting unwanted services and modules at bootup. I've installed readahead and profiled my bootup. But still its slow.

I don't think I need to load much modules at bootup (like restricted-kernel-modules). 

Can anyone tell me how to know the services and modules loaded during bootup and how to remove the unwanted ?

I'm aslo attaching the /etc/readahead/boot. I think it contain those loaded at bootup, right ?

---

### Post by alwayshere on 2008-11-13
For start up programs 

go to system 
then
preferences 
then 
sessions

---

### Post by sreejithemk on 2008-11-13
Ya I know it. but it deals only with the GNOME session. I want the services and modules before that. I'm also using Boot Up Manager.....

Any other ideas ?

---

### Post by Peter09 on 2008-11-13
install BUM (Boot Up Manager) Its in the repositories. It will show you Services starting at Boot. 

As for Modules I think modprobe has an option to list modules

Yep```
modprobe -l
```

---

### Post by iponeverything on 2008-11-13
Take a look at 

System -> Administration -> Services

Those are started at boot. Just google around to find out which ones you want started or need, post back if you have questions.

---

### Post by sreejithemk on 2008-11-13
Okay thanks.

I've used that services option to disable some services such as bluetooth and schedulers (cron) etc. I've also used BUM to remove services. But still my PC bootup is slow.

The bootup till GDM is fare but I've t wait for some 20 sec for the complete GNOME desktop to be active..

Any tweaks to speed up X ?

---

### Post by Peter09 on 2008-11-13
Hit the ESC key at the GRUB prompt and then E (for edit) remove the boot options 'quiet'. This will let you see the boot process and might give you an idea of where it is slow.

---

### Post by aysiu on 2008-11-13
> **Peter09 said:**
> Hit the ESC key at the GRUB prompt and then E (for edit) remove the boot options 'quiet'. This will let you see the boot process and might give you an idea of where it is slow.
I have *quiet* but still see the boot process.

If you remove *splash*, that allows you to see the boot process. You can keep *quiet*.

---

### Post by binbash on 2008-11-13
for mods load at boot time

cat /etc/modules

---

### Post by sreejithemk on 2008-11-13
Thanks. Actually its not the bootup which is slow now, but GDM loading and GNOME loading is too slow.

Any way to solve this ?

---

### Post by philinux on 2008-11-13
See if it's compiz. Set desktop effects to none to compare login times. On intrepid its about 29 seconds as compiz seems to hang,it's bugged too. I dont think Hardy did this at all.

---

### Post by TeXtonyx on 2008-11-13
How full is your hard drive or Linux area? Processes will start 
to slow at 80% full and are quite slow at 95% full. The situation
is worse with the Windows OS.

---

### Post by sreejithemk on 2008-11-13
I've disabled the Compiz and I've 22GB of free space on Ubuntu partition. I dont thinks it Compiz. It doesn't matter with me. But its something else ?

The freshly installed Ubuntu was fine. But I'm using it for a while now, updated it. But its too slow now.

---

