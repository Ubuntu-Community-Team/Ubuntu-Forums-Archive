---
title: "Fans always on High even though temp is Low"
date: 2008-10-02
forum: Hardware
---

### Post by citro_cell on 2008-10-02
Problem: CPU fan & PSU fan, running at full speed, all the time.

Background: I followed multiple tutorials to install lm-sensors, fan control, and other monitoring devices on my first install of Ubuntu Hardy (last week).  I successfully installed and configured fan control to modulate both fans according to cpu temp (ie when CPU temp < 55c fans are off, when CPU temp > 55c fans are on).  Since then I reinstalled Hardy.  I followed the tutorial below and everything seems to work up to the point where the system should auto regulate the fan (ie sudo pwmconfig is able to configure both fans and output the correct file).  Note: I disassembled and cleaned all components of the computer between installs.

Tutorial: I followed a combination of many different tutorials the first time (maybe something in one of those tutorials made my first try successful).  On my second attempt, I found this very descriptive tutorial and followed it: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")

Hardware:  Sony Vaio desktop PCV-RX650. 1 CPU fan, 1 PSU fan.  Ubuntu Hardy 8.04.1 fully updated.  Current temps in PC are all under 35c according to sensor applet.

Me: A linux convert as of last week - decided to dive in before I knew how to swim - Love Ubuntu.  (may need help spelled out a bit)

Question: Is this tutorial lacking something (although I have scanned many tutorials since then and do not see what)?  What are my options now?  

Thank you in advance for any help you can provide!

---

### Post by Nordic on 2009-09-18
I'm working on this also, with the same machine. I'll let you know if I figure anything out!

---

