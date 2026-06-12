---
title: "How do I find my CPU socket type from my motherboard in Ubuntu?"
date: 2010-04-08
forum: Hardware
---

### Post by TheNerdAL on 2010-04-08
I might upgrade my CPU and would like to know what my socket type is, thanks.

---

### Post by PRC09 on 2010-04-08
I dont know if you can find it that way but if you go to the manufacturers website with your motherboard model number it should tell you everything you need to know......

---

### Post by TheNerdAL on 2010-04-08
What if I don't know my model number? O.o

---

### Post by PRC09 on 2010-04-08
It should say what the number is and the manufacture on the motherboard itself.Other than that I dont know.In some cases if you dont see either then the serial number and the model number on the back of the case (tower) will help and just google it.....

---

### Post by PRC09 on 2010-04-08
In a terminal type:

   cat /proc/cpuinfo 

That will give you the info,then google the processor results....

---

### Post by TheNerdAL on 2010-04-08
Thanks! :D

---

### Post by cascade9 on 2010-04-10
I happen to already know you have a socket 754 motherboard , TheNerdAL/. 

The best CPU you will be able to find for that is a socket 754 3700+ (2.4Ghz, 1024k cache) 

BTW, your current CPU is a 3100+, but that is a sempron, so the 3100+ is measured against a celeron. If you get an athlon 64, the xxxx+ naming is measured against a 'full' P4 so (for example) an Athlon 64 at 3200+ is faster than a sempron 3200+

Sempron 3200+ 1.8Ghz, 256k cache 
Athlon 64 3200+ 2.4Ghz, 512k cache

> **PRC09 said:**
> In a terminal type:

   cat /proc/cpuinfo 

That will give you the info,then google the processor results....

A flawed method. 

There are lots of CPUs that will output the same basic info with that command that have different CPU sockets.

---

### Post by PRC09 on 2010-04-10
Do you have another command that will tell the socket type? I just tried the 2 machines I have close to me and googled the results both were correct according to the spec sheets for both processors,both were amd,1 socket A and the other was a socket 939....I dont have anything else powered up right now but I am curious.......

---

### Post by cascade9 on 2010-04-10
As far as I know, there is no command to get the socket type. 

lshw might work a little better than just the cat proc/cpuinfo command. You would have to search both the CPU type and the chipset, but and even that still has flaws- eg the 915 chipset ihas both lga 775 and socket 478 version. 

cat proc/cpuinfo is more flawed, because of the number of CPUs that have different CPU sockets on CPUs with the same name, eg P4 EE 3.4 (socket 478 and lga 775), athlon 64 3200+ (socket 754, 939 and AM2)

*edit- I do far more hardware than software, and my prefered mehtod for finding CPU socket type is via 'eyeball' ;) But if anybody does know a method that will give the soket type from command, or from a GUI, in linux, please post it ;)

---

### Post by ffejie on 2012-12-04
I'm pretty sure that this command will get it for you:

sudo dmidecode –t 4 | grep "Socket"

> **cascade9 said:**
> As far as I know, there is no command to get the socket type. 

lshw might work a little better than just the cat proc/cpuinfo command. You would have to search both the CPU type and the chipset, but and even that still has flaws- eg the 915 chipset ihas both lga 775 and socket 478 version. 

cat proc/cpuinfo is more flawed, because of the number of CPUs that have different CPU sockets on CPUs with the same name, eg P4 EE 3.4 (socket 478 and lga 775), athlon 64 3200+ (socket 754, 939 and AM2)

*edit- I do far more hardware than software, and my prefered mehtod for finding CPU socket type is via 'eyeball' ;) But if anybody does know a method that will give the soket type from command, or from a GUI, in linux, please post it ;)

---

