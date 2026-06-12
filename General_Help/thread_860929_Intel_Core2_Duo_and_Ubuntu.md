---
title: "Intel Core2 Duo and Ubuntu"
date: 2008-07-16
forum: General Help
---

### Post by ieee2 on 2008-07-16
Gretings:

I am a newbie in Ubuntu. I want to install it to My HP Personal Computer which is Core2 Duo. Will I be able to install ubuntu in Core2 Duo? what is the system requirements for Ubuntu? I have read it from the Home page & it says:

> System Requirements 
Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space. 

I could not undeerstand what do they mean by available for PC ? does it include core2 duo? 

Regards,
ieee2

---

### Post by iaculallad on 2008-07-16
Intel Core2 Duo are 64-bit arch processors. You could install either 32-bit or 64-bit version of Ubuntu.

EDIT: [Core2 Duo]("http://en.wikipedia.org/wiki/Intel_Core")

---

### Post by tomcheng76 on 2008-07-16
Yes. it does.
I am using E8200 and it works, so no need to worry :)

---

### Post by dcstar on 2008-07-16
> **ieee2 said:**
> 
.......
I could not undeerstand what do they mean by available for PC ? does it include core2 duo? 

Regards,
ieee2

"available for PC" means any Intel (or AMD) CPU based PC hardware that meets the resource requirements that follow.

---

### Post by ieee2 on 2008-07-16
I am not convinced that Core2 duo is 64 bit. I have followed these steps on my PC which is labeled as Core2 duo to check the Processor Archeticture:
Right click on My Computer -> Properties -> Advanced -> Environmental Variables -> under System variables I checked the Processor Archeticture and found that it is x86 which means 32 bit, isn't true that x86 means 32 bit??

Regards,

---

### Post by inteluser on 2008-07-16
You are likely running a 32-bit operating system, which is therefore seeing the processor as a 32-bit processor.  The Intel Core2 Duo is indeed a 64-bit processor, and will be seen as such under a 64-bit operating system (and as a 32-bit processor under a 32-bit operating system)

---

### Post by bodhi.zazen on 2008-07-16
You can :

```
cat /proc/cpuinfo
```

---

### Post by mikewhatever on 2008-07-16
> **ieee2 said:**
> I am not convinced that Core2 duo is 64 bit. I have followed these steps on my PC which is labeled as Core2 duo to check the Processor Archeticture:
Right click on My Computer -> Properties -> Advanced -> Environmental Variables -> under System variables I checked the Processor Archeticture and found that it is x86 which means 32 bit, isn't true that x86 means 32 bit??

Regards,

Core2duo is both 32 and 64 bit capable. In other words, both kinds of operating systems can be run on it. For more info --> [http://en.wikipedia.org/wiki/Core2Duo](http://en.wikipedia.org/wiki/Core2Duo)

---

### Post by ieee2 on 2008-07-16
Thank you all for your information.

Ok, I have important question:
How can I know if my Processor is 64 bit or 32 bit? I need a way where I can check by a command or some easy way like this if you suggest that I don't have the PC specification that is from the vendor and I have installed 32 bit OS ?

Also, I have a server with the following processor:
[SIZE="4"]Intel(R) Xeon(R) CPU 5140 @ 2.33 Ghz[/SIZE]
Is it a 64 or 32 bit processor?

Regards,
ieee2

---

### Post by mikewhatever on 2008-07-16
**cat /proc/cpuinfo**, see post #7.

Are you trying to make a simple thing difficult?

---

### Post by ieee2 on 2008-07-16
Dear mikewhatever

I didn't undersant the post #7. I think it is a linux not a windows command because it didn't work with windows. I am in the stage of System Requirements and didn't install linux yet.

---

### Post by mikewhatever on 2008-07-16
> **ieee2 said:**
> Dear mikewhatever

I didn't undersant the post #7. I think it is a linux not a windows command because it didn't work with windows. I am in the stage of System Requirements and didn't install linux yet.

Of cause it is a Linux command. Unless you've noticed, this forum is dedicated to Ubuntu/Linux, and that's what most of us use.

---

### Post by Fire_Chief on 2008-07-16
If you boot up the Ubuntu LiveCD, you can run the command to determine what will be seen by Ubuntu. Then you can reboot with no ill effects.

Cheers!

---

### Post by Cone on 2008-07-16
Or you could [Google]("http://www.google.com/search?q=xeon+5140&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") and [read a description.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117088")

But if you want to be sure beyond a doubt of a paranoid mind, sure -- boot Linux (LiveCD or whatever) and use the terminal command.

---

