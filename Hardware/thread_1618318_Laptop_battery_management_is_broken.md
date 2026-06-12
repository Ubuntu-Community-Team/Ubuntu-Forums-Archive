---
title: "Laptop battery management is broken?"
date: 2010-11-10
forum: Hardware
---

### Post by mahershi on 2010-11-10
Hello peeps!

I am running Ubuntu on a couple of old and a few new laptops.

I had been noticing this for sometime, but, I wasn't sure I whether my observation was right/wrong. Recently, the observation was CONFIRMED, so here's the question: **is laptop battery management BADLY BROKEN in Ubuntu/Linux**?

This specific observation was made on 2 portable-computers:
-> A laptop
-> And a brand new netbook

Both the laptop and the netbook are dual-boot: Windoze and Ubuntu.

When I run Windows on the laptop/netbook, the battery "left" and the actual run-time on the battery is fairly good (about 2-1/2 hours for the laptop and about 5-1/2 hours for the netbook).

But, when I run Ubuntu 10.04 (on the laptop) or 10.10 (on the netbook), first I get the "battery is broken" message. Then, the laptop lasts for only about 1-1/2 or less than that and the netbook lasts only about 3-1/2 hours. Clearly, that's ridiculously LOW time for the battery considering that the same battery lasts a LONG time under Windows. **So, I am wondering if battery management is broken under Linux/Ubuntu**?

Let me know what specific info you would want me to post here to help you debug this issue, but, here's some info I thought I should post for now (from the laptop):

For the Laptop:

# cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mW
remaining capacity:      25270 mWh
present voltage:         12523 mV

# cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         56160 mWh
last full capacity:      25970 mWh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 1295 mWh
design capacity low:     777 mWh
capacity granularity 1:  518 mWh
capacity granularity 2:  24675 mWh
model number:            LNV-42T4509
serial number:            1246
battery type:            LION
OEM info:                06

I have similar info for the netbook, but, that is "sleeping" under the covers for now. :) So, I hope this info is sufficient for now.

BTW, the netbook is new (just a couple of weeks old) and the battery lasts for 5-1/2 hours on Windows and less than 3-1/2 hours under Ubuntu!!!??? What gives? :confused:

Warm regards and keep on rocking.
:guitar:

---

### Post by shuukazedojo on 2010-11-17
Similar issue here

---

### Post by manco1911 on 2010-11-17
mmm.. i dont know if broken is the right word. 
I had/have the same experiense on one of my laptops. On Windows 7 (as it came from factory) it last "up to 10hs" that would be around 9 real time. On wifi, browsing. 

On Ubuntu that time droped to 4.1/2 hs. I had an issue on Ubuntu about the hibrid video card, so i was running both video cards, at lest on "energy" speaking. So maybe a plus there.. but yeah, not even close.. 

I found usefull to install "powertop", it can list your processes and hardware which is draining you power, and lets you to kill it. 
Read here:
[URL="http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1"]
Phoronix PowerTOP solution[/URL]
[Ubuntu-Tutorials.com powertop solution]("http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/")

On reports about the power drain:
[Phoronix review]("http://www.phoronix.com/scan.php?page=article&item=linux_windows_part2&num=1")

Seems to extend at least a bit your battery lifetime.. 
Hope it helps

---

