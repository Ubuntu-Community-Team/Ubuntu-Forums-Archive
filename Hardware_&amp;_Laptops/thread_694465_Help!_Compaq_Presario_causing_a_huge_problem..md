---
title: "Help! Compaq Presario causing a huge problem."
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by arshling on 2008-02-12
So here's the deal: I installed Gutsy on my main PC, and my hp dv2000 series laptop. I had barely any issues on both, so I offered to update my friend's laptop to Gutsy since she was having Windows issues.

Here's the issue I've run into though: When her laptop is plugged in, everything runs fantastically and she has absolutely no issues, but when the laptop is taken over to battery power, she has about 5 or 10 minutes of decent usage before the entire system bogs down, starts lagging, and usually ends up freezing all together.

I've tried several different booting options (acpi=off, noapic, acpi=noirq), played around with different laptop mode settings, changed around her bcm43xx drivers to open source, used envy for the ati drivers, and have finally run out of ideas of what might be wrong.

I've heard it's an issue sometimes that a laptop can't boot when solely on battery, but I can assure you the laptop boots very well.

Please! By all means, recommend something to help me get her laptop doing fantastically on battery power, so she can have a happy ubuntu experience :)

For detailed specs on her model of presario, refer to [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00613181&lc=en&cc=us&dlc=en&product=1841909&rule=46084&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00613181&lc=en&cc=us&dlc=en&product=1841909&rule=46084&lang=en)

---

### Post by agim on 2008-02-12
This is a strange problem. What I would to is open the gnome-system-terminal before you unplug the machine. To do this go to Applications->System tools. Or possibly Applications->Accessories.

This will show you what programs are being run (on the processes tab) as well as cpu and ram usage (on the resources tab).

Look for something that suddenly starts hogging resources.

The command 'top' can also be helpful. It will show cpu usage also. Type this into a terminal to use.

top

Edit: I won't be on for a few hours, but I will check on your progress afterwards.

---

### Post by arshling on 2008-02-12
Alright, I checked out her resource usage on battery power.

When the computer would actually let me look at the monitor, it showed that the monitor (or something even firefox) was using approximately 45% of her CPU. I'm not entirely sure how to interpret it... Her RAM looks completely fine, and it doesn't seem like her CPU would get throttled down on battery power, would it? There was nothing in particular that seemed to exclusively bog it down.

Perhaps there's some sort of power management setting?

---

