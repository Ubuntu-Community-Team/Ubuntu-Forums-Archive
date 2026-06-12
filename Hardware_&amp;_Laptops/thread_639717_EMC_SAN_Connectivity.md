---
title: "EMC SAN Connectivity"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by kcnoodle on 2007-12-13
Has anyone had success connecting their Ubuntu installation to an EMC SAN?  EMC isn't currently offering Navisphere Agent support for Ubuntu / Debian, and I haven't had any luck even manually registering the server.  Just wondering if I'm missing a package, or if it's user error?  :)  Thanks!

---

### Post by bhursey on 2008-01-02
You know ubuntu is not supported by EMC for use on an EMC san?  So I would not recommend using this for production if you do get it working.

---

### Post by sillyVM on 2008-01-14
Hi, Just want to say this for the record, yes it does work ubuntu manually. However I am not be able to get it to install the navisphere driver and have it load balanced.

So it's a single connection without failover. I agree it is not recommended for production. So i would recommend RHEL for this job. As much as I hate RHEL, i would like to see ubuntu have some more vendor support in the future.

---

