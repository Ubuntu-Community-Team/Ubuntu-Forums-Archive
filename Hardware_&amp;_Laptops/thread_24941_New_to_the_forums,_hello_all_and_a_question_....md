---
title: "New to the forums, hello all and a question ..."
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by seamuso on 2005-04-08
Hello all!

As my signature says, my primary OS is a custom LFS build, just 32bit. Having upgraded my system recently to 64bit capability, I will eventually have to rebuild my system using a pre-exisitng 64bit system. I have used Ubuntu as a host for building (I actually have an install save on a hard drive so I have access to a known working 32bit host) and would like to use it for my 64bit host as well, that said ...

the NIC that I use is my onboard Marvell gigabit (sk98lin) which works fine with everything except the current 64 hoary release. Module is loading correctly, but the NIC never really starts.  

dmesg show these errors:

eth0: -- ERROR --
        Class:  internal Software error
        Nr:  0x19e
        Msg:  Vpd: Cannot read VPD keys

but that shouldn't be stopping the NIC .. it didn't in the LFS install after I upgraded, though the same messages were happening. Anyone else run into this same issue with a Marvell onboard not starting correctly?

---

### Post by seamuso on 2005-04-08
resolved .. downloaded new driver from sysconnect, built and installed .. problem is fixed

---

