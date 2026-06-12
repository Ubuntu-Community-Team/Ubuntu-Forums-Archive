---
title: "Just updated 14.04 and getting &quot;System is running in low-graphics mode&quot; message"
date: 2014-10-25
forum: Hardware
---

### Post by mathew2 on 2014-10-25
Hello Ubuntu users,

I installed some updates today and got this message on reboot. The message further goes on to say,

"Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.".

I am using an AMD E-350 processor with updated drivers and everything was running smoothly before the updates. Any help is appreciated.


Thank you in advance,

---

### Post by Bashing-om on 2014-10-25
mathew2; Hi ! Welcome to the forum.

What we often see in this respect is that you "were" running a proprietary (non-ubuntu) graphics driver that got broke in the upgrade process.

Try to (RE-)install a graphics driver from the Additional Drivers utility.
If that broke driver was installed direct from the manufacture's site, or from a PPA, will require manually removing the driver prior to attempting to install another.

If you require guided assistance, provide the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
So we know what we are working with, and what we are working toward.

[INDENT][INDENT]a failure to communicate ( broke driver) 
[/INDENT][/INDENT]

---

### Post by mathew2 on 2014-10-25
Hi Bashing-om,

Thank you for the advice. I will look-up how to manually remove the existing driver. If you have any problems, I will post the outputs from the commands you provided. Thank you also for offering some guided assistance.

---

### Post by mathew2 on 2014-10-25
Hi again Bashing-om,

I was able to uninstall the propriety driver and the GUI came up on reboot.

Thanks again,

mathew2

P.S. -In the 1.5 years, on and off, of fiddling with Ubunutu, the forums have been a huge help. I appreciate the help pros like you give to those us who are still on our first or second "cup of Ubuntu"

---

### Post by Bashing-om on 2014-10-25
mathew2; Great !

We are all at some point on the learning curve. I am glad that I am to the point that I can help others along my way.
(and believe me I am no pro, so much more I want to know/learn -> this operating system of choice) 

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'til we meet again
[/INDENT][/INDENT]

---

