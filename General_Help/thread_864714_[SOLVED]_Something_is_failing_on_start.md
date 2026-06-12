---
title: "[SOLVED] Something is failing on start"
date: 2008-07-19
forum: General Help
---

### Post by jamesdcarroll on 2008-07-19
I've been installing some things. When I rebooted the splash screen came up and the progress bar was moving nicely. Then about 5/6 of the way it stopped.  The screen went to text mode and at the top scrolling out of view were some lines with [....] on them the last with [COLOR="Red"][fail][/COLOR] to the far right; the name of the process had already scrolled off. It then continued and seems to be fine.

How can I find out what failed?  I installed oralce xe in particular and I did tell it to start on boot,but I don't know if that the problem since it scrolled so fast.

Thanks!

---

### Post by jamesdcarroll on 2008-07-19
Well, I had to reboot and this time it scrolled slowly enough for me to catch what was failing:

"Binding to YP server"

I have a feeling that this is a result of a failed/botched attempt to get Oracle 10g Enterprise installed. I was hoping I could fudge it. I was wrong 

:( 

So now the question I have is... how do I tell back that out and tell it not to try to bind?

Thanks,

---

### Post by jamesdcarroll on 2008-07-20
> **jamesdcarroll said:**
> Well, I had to reboot and this time it scrolled slowly enough for me to catch what was failing:

"Binding to YP server"

I have a feeling that this is a result of a failed/botched attempt to get Oracle 10g Enterprise installed. I was hoping I could fudge it. I was wrong 

:( 

So now the question I have is... how do I tell back that out and tell it not to try to bind?

Thanks,

I went into Services and disabled the 'Account information resolver (nis)' service and its fine now.

WHEW!

:)

---

