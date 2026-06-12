---
title: "Boot dependency on keyboard controller and video adapter"
date: 2010-03-18
forum: Hardware
---

### Post by terovn on 2010-03-18
Hi everyone,

I am doing a project which involve booting Ubuntu in a virtualized environment without some legacy devices and this seem to be the best place to post this question. 

What I have discovered from my initial experiments is that Ubuntu 9.10 would not boot up without either a keyboard controller (kbc) or a video adapter. The kbc I am pretty certain but the video adapter I am not so sure about. So I have few questions, hopefully someone with more experience on Ubuntu booting process and point me in the right direction:

- Is it true that Ubuntu 9.10 needs those two devices to boot up, and if so why?
- How can I go about debugging Ubuntu booting process to see what really happened? Is there a way to debug Ubuntu via a COM port? And how to load debug symbols?

Of course, I can install those two devices back and Ubuntu would load, but my goal here is to find out why it wouldn't boot without them.

Thanks,

---

