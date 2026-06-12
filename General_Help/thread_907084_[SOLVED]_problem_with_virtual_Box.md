---
title: "[SOLVED] problem with virtual Box"
date: 2008-09-01
forum: General Help
---

### Post by Uchiha_madara on 2008-09-01
I need to install WinxP as virtual OS to install visual studio 2005 on it ...


i Made the virtual machine the problem is :

when i start the machine the problem is this message :

" The Virtual Drive is Missing you must to install the virtual drive to make it work"


what shall i do i need to install visual studio 2005 necessary please help??

---

### Post by rouben on 2008-09-01
I never encountered this error myself, but I think VirtualBox is trying to tell you that it can't find the file that's supposed to represent your virtual machine's hard disk. When you created the virtual machine, did you create any virtual disks (hard drives) for it? Did you set them up as SATA? Can you check your hard disk to make sure the files for the virtual disks are still there?

Let me know if you need help with any of the above tasks...

---

### Post by Bakon Jarser on 2008-09-01
that is a strange message.  I happen to have this link in my clipboard right now, maybe it will help.

[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

---

### Post by Uchiha_madara on 2008-09-01
> **rouben said:**
> I never encountered this error myself, but I think VirtualBox is trying to tell you that it can't find the file that's supposed to represent your virtual machine's hard disk. When you created the virtual machine, did you create any virtual disks (hard drives) for it? Did you set them up as SATA? Can you check your hard disk to make sure the files for the virtual disks are still there?

Let me know if you need help with any of the above tasks...

i made the hard disk on 10 GB ntfs drive, if this cause any trouble ???
i made previous hard disk but i removed it .....!!!

---

### Post by Uchiha_madara on 2008-09-01
> **Bakon Jarser said:**
> that is a strange message.  I happen to have this link in my clipboard right now, maybe it will help.

[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

in this Link you gave me I read this note :
> 
Note: The VirtualBox that you have in the Add/Remove Programs list is different because it is the Open Source Edition. This is generally more difficult to configure, so use the normal VirtualBox program found in the link above.



I have installed the virtual box from the terminal if there is any problem with that ???

---

### Post by Uchiha_madara on 2008-09-01
> **Bakon Jarser said:**
> that is a strange message.  I happen to have this link in my clipboard right now, maybe it will help.

[http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

thanks a lot it works it is really works but the problem still with Memory,
it is 265 ram i 'll increase it to 1G

thanks a lot dude:guitar::lolflag:

---

