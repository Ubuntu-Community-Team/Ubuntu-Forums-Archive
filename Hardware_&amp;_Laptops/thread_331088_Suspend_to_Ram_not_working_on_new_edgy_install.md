---
title: "Suspend to Ram not working on new edgy install"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by superm1 on 2007-01-04
Hi,

I was setting up a laptop for my mother to use Ubuntu 6.10 in a dual boot with Windows in an attempt to ween her away from her Windows.  The laptop is a HP ze4430us (AthlonXP 2400+, 512 Ram, Radeon IGP (R200 series)).

I've gotten the entire laptop working fairly well, got her wireless going, and all of the stuff she needed imported, but forgot to check suspend support until the last minute.  It appears that suspend to disk works no troubles, wireless comes back immediately, and all is fine.

The problem is Suspend to Ram.  I know she will use it rather than suspend to disk because that is what she uses in windows constantly.  The machine suspends fine, but when trying to resume will turn back (fan spins up and lights turn on) on and then immediately off (as in fully off).

I experimented with using the boot parameter
```
acpi_sleep=s3_bios
```and this appears to provide a little more luck.  The machine stays on for a resume, but appears to be hung at a black screen.

I updated the BIOS to the latest BIOS available at this time, revision 60.
Since this is a R200 based graphics card, i'm not bothering to install the fglrx drivers - the open source driver is very well supported for the R200 card.
I messed around with a few of the options that affected changing radeonlight and vbestate in /etc/default/acpi-support, but didn't come across any further luck.

It also appears that searches across google point to failed attempts with FC5 and earlier with suspend to ram for models in the ze' series.

I'm hoping to get this working for her in the next two days before I head back to school :)

On a side note, what is the big appeal in suspend to disk anyway?  It takes longer to resume a suspended to disk setup then it does for a fresh boot!

---

### Post by greg.hagen on 2007-01-12
I have a similar problem, except mine stays on. Nothing wrong except a lit, but black screen and no keyboard functionality. I can even SSH to it. This seems to be a really common problem. I'll be sure to post here if I get mine working.

---

### Post by superm1 on 2007-01-12
> **greg.hagen said:**
> I have a similar problem, except mine stays on. Nothing wrong except a lit, but black screen and no keyboard functionality. I can even SSH to it. This seems to be a really common problem. I'll be sure to post here if I get mine working.

For now I just told her, suspend doesn't work - just turn the machine off when she is done using it.  Thank goodness for edgy's quick boot up times :)

That'll be awesome if you find something though :)

---

### Post by trubblemaker on 2007-01-18
my suspend does kinda work  the power modules that I have 

acpi
gnome-power-manager

(My synaptic touch pad doesn't work after suspend, but everything else does and I'd suspect that a normal mouse would be fine.)

an alternative method to suspend checkout  [www.suspend2.net](www.suspend2.net)

hope this helps, glad our paths crossed again.

---

### Post by superm1 on 2007-01-18
> **trubblemaker said:**
> my suspend does kinda work  the power modules that I have 

acpi
gnome-power-manager

(My synaptic touch pad doesn't work after suspend, but everything else does and I'd suspect that a normal mouse would be fine.)

an alternative method to suspend checkout  [www.suspend2.net]("http://www.suspend2.net")

hope this helps, glad our paths crossed again.
Ah hello trubblemaker :)
suspend2 is another method for writing to disk though at shutdown( eg hibernation), correct?  Does it also have alternative suspend to ram support too?


Also, what model computer were you using that you had things "just working" with acpi and just suspend2 patches/sources.

---

### Post by trubblemaker on 2007-01-18
I apologize for not being clear, I didn't have suspend2 working on edgy I had previosly used it for dapper and it was to disk.  It's been awhile since I used it and apologize I thought I had used it for suspend to ram aswell.

My suspend to ram now kinda works (again with the exception of no mouse on wake)

if you have a think pad  [here's a big report]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59851") with patch for suspend issue that sounds similar

Of course if you don't have a think pad it might not help you.

I happend to be looking into the issue to get my mouse fixed.

on the bright side the thread also mentions the fix you looked into "acpi_sleep=s3_bios"

hope this helps :)

---

