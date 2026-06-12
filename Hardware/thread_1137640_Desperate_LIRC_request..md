---
title: "Desperate LIRC request."
date: 2009-04-25
forum: Hardware
---

### Post by markitoxs on 2009-04-25
Hello,

First of all, after reading what I think was all the possible threads regarding lirc configuration and having achieved quite little... i am desperate and begging for any hint/clue.

I have an hp pavillion dv3500ea, that has a built-in ir receiver. The included remote says on the back RC6. I am not quite sure if my IR receiver is usb as **$lsusb** gives me back:

```
Bus 008 Device 004: ID 10f1:1a09  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 003: ID 138a:0001  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0603:00f1 Novatek Microelectronics Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**138a:0001** is the fingerprint reader / **10f1:1a09** i have no idea and google does not seem to know.

When I try running **$lircd -n** i get:
```

lircd-0.8.4a[9784]: lircd(default) ready
```

and afterwards **$irrrecord attempt.txt** gives:

```
irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

which is quite obvious considering that: 

[B]$ls -l /dev/lir*
srw-rw-rw- 1 root root 0 2009-04-26 01:08 /dev/lircd
[/B]

I have tried **$ln -s /dev/lircd /dev/lirc** and then run irrecord again, wich works, but exits after 10 secs because it cant get any data.

One weird thing is that if i put the laptop to sleep, i can press the power button on the remote, and it will come out of sleeping mode. Just like that.

Any help would be extraordinarely appreciated.

---

### Post by markitoxs on 2009-04-26
*bump

---

### Post by markitoxs on 2009-07-01
bump

---

### Post by tjodSK on 2009-08-17
hello, any news on this? 
I have the same problem...

---

### Post by markitoxs on 2009-08-17
> **tjodSK said:**
> hello, any news on this? 
I have the same problem...

I had ZERO luck so far...

---

### Post by tjodSK on 2009-08-17
as you have probably the same PC, is your fingerprint reader working?

and one more question... the volume touch-control behaves just weird in my case... sometimes, if i want to control the volume the touch control generates too many keystrokes (i guess) and my keyboard locks down, i'm not able to type any character afterwards...

do you experience similar behavior?

---

### Post by markitoxs on 2009-08-17
> **tjodSK said:**
> as you have probably the same PC, is your fingerprint reader working?

and one more question... the volume touch-control behaves just weird in my case... sometimes, if i want to control the volume the touch control generates too many keystrokes (i guess) and my keyboard locks down, i'm not able to type any character afterwards...

do you experience similar behavior?


The fingerprint (a validity vfs101) does not work as it is not supported by fprint yet. There is a bug report for this: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285089)

However, it is already in the developers queue, you can follow progress here:
[http://reactivated.net/fprint/wiki/Unsupported_devices#Daniel.27s_reverse_engineering_queue](http://reactivated.net/fprint/wiki/Unsupported_devices#Daniel.27s_reverse_engineering_queue)

For the volume keys, same behavior as yours. I even sent the laptop back to HP hoping it might be a hardware fault (no chance, but if you dont ask you dont get), but nothing changed. 

Otherwise, I have almost everyhting working with it. Does yours have a backlit keyboard? I love the feel of the keyboard.

I have set up my phone, via bluetooth to control the pc so the remote is not as important. Funny thing, I can control my xbox360 with it.

---

### Post by LubindaMaim on 2009-08-29
I would like to bump this for the lirc problem, all I can add is the model seems to be a 'ITE 8708' judging from the HP driver download section for vista.

---

### Post by markitoxs on 2010-01-09
bump!

**EDIT: significant progress has been made, look here:**

[http://ubuntuforums.org/showthread.php?p=8638716](http://ubuntuforums.org/showthread.php?p=8638716)

---

