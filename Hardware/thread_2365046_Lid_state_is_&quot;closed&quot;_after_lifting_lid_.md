---
title: "Lid state is &quot;closed&quot; after lifting lid to resume from suspend (DSDT patch needed)"
date: 2017-07-01
forum: Hardware
---

### Post by emptystorage on 2017-07-01
Hi Folks,

I'm hoping to get some help with this tricky problem:

Summary:

The problem occurs on an HP Pavilion dv5120us (XP era laptop). I've tested it on Lubuntu 16.04 and 12.04 with various kernels (vanilla and Ubuntu) and it has occurred in every case.

When the system is not configured to suspend on lid close, the lid state (/proc/acpi/button/lid/LID/state) is always accurate. However, when the system is configured to suspend on lid close, here is what happens:

I close the lid and the system suspends
I open the lid and the system resumes but the lid state reads "closed"
I close the lid and nothing happens (state remains "closed")
I open the lid and the state changes to "open"
Then I can repeat the cycle

Details:

This problem has been solved by other users by patching and overriding the DSDT. In this [blog post]("https://blog.twcloud.tech/2013/04/29/fixing-incorrect-lid-state/"), the fix is described in detail, but if I apply it to my DSDT, it causes iasl to report an error. I'd be happy to tinker around with it, but nowadays the only way to override the DSDT is to compile it into the kernel which takes over 5 hours on this machine. I'm hoping somebody with more knowledge can look at [my unmodified DSDT]("https://drive.google.com/open?id=0B1FM3dYlkU7YNjQ2UmFzUUxhdEk") (31.8 kb) and give me some guidance. 

Any help would be greatly appreciated. 

Eric

---

### Post by emptystorage on 2017-07-05
Turns out a DSDT patch was not needed. Here's the solution: [https://bugzilla.kernel.org/show_bug.cgi?id=196249](https://bugzilla.kernel.org/show_bug.cgi?id=196249)

---

