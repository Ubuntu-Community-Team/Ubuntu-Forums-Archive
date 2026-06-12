---
title: "Laptop Battery troubles"
date: 2010-01-23
forum: Hardware
---

### Post by dalty on 2010-01-23
Recently I have switched to Ubuntu 9.1 from Windows XP for a number of reasons.  Yesterday I installed everything and was working fine, except for one thing.  The battery icon in the top right corner said that the battery was charging but at 0% and was not moving.  As soon as I pulled the charger it would IMMEDIATELY shut off.

 I ran some simple commands in terminal and it detected the battery was there and that it was charging. It said it had full capacity and everything else was normal. I know it is not the battery itself because I recently replaced it and it was working without problems on windows.

Also it is not the charger as I have tried another one and still the same problem consists. 

I also shut down and started up several times and plugged and unplugged with no effect.

Also I have a Dell 700m [old I know] but it gets the job done [or used too]

Any help is appreciated =]

---

### Post by JackRock on 2010-01-23
It is highly unlikely the OS has anything to do with it, other than reporting the battery level.  But, if it shuts off immediately after unplugging, it's more than just reporting.

Do you have a dual-boot setup on this machine?  If so, boot into Windows and see what happens.

Does the battery seem to charge when the machine is powered off (not just on hibernate or standby)?  Test this by powering all the way down, charging for a while, and turning the machine off without being plugged in.

Something I did think of is that if Linux *believes* there to be no battery power left, it will shut down the machine to save data, so it could be a reporting issue on that end.

---

### Post by dalty on 2010-01-23
I am no longer dual booting, I was before and it was working fine on both ubuntu and windows.

I will try your suggestion and tell you if it works though.

The reason it is not shutting down is because it says there is a power source charging the battery. 

The battery light on the front of my laptop under the display is on, showing that is charging also.

This has got me completely confused.

---

### Post by mudguts on 2010-01-23
That does seem odd.
what is the model of your laptop? 
and have you googled that issue to see if it's something else?
I run 9.04 and it doesn't even show my battery charging but pops up when unplugged.

Have you also tried installing BatMon from the repository?

---

### Post by dalty on 2010-01-23
I have a Dell 700m that is around 4 years old, but everything was working fine with windows installed. I've google'd the problem and there are no other results with the same problem that I have that I could find. I think that you can change the settings to choose when the battery icon is displayed or not.

I'm not familiar with BatMon, what does it do?

also, JackRock, I attempted your suggestion and when i tried to power on it wouldn't even start to turn on

---

### Post by mudguts on 2010-02-02
batmon is a battery monitor that is on the panel near the date/time/wifi area.  it can show you a graph of how the power is used and if it spikes or drains quicker then expected etc.etc.  it's in the repository.

---

### Post by whitehaint on 2010-02-02
I had a similar issue with a not too old battery in a vaio laptop.  It will charge, but for some reason it always thinks the battery is dead.  If possible, try a new battery.

---

