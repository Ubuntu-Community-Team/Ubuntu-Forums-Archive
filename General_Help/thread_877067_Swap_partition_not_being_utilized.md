---
title: "Swap partition not being utilized?"
date: 2008-08-01
forum: General Help
---

### Post by cchung85 on 2008-08-01
Hey guys,

I've read a lot of the posts on here and have read the FAQ section but I still don't quite understand some of this stuff.
([https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq))

What exactly does changing the value for "swappiness" do?
Also,
Awhile ago I asked people what my swap size should be for a 4 Gig install.
I use the suspend function quite often (I don't know the difference between hibernate and suspend...) and someone told me to try a 1 gig swap partition. When I was using my computer I noticed the swap partition was almost never accessed. Does the swappiness instruct linux to utilize that swap partition more frequently?

If only 3 Gigs of ram is recognize should I make my swap size 6 gigs?

I know I'm hitting the community with a lot of questions but it seems like all the other threads have some twist to it that doesn't answer these questions.

Any input would be greatly appreciated, thanks :)

---

### Post by knightcoder on 2008-08-01
What I believe is that when you hibernate your computer, your RAM contents are dumped in the swap partition so that the exact same desktop can be reproduced when you get your computer back up.

So, the swap partition has to be atleast the size of your RAM..

---

### Post by cchung85 on 2008-08-01
But if I don't use hibernate, just suspend would that work as well?

---

### Post by knightcoder on 2008-08-01
Suspend and Hibernate are two different things.

Suspend reduces the power consumption of your computer by cutting power to hardware components that you are not using. Suspend can cut power to peripheral devices, your monitor, even your hard drive, but maintains power to your computer's memory so you don't lose your work.

Hibernate completely shuts down your computer and copies the RAM contents to the swap space(on the hard drive) before shut down. When the computer starts up again, it loads the RAM from the swap space and you have your session back.

---

### Post by cchung85 on 2008-08-01
> **knightcoder said:**
> Suspend and Hibernate are two different things.

Suspend reduces the power consumption of your computer by cutting power to hardware components that you are not using. Suspend can cut power to peripheral devices, your monitor, even your hard drive, but maintains power to your computer's memory so you don't lose your work.

Hibernate completely shuts down your computer and copies the RAM contents to the swap space(on the hard drive) before shut down. When the computer starts up again, it loads the RAM from the swap space and you have your session back.

Thanks knight, but I still don't understand what swappiness does exactly..

---

### Post by y@w on 2008-08-01
Swappiness just determines how aggressive the kernel is in swapping memory out to disk. The higher the number the more aggressive. In general, the more memory you swap out, the slower your machine will run since disk access is much slower than RAM access. The fact that your swap isn't needed is actually a good thing. It means you have enough RAM for what you're doing.


[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by cchung85 on 2008-08-02
Thanks guys,
Would it be helpful then to keep the setting so that IF swapping is needed, it'll still be there that way it's not eating up the ram the whole time?

---

