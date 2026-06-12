---
title: "Pulseaudio does not always start HMDI output after monitor change"
date: 2016-12-30
forum: Hardware
---

### Post by owise1 on 2016-12-30
Hi - Posting this as I have solved an annoying problem with pulseaudio - HDMI output would stop working after the monitor was turned off and required a restart to get working again.  The problem started after replacing a failed monitor with a TV using HDMI (previous monitor also used HDMI but no problems).  I suspect it was how HDMI implemented in the TV I was using.
Looking though the forums did not provide any solutions but after reading the Arch pulse audio troubleshooting guide ([https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#No_HDMI_sound_output_after_some_time_with_the_monitor_turned_off](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#No_HDMI_sound_output_after_some_time_with_the_monitor_turned_off)) I had my solution.  Switch VT and back again.  Avoids restart but I suppose does not fully address the hardware issue but simple fix.

Hope this helps anyone else with this problem.

Dave

---

