---
title: "Core Duo Laptop"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by COKE CAN on 2006-09-06
What do I need to install to have my Core Duo functioning properly?  Do I do this via command line like sudo apt-get or can it be installed via GUI in GNOME?  Thanks for the help!

P.S.  Should wireless work out of the box?  I have a Dell E1505 with Intel Pro Wireless 3945.  I read a thread where the E140X worked out of the box.

---

### Post by COKE CAN on 2006-09-06
My current kernel is 2.6.15-26-386

I thought I read somewhere that I needed 686 kernel and something about SMP?

---

### Post by azraelx401 on 2006-09-06
as far as the processor i'm not 100% sure but it should work fine out of the box.  I too was wondering the same thing about a kernal upgrade for my Dell XPS M140.  But your wireless should work out of the box.  I know mine did. (i don't have my laptop so i can't say which wireless card i have)

---

### Post by COKE CAN on 2006-09-06
I am at work right now so when I get home I will try again.  How can I make sure that my wireless is configured to connect?

---

### Post by azraelx401 on 2006-09-06
if it worked out of the box after you installed Ubuntu it should of prompted you that there are updates, because there's alwasy updates for anything you install on any OS.  but if it doesn't try to check if your drivers are installed

sudo lsmod | grep ipw2200

if anything shows up then the ipw2200 driver is installed.  alot of intel use the same drivers.

---

### Post by COKE CAN on 2006-09-06
I actually did what you said o do but istead of ipw2200 I did:

```
sudo lsmod | grep ipw3945
```

Which returned:

```
ipw3945           126620   1
ieee80211          37064   1   ipw3945
```

---

### Post by azraelx401 on 2006-09-06
alright then the drivers are installed, so you should be able to get online.  If you use WPA for your wireless it's gonna take another program for you to be able to use it.  I'm at work right now so I don't have my laptop on me to tell you what it is.  but your gonna need Automatix to get the program....but if you have an unsecured or WEP connection then you should be good to go.

---

### Post by azraelx401 on 2006-09-06
alright then the drivers are installed, so you should be able to get online.  If you use WPA for your wireless it's gonna take another program for you to be able to use it.  I'm at work right now so I don't have my laptop on me to tell you what it is.  but your gonna need Automatix to get the program....but if you have an unsecured or WEP connection then you should be good to go.

---

### Post by COKE CAN on 2006-09-06
So I have a question.  For example, I have an unsecure wireless network.  When I make sure my wireless is on on my laptop, will it act just like WinXP and pop up telling me that wireless networks are available?  If not, where do I go to find what is available?  Do I have to change it from eth0 to something else?

---

### Post by azraelx401 on 2006-09-06
Well just make sure that eth0 is active if that's what your wireless card is set up on.  I think on mine it's eth1 so just look into that.  but as far as telling you that there are wireless networks i don't think it does or aleast i've never noticed if it did.  and if it does I don't notice them cause I'm on a secured connection using WPA and by default i connect right away.  now to view the connections on the top panel there should be the network icon (the two monitor) i think if you right click on it some options should show up and i believe that view wireless networks is on that.  like i said i don't have my laptop on me so i could be wrong.

---

### Post by COKE CAN on 2006-09-06
Ok, I am away from home as well that is why I am trying to pick your brain as much as possible.  I right click on the network icon and go to properties.  Then I click configure.  That brings up Network Settings.  In there it states "Wireless Connection:  The interface eth1 is active."  Now, when I get around a wireless connection, will it automatically connect?

---

### Post by COKE CAN on 2006-09-06
P.S. I appreciate your kind assistance!

---

### Post by wjp.reg on 2006-09-06
> **COKE CAN said:**
> Ok, I am away from home as well that is why I am trying to pick your brain as much as possible.  I right click on the network icon and go to properties.  Then I click configure.  That brings up Network Settings.  In there it states "Wireless Connection:  The interface eth1 is active."  Now, when I get around a wireless connection, will it automatically connect?

I think you might get what you're looking for by installing the network-manager which lets you set up multiple connections for home, work, etc., with auto detection/connection.  Have a look in synaptic and read the description.

cheers!

---

### Post by bekiil on 2006-09-06
For the cpu thing, you have to use a smp enabled kernel, do a cat /proc/cpu
to se what prosessors that are listed, there should be two cpu`s there.

like this: 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1828.995
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 3663.85

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1828.995
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 3657.79

My problem is that the cpu is not detected as a Centrino, so cpu frew scaling dont work.
Linux xxxxx 2.6.15-26-686 #1 SMP PREEMPT

For the wifi, i only installed network-manager-gnome and my wpa/psk enabled wireless network worked.

---

### Post by azraelx401 on 2006-09-06
> **COKE CAN said:**
> Ok, I am away from home as well that is why I am trying to pick your brain as much as possible.  I right click on the network icon and go to properties.  Then I click configure.  That brings up Network Settings.  In there it states "Wireless Connection:  The interface eth1 is active."  Now, when I get around a wireless connection, will it automatically connect?

i believe it does actually.  once you try to connect to it once it should configure it as a default and try to connect you to it automatically.

---

### Post by COKE CAN on 2006-09-06
What do you mean by this:

> My problem is that the cpu is not detected as a Centrino, so cpu frew scaling dont work.

---

### Post by COKE CAN on 2006-09-06
I appreciate all of the help guys!

---

### Post by COKE CAN on 2006-09-06
So if I go into Synaptic and mark linux-image-2.6.15-23-686 for installation, it should take care of only seeing one processor?

---

### Post by ronintiger on 2006-09-11
Regarding the kernel. You´ll need 686 kernel. 

I too have a Core duo and when I tried the SMP kernel I had problems (mayby somethings was missing I don't know :-k  ). But the 686 worked just fine.

After you install the 686 kernel you can observe the status of both cores on the system monitor (you can add one for each CPU) 8)

---

### Post by David Corrales on 2006-09-11
I should add that on my Inspiron 9300 wireless works out of the box but the LED doesn't -_- lol
To check the status you can go into the console and type: **iwconfig**
On the first line of the output you can read *Radio: <status>* (on/off) in case you're wondering if the card is on or off hehe.

---

### Post by kondor on 2006-09-13
> **ronintiger said:**
> Regarding the kernel. You´ll need 686 kernel. 

I too have a Core duo and when I tried the SMP kernel I had problems (mayby somethings was missing I don't know :-k  ). But the 686 worked just fine.

After you install the 686 kernel you can observe the status of both cores on the system monitor (you can add one for each CPU) 8)

Are you saying that you installed the non-SMP 686 kernel? I cannot get the 686 SMP kernel to work with a P4 HT laptop as it freezes after booting. Since the SMP portion was written initially for HT, perhaps dual core boxes do not benefit from it that much. The 386 kernel works fine but no HT.

---

### Post by jdong on 2006-09-13
With Dapper Drake, there is **no such thing** as the non-smp 686 kernel. There is only one 686 kernel, the 686 kernel, and it's SMP. The 686-smp package merely points to the 686 package.

This kernel should work for both HT (SMT) and "true" SMP.


Your ipw3945 should work out-of-the-box, too. Make sure you installed the package **linux-686** and not just linux-image-686, and your wireless should show up in the configuration utilities.

If your laptop has a hardware wifi switch (either a key combination or a physical flip-switch), try toggling it. Sometimes it likes to default to off :)

---

