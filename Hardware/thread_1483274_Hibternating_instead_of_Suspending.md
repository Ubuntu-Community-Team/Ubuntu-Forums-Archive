---
title: "Hibternating instead of Suspending"
date: 2010-05-14
forum: Hardware
---

### Post by gdi2k on 2010-05-14
On Lucid I would like to set my laptop (Lenovo X200) such that it suspends if left idle for 10 minutes when on battery power. The Power Management Preferences look like they would allow me to do this via the "On Battery" tab, "Put computer to sleep when inactive for 10 minutes". 

However, after 10 minutes, it hibernates instead of suspending. Resuming from hibernation on this machine doesn't work well (it takes around 3 mins with lots of disk thrashing), so I would much rather have it suspend.

I've attached screenshots for my power options, but I can't see anything that I might be doing wrong...

---

### Post by burton247 on 2010-05-14
Mine does a similar thing which I find odd. Does yours go into hibernate straight away. Mine seems to sit on standby for a while then swtich to hibernate...I don't get it. And my laptop doesn't come out of hibernate full stop, never had a laptop that will

---

### Post by gdi2k on 2010-05-14
When you say "Standby", do you mean sleep mode, or just screen blanking? My screen blanks after 5 mins, which it's set to do in the Preferences, then goes into hibernation after 10. 

What makes this issue more confusing is the lack of consistent terminology - on the "Battery" tab of the Power Management Preferences, it says "Put computer to *sleep* when inactive for...", then the very next line (Laptop lid) offers "Suspend" and "Hibernate" as options, but not "Sleep". So "Sleep" is hibernate or suspend? (to me [sleep is suspend]("http://en.wikipedia.org/wiki/Sleep_mode") (as in Windows), but maybe others see it differently)

Sadly hibernation still seems to be a big issue on Linux - I did a Google search to see if I could resolve my issue, and there are so many different types of problem on so many laptop brands accross so many different Linux versions and distros, I didn't feel like wasting my weekend on it. :-(

---

### Post by fari81 on 2010-05-28
I have the same issue here on Sony Vaio SR220. I had no problem in 9.10, and the system used to go to sleep (i.e., suspend) after 10 min when on Battery. 

However, As soon as I upgraded to Lucid (10.04), it hibernates after 10 minutes instead of sleeping. And of course, my laptop takes more than two minutes to come out of hibernation. I think this is a serious usability issue. :(

For now until I find a solution, I'm going to set the sleep time to never.

Have you filed a bug in launchpad for this?

---

### Post by gdi2k on 2010-06-01
I've found the bug in Launchpad here: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/576698](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/576698) 

There's also a workaround in there which is very easy to apply at comment number 3, which says: 

> 
I had this same problem but I fixed it by changing this key in the configuration editor from "hibernate" to "suspend"

/apps/gnome-power-manager/actions/sleep_type_battery


---

### Post by gotgenes on 2010-06-02
> **gdi2k said:**
> I've found the bug in Launchpad here: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/576698](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/576698)
Many thanks!

---

