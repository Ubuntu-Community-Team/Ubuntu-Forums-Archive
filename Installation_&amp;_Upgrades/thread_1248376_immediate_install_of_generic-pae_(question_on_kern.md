---
title: "immediate install of generic-pae? (question on kernel images)"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by edgue on 2009-08-24
Hello there,

two questions:

a) Karmic will come with the 'generic-pae' kernel that supports > 4GB of RAM. Is there a way to install this kernel (instead of the 'generic' one with the 'first install' that takes place when I insert the CD? [ compared to: have the generic kernel installed, boot the first time, install generic-pae; reboot; uninstall the generic kernel ]

b) i am running with the server kernel for quite a while ... but kept the generic stuff around. Just wondering: is it safe, to completely throw away the generic kernel; and if so: which packages do I need to remove?

---

### Post by stlsaint on 2009-08-24
> **edgue said:**
> Hello there,

two questions:

a) Karmic will come with the 'generic-pae' kernel that supports > 4GB of RAM. Is there a way to install this kernel (instead of the 'generic' one with the 'first install' that takes place when I insert the CD? [ compared to: have the generic kernel installed, boot the first time, install generic-pae; reboot; uninstall the generic kernel ]

b) i am running with the server kernel for quite a while ... but kept the generic stuff around. Just wondering: is it safe, to completely throw away the generic kernel; and if so: which packages do I need to remove?



a. I would wait until the pae kernel becomes stable and in full swing production...not just a rc!

b. technically>yes...good practice>no...you never want to be stuck with just one kernel unless your a absolute expert in ubuntu and can re-build your kernel in case something goes wrong!

---

### Post by edgue on 2009-08-24
> **stlsaint said:**
> a. I would wait until the pae kernel becomes stable and in full swing production...not just a rc!

b. technically>yes...good practice>no...you never want to be stuck with just one kernel unless your a absolute expert in ubuntu and can re-build your kernel in case something goes wrong!

Sorry, you are answering some easy questions I didnt even ask :(

a) I asked for _how_ to do that ... not on _when_ to do it. I understand that something that is called "alpha" is not ready for a production system. 

b) Who told you that I would rely on ONE kernel? I usually dont delete old kernels - so I got 5 or 6 server kernels around. Plus: I am talking about removing "the kernel family" that I am not at all using in the first place. The only reason for me to remove the "generic" kernel is the fact that they want to be upgraded as long as they are around.

---

### Post by mcduck on 2009-08-24
> **edgue said:**
> Hello there,

two questions:

a) Karmic will come with the 'generic-pae' kernel that supports > 4GB of RAM. Is there a way to install this kernel (instead of the 'generic' one with the 'first install' that takes place when I insert the CD? [ compared to: have the generic kernel installed, boot the first time, install generic-pae; reboot; uninstall the generic kernel ]

b) i am running with the server kernel for quite a while ... but kept the generic stuff around. Just wondering: is it safe, to completely throw away the generic kernel; and if so: which packages do I need to remove?

a) Not likely. Ubuntu's installer tries to be usable even for less computer literate people, and having too many options like this would make that rather hard.

b) It's safe. Remove "linux-generic" and other generic kernel meta packages, and of course the actual kernel images, headers & restricted module packages.

---

### Post by edgue on 2009-08-24
> **mcduck said:**
> a) Not likely. Ubuntu's installer tries to be usable even for less computer literate people, and having too many options like this would make that rather hard.

b) It's safe. Remove "linux-generic" and other generic kernel meta packages, and of course the actual kernel images, headers & restricted module packages.

Thank you very much. I dont think that another "hidden" expert menu to make such a choice would not be too much of a deal. There is an "expert" menu for disk partitioning available too. And that is more complicated and dangerous than the three options menu ("you can choose between: generic, generic-pae, and server) I would spend here ...

---

