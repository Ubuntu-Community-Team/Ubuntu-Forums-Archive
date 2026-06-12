---
title: "How to disable autoloading certain kernel modules"
date: 2008-04-24
forum: Hardware
---

### Post by wokick on 2008-04-24
For example, I don't want the kernel to automatically load ipw2100 module. What should I do? 

Thanks!

---

### Post by djselbeck on 2008-04-24
Hello,

you should add "blacklist ipw2100" to the /etc/modprobe.d/blacklist file.

DJSelbeck

---

### Post by besneatte on 2011-02-09
I know this is an old thread, but is it possible to do this on a per kernel basis?

For example, I would like processor frequency scaling enabled on my standard kernel, but I would like it to be disabled for my realtime kernel.

Is this possible?

---

### Post by sisco311 on 2011-02-09
> **besneatte said:**
> I know this is an old thread, but is it possible to do this on a per kernel basis?

For example, I would like processor frequency scaling enabled on my standard kernel, but I would like it to be disabled for my realtime kernel.

Is this possible?

Please start a new thread.

---

### Post by cariboo on 2011-02-09
Closing a 3 year old thread.

---

### Post by overdrank on 2011-02-09
Agreed. :) Please start a new thread. Thread closed.

---

