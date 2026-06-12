---
title: "AMD Radeon 7700 not accelerating graphics - 14.04"
date: 2014-11-11
forum: Hardware
---

### Post by tns2 on 2014-11-11
Hello,


I have Ubuntu 14.04 on a Phenom X4 processor with Radeon 7700 graphics card. So i've installed the fglrx driver and it seems to be setup correctly:

*display: :0  screen: 0*
*OpenGL vendor string: Advanced Micro Devices, Inc.*
*OpenGL renderer string: AMD Radeon HD 7700 Series  *
[I]OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005

[/I]but what i notice is for example, playing a .flv file gets all 4 cores over 25% utilization (according to System Monitor tool). The system runs around 10 - 15 % cpu at idle. It seems as though graphics is still processed by CPU.

 How can i troubleshoot this?

---

### Post by Mark Phelps on 2014-11-11
> How can i troubleshoot this? 

I'm running fglrx drivers on an AMD R7 and checked the output of fglrxinfo -- and get nearly identical info as you.

There is nothing to troubleshoot -- the fglrx drivers are running.  IF they weren't, fglrxinfo would have failed.

---

### Post by tns2 on 2014-11-12
Hello Mark,


Thank you for  your reply, since then i've reinstalled the drivers - used ones directly from AMD. With just a web browser opened i have ~20% CPU utilization on all 4 cores, which for me is way to high.

The thing is, that i remember on 12.10 i had a similar issue and installing drivers (it took me some time to get them working) solved the high CPU util.

---

