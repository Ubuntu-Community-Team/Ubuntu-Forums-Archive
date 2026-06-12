---
title: "Running multiple computers together?"
date: 2012-04-09
forum: Hardware
---

### Post by DaimyoKirby on 2012-04-09
So I have this idea, and it makes sense in my head: Is there a way to hook multiple computers together and make them *combine*, per say, their computer power, to make a single computer run faster?

I did some searching, and people generally tended to say that this was mostly theoretical/too expensive/impractical, so I decided to be stubborn, and get some more verification, another newer opinion.

So can anyone tell me, is it possible to do this? To basically "funnel" power from multiple computers into a single computer, essentially pumping up its processing speed?

---

### Post by Penguinnerd on 2012-04-09
You're talking about a "computer cluster".

[https://en.wikipedia.org/wiki/Cluster_%28computing%29](https://en.wikipedia.org/wiki/Cluster_%28computing%29)

Not really for end users, and typically not something most people want to try "at home" anyway. But it is frequently done by businesses and such.

---

### Post by DaimyoKirby on 2012-04-09
Yes! That is in fact what I'm looking for!

When doing this, do all the computers need to be the same, and if so, to what extent?

---

### Post by ridetheteapot on 2012-04-10
In a beowulf cluster they should at least all be the same arch--- all x86 or all sparc or all ppc, etc. Not totally mandatory, but....

Anyways I'm guessing you have a couple old pcs that you want to turn into a cluster... Basically beowulfs are network connected so....

But if thats not specifically it, check this out:
its a bit old but its a cool reference [http://www.calvin.edu/~adams/research/microwulf/](http://www.calvin.edu/~adams/research/microwulf/)
Now that is a cool low cost envy machine ;)

---

### Post by DaimyoKirby on 2012-04-11
Oo, that's pretty interesting.  I'm gonna look through that, and weigh the pros and cons of both the microwulf and the beowulf, and decide.

Another question: do all the computers have to support 64-bit (since by the end I'll probably have more than 4GB of ram), or just the master operating system?

---

### Post by ridetheteapot on 2012-04-12
I guess you /could/ but its a more comlicated setup (sharing the binaries).

That microwulf setup is a beowulf cluster, it's just a neat (&cheap) setup. I gonna just guess here, but if your going cheap these days you'd probably want to utilized cheap gfx card crunching with opencl - so from scratch if you redid a setup from scratch like that, it would be a little different - I bet if you search through some hardcore bitcoin communities you'd probably find some good examples for mining.

---

