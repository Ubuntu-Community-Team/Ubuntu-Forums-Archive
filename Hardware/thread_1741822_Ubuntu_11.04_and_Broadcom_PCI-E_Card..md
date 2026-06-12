---
title: "Ubuntu 11.04 and Broadcom PCI-E Card."
date: 2011-04-28
forum: Hardware
---

### Post by irv on 2011-04-28
Yes, I been around Ubuntu Linux for awhile. I think it was the second release 5.04 or 5.10 I don't remember any more, but I am really backing off of Ubuntu for two reasons. 
[B]
The first[/B] is my Broadcom wifi card and Ubuntu do not play well with one another. For the last few releases I have had to go from using windows drivers to 3rd party drivers and sometime jump through hoops to get it to work. This last release 11.04 was the straw that broke the camel's back. 

I was going to really give 11.04 a fair shot. I even went out and bought a new Hard Drive and loaded it this morning. No go! can't get the Broadcom card to work with 11.04.
**The Second thing:** This has nothing to do with the hardware problem, I just don't like Unity.

[COLOR="Navy"]OK I have a question and it is for anyone who has a Dell Inspiron 1521 or one of the Inspiron's that use a PCI-E card.[/COLOR] 

[COLOR="Red"]Is there another card I can buy and install that will play well with Ubuntu?[/COLOR] 
There must be someone out here that has a card that works well and will fit in my Dell.

From everything I read it is the Broadcom card that is the problem.

There is a Dell Intel Pro Wireless 3945 802.11 a/ b/g LAN Mini-PCI-E Card that I can pick up for about $15, but I need to know if it will work?
Any help would be greatly appreciated.
Thanks

---

### Post by irv on 2011-04-29
Well, it been almost 24 hours without a replay, thought I would just give this a little bump.
And while I am add it, let me ask one more question. Has anyone got a Broadcom wife card to work with 11.04 yet? I haven't.

---

### Post by IcarusR on 2011-04-29
> There is a Dell Intel Pro Wireless 3945 802.11 a/ b/g LAN Mini-PCI-E Card that I can pick up for about $15, but I need to know if it will work?

My Tosh has this wifi card which I believe is the same as the one you asked about & it works well in 10.04, don't know about 11.04.

```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

I also have a pcmcia Belkin wifi with broadcom chipset it works well in 10.04 with Broadcom B43 wireless driver installed as proprietary driver.

```
08:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

Which broadcom card do you have ?

---

### Post by IcarusR on 2011-04-29
Downloading 11.04 iso now, will try both in 11.04 later & let you know how they work

---

### Post by collisionystm on 2011-04-29
> **irv said:**
> Yes, I been around Ubuntu Linux for awhile. I think it was the second release 5.04 or 5.10 I don't remember any more, but I am really backing off of Ubuntu for two reasons. 
[B]
The first[/B] is my Broadcom wifi card and Ubuntu do not play well with one another. For the last few releases I have had to go from using windows drivers to 3rd party drivers and sometime jump through hoops to get it to work. This last release 11.04 was the straw that broke the camel's back. 

I was going to really give 11.04 a fair shot. I even went out and bought a new Hard Drive and loaded it this morning. No go! can't get the Broadcom card to work with 11.04.
**The Second thing:** This has nothing to do with the hardware problem, I just don't like Unity.

[COLOR=Navy]OK I have a question and it is for anyone who has a Dell Inspiron 1521 or one of the Inspiron's that use a PCI-E card.[/COLOR] 

[COLOR=Red]Is there another card I can buy and install that will play well with Ubuntu?[/COLOR] 
There must be someone out here that has a card that works well and will fit in my Dell.

From everything I read it is the Broadcom card that is the problem.

There is a Dell Intel Pro Wireless 3945 802.11 a/ b/g LAN Mini-PCI-E Card that I can pick up for about $15, but I need to know if it will work?
Any help would be greatly appreciated.
Thanks


[http://ubuntuforums.org/showthread.php?p=10736018](http://ubuntuforums.org/showthread.php?p=10736018)


I followed the instructions, ran the Additional Drivers app and after a reboot... happy happy.

---

### Post by irv on 2011-04-29
> Which broadcom card do you have ?

```
irv@irv-laptop:~$ lspci -vvnn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
irv@irv-laptop:~$ 

```

---

### Post by irv on 2011-04-29
> **collisionystm said:**
> [http://ubuntuforums.org/showthread.php?p=10736018](http://ubuntuforums.org/showthread.php?p=10736018)


I followed the instructions, ran the Additional Drivers app and after a reboot... happy happy.

I tried this link and it did not work. still can't use the wifi card.

---

### Post by irv on 2011-04-29
I have no idea what changed from 10.04 and 10.10 to 11.04, but nothing I have tried has worked. I know this driver worked with 10.xx but it will not work with 11.04. [ATTACH]190453[/ATTACH]

---

### Post by irv on 2011-04-30
Day three:
I know that when designing an OS it is hard to get it to work with all hardware, but it seem like Ubuntu is going backwards. There are many users like me out here that use Broadcom wifi cards and Ubuntu had it supported in the last couple of releases, but now I am back to the same problem I had with 8.04. Will I have to install a Windows driver to get my wifi to work?

Until I get some new hardware or figure out how to get this card to work with 11.04 I am sitting stationary with a cable plugged into my laptop to get on the Internet and my network. No more taking my laptop with me on the road and working in Ubuntu. I might be forced to use Windows. :( That will be a very sad day. (This is not a threat but only an option). I could never go back to Windows.

---

### Post by irv on 2011-04-30
> **irv said:**
> Day three:
I know that when designing an OS it is hard to get it to work with all hardware, but it seem like Ubuntu is going backwards. There are many users like me out here that use Broadcom wifi cards and Ubuntu had it supported in the last couple of releases, but now I am back to the same problem I had with 8.04. Will I have to install a Windows driver to get my wifi to work?

Until I get some new hardware or figure out how to get this card to work with 11.04 I am sitting stationary with a cable plugged into my laptop to get on the Internet and my network. No more taking my laptop with me on the road and working in Ubuntu. I might be forced to use Windows. :( That will be a very sad day. (This is not a threat but only an option). I could never go back to Windows.

I am going to comment on my own post, weird: But I read this under Additional Drivers.
> Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  Security updates and corrections depend solely on the responsiveness of the manufacturer.  Ubuntu cannot fix or improve these drivers.
I just want to say sorry to the Ubuntu developers, it's not your fault for my problems it is the hardware manufacture. If I can get my new card to work I will never use Broadcom products again.

---

### Post by A4orce84 on 2011-05-01
Any updates? I have the same issue..thinking about going back to 10.10

---

### Post by A4orce84 on 2011-05-08
bump

---

### Post by irv on 2011-05-09
Checkout this thread:  [http://ubuntuforums.org/showthread.php?t=1742147&page=4]("http://ubuntuforums.org/showthread.php?t=1742147&page=4")

---

