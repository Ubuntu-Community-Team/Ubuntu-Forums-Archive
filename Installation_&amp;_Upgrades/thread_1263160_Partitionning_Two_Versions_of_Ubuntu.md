---
title: "Partitionning Two Versions of Ubuntu"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Prosis on 2009-09-10
I already have Intrepid that I have to keep for work (don't ask :P)

But I want to use Jaunty for my personal use.  So I'm setting up a dual-boot for this.

I have 40 gb to install. I was wondering, size wise, what would be ideal for / ? 

Also, can I share my /tmp with my Ubuntu Intrepid installation?

Finally, I have 4gb of Ram. Do I really need to make my swap 8gb? I read that it has to be twice the amount of ram?

Thanks :)

---

### Post by -kg- on 2009-09-10
> I have 40 gb to install. I was wondering, size wise, what would be ideal for / ?

Depends on what other partitions you wish to include.  I have just over 9 GB for / and am using around 4 GB on my laptop.  Of course, I don't use this laptop for very much.  On my desktop I have around 15 GB and use around 9 GB.

It all depends on what you want to do with the computer.  If all you're going to use it for is surfing the net, reading emails and viewing videos and pictures, you won't need as much.  The other end of the spectrum would be video editing or CAD-type activities, in which case you would need more.

> Also, can I share my /tmp with my Ubuntu Intrepid installation?

I would think so.  All you would need to do is mount the directory and deal with the ownership and permissions.  I'm not terribly sure about this aspect.  If it were too much trouble, I personally would end up just using the /tmp created in my /home folder (or where ever it's put).  40 GB of space is large enough for just about anything except for exceptional requirements.

> Finally, I have 4gb of Ram. Do I really need to make my swap 8gb? I read that it has to be twice the amount of ram?

While it's nice to have that much swap space (if you can afford it), it's not really necessary except under the aforementioned exceptional circumstances.  I'm assuming you are talking about a laptop.  The only reason you might need some amount of Swap is if you use Hibernate.

When you hibernate, you save an image of what is loaded in RAM at the time.  In this case, you only really need around 1 1/2 X RAM.  2 X is a bit of overkill, unless you do RAM intensive operations with some of your software or hardware; again, exceptional circumstances.

I run with 1 1/2 X RAM on both my machines, and I don't use hibernate.  I don't believe I have *ever* used any of my swap space.  If you don't need to use hibernate, you can probably get away with 1 X, or even less.  Experiment with it and see what you can get away with before you run into trouble, then increase it from there a bit and expand whatever partition into the remaining free space.  I'd say the 40 GB is enough to do that much.

BTW, on my laptop, the total space used for my Ubuntu installation, with swap space (I have 2 GB RAM) is 26.4 GB, with 11.1 GB used in both / and /home.  Of course, I cheat and use other partitions on other drives for some storage, but the same could be done on your machine.

I say I cheat because I also have a 1 TB external drive hooked to it. :lolflag:

> I already have Intrepid that I have to keep for work (don't ask :P)

Oh man, were that we *all* (at least, all of us that like to run Linux) could work at a place such as yours!

=P~

---

### Post by running_rabbit07 on 2009-09-11
I use 10 Gig / and the rest for /home.

---

### Post by Prosis on 2009-09-11
> **-kg- said:**
> Oh man, were that we *all* (at least, all of us that like to run Linux) could work at a place such as yours!

lol yeah let's just say it sealed the deal as far as replacing Windows :)

Thanks for your response.  I'll try to lower my swap because yes it's a laptop but I never use hibernate.  So I guess I don't need that much.

For /tmp, I decided not to do it.  40 gb seems to be enough especially since I don't use /home for everything (I have another partition for all my files).

So thanks guys! :)

---

