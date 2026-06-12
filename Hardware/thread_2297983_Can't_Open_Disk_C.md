---
title: "Can't Open Disk C?"
date: 2015-10-08
forum: Hardware
---

### Post by Samir_Ahuja on 2015-10-08
Hello. I have installed Ubuntu 15.04 dual boot alongside windows 10.
When i try to access my local disk c (Named as Windows 8_OS C: on my  pc,) I get some vague error that could not be mounted. Shut down windows and try again.
Please help. why is it showing windows when I am in ubuntu? Please gimme a solution ASAP as I really need access to some important data on that drive. Thanks.:(

---

### Post by efflandt on 2015-10-08
By default Windows 8 or newer use fast startup which is sort of a hibernate mode when they shut down, so they can boot from virtual memory (similar to a Linux swap file). But that sets a flag so nothing will mount the partition read-write that could disrupt Windows. But if you web search "disabling windows fast startup" you can find more details about how to disable that, for example [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) (note that you would have to boot into Windows to disable that).

Or here see [http://ubuntuforums.org/showthread.php?t=2297611](http://ubuntuforums.org/showthread.php?t=2297611)

---

### Post by Samir_Ahuja on 2015-10-10
Thanks I'll try this and get back to you.

---

### Post by Samir_Ahuja on 2015-10-10
> **efflandt said:**
> By default Windows 8 or newer use fast startup which is sort of a hibernate mode when they shut down, so they can boot from virtual memory (similar to a Linux swap file). But that sets a flag so nothing will mount the partition read-write that could disrupt Windows. But if you web search "disabling windows fast startup" you can find more details about how to disable that, for example [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) (note that you would have to boot into Windows to disable that).

Or here see [http://ubuntuforums.org/showthread.php?t=2297611](http://ubuntuforums.org/showthread.php?t=2297611)
Nope didn't help. I did disable fast startup and shut it down to boot into Ubuntu. But it was on the Shutting down screen for 35 minutes. So I just switched it off via the power button and booted to Ubuntu. Still I get the same error on mounting. Is there anything else that may be causing this problem?
Appreciate the help.

---

### Post by coffeecat on 2015-10-10
> **Samir_Ahuja said:**
> Nope didn't help. I did disable fast startup and shut it down to boot into Ubuntu. But it was on the Shutting down screen for 35 minutes. So I just switched it off via the power button and booted to Ubuntu. Still I get the same error on mounting. Is there anything else that may be causing this problem?
Appreciate the help.

If you do a hard shutdown with the power button, you leave the Windows C: filesystem in an inconsistent state and Ubuntu will give you an error if you try to mount it. You need to shutdown properly. Perhaps it was installing updates - unfortunately you need to be patient with Windows sometimes! Also - don't restart from Windows. You get the same problem. If you need to reboot from Windows into Ubuntu, you need to do a proper shutdown and allow Windows to complete the shutdown process.

[quote=Samir_Ahuja]why is it showing windows when I am in ubuntu?[/quote]

I don't follow exactly what you mean. If you are asking why the file manager shows the Windows C: partition in the left pane, it is because it shows all non-hidden partitions in the left pane.

---

### Post by Samir_Ahuja on 2015-10-10
> **coffeecat said:**
> If you do a hard shutdown with the power button, you leave the Windows C: filesystem in an inconsistent state and Ubuntu will give you an error if you try to mount it. You need to shutdown properly. Perhaps it was installing updates - unfortunately you need to be patient with Windows sometimes! Also - don't restart from Windows. You get the same problem. If you need to reboot from Windows into Ubuntu, you need to do a proper shutdown and allow Windows to complete the shutdown process. 

Thanks I'll try again and get back t you.
Really appreciate all your help.:D

---

