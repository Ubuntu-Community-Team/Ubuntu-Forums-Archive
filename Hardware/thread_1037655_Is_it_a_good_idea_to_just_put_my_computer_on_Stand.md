---
title: "Is it a good idea to just put my computer on Standy instead of Shutting Down?"
date: 2009-01-12
forum: Hardware
---

### Post by black3ug on 2009-01-12
I'm running an Aspire 5570 laptop and there's a problem with the power button. It's very difficult to turn it on. I suspect it's the push button but I don't have the time to fix it. My laptop is my primary work machine.

So, to avoid the "powering-on" problem, I'm thinking I should just put my computer to sleep instead of shutting it down every night. This would mean that my laptop would always be on (even though it would be on minimal power when it's on standby).

My question: Is this a good idea? Will the "always on" state decrease the lifetime of the laptop's components? Can I keep this up indefinitely?

---

### Post by blackened on 2009-01-12
As long as you remove the battery and have it plugged into ac power it should be fine. The minimal power draw used to keep the data in RAM shouldn't lessen the life of any of your components. Leaving it on all the time is a different story.

---

### Post by sdennie on 2009-01-12
Using suspend may even increase the life of the machine.  The "boot" process is far less intensive on the disk with suspend/resume and the disk cache is in tact so you will be accessing the disk less often than from a cold boot.  Whether or not that actually has a noticeable effect on the machines lifetime, I'm not sure.

---

### Post by black3ug on 2009-01-12
@ blackened: why is it necessary for me to remove the batteries? does this have something to do with my battery lifetime? I was planning to use the batteries to power the laptop when in sleep mode. When in work mode, I'd plugin the mains when needed and remove it every now and then to let the battery cycle through drain and recharging states.

@ sdennie: the decrease on hard drive access is definitely a plus. however, since "sleep" uses the ram, does it also mean that the "wear and tear" is transferred to the RAM? also, how big a problem is "fragmentation" in linux machines (obviously, i originally came from the windows world :lolflag:. I "landed" here two years ago.)

---

### Post by oilchangeguy on 2009-01-12
> **sdennie said:**
> Using suspend may even increase the life of the machine.  The "boot" process is far less intensive on the disk with suspend/resume and the disk cache is in tact so you will be accessing the disk less often than from a cold boot.  Whether or not that actually has a noticeable effect on the machines lifetime, I'm not sure.

i'm inclined to think the life of the computer will be decreased by never turning it off. lappy's don't get rid of heat as well as their desktop cousins. and never being turned off, means a build up of vent clogging dust.

---

### Post by blackened on 2009-01-12
> **black3ug said:**
> @ blackened: why is it necessary for me to remove the batteries? does this have something to do with my battery lifetime? I was planning to use the batteries to power the laptop when in sleep mode. When in work mode, I'd plugin the mains when needed and remove it every now and then to let the battery cycle through drain and recharging states.


It's not good to keep the battery fully charged for extended periods of time. If you find yourself using it as more of a small desktop machine, then it's best to discharge the battery to about 40-50%, remove it, then run only on mains.

Make sure you use the battery at least once a month or so, even if you're not going mobile with it.

> @ sdennie: the decrease on hard drive access is definitely a plus. however, since "sleep" uses the ram, does it also mean that the "wear and tear" is transferred to the RAM? also, how big a problem is "fragmentation" in linux machines (obviously, i originally came from the windows world :lolflag:. I "landed" here two years ago.)

Keep in mind that harddrives are pieces of hardware with moving parts, while RAM is not. Lessening the use of an HD can dramatically increase its lifespan, whereas lessening the use of RAM does not.

Most modern filesystems don't suffer from fragmentation the way NTFS and FAT do. Which is why you're not ever likely to see a defrag program installed by default on a Linux distro.


> **oilchangeguy said:**
> i'm inclined to think the life of the computer will be decreased by never turning it off. lappy's don't get rid of heat as well as their desktop cousins. and never being turned off, means a build up of vent clogging dust.

In suspend all of the hardware is shut down leaving it to draw just enough power to keep the suspend data in RAM. Little to no heat should be built up (and thus no need to be dissipated) while the machine is suspended or in sleep mode.

---

### Post by black3ug on 2009-01-14
thanks for all that info **blackened**. For the past two days, I've been putting my laptop to sleep instead of shutting down every night. It's been great so far. My boot time is faster and I find myself jumping right into my work every time I flip the lid of my laptop open. On the whole, this has turned out to be a great idea!

about **oilchangeguy's** comments, he might have something there. I've read somewhere that electricity does something to dust. I can't remember if it is "attract" or "repel" dust. Also, I'm wondering how much heat a laptop retains if it is continuously powering the RAM when in sleep mode. 

Thanks for the reply guys. ([COLOR="Silver"]I'm marking this thread "solved" just because I've got some answers now[/COLOR]). However, I think the "sleep vs shutdown" issue needs more discussion.

---

