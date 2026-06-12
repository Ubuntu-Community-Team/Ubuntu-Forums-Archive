---
title: "Toshiba L300D 10A &quot;lid&quot; + standby probleb"
date: 2008-10-31
forum: Hardware
---

### Post by blagojkk on 2008-10-31
I have this model, and everything is working just fine on any Ubuntu distro, except that when I close the "lid" of the laptop the machine does not go to standby. 

I configure in the "power options" that when I close the lid I want to go to "standby" but nothing happens. I have noticed that the default option in the "power option" menu under the "what I want to do when the lid is closed" is "black screen" which actually works, so when I close the lid of the laptop the screen becomes black. Actually no mather which option I choose "standby", "hibernete" etc... nothing happens, everytime the default option "black screen" is executed. How to fix this, the only thin that stops me to use Ubuntu is this "lid" "standby" problem.

thanks in advance.

---

### Post by tw33 on 2009-02-20
Did you manage to get suspend and hibernate working on this laptop?
I have the L300D-11L and it refuses to do either. Does it work when you suspend/hibernate manually?

---

### Post by blagojkk on 2009-02-20
No, unfortunately not. But I found that it is a kernel problem. All the kernels older that 2.6.26, including 2.6.26 ACPI is working without a problem, all the kernels that are newer than 2.6.26 have this problem. Currently I'm using PCLOS 2009 TR6 and everything is working excellent, out of the box.

---

