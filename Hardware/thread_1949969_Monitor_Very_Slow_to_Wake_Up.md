---
title: "Monitor Very Slow to Wake Up"
date: 2012-03-31
forum: Hardware
---

### Post by dschaller on 2012-03-31
On my desktop system with Ubuntu 10.04 I've been having trouble the last few months with my monitor being *very* slow to wake up after power management puts it in standby. It used to come back up right away... then it took 30 seconds... then it took a minute... now it takes nearly four minutes. I suspect the delay will only get longer over time until it just won't come back at all.

I thought first of a possible hard drive issue. Maybe the system can't read what it needs to off the drive to wake up? Once the monitor is up, however, there are no obvious issues with the drive, although it is an older one.

I don't really have any other guesses. Anybody have any ideas?

---

### Post by LinuxFan999 on 2012-03-31
Do you have other monitors to test?

---

### Post by 2F4U on 2012-03-31
Are we talking about suspend/hibernate or just powering the monitor off? When only the monitor is powered off, there should be no need to access the hard drive. Since the machine is running normally when just the monitor is powered off, there is no need to read something from hdd when the monitor is powered on again.

---

### Post by dschaller on 2012-03-31
Thanks for the replies. If I understand it correctly, I just have it set to power the monitor down. My power management preferences are set to: "Put computer to sleep when inactive for: Never" and "Put display to sleep when inactive for: 1 hour"

---

### Post by dschaller on 2012-04-02
Yesterday I couldn't get the monitor to wake up for about 45 minutes. The issue does seem to be the monitor itself. I plugged in a different one and it appeared to work normally. I have noticed that the longer the monitor is asleep, the longer it takes for it to wake up. If it has just recently gone down, it will wake up quickly/normally within the first couple minutes.

So, it doesn't seem to be hard drive but a slowly failing screen.

---

