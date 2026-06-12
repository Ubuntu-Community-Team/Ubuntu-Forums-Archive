---
title: "I don't think Ubuntu recognizes my laptop's fan."
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Ranfea on 2008-02-05
I'm running Gutsy on a Dell Inspiron E1405.
I'm pretty sure my fan hasn't turned on once since I installed Ubuntu a few months ago, despite having gotten worryingly hot.

What should I do?

---

### Post by solitaire on 2008-02-05
Can you see the fans? if you can try seeing if they can turn by using a toothpick or paperclip. they might just be stuck.

you could try the i8k prog in the distros.

After you have installed the i8k you might have to run 
```

you@pc:~$ sudo monprobe /proc/i8k/ 
you@pc:~$ cat /proc/i8k/

```
for i8kmon to see your fans and currrent temps

---

