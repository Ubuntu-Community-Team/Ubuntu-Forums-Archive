---
title: "Thoughts on the Acer 5315 overheating"
date: 2009-12-31
forum: Hardware
---

### Post by UbuMelancholy on 2009-12-31
Hi.

My problem is a veyr known one: Acer Aspire 5315 overheating, caused by the improperly working of the fan.

The fan is in perfect state, the real problem is on the hardware (MAYBE THE SOFTWARE???) controlling the velocity of cooling. There are A LOT of post about it and it can be classified on 3 types:

*Those guys that do not read the previous posts and are wondering if the fan is dirty or something like that.
 
*Those guys proposing a very colourful set of solutions but all of which do not solve the problem, as indicated by themselves in the later posts.

*Those guys suggesting that a BIOS update is the fixing solution, some proving it correctnesss, some discarding it.

Well, I want to know if there is a FIXING COMMAND or FINE HACKING WORK I can implement on the terminal . I have to say that the fan only turns on when the notebook boots the kernel while it is very hot, not on those times it starts from cool. Im afraid of do a BIOS update, they say it leaves my laptop DEAD.

Im a Fedora user, but they really have a few posts (FedoraForums.org) about this issue when compared with you, Ubuntu users...Hope help. Thanks.

---

### Post by joeganda on 2010-01-17
Also my problem with overheating is gone after updating my bios from v1.29 to v 1.43. I kicked of Vista, but could update anyway with an iso described in msg 39 on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
The fan runs every now and then, I hope it will be enough. Strangely it works, despite I turned off acpi in the boot and told grub to use the acpi of Linux.

---

### Post by UbuMelancholy on 2010-01-18
Hi joeganda. Im really afraid of performing that update. The image of a dead motherboard on my head is still bothering me!
Also your notebook turned on the fan when it starts from hot? Do you use ubuntu?

---

### Post by Beyo on 2010-01-22
If you have master degree in kernel developing you need to download sources for acerhdf module and find the acerhdf.c file
and add proper lines for 5315, unfortunately there are described solutions on internet for other models of acer just not for 5315 :(

---

### Post by Hermes7 on 2010-01-26
Hi,
I know absolutely nothing about ubuntu but have managed to install it on my ACER 5315 before I read the posts about the overheating problem in these forums. I quickly found out that my fan was not working and it shut down the laptop much to my surprise.
 
Today I was running it on a laptop riser with built in fan powered from the USB on the Acer to keep it cool so I could update Ubuntu for the first time and this is strange because after re-booting the fan now appears to work???????????????????? 
 
I set it to hibenate and start up again and the fan still works so my question is has any of the new Ubuntu updates got a FIX included for this problem?
 
Puzzled but so far pleased:)

---

### Post by filolog on 2010-10-17
Hi,

I had the same fan & overheating problem on Acer  Aspire 5315  (bought in UK). Although I was a bit weary after reading so many  forums, I managed to update my BIOS.

However, instead of flashing in Vista using the .exe application with BIOSv1.45 (from this  ACER.CO.UK site: [http://www.acer.co.uk/acer/service.d...CRC=3713735360]("http://www.acer.co.uk/acer/service.do;jsessionid=AB12754677EB7CC33930582BE04AB4BA.public_a_14a?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360")   ), 

I used the live CD ISO (FreeDOS) prepared by Angel Garcia and following  Groszman's instructions. Read this post:

[http://ubuntuforums.org/archive/inde...t-1043129.html]("http://ubuntuforums.org/archive/index.php/t-1043129.html")

It helped me, I now have BIOS v1.43  and  my fan works perfectly under Ubuntu and LiveUSB with PSlinuxOS e17.

(by the way, v1.43 of BIOS seems to be  the latest on ACER.COM site: 
[http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html))

I hope it helps.
:smile:

---

### Post by Thulitharn on 2012-07-17
The dropbox file no longer exists.

---

### Post by rizal23 on 2012-07-17
> **Thulitharn said:**
> The dropbox file no longer exists.

 yes I agree that the dropbox file no longer exists.

---

### Post by Thulitharn on 2012-07-19
I have not been able to get the fixes to work with 12.04 and I cannot flash the BIOS as I do not have the Vista partition. I have tried to re-isntall Vista but that does not seem to work either as I cannot get the think to connect to the internet.

So I am sure that I, and may others, are still stuck.

I really wish I had not bothered to try a new operating system. The overheads are far too high.

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

