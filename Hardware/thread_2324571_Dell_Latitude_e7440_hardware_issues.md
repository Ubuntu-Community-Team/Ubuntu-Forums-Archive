---
title: "Dell Latitude e7440 hardware issues"
date: 2016-05-14
forum: Hardware
---

### Post by John_Kreis on 2016-05-14
I have had nothing but issues since installing Ubuntu on my Dell Latitude E7440 laptop. I likely have more than one issue so I will try to to focus on what I believe my main issue is based on my observations. Basically put my laptop crashes and becomes completely unresponsive. Sometimes the laptop just shuts right off in the middle of doing something. Sometimes the screen goes blank and the device powers off, no message no warning, as if the battery was pulled right out. Most frequently I get a checkered black and screen (picture attached). Sometimes it shuts itself off after a few seconds although this varies, sometimes its a second, sometimes its 15 seconds sometimes I have to hold the powere button. I cannot drop to any other run level and any combination if SysRq keys I could find on the internet does not revive it. 


So let me start at the beginning. This is a work laptop I was issues in Jan 2015. Its a Dell E7440 with i7-4600U, Intel HD 4400 graphics, 16GB ram and 256 SSD. It had Windows 7 and the company locked it down bad I could not even do my day to day work on it. For example, we have Symantec DLP running on it. I literally could not copy a 50MB zip file to a USB drive without the entire system freezing. I know the short answer to this issue is have your desktop guys fix it, their hands are tied due to bureuacracy. I did have issues with the Bluetooth drivers in Win7 but i didnt use it so I didnt worry about it. Never had any sort of hardware issues outside of that, especially nothing like what I am experiencing now. About a month ago I decided it was time to install Linux. I grabbed a dev release of Ubuntu 16.04 and installed it. Didnt have an issue with it for about a week until I tried to put it in my docking station. The symptoms varied but most typically I would get the black and white screen. I could typically undock the laptop open the lid and be OK. I tested a bit and narrowed it down to the DisaplyPort connector on my dock. Also running more than 1 monitor was an issue as well. Another week goes everything seems fine and I start getting the screen again. This time it is happening when docked and also when not docked. From the beginnnig I has issues with the built in card reader but it wasn't essential, though useful, so I disabled it in the BIOS. I saw buffer underrun messages in the logs (also attached) and recalled a colleague who had similar issues with the Intel HD 4400 graphics. He recommeded I disable OpenGL since Ubuntu uses CompWiz. The next part gets long so to make short I played around with the Dell i915 chipset drivers and ultimately determined to rule out the OS, not yet bring the actual LTS relase, and installed Mint.


To make another log story short Mint doesnt help. During this time 16.04 LTS is released so install that. System seems decetly stable but still crashes beyond recovery daily. I finally did get a dock at my house and a dock at work stable. In fact the only time the system is stable is when it docked but using the HDMI video connection on the laptop. The laptop crashes about once an hour on average when not on the dock. Maybe a bit more frequently when on battery. I worked all dat Wendesday in the dock without one issue. 


I have run the CheckBox diagnostic in Ubuntu as well as the Dell diagnotics tool and memtest86. I have tried different desktop environments, different distros and different kernels. Including different variations of acpi boot settings. I have tried different video connections, monitors and reosolutions. I have different docks, power supplies and batteries. I have tried 3 different BIOS versions. I have disabled everyhting in my bios and tried enabling specific settings one by one. 


Today there was a period of time that the laptop would last about 100 seconds and turn off. This happeneed about 5 or 6 times in a row, on the battery and on the charger. I downgraded the bios as I saw some others were having the same mmc errors I was seeing since upgrading to A15.


I suspect acpi issues based on the error messages below and the nature of the instability. Beleow are a few of the messages i have recieved. I have changed so many settings by now that I am sure I have done something to break something else. What I really need help with at this point is isolating the issue(s) causing the system crashes. Im tired of playing whack a mole with this damn thing.




johnnykilo@DellBuntu:~$ dmesg | grep error -i
[    0.177408] ACPI Error: [^CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.177414] ACPI Error: Method parse/execution failed [\_PR.PPCE] (Node ffff88040e0c9190), AE_NOT_FOUND (20150930/psparse-542)
[    0.177420] ACPI Error: Method parse/execution failed [\EV10] (Node ffff88040e0cd7a8), AE_NOT_FOUND (20150930/psparse-542)
[    0.177424] ACPI Error: Method parse/execution failed [\SMIE] (Node ffff88040e0cb2d0), AE_NOT_FOUND (20150930/psparse-542)
[    0.177427] ACPI Error: Method parse/execution failed [\NEVT] (Node ffff88040e0cb258), AE_NOT_FOUND (20150930/psparse-542)
[    0.177429] ACPI Error: Method parse/execution failed [\_SB.PCI0.LPCB.ECDV._Q66] (Node ffff88040e0c9b90), AE_NOT_FOUND (20150930/psparse-542)
[    8.120432] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
johnnykilo@DellBuntu:~$ dmesg | grep mmc
[    0.695693] mmc0: Unknown controller version (3). You may experience problems.
[    0.695736] sdhci-pci 0000:03:00.0: No vmmc regulator found
[    0.695737] sdhci-pci 0000:03:00.0: No vqmmc regulator found
[    0.703565] mmc0: SDHCI controller on PCI [0000:03:00.0] using ADM02:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
johnnykilo@DellBuntu:~$ 


[ATTACH=CONFIG]269069[/ATTACH][ATTACH=CONFIG]269070[/ATTACH]

---

### Post by John_Kreis on 2016-05-31
Anyone out there? Having the same issue with Debian 8.4.1 now, so issue appears to further upstream for me

---

### Post by damonw5 on 2016-05-31
Please try updating your BIOS with the latest version from Dell Support's website.

See [https://access.redhat.com/articles/65378](https://access.redhat.com/articles/65378)

---

