---
title: "how to auto upgrade all packages each week"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by monkeyking on 2009-06-27
Hi,

I've been trying to setup a cron script to
[PHP]
apt-get upgrade -y
[/PHP]

But I can't get it to work,
has anyone tried similar stuff?

---

### Post by sp0nge on 2009-06-27
I have this in place on a couple machines to update via cron. The thing I'm noticing right off the bat is the lack of sudo, which may be an issue. What exactly are the errors you encounter?

---

### Post by monkeyking on 2009-06-27
thanks for your reply,

how does your script behave with packages that ask something like

"Do you which to install the package mainters version of ...."

---

