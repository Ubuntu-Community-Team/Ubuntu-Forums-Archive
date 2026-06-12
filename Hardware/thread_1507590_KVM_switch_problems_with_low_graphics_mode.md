---
title: "KVM switch problems with low graphics mode"
date: 2010-06-11
forum: Hardware
---

### Post by marca311 on 2010-06-11
Hi there!
I have a slight problem with my KVM switch relating to low graphics mode.
Every time I switch my monitor, keyboard, and mouse to a different computer, my Ubuntu computer goes into low graphics mode because it can no longer detect my monitor. The interesting thing is that this only started happening after I upgraded to 10.04.

I can post any logs if information is needed.
My KVM switcher is made by Belkin and is ps/2 based with VGA monitor ports.
The monitor is a HP 9500 and my computer is a IBM Thinkcentre with a Intel Graphics card and chipset. And while I'm at it, my shoe size is 10 (US).

Any suggestions would be appreciated. (Not on my shoe size)

Thanks,
marca311

---

### Post by Xan.Manning on 2010-06-23
I have had much the same problem, in fact I am  suffering from this right now.

I have a Belkin Switch2 KVM, the model with the USB keyboard and mouse, monitor and audio... with wired 'puck'. I believe this is my model: F1DG102Uuk.

I find that the problem seems to happen when I am using the NVidia proprietary driver and there is a power cut, don't ask me why.

This has been happening with me since 9.04. ¬.¬

I installed 10.04 a few weeks ago and had the KVM plugged in, this was working fine, recognising the monitor perfectly as a Samsung SyncMaster 913N (1280x1024). However, this morning I had a powercut and now when I boot Ubuntu with the KVM plugged in it only recognises the monitor as a generic 'CRT' with a maximum resolution of 1024x768 (although was only letting me select 640x480 or 320x240).

The only solution I have ever found to this is to completely reinstall Ubuntu as all changes I have made have always ended up being reverted once I restart the computer ¬.¬ - I used to try completely removing the NVidia driver, config and all but when I reinstall it the same problems occur. I am sure there is a better way of doing it as I am sooo terribly n00b but I cannot get any changes to stick.


I appreciate this is a laptop thread and my desktop is what is an issue here, but it is a related problem I have and a laptop is involved in this issue.


If anyone knows a solution, marca311 and myself would be forever grateful.


Thanks for taking the time to read.

Take care all,
Xan.

---

### Post by Xan.Manning on 2010-06-23
Right, I may have just found a solution for anyone with the Belkin Switch2 - if they have had problems like this (can't believe it worked, clearly I did this in the wrong order on previous occasions).

[LIST=1]
[*]With your main computer connected to the switch, open up the monitors dialog *(or nvidia-settings for me)*.
[*]Disconnect the USB from your secondary computer.
[*]With the USB still plugged into the main computer, *(and the mains power, if your switch needs it)* turn the monitor off.
[*]Disconnect the Switch's USB cable from the main computer, the switch should power off. *If your KVM is powered by the mains, disconnect from the mains*.
[*]Wait 15-30 seconds
[*]Plug the Switch's USB back into the main computer and make sure it is powered on *(plug into mains if you require mains power)*.
[*]Turn the monitor on.
[*]Press 'Detect Monitors' in Ubuntu
[*]Hopefully the screen will have flashed or something will have changed. In the dropdown menu of resolutions, the list should have refreshed itself.
[*]Reconnect all as normal.
[/LIST]

May be worth a try yourself, marca311, if it doesn't work, my apologies.

---

