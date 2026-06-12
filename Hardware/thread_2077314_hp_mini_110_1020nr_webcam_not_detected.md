---
title: "hp mini 110 1020nr webcam not detected"
date: 2012-10-28
forum: Hardware
---

### Post by a z on 2012-10-28
searched these forums and the internet in general - the threads for this seem to go unanswered - hope that doesn't happen here.

webcam has worked in the past(with another distro before i installed Lubuntu 12.10). 

don't point me to rastageeks site for the ov51x thing - it's apparently no longer there.

help
please

---

### Post by mikewhatever on 2012-10-28
Can you post the output of **lsusb**, and also explain why you think it's undetected.

---

### Post by a z on 2012-10-28
sure.

az@az-mini:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

any ideas?

---

### Post by a z on 2012-10-28
...no idea what that output means, but it doesn't look good.

really appreciate any help,
a z

---

### Post by a z on 2012-10-29
i didn't mean it to sound snarky when i said (in original post) that webcam worked with a previous distro, only wanted to point out that the webcam ITSELF is probably not the issue.

love ubuntu (lubuntu 12.10)!!!

just want to resolve this so i can skype my family when i work out of town.

thanks,
a z

---

### Post by a z on 2012-10-30
well, i have no idea what i did, but now webcam works..
lsusb output looks like this, now:

az@az-mini:~$ lsusb
Bus 001 Device 002: ID 174f:1105 Syntek SM-MS/Pro-MMC-XD Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

go fig...

---

