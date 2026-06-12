---
title: "why does grub update ask confusing questions"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by tomhorsley on 2009-11-07
I just ran synaptic to get karmic updates today, and got a confusing pop-up when processing the grub-pc update asking things like "Do I walk to school or carry my lunch?". With grub.cfg now always being reconstructed from scratch, why do I get these messages about how to best merge changes? Is it now asking how to merge the /etc/default/grub file? Why wouldn't it just always use whatever is already on the system for that?

---

### Post by jheaton5 on 2009-11-07
Well.  Do you walk to school or carry your lunch?:-({|=

---

### Post by w2vy on 2009-11-07
I think this is the root of the bulk of the booting problems we are seeing.

yes my system is dead in the water and I KNOW that a fresh install is NOT the answer, it is not like I am trying to do anything hard!

I did a distribution upgrade from 9.04 and now get the common message
such as:

> 
init: sreadhead main process (2783) terminated with status 1
mountall start/spawned, process 2784
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/information: No such file or directory
mountall: root filesystem isnt mounted
init: mountall main process (2784) terminated with status 1
General error mounting filesystems.


I did find it odd that I was asked 3 times about menu.lst
and each time the default answer was keep existing file

Why was I prompted that way (No I do not care what the answer is)

I think it should have tried to do the right thing.

tom
ps. I did both walked to school AND carried my lunch

---

### Post by presence1960 on 2009-11-07
> **tomhorsley said:**
> I just ran synaptic to get karmic updates today, and got a confusing pop-up when processing the grub-pc update asking things like "Do I walk to school or carry my lunch?". With grub.cfg now always being reconstructed from scratch, why do I get these messages about how to best merge changes? Is it now asking how to merge the /etc/default/grub file? Why wouldn't it just always use whatever is already on the system for that?
Even GRUB Legacy asked those questions on a kernel upgrade. I always chose and still do choose " use the package maintainer's version" and have never experienced any problems.

---

### Post by w2vy on 2009-11-07
It looks like I fixed it!

In the recovery console I mounted /boot

mount /dev/sda1 /boot

(gotten from fdisk -l )

I then looked to see what kernels I had and found

initrd.img-2.6.31-14-generic and vmlinuz-2.6.31-14-generic 

which happens to be 9.10 (there were some others...)

I then edited /boot/grub/menu.lst to point to this kernel and I was up!

I hope this helps others!

tom

---

### Post by presence1960 on 2009-11-07
> **w2vy said:**
> It looks like I fixed it!

In the recovery console I mounted /boot

mount /dev/sda1 /boot

(gotten from fdisk -l )

I then looked to see what kernels I had and found

initrd.img-2.6.31-14-generic and vmlinuz-2.6.31-14-generic 

which happens to be 9.10 (there were some others...)

I then edited /boot/grub/menu.lst to point to this kernel and I was up!

I hope this helps others!

tom

When you choose "use package maintainer's version" the new kernel is written to the file along with your older kernels. If you choose "use (or keep) your installed version" the new kernel will not be in the file.

---

### Post by tomhorsley on 2009-11-08
> **presence1960 said:**
> When you choose "use package maintainer's version" the new kernel is written to the file along with your older kernels. If you choose "use (or keep) your installed version" the new kernel will not be in the file.

That all makes sense with the old grub, but I installed 9.10 from scratch, I have grub2, the only user editable file is /etc/default/grub, and that file doesn't need to change when new kernels show up. So my question is still there: On a new karmic system using grub2, why on earth do package updates need to ask me the same old questions about merging versions?

---

### Post by w2vy on 2009-11-08
> **presence1960 said:**
> When you choose "use package maintainer's version" the new kernel is written to the file along with your older kernels. If you choose "use (or keep) your installed version" the new kernel will not be in the file.

Is there any way that "use package maintainer's version" could be the default?

Shouldn't the default selection be the one 99% of the people use?

IMHO

tom

---

### Post by tomhorsley on 2009-11-08
> **w2vy said:**
> Is there any way that "use package maintainer's version" could be the default?

Shouldn't the default selection be the one 99% of the people use?

IMHO

tom

That is the default, but from what I read about grub2, there is absolutely nothing to merge, so there is no reason to ask the question at all, that's the part I'm trying to understand. Is it just a leftover script in the packages which should have been removed on the switch to grub2?

---

### Post by w2vy on 2009-11-08
> **tomhorsley said:**
> That is the default, but from what I read about grub2, there is absolutely nothing to merge, so there is no reason to ask the question at all, that's the part I'm trying to understand. Is it just a leftover script in the packages which should have been removed on the switch to grub2?

I was upgrading from 9.04 so  think it uses the legacy grub, not the new version with the new config file.

In any case, it should prompt to do the most logical thing...

keep old was a bad thing to do

tom

---

### Post by drs305 on 2009-11-08
I read the choices as 
"Do you want to keep what works?"
or
"Do you want to try what may be an improvement but may break your system?"

Viewed in that light, I think keeping the default choice as the current version makes sense.

Of course, I usually choose to upgrade to the package maintainer's verison.  ;-)

---

### Post by w2vy on 2009-11-08
> **drs305 said:**
> I read the choices as 
"Do you want to keep what works?"
or
"Do you want to try what may be an improvement but may break your system?"

Viewed in that light, I think keeping the default choice as the current version makes sense.

Of course, I usually choose to upgrade to the package maintainer's verison.  ;-)

All I am saying is that in THIS case KEEP WHAT WILL WORK is what was desired since adding the new kernel the default choice was bad

I guess from all the comments maybe the install process has no way for the package to more strongly recommend a different choice?

Again I was doing a Distribution Upgrade to a single boot system just taking the default choices as most plain users (non-sysadmin) will do.

I tend to expect this to work because the whole foundation of Ubuntu has always been let's put together a linux distribution that regular people can use.

tom

---

### Post by drs305 on 2009-11-08
> **w2vy said:**
> All I am saying is that in THIS case KEEP WHAT WILL WORK is what was desired since adding the new kernel the default choice was bad
tom

I see your point and think it would be worth a bug report to see what the devs say. If your install was performed correctly and the grub menu wouldn't work with the original menu.lst it shouldn't be offered as the default choice - at least not without an explanation of the consequences.

---

