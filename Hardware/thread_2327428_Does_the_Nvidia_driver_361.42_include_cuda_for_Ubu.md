---
title: "Does the Nvidia driver 361.42 include cuda for Ubuntu 16.04?"
date: 2016-06-10
forum: Hardware
---

### Post by Karl_Hungus on 2016-06-10
I installed the Nvidia driver 361.42 (GTX970) from the normal native "drivers" with in System Settings,

My question is does this automatically include Cuda for Ubuntu 16.04?


Thanks in advance.

---

### Post by Linuxisfast on 2016-06-10
> **Karl_Hungus said:**
> I installed the Nvidia driver 361.42 (GTX970) from the normal native "drivers" with in System Settings,

My question is does this automatically include Cuda for Ubuntu 16.04?


Thanks in advance.

It includes necessary files to run CUDA but you have to install CUDA via apt or Software Center. Make sure to install nvidia-modprobe via apt to make CUDA and OpenCL work.

---

### Post by Karl_Hungus on 2016-06-13
Thanks mate!

---

### Post by oldrocker99 on 2016-06-13
If your problem is solved, please mark the thread as [SOLVED].

---

