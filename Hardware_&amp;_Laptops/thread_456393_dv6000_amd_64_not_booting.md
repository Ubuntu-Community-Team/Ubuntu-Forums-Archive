---
title: "dv6000 amd 64 not booting"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by taintedclarity on 2007-05-27
Hello, i've new to ubuntu and looking for a change from SUSE. I've recently installed the i386 version of Xubuntu 7.04 on my hp dv6000 and it froze during installation. After following the instructions on the ubuntu wiki and added NOAPIC NOAPCI NOIRQPOLL NOSMP to the boot line, it starts and I am able to install it. However, after rebooting the system, I get a black screen

---

### Post by jcaveman on 2007-05-30
try editing the boot line for your kernel during start up and adding NOAPIC NOAPCI NOIRQPOLL NOSMP  to the end of the kernel line

---

### Post by nbayiha on 2007-06-04
Can you be more explicit? When do you have to a black? after ther  place where you are suppose to choose you OS or before?
Because if the problem is after, that mean's that you should try to edit the line where is (Ubuntu....) click "e" after that you'll have 4 news lines, just edit the first one adding "noapic nolapic" a the end and after that click 'b"

---

### Post by jcaveman on 2007-06-07
At the boot up screen hit F6 and add NOAPIC NOAPCI NOIRQPOLL NOSMP  to the end of the line and hit enter

---

