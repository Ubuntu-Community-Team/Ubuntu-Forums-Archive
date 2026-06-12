---
title: "[SOLVED] How do I startup only one instance of a program?"
date: 2008-09-15
forum: General Help
---

### Post by HousieMousie2 on 2008-09-15
Hiya,

Here's the issue:

I have gotten used to shutting down with programs running so that they load automatically upon the next startup... the two main programs in question being Thunderbird and Amarok.

Unfortunately sometimes they fail to reopen... so I placed them in the startup dir... but now it often tries to open two instances Thunderbird and does open two Amaroks.

Without having to add extra steps to my daily boot-up or shut down, how can I make sure it does not try to open more than one without having to either manually close them before shut down or manually open them after start up?

Can this be done?  If so... can it be done by a newbie?  ;)

Cheers!

---

### Post by Locutus_of_Borg on 2008-09-15
stop saving your sessions and put everything you want started in your autostart directory

or write a script that checks for the instance of a process and if it is not running launch it, else do nothing

---

### Post by HousieMousie2 on 2008-09-15
> **Locutus_of_Borg said:**
> stop saving your sessions and put everything you want started in your autostart directory

or write a script that checks for the instance of a process and if it is not running launch it, else do nothing

LOL Thank you!  I think I am years away from writing my own scripts, but I will keep it in mind.

Stop saving sessions!  Excellent... and a big DUH to me, why didn't that dawn on me???  Oh well. lol

Thanks, Locutus of Borg!

---

### Post by dazzlindonna on 2008-09-15
And how would one go about the process to "stop saving sessions"?

---

### Post by HousieMousie2 on 2008-09-15
> **dazzlindonna said:**
> And how would one go about the process to "stop saving sessions"?

I'm not sure unless you are using Kubuntu, (I'm on Hardy)...

If you are, then it is:

Kmenu/System Settings/Advanced/Session Manager

Click the radio button marked either "Restore manually saved session" (obviously you would need to save one first) or "Start with an empty session."

But it REALLY means it... it will not load much of anything that you might expect it to.  For instance, normally I start up with Kopete, KAlarm, SuperKaramba loads LiquidWeather... now all that loads is my Eth0 connection icon and Klipper (Thunderbird and Amarok also load, but that is because I added them to the Autostart directory... I will need to add the others as well.)

Hope this helps... if you are not using a KDE flavor, you should still have some sort of Session Manager somewhere.

---

