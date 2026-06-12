---
title: "Problem: services that require usernames (startup)"
date: 2008-07-31
forum: General Help
---

### Post by j3r3my86 on 2008-07-31
Hi

I've install the dansguardian GUI Parental Control found from the UC (ubuntu christian) edition. and Joined my system to an active directory domain.

I've also setup auto mount using pam mount

When I boot up, and for clamav to load, it needs to su into clamav username. PAM will then return asking for a password.

Subsequently by pressing [enter], pam mount will try to load the shares specified unsuccessfully.

Then. it will move on to start HAL but fail after about 3 mins of waiting followed by samba taking very long to load.

So my question is...

1) Is there anything i can configure to not allow services that required "su-ing" to be interfered by PAM and its modules

2) after disabling the clamav service from starting during boot-up, winbind service would not start properly. It would show [OK] but by doing wbinfo -p it shows that winbind is not up n running properly. I would need to restart the winbind service before I can login using a domain account


Is there anyone who have faced such problems or know what I can do to solve my problems ? I do not know if they are linked or just isolated problems but they are bugging me and forbidding me from putting a close to my project. 

Thx in advance

Regards
Jeremy

---

