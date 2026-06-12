---
title: "Broadband reconnect"
date: 2010-11-27
forum: Hardware
---

### Post by alaksandarjesus on 2010-11-27
Guys,

 I have a doubt..I configured my DSL Connection as every time i switch  on the system, the internet connection is switched automatically.

 Now as i use it in Laptop, i dont shutdown everytime and i just lock  it. So what happens is the internet connection is lost.. To get back the  internet connection, i need to restart again..Though it was not a tough  process, is there any other solution to workout.

The same happens when power goes off too.. 

I used Pon dsl-provider command, but the internet connection is not started.

is there any application like in windows i would give connect so it connects.

I hope i was clear


-- 
Endrum Anbudan
A.M.S.ALAKSANDAR JESUS GENE

---

### Post by Cheesehead on 2010-11-27
Since you are using pon, in /etc/ppp/options have you enabled the 'persist' option?

---

### Post by alaksandarjesus on 2010-11-30
Hi.

Thanks for the reply.

As i am new to linux, i am not sure of what u are asking about.. I just go to the terminal and type pon-dsl provider.

---

