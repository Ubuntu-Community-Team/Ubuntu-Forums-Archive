---
title: "Suspend problm in kramic"
date: 2009-12-06
forum: Hardware
---

### Post by ali780 on 2009-12-06
Hello all

I have seen some threads about suspend problem in ubuntu 9.10, but I have not seen any solution for it. Does anybody know this problem finally have been solved?

Regards

---

### Post by aysiu on 2009-12-06
What's the problem for you, exactly?

That it doesn't suspend? That it doesn't resume from suspend? That it resumes from suspend for a second on battery power but then goes immediately back to suspend? That it randomly resumes from suspend even when the lid is closed?

And what hardware do you have? Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
lspci -vvnn
dmesg
```

---

### Post by ali780 on 2009-12-06
> **aysiu said:**
> What's the problem for you, exactly?

That it doesn't suspend? That it doesn't resume from suspend? That it resumes from suspend for a second on battery power but then goes immediately back to suspend? That it randomly resumes from suspend even when the lid is closed?

And what hardware do you have? Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
lspci -vvnn
dmesg
```

Actually I installed kramic and I had lots problem with suspend.
Because I installed it on my laptop so suspend was very important.
I tried a lot for fixing but no progress. after one month I returned to 9.04. At the moment I have 9.04 on my laptop.

I want to know if the problem has been fixed and the kramic can do suspend - resume by itself, I install kramic again.

---

### Post by aysiu on 2009-12-06
I never had problems with Karmic not being able to suspend and resume. That's why I asked exactly what your problem was and also the output of those two commands.

---

