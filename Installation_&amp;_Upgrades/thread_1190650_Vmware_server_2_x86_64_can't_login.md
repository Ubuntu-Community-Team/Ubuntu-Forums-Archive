---
title: "Vmware server 2 x86_64 can't login"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by karneevor on 2009-06-18
Hi there.

On three newly installed servers I can't login as root. It's just vanilla installations.

I've followed lots of howto's but my specific problem is never discussed.

My problem is NOT:
- an issue with pam_unix.so vs pam_unix2.so
- an issue with proxy or hosts.allow

My log when I fail to login:
==> /var/log/vmware/webAccess/proxy.log <==
[2009-06-18 10:29:52,994,http-8308-4<=>,RequestProcessor] Error processing action request /action/login : [NoClassDefFoundError] org/aspectj/runtime/internal/AroundClosure

I cannot find log entries related to my login failure.

Has anyone of you ever seen something like it? Does anyone have a clue or solution?

Thanks in advance. :-)

/Karneevor

---

