---
title: "Graphical Environment Bricked - No Storage Space"
date: 2022-10-10
forum: Hardware
---

### Post by hyp-r on 2022-10-10
Hey, I just got his issue last night and (pretty desperately) need some assistance. I had started my computer, waited for it to boot up, and then attempted to login. Upon this happening, it had been taking much more time than usual. After about 5 minutes, I knew something was up. I booted into my TTY and ran 'df -h ~'. 0 bytes of storage space left. I figured that was the issue. Apt autoclean, Apt clean, Rm -rf .cache, rm -rf /tmp/ systemd* all didn'nt free anything up. I can't login! Any help would be appreciated.

---

### Post by yancek on 2022-10-11
You might try going to /var/log and delete files there.

---

### Post by mIk3_08 on 2022-10-12
How about "apt autoremove", Did you already run this command? This will also take a space in your storage. Regards and cheers.

---

