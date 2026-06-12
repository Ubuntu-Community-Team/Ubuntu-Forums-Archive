---
title: "brsaneconfig4 syntax error for Brother MFC-J825Dw"
date: 2013-06-11
forum: Hardware
---

### Post by LarryMcMains on 2013-06-11
Running Ubuntu 12.04 LTS, trying to get the scanner function of my Brother MFC-J825DW printer/scanner to work. The scanner drivers appear to be installed OK, but when I perform the scanner configuration step from the Brother instructions:
sudo brsaneconfig4 -a name=Scanner model=MFC-J825DW ip=192.168.1.2
the response is always
/usr/bin/brsaneconfig4: 1: /usr/bin/brsaneconfig4: Syntax error: "(" unexpected

I tried multiple names and different model variations, ultimately discovering that even the query form of the command:
sudo brsaneconfig4 -q
results in exactly the same error message.

Clearly, there's no parenthesis in the arguments of either of the commands, so I'm wondering if it's in a script somewhere. Any ideas on how I might proceed?

Larry

---

### Post by gifford on 2013-06-11
Should be:
brsaneconfig4 -a name=SCANNER model=MFC-J825DW ip=192.168.1.2
Just try SCANNER, all in caps.

---

### Post by LarryMcMains on 2013-06-11
No change:

larry@R61:~$ sudo brsaneconfig4 -a name=SCANNER model=MFC-J825DW ip=192.168.1.2
/usr/bin/brsaneconfig4: 1: /usr/bin/brsaneconfig4: Syntax error: "(" unexpected

---

### Post by gifford on 2013-06-11
I cannot see where the syntax error is. Did you install sane-utils before?
Maybe try installing the driver again and then do the config?
Try this link to see if there is anything that helps. [https://secure.kitserve.org.uk/content/ubuntu-brother-printer-scanner-network-setup](https://secure.kitserve.org.uk/content/ubuntu-brother-printer-scanner-network-setup)

---

### Post by jaras67 on 2014-05-31
If you config scanner do not use sudo.

---

