---
title: "Dell XPS m1530 HDD Health Concerns"
date: 2008-07-10
forum: Hardware
---

### Post by Redscare on 2008-07-10
I have just recently got a new Dell XPS m1530 laptop, and am very impressed. I have installed Ubuntu through wubi and it works fine, after a few tweaks. The only issue that I am worried about is Ubuntu's impact on the hard drive. I need this laptop to last, and the last one i got had its hard drive fried by Ubuntu. I am wondering if there is a way to prevent this from happening, and if this issue is applicable to this particular laptop. Until I am sure of the hard drive's safety I think Vista is the only option. 
Thank you in advance.

---

### Post by sdennie on 2008-07-10
It's fairly easy to check this.  See the sticky about Load_Cycle_Count at the top of this forum.

---

### Post by Redscare on 2008-07-10
If I do apply the unofficial fix, does that alleviate all the damage that ubuntu may do to the hard drive? I need this machine to last more than 3 years.

---

### Post by sdennie on 2008-07-10
I would honestly recommend using Ubuntu for a month and then check the Load_Cycle_Count.  If you are getting less than around 15,000 per month under normal usage, Load_Cycle_Count problems shouldn't become an issue for at least 3 years and you shouldn't need to apply any fixes.

---

### Post by Redscare on 2008-07-10
What will happen in 3 years?
Also, what disadvantages apart from decreased impact protection do the fixes carry?

Thank you very much for the responses.

---

### Post by sdennie on 2008-07-10
> **Redscare said:**
> What will happen in 3 years?
Also, what disadvantages apart from decreased impact protection do the fixes carry?

Thank you very much for the responses.

Well, at 15000 Load_Cycle_Counts per month, after about 3 years (a little more than 3 years actually), the chance that excessive Load_Cycle_Counts could kill your drive will increase.  However, if this is something you are concerned about, it's easy enough to just check the Load_Cycle_Count once a month and, when you feel it's getting too high, then completely turn them off with the fixes.

The only other advantage that the fixes carry is that it will remove (or reduce) the annoying click that the Load_Cycle_Counts produce.

---

### Post by Redscare on 2008-07-10
Thanks again, great response, i was actually asking what *disadvantage* the fix carries? so, why would i not apply it?

Thank you very much.

---

### Post by sdennie on 2008-07-10
Other than the decreased impact protection (which is barely a disadvantage if the machine is doing Load_Cycle_Counts constantly) I can't think of any other disadvantage.

---

### Post by Redscare on 2008-07-10
Will it greatly affect temperature? To a dangerous point?

---

### Post by sdennie on 2008-07-10
Oh...  Temperature.  I had forgotten about that.  It may make the disk run a bit hotter.  You can also keep an eye on that with:

```

sudo smartctl --all /dev/sda | grep Temp

```

Or, reducing disk activity could help with both the temperature and Load_Cycle_Count: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).

But, as I said before, I would give the machine a month using Ubuntu and then check how the disk looks.  In my experience, it's best not to mess with things until you are sure they are a problem.

---

### Post by Redscare on 2008-07-12
I'd just like to say that I ended up applying the fix; the Load_Cycle_Count increased approximately every 9.3 seconds, which, if one were to calculate it, is far too much.

---

### Post by matt$2 on 2008-07-12
Is that an  a b comparison with Windows?

---

### Post by Redscare on 2008-07-12
Im not exactly sure what an a b comparison is, but I know for a fact that windows does not increase the load_cycle_count due to constant disk access. Hard drives are also designed with windows compatibility in mind, so windows provides a naturally more stable environment.

---

