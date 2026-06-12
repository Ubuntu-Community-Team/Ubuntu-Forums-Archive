---
title: "NIC Hardware level interface driver."
date: 2013-06-21
forum: Hardware
---

### Post by C G C on 2013-06-21
I have searched around and have yet to find anything about the topic.  Is there anything out there to directly control the nic card and send out data based on a program. I am trying to simulate ARINC 664 network data to test other devices.

---

### Post by TheFu on 2013-06-21
Direct control over a NIC is performed by the driver. The source for most NIC drivers is available, so you can modify it any way you need.  Knowing the correct question to ask can be hard when learning a new skill. We've all been there.

Doing this is a kernal-hacking 101 exercise.  I've modified a driver to swap word-A for word-B at the network level in any packets that were transmitted AND/OR received.  It was stable enough that I forgot about it until a few months later when I was dealing with a company named in "word-A" and it was always replaced by "word-B" in all emails in and out. I was embarrassed. Anyway, it was the first kernel hacking that I ever did.  The kernel is different now - should be easier to hack a network card driver.  If the exact driver isn't available, perhaps another driver from the same family can be used to start out?

This article might be helpful - [http://www.ibm.com/developerworks/linux/tutorials/l-kernelhack2/section4.html](http://www.ibm.com/developerworks/linux/tutorials/l-kernelhack2/section4.html)

---

### Post by C G C on 2013-06-21
Thanks for the help you were right I was searching for the information the wrong way, I was able to find the source of a driver.

---

