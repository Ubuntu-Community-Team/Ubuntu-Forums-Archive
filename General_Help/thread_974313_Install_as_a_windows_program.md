---
title: "Install as a windows program"
date: 2008-11-07
forum: General Help
---

### Post by Stan57 on 2008-11-07
I tryed to install ubuntu with the windows install as a program,it didnt work. I uninstalled ubuntu in the windows uninstall programs and tryed to install again no good. I uninstalled again and now i have 2 ubuntu on bootup. The install did not create a partition so i cant remove it that way.
How can i remove the 2 ubuntus from the boot menue? the uninstall doesnt work properly,it should be removing everything but its leaving leftovers

Thanks
Stan

---

### Post by yt_l9 on 2008-11-07
I've only used wubi once so I hope this helps at least a little.

Grumpy Mole has a great walkthrough as to how to edit the grub bootloader but if you have a duplicate OS it will not delete it (again this works in regular Ubuntu I don't know about wubi)
you can find it here
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by anystupidname on 2008-11-07
> **Stan57 said:**
> I tryed to install ubuntu with the windows install as a program,it didnt work. I uninstalled ubuntu in the windows uninstall programs and tryed to install again no good. I uninstalled again and now i have 2 ubuntu on bootup. The install did not create a partition so i cant remove it that way.
How can i remove the 2 ubuntus from the boot menue? the uninstall doesnt work properly,it should be removing everything but its leaving leftovers

Thanks
Stan

@YD_9T: If I'm not mistaken, the install he is talking about installs to a folder in the NTFS partition and adds an entry to the boot.ini

@Stan: Are you running XP or Vista?
Assuming XP, you'll just need to edit your boot.ini and remove the 2 unwanted entries. WIN+BREAK>Advanced tab>ALT+T>ALT+E

---

### Post by Stan57 on 2008-11-07
> **anystupidname said:**
> @YD_9T: If I'm not mistaken, the install he is talking about installs to a folder in the NTFS partition and adds an entry to the boot.ini

@Stan: Are you running XP or Vista?
Assuming XP, you'll just need to edit your boot.ini and remove the 2 unwanted entries. WIN+BREAK>Advanced tab>ALT+T>ALT+E

Running Vista Premium 64bit,it did install to the x86 folder btw

---

### Post by anystupidname on 2008-11-08
Gah! You made me boot to Vista... ::shudder::

Run CMD
BCDEDIT /?
for info

BCDEDIT /enum
should show you the extra ubuntu entries

BCDEDIT /deletevalue <whatever>
should do what you need

---

### Post by Stan57 on 2008-11-10
> **anystupidname said:**
> Gah! You made me boot to Vista... ::shudder::

Run CMD
BCDEDIT /?
for info

BCDEDIT /enum
should show you the extra ubuntu entries

BCDEDIT /deletevalue <whatever>
should do what you need


sorry but what value do i delete identifier,device,path,discreption,Real-Mode Boot Sector? Dont wanty to make a mistake lol

---

### Post by anystupidname on 2008-11-10
That is why you use the backup/export option first :-)
Examples I looked at online suggest it is identifier but don't take my word for it...

---

### Post by Stan57 on 2008-11-12
> **anystupidname said:**
> That is why you use the backup/export option first :-)
Examples I looked at online suggest it is identifier but don't take my word for it...

Well,when i read that Ubuntu can be installed as a windows program and no indcation that it would be a multi boot operation. to me there would be no reason to backup my boot records. I would also expect that the uninstaller work properly and undo what it has done to install Ubuntu. I have filed a bug report for this problem :)

Thanks for all your help and time
Stan

---

