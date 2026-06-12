---
title: "Mousepad not working on netbook"
date: 2010-12-20
forum: Hardware
---

### Post by tmilam on 2010-12-20
I have one of those $99 Sylvania netbooks running Ubuntu Netbook Remix. The touch pad will not work. An external mouse works great. How do I get the touch pad working?

The model is Sylvania SYNET583-PK.

---

### Post by PhantmKllr on 2010-12-20
Is it a Synaptics touchpad?

---

### Post by tmilam on 2010-12-21
I don't know. It isn't listed in 
```
xinput list
```

...just the external mouse. This problem is with 10.04. I'm going to try upgrading to 10.10 and see if the results are better.

---

### Post by tmilam on 2010-12-21
I've tried 10.10 and the track pad does not work on this version of Ubuntu either. Please help!

---

### Post by PhantmKllr on 2010-12-21
Install the "xserver-xorg-input-synaptics" package in "System -> Administration -> Synaptic Package Manager"

---

### Post by Penelope Antelope on 2012-05-14
> **tmilam said:**
> I have one of those $99 Sylvania netbooks running Ubuntu Netbook Remix. The touch pad will not work. An external mouse works great. How do I get the touch pad working?

The model is Sylvania SYNET583-PK.
Hold down Fn + F4

---

