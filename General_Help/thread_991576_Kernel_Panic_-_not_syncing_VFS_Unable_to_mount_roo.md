---
title: "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2008-11-23
forum: General Help
---

### Post by kmacmillan on 2008-11-23
Hi,

recently my laptop stopped booting altogether:

I have a dual-boot XP and Hardy running on an older Compaq V2000 laptop.

Hardy gives this error when it tries to boot:
"
Starting up...
[    32.774566] incomplete literal tree
[    32.774566] invalid compressed format (err=1)
[    32.774566] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
"
and when I try to boot XP, it starts booting then restarts the computer.

Help! I know enough about this that I can try to do a windows restore via the XP disc, but if there is something easier and less time consuming I would do it.  I am not sure why my drive no longer mounts (if that is the problem).

Any help appreciated.

-Keith

---

### Post by prshah on 2008-11-24
> **kmacmillan said:**
> 
and when I try to boot XP, it starts booting then restarts the computer.


Clearly, this looks like a hardware problem, since both XP and Ubuntu are affected. We can troubleshoot this by checking the Windows error message (Blue Screen) as below.

You need to see why Windows is (instantly) restarting; you can do this in two ways:

1) Immediately after selecting the Windows option in GRUB, keep tapping F8 to get the startup options menu.

== OR ==

2) From Ubuntu (installed or liveCD), edit the MSDOS.SYS file in your Windows partition, and add the below line to the [Options] section:
```

BootMenu=1

```

(if there is no [options] section or if the msdos.sys file is blank, then use
```

[Options]
BootMenu=1

```

Now, when you boot Windows, the startup options menu will appear automatically, without the need to tap F8.

==

Then, from the boot menu, choose the "Disable Automatic Restart on Failure" option. Then let windows boot normally; near the end of the process, you will get a blue screen which will state the cause of the error; post back the error message and details, and we can see how to resolve it easily.

Most likely the error will be similar to "Cannot find NTLDR/System.Dat/User.Dat/SAM/SECURITY" etc. In this case, it's quite easy to resolve, depending on the actual file (area) affected.

However, since Ubuntu is also affected, I suspect a memory issue; have you recently made a RAM change or so? In that case, use the "Test Memory" option from the live CD, or the memtest option from GRUB (If you have it.)

Post back with results...

---

### Post by kmacmillan on 2008-11-24
Blue screen gives only this

"Technical information:

*** STOP: 0x0000007E  (0xC0000005, 0xF7716DB6, 0xF7AAF688, 0xF7AAF384)"

When I run a mem test from the GRUB menu, it just spits out errors in the millions. At first I was thinking I could just reinstall XP on this pc and just forget about my lost data, but now I'm thinking it might just be trash.

---

### Post by kmacmillan on 2008-11-24
Do you think new RAM would solve this problem?

---

### Post by prshah on 2008-11-25
> **kmacmillan said:**
> 
*** STOP: 0x0000007E  (0xC0000005, 0xF7716DB6, 0xF7AAF688, 0xF7AAF384)"
When I run a mem test from the GRUB menu, it just spits out errors in the millions. 

> **kmacmillan said:**
> Do you think new RAM would solve this problem?

The 0x0000007E error is a "generic" error message that can be related to any or all of the below:

a) Bad memory
b) Lack of HDD space
c) Corrupt HDD structure (usually falsely resulting in (b) above)
d) Corrupt or damaged driver file(s)
e) Malicious or faulty driver file(s)
f) Certain third party remote control programs
g) Incompatible or damaged BIOS on motherboard

Since you say that memtest is spitting out errors (Anything in RED is bad), then I suspect memory. In that case, replacing the memory should clear the problem.

However, if you've recently flashed the BIOS, then that may be the cause of the problem; in that case, post back for steps that can possibly solve the problem.

If the system was working fine all along, it is unlikely that your RAM is damaged; solid state devices such as RAM hardly ever fail; I'm still using RAM that is over 15 years old.

If your board is dusty, it may be causing false connections or shorts; so I'd suggest as a first step, you should open up your case, and use a [powerful vacuum cleaner set on _BLOW_ **not suck** and give your case a good airing]("http://www.youtube.com/watch?v=euvuDQLaIsY"). Then use a flat brush to clear out visible / matted dirt, and give it one more good airing. Then put your RAM back in and try to see if the system works.

---

### Post by kmacmillan on 2008-11-26
Well if we say that a RAM problem is highly unlikely on a 2 year old laptop,
Rule out lack of HDD space,
and since I have not flashed the BIOS then we can also rule out a damaged motherboard.

which leaves:
corrupt Driver Files/HDD structure
Malicious/faulty driver files,
and third party remote software.

Is VNC an example of third party remote software? because I had tightVNC running and my laptop was set up as a VNC server for the network.

I checked inside the casing for the RAM, not dusty at all, I blew out some dust near the fan, but that was all the dust I could see.

I suspect something to do with bad driver files, but how could I find out which files were the problem, and how do I correct them?

---

### Post by prshah on 2008-11-26
> **kmacmillan said:**
> say that a RAM problem is highly unlikely on a 2 year old laptop,

which leaves:
corrupt Driver Files/HDD structure
Malicious/faulty driver files,
and third party remote software.

Is VNC an example of third party remote software? because I had tightVNC running and my laptop was set up as a VNC server for the network.


Ruling out RAM is a pretty unreliable conclusion, since memtest gives errors. 

To repair all the rest of the possibilities, you need to use the Recovery Console, from the XP setup disk. Start with chkdsk.

Yes, VNC can be counted as remote third party software, but that is unlikely to have caused this problem.

---

### Post by kmacmillan on 2008-11-28
I pulled out my ram, and tried booting the computer one 512mb stick at a time, and I had the same errors.

when starting in safe mode on windows it gets hung up on mup.sys

So I should run chkdsk through the recovery console?

---

### Post by prshah on 2008-11-28
> **kmacmillan said:**
> I pulled out my ram, and tried booting the computer one 512mb stick at a time, and I had the same errors.
when starting in safe mode on windows it gets hung up on mup.sys
So I should run chkdsk through the recovery console?

Yes, but considering all your actions, I'd say RAM (or related) is the likely culprit. 

Did you try swapping the two sticks? Or using each stick individually?

---

