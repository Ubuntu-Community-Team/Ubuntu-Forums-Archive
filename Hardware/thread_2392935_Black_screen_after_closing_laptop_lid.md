---
title: "Black screen after closing laptop lid"
date: 2018-05-27
forum: Hardware
---

### Post by Maximus559 on 2018-05-27
I'm running Xubuntu 18.04 on a Compaq Presario V2000. It's an older laptop with a physical lid switch button that I can press without closing the lid.

In Power Manager, I have Xubuntu configured to suspend when the laptop lid is closed. The system successfully suspends when I close the lid but resumes to a black screen when I open it. I can switch to a terminal with **Ctrl+Alt+F1**, but I can't switch back to X with **Ctrl+Alt+F7**. I have to restart the machine to get the desktop back.

This machine had a similar problem with Xubuntu 16.04 which I was able to fix by adding these lines to **/etc/systemd/logind.conf**:

[B]HandleLidSwitch=suspend
HandleLidSwitchDocked=suspend[/B]

However, this doesn't seem to work with 18.04.

Here are some things I have tried:

1) If I suspend using the Whisker menu or the sleep key, the system suspends and resumes successfully. So this problem is somehow tied to the lid switch.

2) If I add **IgnoreLid=true** to **/etc/UPower/UPower.conf**, the system no longer suspends when I press the lid switch. However, the display turns off and remains off while the switch is depressed. Releasing the switch turns the display back on and everything is usable.

3) If I use Power Manager to set the lid close action to "switch off display" or "lock screen", the display turns off when I press the lid switch and stays off when I release it. As before, I have to restart the machine to get back to a usable state.

The results of 2) suggest that something other than systemd and UPower is also handing the lid switch event and turning off the display. My conjecture is that this other thing is interfering with one or both of the others and preventing the display from turning back on after suspend/resume. Is there anywhere other than Power Manager, logind.conf, and UPower.conf where I can control lid switch behavior?

---

