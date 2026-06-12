---
title: "Not All RAM recognised"
date: 2011-02-18
forum: Hardware
---

### Post by xtremesupremacy3 on 2011-02-18
Hello, I am using Ubuntu 10.10 64bit.

I am running a laptop with 3Gig RAM, and there is annoying problem that keeps coming up.

When I start my laptop up, most times it starts slow and when I check the System Monitor it shows up as having 744.4MiB Memory.
Now using 'free' it only shows up as having that amount of RAM listed.
When I restart the laptop it tends to just stick on 744MiB but after a few times of restarting it lists the correct 2.7GiB RAM.

I have noticed how this happens mostly if my laptop has been started on a non-full battery. Now I don't know whether that's a safety feature to preserve battery power or not. 
One thing I noticed (if the battery is the culprit) is that for some unknown reason, when I have a full battery and take it off the mains, it pops up saying that I am on critically low battery, I can confirm that this is a wrong diagnosis. I have plenty of battery power left, it is just being read wrong.

So my question is, is there anything I can do to let the RAM be fully read each time, or if it's due to critical battery reading, is there anyway I can shut off the critical message so the battery doesn't affect it?

Arthur

---

### Post by xtremesupremacy3 on 2011-02-18
Just wanted to update and give those people who have a similar problem perhaps a bit of hope.

I tried restarting my computer several times in succession whilst the battery was NOT fully charged and every single time it showed up as the false amount of RAM. 
When I restarted the laptop after the battery was fully charged, it showed 2.7GiB RAM (correct amount)...This furthers my curiousity whether the two are related or not.

My thought here is that (I am not sure though) I have 2 RAM chips and due to battery power it decides to only run 1 for saving power(?)

Anyway, I have found that there is a bug (Bug #558627) relating to a false critical power issue on the MSI Wind, considering I am running an MSI laptop, it is fairly safe to say that I am probably suffering from that.

Having found a workaround I will see if this also fixes the RAM issue and will report for those who have similar problems.

If you too get a 'critical battery level' warning when you have a near full battery, try this:

> Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

No need to restart, just close the config editor.

I read in another forum thread that the same problem / workround also work on a Dell Vostro 1310.(From Launchpad)

Arthur

---

### Post by xtremesupremacy3 on 2011-02-19
Another update:

Having carried out the gconf-editor trick, I no longer get a warning for critical battery.

What is also amazing is that it seems my suspicion was correct.
I have started my laptop off charge which in the past has always ended in having 744MiB. But what's strange is that this time I have the full 2.7GiB RAM showing.

It seems that the two were indeed related.

Problem SOLVED

---

