---
title: "No touchpad after suspend (unable to enumerate USB device on port 1)"
date: 2009-02-20
forum: Hardware
---

### Post by gumbeto on 2009-02-20
Hello,

I have a Dell Studio XPS 16 and, after suspending and waking up, my touchpad doesn't work. I have searched a lot about this issue, but I can't find any solution. 

I already tried adding resume scripts as suggested here: [http://ubuntuforums.org/showpost.php?p=2690982&postcount=14](http://ubuntuforums.org/showpost.php?p=2690982&postcount=14)
but it didn't solve the problem. In fact, even doing the unbind and bind manually has no effect. 

I also tried adding to grub's menu.lst the option "i8042.reset" alone, as well as along with the option "i8042.nomux". After restarting, no success either.

I noted that when I waked up the computer, the following message showed up for less than a second: "hub 2-0:1.0: unable to enumerate USB device on port 1". I did a grep in /var/log/ (because I don't really know what each log is responsible for) and found this message in the logs .dmesg, .dmesg.0, kern.log, and syslog.

I can't go any further. My usb mouse works fine though. Anyone has any other suggestions?

Thank you

---

### Post by theOtherMarino on 2009-03-26
In yesterday dmesg:

```
[    3.140120] usbcore: registered new interface driver hub
[    3.592959] hub 1-0:1.0: USB hub found
[    3.592967] hub 1-0:1.0: 2 ports detected
[    3.800534] hub 2-0:1.0: USB hub found
[    3.800541] hub 2-0:1.0: 2 ports detected
[    4.009748] hub 3-0:1.0: USB hub found
[    4.009756] hub 3-0:1.0: 2 ports detected
[    4.216424] hub 4-0:1.0: USB hub found
[    4.216433] hub 4-0:1.0: 2 ports detected
[    4.532832] hub 5-0:1.0: USB hub found
[    4.532845] hub 5-0:1.0: 8 ports detected
[    4.588042] hub 2-0:1.0: unable to enumerate USB device on port 2
```

In today's:

```
[    3.067063] usbcore: registered new interface driver hub
[    3.112225] hub 1-0:1.0: USB hub found
[    3.112234] hub 1-0:1.0: 8 ports detected
[    3.720877] hub 2-0:1.0: USB hub found
[    3.720885] hub 2-0:1.0: 2 ports detected
[    3.928446] hub 3-0:1.0: USB hub found
[    3.928455] hub 3-0:1.0: 2 ports detected
[    4.136429] hub 4-0:1.0: USB hub found
[    4.136438] hub 4-0:1.0: 2 ports detected
[    4.344448] hub 5-0:1.0: USB hub found
[    4.344456] hub 5-0:1.0: 2 ports detected
```

Yet another kernel bug? See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767") Searching the web, you'll find many distros (fedora, redhat) are affected too.

My kernel is 2.6.27-11 generic.

---

### Post by theOtherMarino on 2009-03-26
> This is a known problem See : [http://forums.debian.net/viewtopic.php?t=36197&sid=fbf5dcda119d8d29693846b241af7ceb]("http://forums.debian.net/viewtopic.php?t=36197&sid=fbf5dcda119d8d29693846b241af7ceb")

---

