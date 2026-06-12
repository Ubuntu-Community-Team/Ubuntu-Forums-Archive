---
title: "[SOLVED] System Freezes on Boot (Ndiswrapper Error?)"
date: 2008-10-26
forum: General Help
---

### Post by Altay_H on 2008-10-26
After attempting to fix my wireless problems with ndiswrapper, my system fails to boot up. The load bar goes to about 90% before freezing up. When I start up in recovery mode, I see the following error.
```

ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: e0e87be3
ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x103
BUG: soft lockup - CPU#0 stuck for 11s! [events/0:6]

```
The last line repeats constantly about once every 11 seconds until I turn off the computer. I'm assuming uninstalling ndiswrapper would solve my problem, but considering I can't boot into ubuntu I don't see how I can uninstall ndiswrapper. Any ideas?

I'll probably end up backing up and doing a clean install when Intrepid Ibex is released, but I would like to resolve this problem first.

---

### Post by agathian on 2008-10-26
I am guessing you should be able to disable/uninstall ndiswrapper in the single user mode..

googling showed this nice post with step by step instructions to get into single user mode..

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

---

### Post by Altay_H on 2008-10-26
> **agathian said:**
> I am guessing you should be able to disable/uninstall ndiswrapper in the single user mode..
I'm afraid not. I receive the error when running in recovery mode, which apparently run in single user mode. I went to append "single", but it was already there. Booting results in the error. Same with running the regular boot up in single user mode. It freezes up 90% of the way through.

---

### Post by Altay_H on 2008-10-27
Well, I don't know how I managed to configure ndiswrapper so that my system wouldn't even boot successfully, but I solved the problem. When booting in recovery mode I chose the low-level root option and entered the following command:
```

apt-get remove ndiswrapper-common

```
It's kind of scary that it didn't even ask me for a password. Anyway, with ndiswrapper removed I'm able to boot successfully again. Gotta love linux...:)

---

