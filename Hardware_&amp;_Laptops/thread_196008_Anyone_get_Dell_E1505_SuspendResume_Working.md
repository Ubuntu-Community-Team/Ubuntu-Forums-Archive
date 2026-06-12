---
title: "Anyone get Dell E1505 Suspend/Resume Working?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by voidPtr on 2006-06-13
With a base install of Ubuntu Dapper Drake 6.06 LTS, Suspend/Resume works just fine.  After upgrading to the 686 kernel (enable dual core processors) and using the 915resolution package to enable 1680x1050, the laptop suspends just fine, but will not resume (upon opening the lid, nothing happens - a power cycle is necessary).

Has anyone managed to get this working?  It's the only thing I don't have working at this point (where I can finally leave Windows XP).

Help!

-voidPtr

---

### Post by acruxksa on 2006-06-13
I just checked mine and suspend seems to work.  Although I recompiled the 686 kernel and changed the processor type to pentium M and the Default CPU Freq Governor to userspace so it's slightly different than what you are running.  The only other kernel config changes I made were to remove a couple usb network driver modules that were giving errors when I tried to compile the kernel.

With that setup I can tell the laptop to suspend via Klaptop and when I press the power switch again it seems to resume just fine.

Also, as you probably guessed since I'm using Klaptop I'm also using Kubuntu 6.06, but I wouldn't think that would matter too much but maybe it does.

---

### Post by nischg on 2006-06-13
Hello:

I am having the same problem. I think I found a solution that I posted on this post: [http://ubuntuforums.org/showthread.php?p=1135520#post1135520]("http://ubuntuforums.org/showthread.php?p=1135520#post1135520")

---

### Post by voidPtr on 2006-06-14
Nope, that didn't seem to work.

I've tried every "solution" I could find in the forums, and nothing has worked.

Again, I'm running an E1505 with i945GM (Intel 950 GMA) using i810 driver and 915resolution package under Linux 2.6.15 686.

I'm hoping someone will figure this out.  It's the only thing I don't have working.

-voidPtr

---

### Post by voidPtr on 2006-06-14
Alright, I noticed in the 2.6.16 Kernel changelog the following:

*Suspend/Resume support for AMD64 GART (commit), ATI (commit) and Intel 945GM (commit)

So, tada.

I figured this might be necessary as this is quite new hardware.

Compiled 2.6.16.20 from kernel.org, and now suspend works. :-)

However, ipw3945 is not working.  *doh*.  How to enable this restricted module?  This was my first shot at compiling a kernel, I hate to be a noobie.

Any help will be appreciated!

-void

---

### Post by acruxksa on 2006-06-14
When I recompiled my kernel I had to create a symlink from /lib/firmware/2.6.15-23-686 to my new kernel.  ie .......... ln -s /lib/firmware/2.6.15-23-686 /lib/firmware/2.6.15-customkernel

Then rebooted and wireless was back up.

Not sure if it will work for 2.6.16 kernels, but it might be worth a try.

---

### Post by voidPtr on 2006-06-15
I tried, but no luck. :-(

ipw3945.ucode is in /lib/firmware/2.6.15-23-686

So under the new kernel I symlinked the output of uname -r (in this case 2..16.20) to /2.6.15-23-686.

It didn't work. :-(

If anyone can teach me how to load ipw3945.ucode under kernel 2.6.16.20 I'd greatly appreciate it!!!  Very close to solution!

-voidptr

---

### Post by voidPtr on 2006-06-15
I seem to have the problem localized.  A modprobe script has to be updated (to start the correct ipw3495 daemon), but more importantly ipw3495.ko (loadable module) has to be compiled against the current kernel ... the only way to get this is building it yourself from sources.  

So, that's what I'll try now.  As soon as I get a solution I'll post the whole bottle of wax for getting Ubuntu 6.06 screaming on the E1505 so others can enjoy it.

-voidptr

---

### Post by voidPtr on 2006-06-15
Well, after today's batch of Ubuntu updates (including 2.6.15-25 coming out), the problem is resolved without any tweaking necessary.

I guess they backported the i945GM fixes from 2.6.16. 

Anyhow, woohoo!  Everything works now.  

-void

---

