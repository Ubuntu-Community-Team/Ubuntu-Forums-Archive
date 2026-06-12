---
title: "cpuidle, state0, state1, state2 times"
date: 2008-08-12
forum: Hardware
---

### Post by quinthar on 2008-08-12
What do the settings in /sys/devices/system/cpu/cpu0/cpuidle mean?  I was just poking around and saw some odd values that made me wonder if my CPU was never going into its highest-performance mode.  For example, the "usage" and "time" of the state0 mode (where power == 1000) is virtually nothing, whereas very high for the other modes (with lower powers).  Does this mean I'm never using more than half of my CPU?

david@SonOfLappy:/sys/devices/system/cpu/cpu0/cpuidle$ grep -r . *
state0/name:C1
state0/latency:1
state0/power:1000
state0/usage:1137
state0/time:0
state1/name:C2
state1/latency:1
state1/power:500
state1/usage:43392
state1/time:8279560
state2/name:C3
state2/latency:57
state2/power:100
state2/usage:612716
state2/time:1185604746
david@SonOfLappy:/sys/devices/system/cpu/cpu0/cpuidle$ 

-david

---

