---
title: "Backup battery?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Puppy fam on 2007-06-20
I want to know if anyone knows of a good backup power supply unit. I don't need one (and I don't know if I will buy one), but it is annoying that I have to shutdown my computer every time there is a thunderstorm. I found one, but it was only for Windows. I want one that gives me just enough time to save what I am doing and then shutdown the computer (this is not for a business with multiple computers. It is just a home desktop).

Does anyone know anything?

---

### Post by jgrabham on 2007-06-20
You can get it built into an extension lead/cord like this - [http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=242289&CatId=1416](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=242289&CatId=1416)

What country are you in?

And wether or not you use windows should be irrelivant.

---

### Post by Puppy fam on 2007-06-20
> **jgrabham said:**
> You can get it built into an extension lead/cord like this - [http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=242289&CatId=1416](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=242289&CatId=1416)

What country are you in?

And wether or not you use windows should be irrelivant.

I live in the U.S. so is there another one? :)

Also, the one I saw (I did not look that much) was one that had software that would save and shutdown programs/computer when the power would go off (this is not something I want or need.)

Thanks,
-Puppy fam

---

### Post by CrispyFried on 2007-06-20
APC makes good ones, Ive used them for years.

these here are inexpensive home units (they make mucho bigger ones):

[http://www.apc.com/products/family/index.cfm?id=21](http://www.apc.com/products/family/index.cfm?id=21)

the 550 will give you around 4-5 minutes of power based on a 300 watt draw.

---

### Post by Puppy fam on 2007-06-20
> **CrispyFried said:**
> APC makes good ones, Ive used them for years.

these here are inexpensive home units (they make mucho bigger ones):

[http://www.apc.com/products/family/index.cfm?id=21](http://www.apc.com/products/family/index.cfm?id=21)

the 550 will give you around 4-5 minutes of power based on a 300 watt draw.

Thanks! I think that is what I was looking for. :D

---

### Post by subject117 on 2008-03-12
I was about to make a new post asking the same question, but I found this thread which almost answers my question.

I also need a battery backup and the APC battery would work great, but I do need the software that notifies processes the machine is shutting down and shuts down properly.  How does that work?  Would the software APC provides work on Ubuntu?

And does anyone know how a java program would find out that the machine is shutting down in this situation?

-Jim

---

### Post by subject117 on 2008-03-12
Hmm, it seems in Java code I can make a shutdown hook so my application will know the JVM is shutting down.  That's great.  But it is still unclear to me how the battery tells Ubuntu and how Ubuntu tells the JVM.  Can anyone tell me?

---

### Post by subject117 on 2008-03-12
I think I found what I need:
[http://www.linux.com/feature/128099](http://www.linux.com/feature/128099)
There is opensource software that can communicate with the battery so the computer knows it is shutting down.  Then I guess it sends shutdown requests to the appropriate processes and lets them know.

If I am missing anything, let me know.

---

