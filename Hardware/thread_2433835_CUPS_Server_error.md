---
title: "CUPS Server error"
date: 2019-12-26
forum: Hardware
---

### Post by zalanz on 2019-12-26
I have been unsuccessfully trying to connect my Canon MG5500 printer to my Lubuntu 19.

I have the printer connected to Google Cloud.

When I try to install my printer it recognises it, but says Server CUPS errors. 

Please help??

---

### Post by CelticWarrior on 2019-12-27
Have you installed the manufacturer's drivers?

---

### Post by brian_p on 2019-12-27
For a quick and simple setup plan, you want ```
https://wiki.debian.org/CUPSQuickPrintQueues
```

---

### Post by zalanz on 2019-12-30
Thanks for the reply but nothing in that URL  makers sense to me.  I only have a limited knowledge of Computers.
Are there any commands that will make my Canaon MG5500 work on Lubuntu 19.04  ??

---

### Post by brian_p on 2019-12-30
> **zalanz said:**
> Thanks for the reply but nothing in that URL  makers sense to me.  I only have a limited knowledge of Computers.

A single, small edit to a single file. :confused:

> Are there any commands that will make my Canaon MG5500 work on Lubuntu 19.04  ??

Some handholding, then.

Put the device on the network and give what you get for ```
driverless
```

---

### Post by zalanz on 2020-01-02
alan@alan-pc:~$ driverless
ipp://1685E4000000.local:631/ipp/print

---

### Post by brian_p on 2020-01-02
Now do:

```
lpadmin -p mg5500 -v ipp://1685E4000000.local:631/ipp/print -E -m everywhere
```

and print with

```
lp -d mg5500 /etc/nsswitch
```

---

### Post by zalanz on 2020-01-03
No luck. This is what I got:
alan@alan-pc:~$ lpadmin -p mg5500 -v ipp://1685E4000000.local:631/ipp/print -E -m everywhere
lpadmin: Unable to create PPD file: No such file or directory
alan@alan-pc:~$ lp -d mg5500 /etc/nsswitch
lp: Error - unable to access "/etc/nsswitch" - No such file or directory
alan@alan-pc:~$

---

### Post by zalanz on 2020-01-03
would there be an easier way like connecting to Google Cloud Print?   I can't fathom it out.     I had no problems with Lubuntu prior to moving up to version 19.04

---

### Post by brian_p on 2020-01-03
> **zalanz said:**
> No luck. This is what I got:
alan@alan-pc:~$ lpadmin -p mg5500 -v ipp://1685E4000000.local:631/ipp/print -E -m everywhere
lpadmin: Unable to create PPD file: No such file or directory

This command is fundamental to CUPS and its failure indicates something seriously amiss. It is likely that there is a firmware bug in the printer. See [https://forums.linuxmint.com/viewtopic.php?f=51&t=285448](https://forums.linuxmint.com/viewtopic.php?f=51&t=285448).

> 
alan@alan-pc:~$ lp -d mg5500 /etc/nsswitch
lp: Error - unable to access "/etc/nsswitch" - No such file or directory
alan@alan-pc:~$

A typo: *nsswitch.conf*

---

### Post by zalanz on 2020-01-04
I give up
Thanks for trying to help maybe I go back to version 18

---

