---
title: "LIRC-induced hard lockups"
date: 2013-12-09
forum: Hardware
---

### Post by DorianX on 2013-12-09
So I've been running mythbuntu 10.04 for some time. I don't really want to upgrade because it's my primary TV-runnin' box. It's been mostly great for years, but it's got this one issue that's driving me crazy. From time to time -- usually no more than once a month but each of the last four days, the system will come ot a complete and total halt. Doesn't respond to the magic sysrq key, no indication of a kernel panic, and nothing is in the logs when it comes back up. Never locks up when idle either, it's always while I'm interacting with it.

After years of this, I finally tracked down the proximate cause: I'm using a TiVo remote with a USB StreamZap IR receiver. I've seen a few references here and there on the internet to people having issues with similar setups, and upon closer inspection, the issue ALWAYS happens while I'm using the remote.

So, I'm pretty well resigned to this setup not being stable, but I'm not sure how to proceed from here -- none of the other references I can find to this kind of issue actually get as far as a solution. 

Does anyone know if this is something I can patch? Or is the issue that my streamzap is physically broken and I should get a new one? Or better yet, is there any IR received that will work with a TiVo remote but which someone can verify DOESN'T exhibit this issue? I'm utterly loathe to buy a random receiver to have it turn out that it's got the same issue. I'm running lirc 0.8.6, which isn't the latest  I know, but nothing later is officially supported, so I don't know if it'll make it better or worse.

So, anyone have any ideas?

---

