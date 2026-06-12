---
title: "partially failed upgrade trouble"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Nastareger on 2009-01-22
Hi, I've recently upgraded from Hardy to Intrepid, but it only resulted in trouble and more trouble.

I suspect it has something to do with the following: it took me a lot of time to d/l all the files, as I currently reside in Suriname, where internet is slow and access to it is scarce, so I had to spread the entire download over nine or ten days, interrupting it each time. While downloading the last files in a cyber cafe, my timer ran out just seconds before completing the last file download. When I'd bought some new time and tried to rerun the updater to download that last file, it didn't give me the standard button that says something like 'upgrade to 8.10', so I pressed 'Install Updates' in the Update Manager. It took some time and afterwards, it seemed my system really was upgraded to Intrepid, but when I rebooted, the problems started. 

The regular boot line (I'm running a dual boot with winvista) with the splash screen fails anyhow. When the progressbar should appear, strange colors fill my screen, after which it goes dead black, but the pc's still on, so I have to do a hard shutdown by keeping the power button pressed. Not that healthy. When I ran it through recovery mode, I was able to login, but got to a blank screen. This seemed to be caused by compiz, so I removed that and now, it works. At least, through recovery mode. The regular one still kills.

That's one. My second problem has been around a little longer, also before the upgrade (actually, it was because of this that I decided to upgrade, hoping that it would be fixed afterwards) - namely sudden total system crashes. I think there are two types: one happens at random when I'm just using my laptop (Dell Inspiron 1525, btw), but it seems to only happen when I've got my wireless card switched on. The screen freezes, I cannot use my mouse, nothing responds, only two lights next to numlock flashing. Kernel panic?

Other one is similar, but this one happens occasionally when booting. Just before finishing the boot, it crashes. Through the 'verbose' mode, I found out this was in fact a kernel panic: not syncing, fatal exception in interrupt and something with wl_add_timer.

Hmm, my time's running out again, let's post this one quick before I lose it all! I hope you guys have some ideas, thanks in advance!

---

