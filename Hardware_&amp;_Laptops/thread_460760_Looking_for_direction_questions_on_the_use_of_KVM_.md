---
title: "Looking for direction: questions on the use of KVM and VT hardware"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by explainer on 2007-06-01
I am not sure I am in the right forum, but here goes.  If there is a more appropriate forum, please point me to it.

I need some help in configuring KVM as a Virtual Machine Manager.  I have Feisty amd64 installed on a dual-core 64 bit AMD processor.  As I understand it, the Feisty kernel has VT hooks built into it.  All that needs to be done to enable KVM is to install the package.  That is what I get from the package documentation.  When I run KVM, I get the following:

kvm 
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

Sure enough /dev/kvm does not exist.  How does this file or directory get created?

---

