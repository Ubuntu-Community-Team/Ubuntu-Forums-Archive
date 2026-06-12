---
title: "Severe Bluetooth trouble in 12.04 - solved in higher versions or hardware related?"
date: 2014-04-03
forum: Hardware
---

### Post by sgofferj on 2014-04-03
Hi,

one of the main reasons why I started tinkering with Ubuntu was that Ubuntu server has newer Kernels than Opensuse and I was hoping that the Bluetooth issues are fixed.

I run an Asterisk PBX with - among others - chan_mobile and 2 CSR USB BT dongles (0a12:0001). Some longer time ago, they started to act up - showing bad voice quality and freezing. The last status with Opensuse was that they would work for something between 1 and 4 days and then stop working with any command sent to the hciX ifs timing out. Additionally, they would start showing a ton of error messages in dmesg after a while (which is supposed to be fixed in >3.9) . Finally, the USB subsys would freeze, still serving connected devices but not reacting to un-/plugging of anything.

With Ubuntu (server 12.04) I don't have the error messages but they go bad much quicker and take the whole system with them. Until now, I only tried them in a virtual machine (virtual box and also in a KVM) and at least there, the whole system just freezes without further comment or message in the logs. Due to the frozen status, I unfortunately don't get to dmesg but until shortly before, they don't show up there with errors. Otherwise, the symptom is similar, commands would start to timeout. But instead of just killing the USB subsys, the whole system goes bad. And it goes bad pretty impressively... It's even not possible to shutdown or reset the VM when that happens!

So, my questions are:
- Does anybody know if this is a problem specific to the CSR devices?
- Are there infos if this is fixed in Ubuntu 13 / 14?

As I don't know what the problem is in detail and I don't have any error messages, Google didn't spit out anything usable.

-S

---

