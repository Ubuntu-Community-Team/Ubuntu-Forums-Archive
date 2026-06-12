---
title: "A new one - software runs on connecting power"
date: 2008-10-03
forum: General Help
---

### Post by abeering on 2008-10-03
Asus EEEPC 1000H, Hardy Heron, eeepc kernel build, gnome.  Adept linux user, enjoying perks of ubuntu, even using Gnome(wow!).

**Meat of the issue**:

When I connect power to the laptop(or netbook, die.), evolution(the mail client) attempts to run.  This wasn't initially a problem, and without any major configuration change, simply began to happen.  So everytime I plugin the power, evolution started.  Don't use evolution, for all I knew it was some stupid bug(read: feature), so I removed evolution.  Now when I plugin power, woops! Gnome spits out a message about evolution not being found.  

I'm struggling to find out what is at fault here, is it gnome?  is is the system? It definitely started to happen after a long period of time  with it not.  Did a little googling:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=910118](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=910118)

Same issue. (I am not Dan)

Any ideas? What it could be, what forum I should post in, what I'm doing for dinner tonight? ANY help or ideas would be appreciated.  

Andy

---

### Post by letatcest on 2008-11-10
Same problem here, Asus 901, intrepid (started with hardy). Akward I would say, and annoying, I don't want to see my office-mail on weekends! 

I'll try to file a bug-report for this, If I can find where to do that

---

### Post by scouser73 on 2008-11-10
Here's the place to register a bug; [https://launchpad.net/]("https://launchpad.net/")

---

### Post by geirha on 2008-11-10
Plugging in/out the power cable triggers an event that is caught by acpid. And I think it runs the script /etc/acpi/power.sh when one of those events occur, and that script in turn runs either all scripts in /etc/acpi/battery.d/ if the power cable is unplugged, or /etc/acpi/ac.d/ if the power cable is plugged in. On my desktop install, there's a script stopping anacron in battery.d/ and one that starts anacron in ac.d/. Have a little peak and see if it perhaps runs something like evolution ...

---

### Post by 3guk on 2008-11-10
This occurs because the asus-acpi module sends hotkey events when connecting to AC power with the wrong code (for the Eee; it's surely the right one on other Asus laptops).

Comment out all lines in /etc/acpi/events/asus-mail (by prepending a #), and restart acpid with sudo /etc/init.d/acpid restart.

---

