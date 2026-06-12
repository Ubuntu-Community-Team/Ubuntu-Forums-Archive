---
title: "Laptop lid close doesn't do anything. Screensaver doesn't work."
date: 2008-06-12
forum: Hardware
---

### Post by Snaip on 2008-06-12
Howdy,

I upgraded Xubuntu to Hardy Heron from the previous release and the suspend on laptop lid close stopped working. To be precise, it worked after the upgrade until second reboot. And it has worked randomly a couple of times during the last to days.

acpi_listen gives on lid close:
video C054 00000080 00000000
button/lid C1E1 00000080 00012b4a

I reinstalled gnome-power-manager and gnome-screensaver without any use. Any ideas? Suggestions? Help appreciated. Thanks!

Also, clicking on Suspend button through gnome-power-manager menu works just fine. So something keeps acpi from telling gnome-power-manager to do its thing..?

---

### Post by Snaip on 2008-06-13
Update: The screensaver now works suddenly (after attempts of removal and install), however the lid close remains a mystery. I've tried also with kpowersaver and I get exactly the same results as with g-p-m. Lid close doesn't do anything, but manually pressing the "Suspend to RAM" in kpowersaver works as expected.

I also tried launching acpid from the terminal, added "echo foo" to /etc/acpi/lid.sh and /etc/acpi/events/lidbtn yet there's no echo. However I'm not sure if there should be any echo in the first place. Just an attempt.

---

### Post by mempman on 2008-07-04
any resolution on this?

---

### Post by Snaip on 2008-07-08
No. I decided to use the power button as a quick way to suspend the computer. 

At the moment I'm receiving an infinite loop of following events at acpi_listen;

video C054 00000080 00000000
button/lid C1E1 00000080 00003fd7

The new thing however seems to be that these events are captured without pressing anything. The events come in pairs (video/buttonlid) once in a 10 second in a roughly 25-35 events per burst. I still think the xubuntu upgrade broke something, but for the moment of being I'm not interested in reinstalling my system.

I suppose this remain as a mystery.

I don't think it's a hardware problem as everything worked fine before the first restart after xubuntu upgrade..

---

### Post by jimmy the saint on 2008-07-20
solution here: [http://ubuntuforums.org/showthread.php?p=5424711#post5424711](http://ubuntuforums.org/showthread.php?p=5424711#post5424711)
gnome power manager is helpless with gnome-screensaver running at startup.  for some reason it isnt.  its easy to fix.

---

