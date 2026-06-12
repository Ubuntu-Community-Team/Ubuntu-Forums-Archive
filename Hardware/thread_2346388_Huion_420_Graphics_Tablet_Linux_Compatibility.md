---
title: "Huion 420 Graphics Tablet Linux Compatibility"
date: 2016-12-14
forum: Hardware
---

### Post by outpact on 2016-12-14
What title says. I have the latest Ubuntu build and I'm wondering how to get my tablet working on Linux.

Thanks in advance.

---

### Post by coffeecat on 2016-12-14
*Thread moved to **Ubuntu Phone and Tablet**.*

I think you are being optimistic in hoping that you can install Ubuntu to almost any tablet, the way you can to a laptop or desktop machine. Here are some links for you. The first is for developers and for information only. Unless you understand everything there, I recommend you don't risk bricking your tablet by trying.

[https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/)

The next two are linked from that page. Supported and Reference devices:

[https://developer.ubuntu.com/en/phone/devices/devices/](https://developer.ubuntu.com/en/phone/devices/devices/)

Community ports:

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

You'll see that most of the devices in the latter are represented by abandoned ports.

---

### Post by outpact on 2016-12-15
> **coffeecat said:**
> *Thread moved to **Ubuntu Phone and Tablet**.*

I think you are being optimistic in hoping that you can install Ubuntu to almost any tablet, the way you can to a laptop or desktop machine. Here are some links for you. The first is for developers and for information only. Unless you understand everything there, I recommend you don't risk bricking your tablet by trying.

[https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/](https://developer.ubuntu.com/en/phone/devices/installing-ubuntu-for-devices/)

The next two are linked from that page. Supported and Reference devices:

[https://developer.ubuntu.com/en/phone/devices/devices/](https://developer.ubuntu.com/en/phone/devices/devices/)

Community ports:

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

You'll see that most of the devices in the latter are represented by abandoned ports.

Think you got me wrong, I'm talking about Graphic Tablets, ones you control your mouse with.

---

### Post by coffeecat on 2016-12-15
Indeed you are - apologies for the misunderstanding. I've amended the thread title to make it explicit and so that others don't make the same mistake.

Perhaps you could clarify what you mean by latest Ubuntu build. Which release and which kernel? You can find kernel details with this terminal command:

```
uname -rv
```

According to [this webpage](https://codeyarns.com/2015/05/11/how-to-use-huion-420-with-ubuntu/), the driver for your tablet is included if your kernel is v3.17 or later. If you are using a later kernel, what doesn't work?

---

### Post by outpact on 2016-12-16
> **coffeecat said:**
> Indeed you are - apologies for the misunderstanding. I've amended the thread title to make it explicit and so that others don't make the same mistake.

Perhaps you could clarify what you mean by latest Ubuntu build. Which release and which kernel? You can find kernel details with this terminal command:

```
uname -rv
```

According to [this webpage]("https://codeyarns.com/2015/05/11/how-to-use-huion-420-with-ubuntu/"), the driver for your tablet is included if your kernel is v3.17 or later. If you are using a later kernel, what doesn't work?

I'm on Ubuntu 16.04 I believe. How do I make sure I have downloaded a kernel or to see its up to date?

EDIT: What you asked me to find came up with this
4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016

---

### Post by coffeecat on 2016-12-16
> **outpact said:**
> 
EDIT: What you asked me to find came up with this
4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016

According to the link I posted, the driver should be included in that kernel and the tablet should work correctly if you plug it in. I have to add that I have no experience of that make of tablet, and the link is one I found in an internet search, but I would be inclined to believe it, since similar information appears elsewhere. 

Does the tablet work at all?

---

