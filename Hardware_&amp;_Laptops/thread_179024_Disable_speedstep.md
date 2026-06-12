---
title: "Disable speedstep"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by olsonar on 2006-05-18
I'd like to know if there is an easy way to disable speedstep. I use VMWare, and when the processor is scaled down, the speed of the virtual machine is awful. I have an HP pavilion dv4000 laptop with a pentium M 1.7 ghz CPU.

---

### Post by 23meg on 2006-05-19
Try ```
sudo killall powernowd
```

---

### Post by patrickfromspain on 2006-05-19
try:

sudo apt-get install emifreq-applet

It's an applet that lets you control the speedstep, so when you use vmware, you can set it to performance

---

