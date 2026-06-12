---
title: "occasional APCI errors on boot - Macbook"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by forbes on 2006-07-09
Hi everyone,

I am getting kernal panics randomly when I start/reboot my linux install on my macbook (not pro):

```

APCI: Looking for DSDT ... not found
ENABLING IO-APIC IRQs
.. TIMER:vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
.. MP-BIOS bug: 8254 timer not connected to IO-APIC
... trying to setup timer (IRQ0) through the 8259A ... failed.
... trying to setup timer as virtual wire IRQ ... failed.
... trying to setup timer as ExtINT IRQ ... failed :(.
kernal panic - notsyncing:IO-APIC + timer doesn't work! Boot with apic=debug and send a report.  Then try booting with the "noapic" option

```

Just wondering if other people are also getting this or its a setup error/corruption on my part. The strange thing is that it is quiet random when it happens.

Any pointers would be great

---

### Post by rapido on 2006-07-10
I thought I would chime in to say that I am also seeing the same issue, but on a Macbook Pro ( 15" ).  Like you mentioned, quite random.  For me, it is about every 3rd or 4th boot.

---

### Post by forbes on 2006-07-10
Thanks rapido.

From the macintel developers list today there was the following emails:

> Message: 1
Date: Mon, 10 Jul 2006 08:27:25 +0200
From: Ketzal <ketzalqoatl@gmail.com>
Subject: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not connected to
	IO-APIC
To: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <200607100827.25314.ketzalqoatl@gmail.com>
Content-Type: text/plain;  charset="us-ascii"

Hello,
on my MacBook (!pro) I experience kernel panic at boot time. it happens 
randomly, but frequently enough for beeing really boring (about 1 time on 3).
I boot via rEFIt / lilo (on bootcamp partition), with a 2.6.17-3 kernel 
patched with the full patchset. After a panic I try sometimes to reboot under 
OSX (in hope that some initialisation will get done, allowing me to restart 
linux cleanly), but it doesn't work consistently.

Here's the message :
MP-BIOS bug: 8254 timer not connected to IO-APIC
... trying to setup timer (IRQ0) through the 8259A ... failed
[some other tier setup failing]
kernel panic - not syncing: IO-APIC+timer doesn't work

Is this hardware pb ? does somebody out there experienced such crashes ?
should I disable the apic (and if I do so what will I loose ?)

> Message: 2
Date: Mon, 10 Jul 2006 03:10:38 -0400
From: Ed Martin <edman007x@mac.com>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to IO-APIC
To: [email]ketzalqoatl@gmail.com[/email]
Cc: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <44B1FD6E.8010508@mac.com>
Content-Type: text/plain; charset=ISO-8859-1; format=flowed

i'm not sure if it really needs code to be edited, but you can just add 
"noapic" to the kernel bootline (no quotes), that will prevent it from 
trying APIC stuff and hence no error and i see no problems on my system 
from not having APIC (i don't really know what it does)

and i think everyone gets this...at least i do, you might be able to 
remove APIC from the kernel, but i didn't feel like testing that

> Message: 8
Date: Mon, 10 Jul 2006 11:15:40 -0400
From: Armando Di Cianno <armando@goodship.net>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to	IO-APIC
To: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <20060710151540.GE4704@chani>
Content-Type: text/plain; charset="us-ascii"

On Mon, Jul 10, 2006 at 03:10:38AM -0400, Ed Martin wrote:


I had something similar to this issue a while back.  I think it has to
do with using the hpet timer as the system timer.

I do turn on:
CONFIG_HPET and
CONFIG_HPET_MMAP
(under Character Device drivers; although I dont know when/if I'll ever
be using this)

I do *turn off*
CONFIG_HPET_TIMER -- this definitely effects the need for different
kernel command line options to get a stable system. (This is under
Processor Type and Features.)

I do not have noapic or any other similar boot options on my MBP 15",
and things boot and run in a stable fashion (even suspend2).

__armando

Not sure what the last comment means, but at least other people are experiencing the same thing.

I'll post here if I see any more comments to this on the mailing list.

---

### Post by forbes on 2006-07-10
and this:

> Message: 1
Date: Mon, 10 Jul 2006 19:39:04 +0200
From: gimli <gimli@dark-green.com>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to IO-APIC
To: Armando Di Cianno <armando@goodship.net>
Cc: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <44B290B8.4020809@dark-green.com>
Content-Type: text/plain; charset=ISO-8859-15

Hi.

Do you also have CONFIG_HPET_RTC_IRQ=y in your kernel config?

cu

gimli


and:

> Message: 2
Date: Mon, 10 Jul 2006 11:52:19 -0400
From: Armando Di Cianno <armando@goodship.net>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to	IO-APIC
To: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <20060710155219.GG4704@chani>
Content-Type: text/plain; charset="us-ascii"

On Mon, Jul 10, 2006 at 07:39:04PM +0200, gimli wrote:
> Hi.
> 
> Do you also have CONFIG_HPET_RTC_IRQ=y in your kernel config?

No, that is off / not-configured.

No particular reason, except that it seemed like it could interfere with
the issue (similar to the one being discussed) I was having.

... can I ask what you are thinking of, with respect to this?

__armando


> 

---

### Post by rapido on 2006-07-11
Thanks for the thorough follow-up ( to your own post ).  BTW, have you decided to try the noapic boot option, or the kernel compile route?

---

### Post by forbes on 2006-07-11
> **rapido said:**
> BTW, have you decided to try the noapic boot option, or the kernel compile route?

TBH now that there seems to be a bit of activity regarding this on the dev list, I'll probably wait for a few days to see what they discover.  These guys have been fairly rapid at fixing issues and wouldn't be surprised if there was a patch for this sooner rather than later.

---

### Post by forbes on 2006-07-11
more:

> Message: 2
Date: Tue, 11 Jul 2006 10:15:37 +0200
From: gimli <gimli@dark-green.com>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to IO-APIC
To: Armando Di Cianno <armando@goodship.net>
Cc: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <44B35E29.9090602@dark-green.com>
Content-Type: text/plain; charset=ISO-8859-15

Is CONFIG_CRASH_DUMP set in your config ?
Dissable CONFIG_HPET_RTC_IRQ makes suspend/resume
unworkable.

cu

Edgar (gimli) Hucek

---

### Post by forbes on 2006-07-12
today:

> Message: 1
Date: Tue, 11 Jul 2006 15:13:49 -0400
From: Armando Di Cianno <armando@goodship.net>
Subject: Re: [Mactel-linux-devel] MP-BIOS bug: 8254 timer not
	connected to	IO-APIC
To: [email]mactel-linux-devel@lists.sourceforge.net[/email]
Message-ID: <20060711191349.GH4704@chani>
Content-Type: text/plain; charset="us-ascii"

On Tue, Jul 11, 2006 at 10:15:37AM +0200, gimli wrote:
> Is CONFIG_CRASH_DUMP set in your config ?
> Dissable CONFIG_HPET_RTC_IRQ makes suspend/resume
> unworkable.

# gzcat /proc/config.gz |grep -i crash
# CONFIG_CRASH_DUMP is not set

So, if I understand you correctly, dissabling CONFIG_HPET_RTC_IRQ makes
suspend not work for you?  Are you using CONFIG_HPET_TIMER?  That is the
configure option that is making suspend not work for me.  I
had some luck, with CONFIG_HPET_TIMER, when I used various kernel
cmdline options, like noapic.  At the time, setting CONFIG_HPET_TIMER
off, and not using the cmdline options seemed like the better option.

So, I guess the question is, is it more valuable to have the system
timer be HPET (I'm assuming the MBP's have an HPET), and not have APIC,
or is it better to use the legacy system timer and have APIC?  I do not
know the factors that would make one option better than the other.

__armando

---

