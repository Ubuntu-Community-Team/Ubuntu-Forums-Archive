---
title: "Using an older kernel version ?"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by tawlboy on 2007-09-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have been using Ubuntu 'Dapper' (6.06) for a while now and it works fine for me. Dapper uses kernel 2.6.15.

I would like to upgrade to 'Feisty' (7.04), because that packages for Dapper are outdated, but there seems to be a bug in the linux kernel with ACPI. I am using a ThinkPad R51e. See here for more details:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/107516)

I have tried following the instructions to get Feisty to work, but I still cannot get it to work correctly.

Is there a way that I could use an old kernel version, such as 2.6.15 ~ 2.6.18 on Feisty ? How do I install an older kernel ? I don't want to have to compile the kernel as that is quite complicated.

---

### Post by eggdeng on 2007-09-28
```
apt-cache showpkg linux-image
``` 
will show you the versions available.

I have never tried it but ```
man apt-get
```says
> A specific version of a package can be selected for installation
by  following the package name with an equals and the version of
the package to select. This will cause that version to be locat&#8208;
ed  and selected for install. Alternatively a specific distribu&#8208;
tion can be selected by following the package name with a  slash
and the version of the distribution or the Archive name (stable,
testing, unstable).
[COLOR="Red"]Both of the version selection mechanisms can downgrade packages
and must be used with care.[/COLOR]

---

