---
title: "thermal module/kacpid issue"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by chromaticbum on 2006-11-02
When the thermal module comes after powernow_k8, I have issues with kacpid. Kacpid will begin to consume 100% of my processing power:

lsmod |grep thermal
thermal                16524  0
processor              29736  2 powernow_k8,thermal

If I

sudo rmmod thermal
sudo modprobe thermal

And then

lsmod |grep thermal
thermal                16524  0
processor              29736  2 thermal,powernow_k8

thermal appears before powernow_k8, and kacpid will not act up.

Is there anyway using configuration files to automatically have thermal load after powernow_k8?

Thank you,
Hollin Wilkins

---

