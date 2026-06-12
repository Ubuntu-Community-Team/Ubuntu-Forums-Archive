---
title: "lm-sensors configuration on Abit AS8 mobo"
date: 2010-03-08
forum: Hardware
---

### Post by JKyleOKC on 2010-03-08
I'm attempting to get temperature sensing working on my AS8 mobo running Hardy LTS 8.04.4, and the output of sensors is totally screwy. Most of the voltage readings are 4.8 VDC and the temp readings are -1.0 and 0.0 C. Fan speeds are all 0 RPM.

It seems obvious that the program isn't getting the correct data from the /etc/sensors3.conf file. However, editing this file in the appropriate "chip" section (following line 429) has absolutely no effect on the output even after running "sudo sensors -s" to make the changes take effect. Specifically, I changed the label "Vcore 1" to "Vcore-1" just to verify that it was reading the changed file, but the change did not appear in the output.

I've run "sensors-detect" twice, and made certain that the recommended w83627hf module is in place. I've searched the forums here, and also googled, but haven't found any ideas of what to try next. The one thing that occurs to me is to create a new sensors.conf file that contains ONLY the data for this driver and see if that makes any difference...

This mobo has Abit's "guru" feature in place, and it reports a CPU temperature of 48 C when I check it in BIOS. I don't have the guru display connected, though. All suggestions will be welcome!

---

### Post by JKyleOKC on 2010-03-09
Update: I found that sensors was not reading the configuration file I was editing. When I use the -c option to point to the proper file, I see the label changes but all of the readings are still unchanged. I suspect that the "calculate" lines are incorrect for this mobo. Also, the -u (raw output) option shows zero outputs for temp and RPM sensors, although the guru display in the BIOS setup screen does show reasonable values for both temp and RPM.

Could it be that sensors-detect is giving me wrong driver module instructions? More detailed troubleshooting leads would definitely help; all that I've found in the HOW-TO threads only say to use sensors-detect; if it's not working, what other options are available?

---

### Post by JKyleOKC on 2010-03-09
> **JKyleOKC said:**
> Could it be that sensors-detect is giving me wrong driver module instructions?That was the precise problem. The sensors-detect program kept telling me to install the w83627hf driver, which was in fact compatible with the mobo but that chip didn't have everything connected. After extensive googling I found that since the system had Abit's uguru feature installed, I needed to install its driver instead. When I did, everything began working as expected.

---

