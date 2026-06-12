---
title: "Ubuntu not using 100% of processor"
date: 2008-06-14
forum: Hardware
---

### Post by Forty-two on 2008-06-14
I'm trying to run a c program that generates matrices for a math problem. I have a duel core processor and one of them maxes out but the other stays at about 25-30%. Is there a way to get it to use both processors completely?

Im running it off of the terminal and have attached a picture of the system monitor during the process if it helps.

Thanks

---

### Post by thideras on 2008-06-14
It may not be a multi-threaded program, which means it won't use two cores effectively.  If it is a multi-threaded program, then it is waiting on something else such as the other core or a system bus is being saturated.

---

### Post by sdennie on 2008-06-14
Unless you are using a multi-threaded algorithm, you can only use a single CPU core.  However, many matrix algorithms lend themselves well to multi-threading so you might be able to find the same algorithm written with parallelism in mind or, it's possible that the package you are using already supports multi-threading and you just need to enable it.

---

