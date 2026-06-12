---
title: "Is the idle=poll argument  in bootprompt the cause of high power consumption?"
date: 2009-03-05
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-05
The battery runtime is so short in Ubuntu while compared with Windows XP. I found out this page [http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html) and it said 
[b]The `idle=' Argument

Setting this to `poll' causes the idle loop in the kernel to poll on the need reschedule flag instead of waiting for an interrupt to happen. This can result in an improvement in performance on SMP systems (albeit at the cost of an increase in power consumption). [/b]
I think it is the cause. But without this argument Ubuntu failed to boot. Any one has a similar situation? Do you need the idle=poll argument in order to boot.

EDIT: just discover a similar thread
[http://ubuntuforums.org/showthread.php?t=618660](http://ubuntuforums.org/showthread.php?t=618660)

[b]Format: idle=poll or idle=mwait
+ Poll forces a polling idle loop that can slightly improves the performance
+ of waking up a idle CPU, but will use a lot of power and make the system
+ run hot. Not recommended.
+ idle=mwait. On systems which support MONITOR/MWAIT but the kernel chose
+ to not use it because it doesn't save as much power as a normal idle
+ loop use the MONITOR/MWAIT idle loop anyways. Performance should be the same
+ as idle=poll. [/b]

EDIT2:
I google with "idle=poll" battery
and it returns with bunches of topic about idle=poll shorten the battery life and increase the temperature, which in turn cause many undesirable problems. Oh, no..... would this argument kill my notebook??

EDIT3: 
I just found out using the argument idle=mwait instead of idle=poll reduces the discharging rate from 3000mA to 2200mA. And the cpu produces less heat too! I think the problem is solved. 

Here's the link about the kernel parameters. [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
[B]776		idle=		[X86]
777				Format: idle=poll or idle=mwait
778				Poll forces a polling idle loop that can slightly improves the performance
779				of waking up a idle CPU, but will use a lot of power and make the system
780				run hot. Not recommended.
781				idle=mwait. On systems which support MONITOR/MWAIT but the kernel chose
782				to not use it because it doesn't save as much power as a normal idle
783				loop use the MONITOR/MWAIT idle loop anyways. Performance should be the same
784				as idle=poll.[/B]

But I cannot find the definition of apicmaintimer and noapictimer. So my now only has this argument [idle=mwait] and everything seems working fine.

---

