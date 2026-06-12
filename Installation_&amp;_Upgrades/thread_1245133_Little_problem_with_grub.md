---
title: "Little problem with grub"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by b.charles.gagne on 2009-08-20
Hello, i'm having a little problem with grub. I've installed Ubuntu 9.04 from windows (as a software into it) to boot from grub but when I've uninstalled it the grub bootloader wasn't removed and I still have the choice between ubuntu (wich doesn't find the files to boot) and windows XP. But now I am planning to upgrade my Windows XP to Vista with an upgrader Cd (not a full version) and I was wondering if this Cd was able to redo my boot sequence or if I have to do it myself before starting my install

---

### Post by Partyboi2 on 2009-08-20
Hi, you can remove the Ubuntu entry ( c:\wubildr.mbr="Ubuntu")  from the C:\boot.ini file to stop Ubuntu appearing as a option when you boot up.

---

### Post by b.charles.gagne on 2009-08-20
and I will be able to upgrade to vista witout a problem?

---

### Post by b.charles.gagne on 2009-08-20
P.S. : thank you very much for your fast answer

---

### Post by b.charles.gagne on 2009-08-20
hum.... i'm a little tricked... even with hided files turned to be seen... It doesn't seem like I even HAVE a C:\boot.ini file in my computer....

---

### Post by Partyboi2 on 2009-08-20
> **b.charles.gagne said:**
> and I will be able to upgrade to vista witout a problem?
I am not sure if you left it as it is if Vista would have a problem with it or not (Wouldn't think so). But it is easy to remove the entry for Ubuntu in the boot.ini before upgrading.

---

### Post by Partyboi2 on 2009-08-20
> **b.charles.gagne said:**
> hum.... i'm a little tricked... even with hided files turned to be seen... It doesn't seem like I even HAVE a C:\boot.ini file in my computer....
Ok, try this
> **Edit the Boot.ini File**

  To view and edit the Boot.ini file:  
[LIST=1]
[*]Right-click **My Computer**, and then click **Properties**.   -or- 
     Click **Start**, click **Run**, type sysdm.cpl, and then click **OK**.
[*]On the **Advanced** tab, click **Settings** under **Startup and Recovery**.
[*]Under **System Startup**, click **Edit**.
[/LIST]


---

### Post by b.charles.gagne on 2009-08-20
then could you tell me which part of this text do I have to delete because I don't want to mess anything up

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"


and I guess after deleting the right part i'll just have to click  >file>save and then reboot my computer to test

---

### Post by Partyboi2 on 2009-08-20
Delete this part
```
 C:\wubildr.mbr = "Ubuntu"
```
then save and reboot

---

### Post by b.charles.gagne on 2009-08-20
Worked Perfectly!! I'm sure too it wouldn't have messed up with vista but I thing I would have kept the same boot menu after installing vista... So it didn't cost much to me to do so before upgrading

Thank you for your gracefull (and FAST) help and I hope i've been clear explaining my problem 

P.S.: I love internet.. i'm in canada so... you're a little far and getting your help without it would have been impossible

---

### Post by Partyboi2 on 2009-08-20
Happy to have helped :)

---

