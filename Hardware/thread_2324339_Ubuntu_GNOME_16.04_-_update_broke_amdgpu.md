---
title: "Ubuntu GNOME 16.04 - update broke amdgpu ?"
date: 2016-05-13
forum: Hardware
---

### Post by Baldwin on 2016-05-13
So, brand new laptop (Lenovo E460 w/ AMD R7 M360 & Intel Graphics), first thing I do is install Ubuntu Gnome 16.04.
Install works perfectly, everything seems great. (Windows 10 on another partition, no problems)

Next day, "updates are available" pops up, so I install them.
It tells me to restart to begin using updated software, so I do, but it hangs somewhere in the process (not sure if shutting down or booting again, wasn't watching). Kill power, turn on again, boots OK.

But, when I login via GUI, I just get a black screen and a crashed computer. Alt-SysRq-R,E,I,S,U,B usually makes it reboot.

I can get to a terminal with Ctrl-Alt-F1, so I run "apt-get update" and "apt-get upgrade", which installed some more updates but didn't fix the problem.

some error messages appeared in my terminal: (similar messages for ring test 1-8)

```
[220.536252] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: ring 2 test failed (scratch(0xC040)=0xCAFEDEAD)
```

and

```
[drm:sdma_v2_4_ring_test_ring [amdgpu]] *ERROR* amdgpu: ring 9 test failed (0xCAFEDEAD)
[drm:amdgpu_resume [amdgpu]] *ERROR* resume 5 failed -22 
[drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-22).
```



I eventually got it working again by installing the 4.4.10 kernel, but dmesg still shows error messages relating to amdgpu

```
[ 3980.252000] [drm] probing gen 2 caps for device 8086:9d18 = 9724043/e
[ 3980.258860] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[ 3980.512792] [drm:gfx_v8_0_hw_init [amdgpu]] *ERROR* amdgpu: cp failed to lock ring (-2).
[ 3980.512802] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 0 (-2).
[ 3980.512807] [drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-2).
[ 3980.512950] amdgpu 0000:03:00.0: couldn't schedule ib
```

Since these errors don't appear when using kernel 4.4.0-21 on a live USB, I'm pretty tempted to do a fresh install and just avoid updating (forever?)

Anyone got any recommendations?

I don't really need the super fast 3D GPU powers at the moment, I'm mainly using text editors and web browsers.

---
update
---

Well my success was shortlived, now 4.4.10 kernel is doing the same "black screen & stop responding" lark.

Fresh install it is.

Would love to know what the root cause is, and how to know when it'll be safe to update again...

---

### Post by vasa1 on 2016-05-13
Hi,

*Please post terminal output within code tags*. You can either use the button with "Wrap [CODE] tags around selected text" just above the text area or do the same manually.

If you don't see the code tags button, click on "Go Advanced" *below* the text area. I did a bit for you so you can see the difference.

---

