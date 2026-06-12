---
title: "X10 Wireless Transceiver does not work"
date: 2010-10-11
forum: Hardware
---

### Post by tnat on 2010-10-11
Hello,

i've a fresh installed ubuntu 10.10 Maverick Meerkat. Until now i used my X10 Remote Control with the module lirc_atiusb. For this i blacklistet the module ati_remote and wrote
```
lirc_atiusb
```
into /etc/modules. This remote is able to use different channels. For this i set an option
```
options lirc_atiusb mask=0x0001
```

Now in Maverick the command sudo modprobe lirc_atiusb gives me:
```
FATAL: Module lirc_atiusb not found.
```

Has anyone a similar problem or an idea, how i can get my remote to work properly again?

some further infos:
```
Bus 004 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)

2.6.35-22-generic
```


Thanks,
Tom

---

### Post by IcarusR on 2010-10-11
> FATAL: Module lirc_atiusb not found.

That means that the module is not installed.
Could try re-installing lirc.
Failing that download & compile the lirc source code.

---

### Post by tnat on 2010-10-11
Thanks,

its a fresh installation with apt-get install lirc. So far it should work. I will try to compile.

Tom

---

### Post by tnat on 2010-10-12
Ok,

now i have blacklistet the ati_remote module and startet lircd with --driver=atilibusb and is does the same job as lirc_atiusb.
So far so good.
But how can i set the channel acceptance mask like i did as module option for the lirc_atiusb? Has anybody an idea?

Thanks,
Tom

---

### Post by IcarusR on 2010-10-13
You can try creating /etc/modprobe.d/atilibusb.conf with module options in it.

---

### Post by outleradam on 2010-10-25
I'm having the same problem.  Could you please explain, or link to module options?  Never heard of them.

---

### Post by tnat on 2010-11-12
I've got it done. Installing lirc-modules-source brought me the lirc_atiusb module automatically (dkms or so).

Created /etc/modprobe.d/lirc_atiusb.conf with
```
options lirc_atiusb mask=0x0001
blacklist ati_remote

```

The mask because of this receiver listening on channel 1.

In /etc/lirc/hardware.conf i set the REMOTE_DEVICE="/dev/lirc0".
Reboot and have fun.

---

