---
title: "Synaptics Touchpad Issues"
date: 2011-03-05
forum: Hardware
---

### Post by thisnamestoolong on 2011-03-05
Hi all -- I'm running the 64 bit version of Maverick on a Dell XPS 14 laptop. The touchpad is having some seriously annoying issues -- first of all, it randomly registers mouse clicks as I am moving it around. This is very annoying. Secondly, multitouch is having major problems. Whenever I touch two different places on the touchpad at the same time, the cursor flies wildly around the screen. This does not seem to be a HW issue, as it works fine in Windows7, as well as my Ubuntu, Fedora, and Arch VMs running through Virtualbox in said Windows install. Thoughts?

---

### Post by JC Cheloven on 2011-03-05
This should help:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

In a VM some services are obtained thru the host system. Thus sometimes something that works in the host is presented in an "understandable" way to the guest VM, and works even though it won't work in a vanilla guest install. It may be the case.

---

### Post by thisnamestoolong on 2011-03-06
That did it! Thanks! :guitar:

---

