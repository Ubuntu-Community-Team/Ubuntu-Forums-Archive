---
title: "System locked up during upgrade"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by ttk1opc on 2009-09-01
So I was bored, and feeling impatient I decided to upgrade to the latest alpha of 9.10. Everything was going fine, and then my system completely locked up, and could not recover from it. And obviously now my problem is ubuntu will not boot, even in recovery mode. Is there any way to recover from this, or do I have to do a complete reinstall? Any help would be appreciated. Thanks in advance.

---

### Post by oboedad55 on 2009-09-01
> **ttk1opc said:**
> So I was bored, and feeling impatient I decided to upgrade to the latest alpha of 9.10. Everything was going fine, and then my system completely locked up, and could not recover from it. And obviously now my problem is ubuntu will not boot, even in recovery mode. Is there any way to recover from this, or do I have to do a complete reinstall? Any help would be appreciated. Thanks in advance.

How did you do the upgrade and from which version?

---

### Post by shredder12 on 2009-09-01
According to me a reinstall is the only way around (if you don't have any data to retrieve)
but let us see what other ubuntu guru's say about it..

---

### Post by Peque on 2009-09-01
Got almost the same problem! 
Ran an apt-get upgrade - then apt-get dist-upgrade on my Poweredge 2950 III server. 
Now rebooting the system starts the bios up - and instead of starting grub - its just write grub on a line an nothing more happens???? 

How do I log into the system and recover this error??? 
I've tried several times using a disk - but there comes errors no matter what. No disk mounted no booting options - and trying to recover the system - ends up in a error in /bin/sh on the root partition??? 

Thanks in advance

---

### Post by oboedad55 on 2009-09-01
> **shredder12 said:**
> According to me a reinstall is the only way around (if you don't have any data to retrieve)
but let us see what other ubuntu guru's say about it..

I'm no guru, but I agree. Save what you can and reinstall. It will, in the long run, be quicker and less painful.

---

### Post by shredder12 on 2009-09-01
> **Peque said:**
>  
Now rebooting the system starts the bios up - and instead of starting grub - its just write grub on a line an nothing more happens???? 

Well, I think it could be jst some grub issue..
> 
How do I log into the system and recover this error??? 
I've tried several times using a disk - but there comes errors no matter what. No disk mounted no booting options - and trying to recover the system - ends up in a error in /bin/sh on the root partition??? 


Do you mean you are unable to mount the linux partition using a live CD ??

---

### Post by ttk1opc on 2009-09-01
I hit alt F2 and ran update-manager -d from 9.04, if I can't save it, can I get my files if I run the liveCD, I remember trying this before and not being able to access them. I probably was doing something wrong.

---

### Post by shredder12 on 2009-09-02
> **ttk1opc said:**
> I hit alt F2 and ran update-manager -d from 9.04, if I can't save it, can I get my files if I run the liveCD, I remember trying this before and not being able to access them. I probably was doing something wrong.

Hey, i am a little confused.. after you system was locked up you weren't able to boot into ubuntu. Right??

if this is the problem then you can probably recover your data by using a live CD. 
Boot into the live session and all of your disk partitions should be automatically mounted.
Go to places-> and you can see and access all of your disk partitions...
( Lets just hope that the linux partition gets mounted)
and then retrieve ur data.

---

### Post by ttk1opc on 2009-09-02
Thanks, Ya that is what I am saying, I will give the LiveCD a shot, I recently did a fresh install so what I do have to save is not that much, and not the end of the world, I was kind of trying to fix this problem (if possible) without a reinstall and turn a mistake into a learning experience. Still learning, and this would be a good thing to know. Thanks for the help.

---

### Post by shredder12 on 2009-09-02
If you really want to try something then first of all u should be able to boot in to ubuntu..
since this seems to be a grub issue primarily
try following this tutorial to get it back..
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ttk1opc on 2009-09-02
I don't think it is a grub issue, I am able to select the ubuntu partition and it starts to load, then I get a blank screen and blinking cursor.

---

### Post by shredder12 on 2009-09-02
If that is so.. then fresh installation seems to be the only approach available..
nd since you have no problem with any data retreival .. so jst go for a fresh new ubuntu..

---

