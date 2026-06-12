---
title: "Can't get HP dv6000 to boot - Gutsy"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by hun7er on 2007-10-22
Before I say anything, I feel like this problem should be solved the same way I solved it under Feisty, but it isn't working.

I'm running an HP dv6449, with a 2GB AMD processor and the like. It refuses to boot off of the Gutsy live CD. It will go through the whole process, but after saying that it is going to start the Gnome Display Manager, it hangs at a black screen. It seems like its the same problem I had with Feisty, which I solved by booting with a whole mess of command line options: noacpi, noacip, nolacip, noirqpoll, nosmp. Under Feisty it worked. Under Gutsy it didn't.

My question is simple: Am I missing something? Did they change something drastically enough that I'm just out of the loop? If so, what can I do to fix it?

Any help at all would be appreciated. Thanks.

---

### Post by Ayuthia on 2007-10-22
Did you mean noapic nolapic instead of noacip nolacip?

---

### Post by hun7er on 2007-10-22
Boy... That would do it, wouldn't it...

I feel stupid now...

---

### Post by Barracade on 2007-10-25
just incase i had to type this

noapic irqpoll noirqdebug


then mine booted fine

Barracade

---

