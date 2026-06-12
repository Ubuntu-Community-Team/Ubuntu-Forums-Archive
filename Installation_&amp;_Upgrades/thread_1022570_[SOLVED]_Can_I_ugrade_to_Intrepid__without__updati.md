---
title: "[SOLVED] Can I ugrade to Intrepid _without_ updating Hardy first ?"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-12-26
Have a 64-bit Ubuntu with Hardy, and no updates for about 3 months or more.

Would like to upgrade it to Intrepid, and have downloaded ubuntu-8.10-alternate-amd64.iso , which I understand will contain 'most' of the .debs required for an upgrade to Intrepid.

Do I have to bring Hardy up to date first ?

Oygle

---

### Post by cariboo on 2008-12-27
You need to upgrade your version fully before considering an update, and then you can't skip versions when updating to a newer version. If you've got the alternate CD I would suggest doing a clean installation after backing up your important data.

Jim

---

### Post by oygle on 2008-12-27
> **cariboo907 said:**
> You need to upgrade your version fully before considering an update, and then you can't skip versions when updating to a newer version.

Isn't a Hardy ==> Intrepid called an upgrade ??  (i.e. not an update)

To me, an update is applied to a version, for example, every few days, there are several updates to do/apply ?

I realise these are just words, but I need to understand the terminology first, please

> **cariboo907 said:**
> 
If you've got the alternate CD I would suggest doing a clean installation after backing up your important data.


To do a fresh install, don't I need the file 'ubuntu-8.10-desktop-amd64.iso' though, not the alternate ?

Oygle

---

### Post by shafi on 2008-12-27
> **oygle said:**
> Isn't a Hardy ==> Intrepid called an upgrade ??  (i.e. not an update)


Yes , It is,
to call an upgrade go to System -> Administration -> Update Manager

or run the following command in terminal:
[PHP]
gksu "update-manager -c"
[/PHP]

I also recommend to do a clean installation via CD.
this is the link, only select the 64 bit version if you need.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Partyboi2 on 2008-12-27
> 
Isn't a Hardy ==> Intrepid called an upgrade ??  (i.e. not an update)

To me, an update is applied to a version, for example, every few days, there are several updates to do/apply ?

I realise these are just words, but I need to understand the terminology first, please
Moving from hardy to intrepid is a upgrade.
> 
To do a fresh install, don't I need the file 'ubuntu-8.10-desktop-amd64.iso' though, not the alternate ? No you don't, you can use the alternate cd to upgrade a current install of ubuntu to the next release or you can use it to do a fresh install.

---

### Post by oygle on 2008-12-27
> **Partyboi2 said:**
> No you don't, you can use the alternate cd to upgrade a current install of ubuntu to the next release or you can use it to do a fresh install.

Okay thanks. Would I need to apply all the Hardy updates, prior to using the alternate CD to upgrade to Intrepid ?

Oygle

---

### Post by Partyboi2 on 2008-12-27
> **oygle said:**
> Okay thanks. Would I need to apply all the Hardy updates, prior to using the alternate CD to upgrade to Intrepid ?

Oygle
Yes it is advised to be current with all the updates before doing a upgrade to Intrepid.

---

