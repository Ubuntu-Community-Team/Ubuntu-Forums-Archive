---
title: "compiz unenabled with 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by frankwakeman on 2009-04-25
I imagine this is to do with the Intel driver problem somehow, but where Compiz worked with 8.10 for me, it no longer does.  I chose the 'normal' setting in appearances to be told effects can't be enabled.

I believe my chip is an intel 965.

I've seen that if you have performance problems with 9.04 you should put the old intel driver back, but I wondered if the problem was different, as in the notes it seems to be saying you'd judge the performance from how it deals with Compiz effects.

The procedure for getting the older driver seems quite long-winded anyway - why not just leave it in the repositary as it's a known problem so that we don't need to learn about pga keys or whatever they're called.

Very grateful to anyone who can give me idiot-proof instructions about this.  Thanks.

---

### Post by frankwakeman on 2009-04-25
I now know the 965 driver is 'blacklisted' and I've typed in a line of code I found to un-blacklist it.

I see that Compiz is quirky now, but it was quirky before with this Toshiba laptop, so I may put up with it, but I'd prefer it if someone can still give me the easy instructions for getting the old intel driver.

Thanks.

---

### Post by frankwakeman on 2009-04-25
Well, touch wood, but the EXA Greedy Migration entry about 9/10ths into the link here...

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

...seems to have solved everything, along with uncheckng the sync to vblank box in Compiz > General Options > Display Settings.

---

