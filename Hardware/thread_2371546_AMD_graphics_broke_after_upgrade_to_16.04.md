---
title: "AMD graphics broke after upgrade to 16.04"
date: 2017-09-15
forum: Hardware
---

### Post by graabein on 2017-09-15
I had it working perfectly with proprietary driver from AMD but since 16.04 upgrade it does not work.

[IMG]https://image.ibb.co/mynNr5/no_drivers.png[/IMG]

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X] [1002:683d]

I'm getting too old for looking for drivers and getting hardware to work. I thought AMD was preferable to Nvidia so that's why I bought it years ago...

**Update:**

I think this describes my problem: [https://askubuntu.com/questions/159586/how-to-install-radeon-open-source-driver](https://askubuntu.com/questions/159586/how-to-install-radeon-open-source-driver)


$ lspci -k | grep -EA2 'VGA|3D'                                                                           ~  
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
	Subsystem: ASUSTeK Computer Inc. Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
	Kernel modules: radeon

$ sudo apt-get install xserver-xorg-video-ati
xserver-xorg-video-ati is already the newest version (1:7.7.0-1).

---

### Post by QIII on 2017-09-15
Hello!

If you upgraded in place, the issue may be that you did not remove the driver before hand.  This would present a problem in that AMD has discontinued development on the fglrx driver, which will no longer work in 16.04 and beyond.

From that point forward, the driver installed by default will either be AMDGPU (if it supports your hardware) or the open source Radeon driver (if the AMDGPU driver does not support your hardware.)

There is nothing the open source community can do about the discontinuation of the proprietary fglrx driver, nor the hardware supported by the AMDGPU driver.  Be aware that development for the AMDGPU driver is ongoing and that AMD is working to get *some* older graphics adapters covered.  That will not include hardware that is not GCN (Graphics Core Next) capable.

AMD has a list of supported cards [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx").  Your card does not appear in that list.  I also wrote a blog article regarding this [here]("http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx").  My list includes cards that are GCN capable, but that does not mean that AMDGPU has been updated to include all of the cards on that list.  I suspect support is coming if your card is not currently supported.

So, the question is this:  Did you upgrade in place without first removing the fglrx driver?

Cheers!

---

### Post by graabein on 2017-09-15
Hi there!

I removed fglrx-core and restarted, voila!

When I did the upgrade to 16.04 (from 14.04 or whatever was the previous LTS) I did not consider any drivers, so I upgraded in place.

Anyhow it works now so I can go back to getting things done. Thanks for writing!

---

### Post by QIII on 2017-09-15
Let's see if that got you the default Radeon driver or AMDGPU (AMDGPU-Pro has to be installed from AMD):

Please post the results of  

```
lsmod | grep amdgpu
```

---

