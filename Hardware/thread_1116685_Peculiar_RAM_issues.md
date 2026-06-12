---
title: "Peculiar RAM issues"
date: 2009-04-05
forum: Hardware
---

### Post by GhentK on 2009-04-05
Hi all,

My brother and I bought two identical Eee 1000s just before Christmas (and both installed the Eeebuntu "distro"/remix on them). He subsequently bought a 2 GB stick of RAM to replace the 1 GB stick in his. The new stick passes memtest with no errors on both his and my Eee, so it should all be good. It's not.

While his Eee is booting, it will freeze up about 30 seconds into the boot (while there is no GUI). When I put the stick in my computer, it will sometimes freeze up completely after I've signed in, and sometimes – like now – it works flawlessly. :???:

I have absolutely *no* idea what's wrong. I hope that some of you might have a clue. :-)

---

### Post by GhentK on 2009-04-09
Bump. Any clues at all?

---

### Post by coffeecat on 2009-04-09
> **GhentK said:**
> The new stick passes memtest with no errors on both his and my Eee, so it should all be good. It's not.

How long did you run memtest for? One successful cycle is not enough. Sometimes you have to run memtest for 24 hours or even days for a fault to show up.

Your two EeePCs both freeze with the 2GB stick. Or sometimes it works. Intermittent and unpredictable freezes are typical of bad RAM - hence having to run memtest for a very long time. That stick is faulty. See if you can get it replaced.

---

### Post by GhentK on 2009-04-12
> **coffeecat said:**
> How long did you run memtest for? One successful cycle is not enough. Sometimes you have to run memtest for 24 hours or even days for a fault to show up.

Your two EeePCs both freeze with the 2GB stick. Or sometimes it works. Intermittent and unpredictable freezes are typical of bad RAM - hence having to run memtest for a very long time. That stick is faulty. See if you can get it replaced.

I didn't know that you had to pass it several times to bee completely sure, but I guess it doesn't test every subtest on the entire stick, and the fault therefore only shows up when something is written to a faulty block (or whatever the correct term is).

I'll be able to RMA it. Thanks a lot for the help; I'll leave my Eee running memtest over night, then.

... The error log will be kept between passes, so that after, say, ten cycles, errors from all ten show in the list, right?

---

