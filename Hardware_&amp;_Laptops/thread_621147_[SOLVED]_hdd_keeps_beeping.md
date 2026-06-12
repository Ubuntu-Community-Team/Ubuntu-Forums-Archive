---
title: "[SOLVED] hdd keeps beeping"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by kaurman on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/152439](https://bugs.launchpad.net/bugs/152439) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi!

I have a strange problem with my laptop. I've described it in launchpad: [https://bugs.launchpad.net/bugs/152439](https://bugs.launchpad.net/bugs/152439) but as it hasn't been solved I thought that maybe I should write here instead.

So, any ideas how to solve this?

PS using the 2.6.20-16-generic kernel is a temporary solution but as it causes quite a few other problems (frequency scaling isn't working etc.) I'd still like to be able to use the proper Gutsy kernel.

Thanks in advance,

Kaur

---

### Post by Linicks on 2007-11-23
In your report you state that hdparm -B 255.

There is NO such value for this flag.  There is a post in the SMART forums somewhere, that the author says this, and you should NOT set hdparm -B 255 as some drives ignore it, and some don't but it does funny things.

Set it to 254 and test.

Nick

---

### Post by kaurman on 2007-11-23
> **Linicks said:**
> In your report you state that hdparm -B 255.

There is NO such value for this flag.  There is a post in the SMART forums somewhere, that the author says this, and you should NOT set hdparm -B 255 as some drives ignore it, and some don't but it does funny things.

Set it to 254 and test.

Nick
Hi!

This value seems to exist. Quoting from the manual of hdparm: 
-B Set Advanced Power Management feature, if the drive supports it. A low value
means aggressive power management and a high value means better performance. A value of 255 will disable apm on the drive.

Though you may be right that setting the value to 255 is not a good idea. In that case I'd appreciate any further information on the subject. For me 255 seems to work fine as hdd stays nice and quiet when apm is disabled. If I'm correct 254 and a few other values I've tried, cause it to start 'clicking' few times a minute which I consider bad.

Kaur

---

### Post by Linicks on 2007-11-23
OK, of course value 255 exists... but what it does it do...

I found the thread from Bruce Allen, smartmontools guy.  Read the second in the thread:

[http://sourceforge.net/mailarchive/message.php?msg_id=449918940710280827g50e829d6oc2773faaa5a1702c%40mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_id=449918940710280827g50e829d6oc2773faaa5a1702c%40mail.gmail.com)

> IMPORTANT INFORMATION BELOW: PLEASE PASS BACK TO THE UBUNTU COMMUNITY
 
 I think that the -B value of 255 is incorrect. You should use 254 for 
 maximum performance. 255 IS DOCUMENTED AS 'RESERVED' IN THE ATA/SATA 
 SPECS. THE BEHAVIOR OF -B 255 THUS IS NOT PREDICTABLE AND IT MAY HAVE NO 
 EFFECT. Also according to the ATA/SATA specs any value greater than or 
 equal to 128 will 'not permit the device to spin down to save power'. So 
 128 will reduce power use as much as possible but not permit spin-down.

...
...

So I suggest you try some different -B values such as -B 254 or -B 128.
 
 The hdparm man page says 'values of 255 will disable Advanced Power 
 Management'. I think this is a mistake in the man page. According to the 
 ATA/SATA specs referenced above, the value 255 is reserved and has vendor 
 dependent meaning (or has no effect).


Nick

---

### Post by kaurman on 2007-11-23
Ok, thanks a lot! With hdparm -B254 and 2.6.22-14-generic seem to work quite well together:) The testing period hasn't been too long though so nothing is certain yet...

I'm 100% sure that the older kernel I mentioned in the bug report worked fine with 255. That's weird as the behavior of the drive should be vendor and not kernel specific if -B is set to 255. Or am I overlooking something here? 

I still have one problem: the beeping sound seems to be still present until I log into gnome.  The value of -B is set using etc/rc.local so I guess it has been set by the time I see the login screen. Considering that I'm a bit confused... What's the trick that gnome does and can I force the system to do it a bit earlier?

---

### Post by kaurman on 2007-11-25
I just want to report that the problem is still present. It seems to occur randomly. Sometimes the system boots up fine but sometimes I keep hearing the beeping sound.

---

### Post by kaurman on 2008-03-18
Hi!

I can report that for me, the problem is solved. It turned out that the beeping component was the CPU.
Solution can be seen [here.]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/155142/comments/21")

---

