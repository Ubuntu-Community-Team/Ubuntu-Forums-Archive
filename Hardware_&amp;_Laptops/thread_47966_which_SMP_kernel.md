---
title: "which SMP kernel?"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by viniosity on 2005-07-10
I have a dual opteron (AMD 64) server and I just noticed I'm only using one processor.  I was going to use apt-get to install the SMP kernel but noticed that there are two available:

```

linux-image-2.6.10-5-amd64-k8-smp - Linux kernel image for version 2.6.10 on AMD K8 SMP.

linux-amd64-k8-smp - Complete Linux kernel on AMD K8 SMP.

```

which one should I use?  Currently I'm using the stock kernel that came with Hoary AMD64.  My preference is for the 2.6 kernel which is why I'm leaning towards the first listing above.

thanks..

---

### Post by Leif on 2005-07-10
linux-amd64-k8-smp. this will install the other one, and whatever else is needed.

---

### Post by WMCoolmon on 2005-07-10
linux-image

Edit: Will linux-amd64-k8 install 2.6.10-5? I've saved a linux-image to a disk, copied it to another computer, and installed it there with no (additional) problems.

---

### Post by Leif on 2005-07-10
linux-amd64-k8-smp is a meta-package which will always be tied to the latest version. So, for example, when 2.6.11 becomes the default, linux-image-2.6.10-5-amd64-k8-smp wouldn't upgrade to this automatically, while linux-amd64-k8-smp would.

There's nothing wrong with using the image, but the other way is easier.

---

### Post by viniosity on 2005-07-10
Awesome -- thanks very much for the tip.. I am now actually using both processors!

---

