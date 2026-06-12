---
title: "Help with LUKS and self compiled kernel"
date: 2008-08-12
forum: General Help
---

### Post by suthagar on 2008-08-12
Hi all,

I've just tried compiling a new kernel on Hardy so that it includes ALSA which in turn with any luck with let me install the latest x-fi drivers. I've been following the instructions in this thread: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675).

The new kernel boots fine but when it gets to the file system check it comes to a screaming stop. It tells me it can't check the file system and that I have to do it manually and then dumps me into a rescue shell. If I Ctrl-D out of the shell the boot up process continues but I can no longer access my /home partition. 

This has partly to do with the way my system has been setup.  "/" "/home" and "/store" are encrypted along with the swap partition. Usually I get the ubuntu splash screen with a prompt for the root partition and then a little later on I get two more LUKS prompts for /home and /store. 

With the new kernel I get the splash screen and the password prompt for the root partition but not the other two i.e the early mounting cypto partitions message and the the LUKS prompt don't appear and instead I get the file check error. 

Is there something I am supposed to add/mark during the kernel configuration process to ensure that the encrypted drives are mounted at boot , or to grub's menu.lst file? I basically just copied my existing .config as a base for the new kernel and the only things I changed were the ALSA support and the processor type (from generic x64 to Core 2).

Any help greatly appreciated.  

Thanks 

S

---

### Post by suthagar on 2008-08-13
[solved]

I managed to solve this one. Apparently some of the filesystem modules for XFS did not get included for some reason. 



Cheers


S

---

### Post by hyper_ch on 2008-08-13
and if you want, you can setup key files for the other two partitions that are encrypted and add it to a new lost on them so that you have to enter the password only once.

I've written a little howto on that - in case you get annoyed entering three times the password ;)

---

### Post by suthagar on 2008-08-13
thanks hyper_ch,

It does get a little tiring typing in three passwords all the time  - do you mind posting the url to your how-to?

Does having keyfiles make it less secure though?


Kind regards


S

---

### Post by hyper_ch on 2008-08-13
> **suthagar said:**
> do you mind posting the url to your how-to?

I don't know it by heart but I'm sure you can find it.

---

