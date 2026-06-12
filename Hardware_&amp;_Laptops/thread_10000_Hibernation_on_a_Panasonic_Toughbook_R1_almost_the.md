---
title: "Hibernation on a Panasonic Toughbook R1 **almost there!**"
date: 2005-01-03
forum: Hardware &amp; Laptops
---

### Post by ming0 on 2005-01-03
I'm having some issues w/ power management on my panasonic toughbook r1...
 
I've upgraded to hoary, and have tried using the recommended kernel 2.6.9-1-386, and have also used hoary's stock 2.6.9-1-686 kernel with the exact same results.  

**I've found a few different ubuntu wiki's on making swsusp work properly, and one suggests building a custom kernel--I used a different wiki's advice, and got a pre-built kernel that included swsusp2**

Also, I've had slackware 10 loaded on this laptop, and was able to get hibernate working very well, so I know it's possible.

On to the problem:

I use the power button to hibernate and am able to bring the system back up, but once I'm up, I get frequent momentary lockups--the touchpad stops working and the cursor freezes for between a half second and three seconds. It happens more often when there is a small (or large) cpu load, and it happens on and off (every 3 to 30 seconds) until I reboot the system.
 
I checked my dmesg, and found some interesting output:
...
eth0: no IPv6 routers present
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 4 bytes 
away.
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 4 bytes 
away.
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
cpufreq: change failed with new_state 2 and result 268369920
psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
cpufreq: change failed with new_state 2 and result 268369920
Warning: CPU frequency is 400000, cpufreq assumed 866000 kHz.
****This goes on for longer--a lot longer****
 
I'm guessing that hibernate kills the script that changes the speedstep frequency on the cpu or something? Alas I have no idea how to remedy the situation  :cry: 

Thanks,
Dean

---

