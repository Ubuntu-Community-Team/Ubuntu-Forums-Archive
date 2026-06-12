---
title: "Empty battery?"
date: 2021-11-12
forum: Hardware
---

### Post by jet-bundle on 2021-11-12
I have a Dell XPS13 9300 with Lubuntu 20.04.3 installed. Occasionally the LXQt battery status indicator disappears, or else shows no charge left; in the latter case clicking to obtain the Battery Info window indicates that the battery is empty -- see attached image. (The battery isn't empty, as the charging cable could well be disconnected with the computer running on battery power. Rebooting usually restores a working battery status indicator).

This problem seems to be correlated with a failure to shut down correctly, reaching Plymouth but remaining there.

A similar laptop (XPS13 9360, also with Lubuntu 20.04.3) doesn't have this problem

I'd be grateful for advice on whether this problem can be resolved.

---

### Post by Autodave on 2021-11-13
I have had issues before with Dell's not reporting battery correctly, not charging past a certain percentage, etc.  A few thing to try:

Remove EVERY cable from laptop.  Remove battery.  Press and hold START button for about 15 seconds.  Wait 5 minutes and reinstall battery and charger ONLY.  Fire it up and see what happens.  IF that seems to correct the issue, then hook up other cables.  Note: If you are using a powered USB hub, that can cause problems like you are having.

---

### Post by guiverc on 2021-11-13
I can't provide any help sorry, but I'll provide some comments.

- I've never experienced this issue
- I'd check your hardware; to me that's the most likely (*from my experience*)

I've been asked to explore this issue before (*I forget which cycle*) and I didn't find any issues in 5-6 laptops I had access to. The issue however is likely to occur only with some laptops.  In exploring this issue I reported the following (*if I recall correctly; it was a number of cycles ago*).

- battery reporting is less accurate if your batteries are in poor health
- the battery info isn't updated every second; some detail (power-attached, disconnected) is monitored more regularly than other details (*energy full, remaining etc as these details change less often*); so some stats are older than others you're shown. I forget how long it took for all stats to be updated (*which may vary on release*) but I vaguely recall 5 mins.

If your box is failing to shutdown; what are you using to shutdown?   A SysRq command? (ie. REISUO maybe). I'd likely explore systemd journal (`journalctl`) looking for clues on the last shutdown if the prior session shutdown is impacting the issue.

Sorry I don't really have any clues.  But the fact that I was asked (*Lubuntu* *team*) to explore this issue does *imply* you're not likely the only person experiencing this (*or equivalent*).  [I]Note: I'm not a developer so wasn't looking at code, just QA-testing


[/I]Additional thought:   You're using the LTS, but didn't state which kernel stack you're using. As switching stacks is *pretty* easy, and you can install & have both stacks installed without effect (*other than slightly more disk space, larger bandwidth for updates as two stacks to upgrade*) I'd likely add the other kernel stack choice & see if that influences behavior. 

 The default stack for Lubuntu 20.04 LTS installs with 20.04 or 20.04.1 media was the GA, however 20.04.2 or later media defaulted to HWE. This differs to Ubuntu Desktop (*which defaulted to HWE for all new installs of 20.04; I'm mentioning this as the wiki doc assumes Ubuntu Desktop installs*).  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by jet-bundle on 2021-11-14
Thanks for the two comments. I'm particularly interested in the remark by **Autodave** about powered USB hubs, because the 9300 with the battery indicator problem has a 4-way powered USB hub plugged into one of the USB-C sockets. I wonder if there are any details of how this can cause problems? I'll disconnect the hub for an extended period (maybe a week or so) and see if the problem fails to recur.

I'll investigate the shutdown problem separately. On the question of kernel stacks: ubuntu-drivers list-oem  gives a null result, so I assume HWE, but I won't experiment with this until the result of the USB hub test is clearer.

Thanks again.

---

### Post by Autodave on 2021-11-14
I have had SO many weird issues with powered hubs.....especially when the hub itself seems to be working OK.  I do not trust them at all any longer and refuse to use them.

---

### Post by jet-bundle on 2021-11-21
Nearly a week of running without the powered USB hub. There has been no recurrence of the battery indicator problem, and in addition the computer has always shut down promptly. I think that's reasonable evidence that the USB hub has caused both problems, so thanks for the suggestion. I'll mark the thread as solved.

---

