---
title: "Thinkpad X301 Won't sleep"
date: 2011-02-21
forum: Hardware
---

### Post by variable7 on 2011-02-21
Hi everyone, this is my first time posting.
Been using Ubuntu 10.10 for about 4 months now. It's the first time I've actually made the jump to Linux from Windows and I'm loving it. I'm an advanced Windows user and intermediate on OS X.

I have a Thinkpad X301 and recently it has begun to refuse sleep. I don't get any error messages. When I close the laptop, or use the FN button combination it does everything that it normally would when going to sleep, but then just goes back to the login screen. (Even the sleep light on the monitor blinks momentarily, then goes off.) The preferences are all configured to sleep when I close the lid. I haven't installed any fancy power management software either.

I'm running 10.10 64-bit. I had everything working fine in 32 bit, but then decided to reinstall from scratch and go with 64-bit when it stopped working in 32-bit. I was happy it went away by reinstalling (64-bt), but now the problem is back again. Just don't know where to begin debugging this. Any advice would be greatly appreciated, thanks!

---

### Post by variable7 on 2011-02-21
A few more details...
What I'm trying to do is also called "suspend" or "sleep" NOT hibernate. I'm trying to save the session to RAM only and go to a low power state.

When I try Hibernate, I get some messages on the screen, which include this:
"[...]device 00:0a failed to suspend
and it does the same thing as when I try sleep.

I looked in system log viewer and found this, which also indicates the error code:
Feb 21 17:20:23 steve-lt kernel: [ 2028.710123] tpm_tis 00:0a: tpm_transmit: tpm_send: error -5
Feb 21 17:20:23 steve-lt kernel: [ 2028.710134] legacy_suspend(): pnp_bus_suspend+0x0/0x90 returns -5
Feb 21 17:20:23 steve-lt kernel: [ 2028.710140] PM: Device 00:0a failed to freeze: error -5

Any ideas? Thanks again.

---

### Post by bawolfe on 2011-02-22
I've been getting this error lately as well.  Looks like someone opened this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707716)  I haven't tried booting into an earlier kernel as suggested in the comment yet, but will try it tomorrow.

---

### Post by variable7 on 2011-02-23
> **bawolfe said:**
> I've been getting this error lately as well.  Looks like someone opened this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/707716)  I haven't tried booting into an earlier kernel as suggested in the comment yet, but will try it tomorrow.

Thanks for responding. Any luck? I've been trying to figure out how to roll back to an earlier kernel, but haven't had a lot of time. I'd like to know it's worth the effort if it works for you.

---

### Post by variable7 on 2011-02-23
Rolled back my kernel to "2.6.35-22-generic" worked for me as well. Thanks! (I did it the newbie way, using "StartUp-Manager")

---

