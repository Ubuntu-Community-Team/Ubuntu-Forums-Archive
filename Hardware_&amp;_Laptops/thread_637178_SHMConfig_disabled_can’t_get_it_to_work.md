---
title: "SHMConfig disabled: can’t get it to work"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by henriquemaia on 2007-12-10
I'm trying to enable shared memory area to configure my laptop's touchpad. I have added the the option SHMConfig "True" to xorg.cong, but I can’t never get it to work. I have restarted, wrote "True" and "On"  and still nothing. Any ideas on how to solve this?

I’m running Gutsy 32bit on a Compal IFL90.

Thanks

---

### Post by henriquemaia on 2007-12-10
> **henriquemaia said:**
> I'm trying to enable shared memory area to configure my laptop's touchpad. I have added the the option SHMConfig "True" to xorg.cong, but I can’t never get it to work. I have restarted, wrote "True" and "On"  and still nothing. Any ideas on how to solve this?

I’m running Gutsy 32bit on a Compal IFL90.

Thanks

According to this page:
[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

[COLOR=DimGray] "**Gutsy:** the touchpad will work but some of the more advanced configuration capabilities will not work right out of the box because it seems the kernel misidentifies the device. See:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775)

**Hardy Heron forecast:** will work out of the box."[/COLOR]    

So I guess I just have to wait. In the meanwhile, I have to try develop special skills to control this erratic touchpad.

**solution**: buy a laptop mouse.

---

### Post by jeracravo on 2008-06-20
I'm having the same problem with 8.04...
Can't get SHMConfig to work.
Any ideas so far?

---

