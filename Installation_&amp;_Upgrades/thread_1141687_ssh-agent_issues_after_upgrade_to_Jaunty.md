---
title: "ssh-agent issues after upgrade to Jaunty"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by dbrian on 2009-04-28
After I upgraded from 8.10 to 9.04 my ssh keys no longer work. Permissions seem fine, .ssh is 700 and everything inside is 600.  I checked my keys against a backup and they work just fine when moved to a RHEL5 box.

I noticed if I copy my private key to another file and specify it with "ssh -i" I am prompted for a passphrase and able to login as expected.

It seems something has to be wrong with ssh-agent.  Does anyone have any ideas on how to fix this?

---

### Post by ecarlseen on 2009-05-12
Same issue... has anybody solved this?

---

### Post by jobix on 2009-05-12
What's the output of "ssh-add -l"?

---

### Post by SDERAWI on 2009-05-25
2048 68:2e:5b:b7:9c:2d:86:b4:b8:d7:f6:9e:73:3c: xx: xx SSH (RSA)

---

### Post by Brandon Williams on 2009-05-25
Try running ssh with the -v option to see if you can get any sense of what's going wrong. You should see a line that looks like this:
```
debug1: Offering public key: /home/user/.ssh/private.key
```
Where the filename specified is the filename of your private key. Do you see such a line? And if so, is there any kind of error message indicating a problem with the key?

---

