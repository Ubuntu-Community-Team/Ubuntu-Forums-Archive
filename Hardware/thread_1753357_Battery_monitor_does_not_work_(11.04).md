---
title: "Battery monitor does not work (11.04)"
date: 2011-05-08
forum: Hardware
---

### Post by silkworm2.5 on 2011-05-08
Hi :)

I've been having trouble with the battery monitor in Ubuntu 11.04.

Back in 10.04 (I skipped 10.10) it could show me the percentage of charge left, but not the amount of time until it ran out/finished charging.
Now though, I just get the message: Laptop Battery (estimating...) twice. It has two in the list at the same time with only one battery.

Is there a way to fix this issue? Or at least get it to display the percentage left rather than estimating the amount of time it has?
Thanks.

Details: Ubuntu 11.04 64 bit. HP Compaq laptop. 2.20 GHz dual core processor. 4 GB RAM.

---

### Post by DavidRaid on 2011-05-17
Same problem here, HP Mini 110 running up-to-date Natty.
When disconnecting power cord, a notification appears telling me the percentage so it is aware of it, it just doesn't show it in the indicator, instead showing two 'estimating' lines.

Restarts with and without battery don't solve the problem.

---

### Post by DavidRaid on 2011-05-17
Installing acpi (sudo apt-get install acpi) seems to get rid of the second 'estimating'. I'll wait it out to see if it finishes estimating completely.

---

### Post by Benchrest on 2011-05-29
Mine was working correctly until two days ago while using my laptop out doors. The display was to dark and if I turned up the brightness, after a few seconds it dimmed again. I turned off "Reduce backlight brightness" and "dim display while idle". After that my battery only showed estimating for both time left and percent charged. I reset the two settings but it still only shows estimating for charging and for time left while running on battery.  I would sure like to get it reset to the default it had.

---

### Post by rich52x on 2011-05-31
I had the same problem

This worked for me

[http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/](http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/)

It replaces the standard battery monitor with one that actually works, just follow the instructions on the page i linked

Didn't take me five minutes :D

---

### Post by Benchrest on 2011-05-31
Yes it works, I have it installed. But it is not a good solution as it adds an additional battery indicator that is there even when your 100% charged. And I can't get rid of the old one as three icons are tied to that applet. Getting rid of the old battery icon I would also lose my wireless internet connection icon and speaker icon.  I sure wish these icons were all separate applets. I bet they can be added individually like this battery applet icon.

---

### Post by rich52x on 2011-06-01
> **Benchrest said:**
> Getting rid of the old battery icon I would also lose my wireless internet connection icon and speaker icon
I wonder why that is, on mine, during the install of the alternative, it asks me if i want to remove the old one, and it just removes that

Strange

But yes, I do agree that it isnt a good solution, such a necessity should be fully working with a distro that should 'just work'

---

### Post by Benchrest on 2011-06-01
I did not get the choice to replace the existing monitor.  Also, the first time I attempted to install update I got an error. I found two entries added to sources for battery monitor. Disabling them allowed updates to work. I am running Natty with Ubuntu classic desktop (gnome).

---

### Post by htedrom on 2011-08-22
same problem here, other battery monitors work fine, just not the default gnome one - shame because I like the new icon (it is a new icon right?) =(

---

