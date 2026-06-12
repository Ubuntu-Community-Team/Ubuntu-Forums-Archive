---
title: "Almost constant HDD activity"
date: 2010-05-03
forum: Hardware
---

### Post by glaze on 2010-05-03
After a clean install of Kubuntu 10.04 my HDD is almost constantly doing stuff. **top** doesn't show anything suspicious. I also tried **iotop**, but it complained that I need to enable CONFIG_TASK_DELAY_ACCT in the kernel. Files in /var/log aren't growing unusually fast. I've disabled Nepomuk search and indexing.

---

### Post by tgalati4 on 2010-05-03
sudo apt-get install htop
htop

It could be indexing going on.  There are several commands that need indexes:

which which
apropos apropos
locate locate
which apropos
apropos which
locate which
locate apropos
apropos locate
which locate

I think I got them all.

---

