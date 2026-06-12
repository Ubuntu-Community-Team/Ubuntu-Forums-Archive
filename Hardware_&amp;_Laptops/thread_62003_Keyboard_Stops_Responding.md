---
title: "Keyboard Stops Responding"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by muzzie on 2005-09-03
after I toggle away then back with my KVM switch.

I am very new to Linux/Ubuntu (actually using Kubuntu) and have come across a little problem that turns out to be very problematic for my situation.

I have a simple IOGEAR MiniView KVM that works fine, except that when I toggle to my Mac and then back to Kubuntu, the keyboard no longer responds.  The mouse works fine, they are both USB and connected to the computer via a single USB cable (mouse and keyboard over same USB cable to PC from KVM).

This behavior persists even when X is not running.  

Now, I also have Debian + KDE installed on the machine, and this problem does not happen on that setup.  The mouse and keyboard both function fine when toggling back with the KVM.

Any of you gurus know why this is happening and how to fix it? 

BTW- Hello folks! Liking what I see so far, new operating systems are so much fun, but boy does it suck being a newbie all over again ;)

---

### Post by muzzie on 2005-09-03
Well, I found my problem.  Had a PS/2 keyboard plugged in also, which never caused any trouble under Debian or Windows, but for some reason Ubuntu doesn't like it.  I unplugged that keyboard, leaving only the USB connections, and it's working fine.

---

### Post by the_person0 on 2005-09-04
I am having this same problem, however it is on a laptop so i can't really disconnect the second kb/mouse. The mouse normally works, however the kb takes a while to work and sometimes it does not work at all.

---

### Post by muzzie on 2005-09-05
I wish I could help, the_person :(
I actually had this crop up a couple more times lately, even with the PS/2 keyboard disconnected.  It's definitely not happening nearly as much, hasn't happened all day today and I've been messing around with this thing for 12 hours straight.  I've toggled my KvM at least a dozen times too, and no trouble.
Before, when I had the PS/2 keyboard in, it would happen basically everytime I toggled with my KvM.

Next time it happens, I'll try and take not exactly what I was doing at the time.

---

