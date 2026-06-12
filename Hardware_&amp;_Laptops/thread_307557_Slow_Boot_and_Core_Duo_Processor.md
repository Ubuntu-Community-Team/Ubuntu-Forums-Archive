---
title: "Slow Boot and Core Duo Processor"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by samba on 2006-11-26
Hi,

I upgraded to 6.10 a few weeks ago. Everything works fine, but I noticed that boot time is longer now than it was on Dapper (at least I think). So I tried to figure out what the problem is. I installed bootchart; I attach to this post what it has drawn in /var/log/bootchart. It looks like the problem is the network part of the boot process (module ipw3945, dhclient, etc.). But I don't know enough about boot processes to understand what is wrong... Anyone knows what the problem is?

On another note, it that picture it says that my processor is a "Genuine Intel(R) CPU T2400 @ 1.83 GHz", while it is a "Intel Core Duo Processor T2400 @ 1.83 GHz". Does that mean it doesn't recognize the Core Duo processor? Or does it not matter?

Thanks :-)
Vincent

---

### Post by pestilence4hr on 2006-11-30
The problem is the networking is being brought up before the wireless is ready.  So you probably have the wireless card set to auto configure when booting, and since it tries to do this before the hardware is made ready (the ipw3945d-`uname -r` program is part of this process), it fails.  But the "fail" takes a really long time, as it basically waits for dhcp to timeout.

The fix is to get it to wait for the hardware to be ready before it brings up the interface.  This is certainly a bug.  If I figure out the workaround, I'll let you know.  Somebody should file a bug report.

---

### Post by pestilence4hr on 2006-12-02
So here's what I did, and it seems to work.  Edit /etc/init.d/networking so that in the "start" action, it sleeps for a few seconds:

```
...
case "$1" in
start)
     sleep 10;
     log_action_begin_msg "Configuring network interfaces"
...
```

This is a hack, but it works.  If you use suspend-to-ram, you will also need to edit /etc/acpi/resume.d/62-ifup.sh to contain a similar sleep command.

A much, much better solution would be for ifup to realize the hardware is not ready and wait.

---

### Post by samba on 2006-12-03
Thanks a lot! It does work indeed. :-)

I'm happy to file a bug if you haven't done so already, but where should I file it? Sorry I'm not that familiar with bug-filing. :-)

Thanks again,
Vincent

---

### Post by sebw on 2006-12-05
Thanks for the fix

I had the same issue and never really bothered trying to address the issue..

My hardware : toshiba L100, Intel Core Duo T2300 + ipw3945

I'll try to find if a bug report has already been filled

---

