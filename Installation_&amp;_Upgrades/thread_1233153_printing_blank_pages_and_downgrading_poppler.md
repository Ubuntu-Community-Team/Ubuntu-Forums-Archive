---
title: "printing blank pages and downgrading poppler"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by ilna on 2009-08-06
Hi!

At some moment my printer has started to print blank pages - even a test page from CUPS web admin. I have looked at apt log and have found the only reason I can guess  - three poppler-related packages were updated just at that moment.

To try previous poppler version I have tried to find a way to set these three packages as "bad" and, as a result, to force a downgrading to previous version. The truth is, I have not found a way for such "masking". The obvious reason is: I'm few days with (K)ubuntu only (in fact, 5 days).

Will anybody point me a direction to dig in?
Up to date Kubuntu Karmic is in use.

---

### Post by kylea on 2009-08-07
Getting the same result, all pages are blank from all sources even text documents




2.6.31-3-generic #19-Ubuntu SMP Tue Jul 14 16:07:02 UTC 2009 x86_64 GNU/Linux
------------------
Description:	Ubuntu karmic (development branch)
Release:	9.10

---

### Post by ilna on 2009-08-07
I have filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/409962](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/409962)

---

### Post by kylea on 2009-08-07
Yeap - saw that - tried to downgrade to an earlier version of HP drivers - it did not help.

I have an earlier un-updated Alpha 3 - two days old - its printing ok, so its a recent change in the last 2 days or so,

---

