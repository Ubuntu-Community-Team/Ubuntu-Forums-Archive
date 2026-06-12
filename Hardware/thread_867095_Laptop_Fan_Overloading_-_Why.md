---
title: "Laptop Fan Overloading - Why?"
date: 2008-07-22
forum: Hardware
---

### Post by Sebastian12 on 2008-07-22
The fan on my laptop has been continuously running much faster than usual to the point where it sounds like my computer is overheating - but by simply feeling it you can tell that its temperature it nowhere near abnormal.  This only happens when I have my desktop loaded with desklets and the AWN manager.

My RAM stays at about a quarter of 2 GBs, so its not being overworked.  Why is the laptop fan overloading then?  It almost never did this in Vista...

---

### Post by spud.dups on 2008-07-22
I have an HP Pavilion dv5170, and the fan does the same thing in windows and Hardy.  After looking into it there didn't seem to be a real problem, just something with how the firmware had been set to handle the fan. If it doesn't bother you having a computer that sounds like it's about to take off, then there will be no damage done, but if you would like to have the fan run a little slower then look into motherboard specific drivers.  It's probably nothing OS specific that can fix the problem.

---

### Post by Sebastian12 on 2008-07-22
This is true, but I plan to use Linux in college next year and a laptop that sounds like it's going to explode just won't do.

Thanks though.

---

### Post by spud.dups on 2008-07-22
Yea, I could see how that would be a problem in a classroom.  Did it do the same thing when/if you were using windows?

---

### Post by Sebastian12 on 2008-07-22
It would only do this in Windows Vista if I was running a high-end game (i.e. Supreme Commander) which would happen with any computer knowing the required specs in that case.

That's why it's so odd.

---

### Post by jay019 on 2008-07-28
> **spud.dups said:**
> It's probably nothing OS specific that can fix the problem.

I'm not so sure about this. With 7.04 the fan would come on when hot and turn off when cool. Now it goes on (not sure of temp when it starts) but it never turns off once its cooled. I have to manually turn it off by, get this, typing acpi -t into a console. This turns off the fan instantly and reports the temp at the time, usually around 25 - 30 degrees. This is new behaviour since installing Hardy, so I am wondering what changed.

Jay

---

