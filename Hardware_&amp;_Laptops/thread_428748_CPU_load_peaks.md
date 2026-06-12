---
title: "CPU load peaks"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by dany_r50 on 2007-04-30
Hi everyone!

I have a Samsung R50 laptop with Ubuntu 6.10 installed on it. The thing is that after I start my system, withouth having initialize any application, the CPU is taking peaks of 90-100%, with a period of 6 seconds between them, over a constant value of 6% approximately. In graphical explanation: ....____/\_____/\_____/\______.....

Because of this the laptop fan is changing its speed continuosly and it's quite annoying. 
I have to say that sometimes I have to use Windows XP (it's installed on the laptop too) and I haven't that problem with it. I think it's not a matter of hardware but a problem of my Ubuntu.

Any help is welcome. Thank you in advance.

---

### Post by dany_r50 on 2007-05-01
The problem was the apt-index-watch process. It was running every 6 seconds and using 100% of the cpu. To solve de that problem I did:

sudo apt-get install --reinstall debtags

---

