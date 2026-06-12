---
title: "Grub4dos booting into ubuntu help!!"
date: 2008-09-09
forum: General Help
---

### Post by OSUfrk09 on 2008-09-09
When i go to boot up ubuntu i get this... [GRUB4Dos 0.4.3 2008-06-03, Memory :638k/510M, codeEnd:0x41A38 Minimal BASH-like line editing is supported| and it gives me a dos menu and doesn't allow me to boot into ubuntu. 

GRUB4Dos 0.4.3 2008-06-03, Memory :638k/510M, codeEnd:0x41A38 Minimal BASH-like line editing is supported

HELP.

---

### Post by OSUfrk09 on 2008-09-09
I do not want to reinstall, and when i type boot under the command line in GRUB... it tells me that the kernels need to be loaded before booting. 

I Did install under wubi, and everything has run fine until this point

---

### Post by caljohnsmith on 2008-09-10
When you are in Windows, do a search for "menu.lst" and post back the results of where the file(s) are located. It might be that your menu.lst is missing or misplaced.

---

### Post by OSUfrk09 on 2008-09-10
It is located in c:\ubuntu\winboot

when im in the grub screen it says press esc for options. it has halt, reboot, find menu boot lists... etc.

---

### Post by beginner1 on 2009-01-04
I have the same problem but your thread ended without a solution. How was this problem resolved?

---

### Post by caljohnsmith on 2009-01-04
> **beginner1 said:**
> I have the same problem but your thread ended without a solution. How was this problem resolved?
If you can, how about reinstalling Ubuntu, but first be sure to turn off all your antivirus type programs in Windows; that is often the cause of problems installing Ubuntu inside Windows. Let me know if that helps or if you still have the same problem.

---

### Post by transit72 on 2009-11-23
After a freeze while playing NWN, I had the same problem. GRUB4DOS could not find the kernel to boot! So I boot from Windows Vista and checked the partition where I had Ubuntu 8.04 installed and noticed that the 'disks' folder was missing. However, I also noticed that the partition was reporting a huge used space, which the visible files did not add up to! I suspected that this meant the data was still there and had not disappeared completely. Searching through the internet I ran into this case

[http://www.experts-exchange.com/OS/Linux/Distributions/Ubuntu/Q_24308234.html](http://www.experts-exchange.com/OS/Linux/Distributions/Ubuntu/Q_24308234.html) 

which suggests an interesting solution. The bottom line is that you boot into Windows and run chkdsk /r in order to recover the lost files and folders.

In my case this took some time due to the ~30GB of data that had to be recovered. Then I boot the Ubuntu CD (selecting the trial - NOT Installation) and mounted the partition. In there I could now find the recovered files (root.disk, swap.disk) inside a folder with the name FOUND.000 or something like that. I renamed it to 'disks' and moved it in the 'ubuntu' folder. After that I restarted and Ubuntu worked fine!!

I hope this will help.

---

### Post by IAmTheLorax on 2009-12-02
I have read in more than 1 place, that the kernel and initrd.gz from the CD can not be used with the grub4dos method. They must be replaced by supposedly downloading the proper files from Ubuntu.

Can anyone verify this? Can anyone provide a link to the files?

Please  **H E L P !!!**

---

### Post by IAmTheLorax on 2009-12-02
Sorry, forgot the documentation:

[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html#comment-3547725998443369362](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html#comment-3547725998443369362)

---

