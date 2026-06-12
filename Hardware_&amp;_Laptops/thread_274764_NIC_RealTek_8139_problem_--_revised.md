---
title: "NIC RealTek 8139 problem -- revised"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by Mr.Hulot on 2006-10-10
Hi, I've had a problem with my realtek ethernet card in my laptop for quite some time now. I've posted in the forum but no one seemed able to help. So after some time of searching and trying I decided to post again with some new info.

The original post is here : 
```
http://www.ubuntuforums.org/showthread.php?t=258712
```


plz read it so that I can keep this one small. So after a while I realized that the problem was not with NFS but with the card itself as it would also hang after a while when using samba, vncviewer or anything. But I wanted to test it with another distro (as I dont have windoze on the laptop) so I put on knoppix. The card worked flawlessly and I was able to connect with NFS and tranfer whatever I wanted. So I guessed it was module problem. So I lsmod-ed knoppix and saw that it only used 8139too and not 8139cp and 8139too as ubuntu did. So I blacklisted 8139cp but the problem remains. 
I know there are a lot of threads about this card but believe me,I've been searching all over the net and I had no luck, because I didn't found the same problem as mine.

The only thing I found is a guy who had the same problem and decided to use ndiswrapper with the windoze driver. I havent gone down that road yet as I want to avoid using ndiswrapper if I can. 

A final note, when i recompiled my kernel (one of my first efforts to do that) I chose that the driver 8139too was compiled instead of being a module. When I fired the system up, it worked better, it even managed to transfer some big quantities of files but eventually hung!

So my question is this ... how can I replace the faulty module? Can I get it from the knoppix kernel? Now that I have 8139cp blacklisted, the dmesg reports 

```
Identified 8139 chip type 'RTL-8100B/8139D'
```

---

### Post by yreynhout on 2006-10-11
I can only agree with what is mentioned here. I find it appalling that one has to jump through so many hoops before (a) anyone reacts, (b) one can find RELEVANT (meaning up-to-date and accurate) information (and I still haven't found any).

This is probably the number 1 distro, but not being able to get a "simple" NIC going is a real turn off for my first experience with linux. There must be someone who is smart enough to explain either how to fix this, or how this is unfixable in the current/future release. And instead of replying here (in full), put the answer in the proper place (like launchpad).

Sorry for the pissed off tone, but after three days of googling, I'm seriously thinking about abandoning this distro.

---

### Post by windwalker78 on 2006-10-12
I absolutely agree that this is almost No1 distro among linuxes and it is awful to have problems with your ethernet card. I have a Toshiba Satellite L100-113 and problem is there since the first install of Ubuntu 6.0.6. Tried blacklisting 8139 cp, but the problem persisits...Can somebody finally post something that really works? It looks like a problem with the driver which occurs immediately when coping large files or after a longer period with low traffic activity.

---

### Post by windwalker78 on 2006-10-12
I am a newbie BTW. I tried "pci=noacpi" and "acpi=off" in grub, but I am unable to boot if I use these options? Any other suggestions? Is there another way of turning off acpi?
 I just recompiled the driver for 8139 in kernel 2.6.18 (not as module) and the problem is still there. :-k

---

### Post by Wim van der Meer on 2006-10-13
First of all let me state that I consider myself only a slightly advanced user, and I don't have the problem reported here myself so i don't know if what I suggest will be of any help. I have had my share of ethernet card problems, and I know it can be a pain to solve them.

I had some problems with a very slow samba connection when using a virtual machine, and when trying to solve the problem I found out about a piece of software called "ethtool". This tool allows you to tune the settings of your ehternet card. Mr. Hulot reports that his card works with Knoppix, maybe he could check the ethernet card configuration using ethtool, and see if it is the same as when he uses it with Ubuntu?

Just for reference, I was able to solve my problem by excucting the following command: "sudo /sbin/ethtool -K eth0 tx off".

Read the man page ("man ethtool") if you want to know more about all the options. I am sorry that I can not be of more help.

--Wim

---

### Post by windwalker78 on 2006-10-13
> **Wim van der Meer said:**
> First of all let me state that I consider myself only a slightly advanced user, and I don't have the problem reported here myself so i don't know if what I suggest will be of any help. I have had my share of ethernet card problems, and I know it can be a pain to solve them.

I had some problems with a very slow samba connection when using a virtual machine, and when trying to solve the problem I found out about a piece of software called "ethtool". This tool allows you to tune the settings of your ehternet card. Mr. Hulot reports that his card works with Knoppix, maybe he could check the ethernet card configuration using ethtool, and see if it is the same as when he uses it with Ubuntu?

Just for reference, I was able to solve my problem by excucting the following command: "sudo /sbin/ethtool -K eth0 tx off".

Read the man page ("man ethtool") if you want to know more about all the options. I am sorry that I can not be of more help.

--Wim


Thanks for giving us a helping hand. I tried "ethtoo -K eth0 tx off" and it give an output:
Cannot set device tx csum settings: Operation not supported

Then I tried TX instead of tx and it accepted the command, but when copying the 8139 hung again. I set speed to 10 Mbit and duplex to half, but without any positive result :(.
I also tried /etc/init.d/acpid stop and /etc/init.d/acpi-support stop just in case. 
I have attached some debugging info for the experts if any.

---

### Post by windwalker78 on 2006-10-13
added "irqpoll" to /boot/grub/menu.lst

I am not having problems for more than one hour of copying. Tests will continue...

---

### Post by yreynhout on 2006-10-16
*added "irqpoll" to /boot/grub/menu.lst*
I can confirm this works on an ACER laptop (Aspire 1600 series) ASPIRE 1604LC with a realtek ethernet chipset/card, BUT in combination with blacklisting the 8139cp module.

:D

---

### Post by Bill80 on 2006-10-29
I have had the same hassle trying to get my Realtek 8139 card to work. I tried all the hints but none worked for me until.......

The problem seems to be an irq conflict and the solution varies depending on each pc setup. That's why adding pci=noacpi or similar to menu.1st work on some pcs.

The one I found that made my card work was pci=biosirq. (Cheers!)
The thread on mepis.org also suggested trying pci=irqmasq.
<http://www.mepis.org/node/912>

Hope this helps.
BillK

---

