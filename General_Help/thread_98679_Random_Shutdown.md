---
title: "Random Shutdown"
date: 2005-12-03
forum: General Help
---

### Post by Limulus on 2005-12-03
I'll be using Ubuntu, not doing anything odd and suddenly the computer will shutdown (I originally thought it was Firefox causing some sort of cascading crash but now I'm not so sure).  How can I go about diagnosing what's going on? (e.g. where would I find system logs?)  Sessionsaver for Firefox has helped turn this from a major pain into a minor one, but I still would like to get it resolved ^_^;

---

### Post by BabaFree on 2005-12-03
Don't know if this helps at all, but if the whole thing is turning off do you know if it might be a malfunctioning power supply?  
Just a thought,
Baba

---

### Post by Limulus on 2005-12-04
Possible but unlikely as it never happened in Hoary.  Its a laptop BTW; dunno if that helps.  I just want to know where to start looking for event logs and such on my system as I am still relatively new to Linux.

---

### Post by Limulus on 2005-12-04
I just found /var/log

I'll be sure to look there next time it happens.

---

### Post by Limulus on 2005-12-04
I just found this in /var/log/kern.log

Dec  3 20:41:21 localhost kernel: [4302910.623000] Critical temperature reached (191 C), shutting down.

191 C?  I think not ;)  The temp sits ~45 C most of the time but almost never even goes up to 60.  Do I maybe have an intermittently faulty temperature sensor?  If it just read 191 for one reading, is there a way to set Ubuntu so that it waits a sec to see if the temp goes down before shutting down?

---

### Post by Limulus on 2005-12-04
Here are the last four instances, starting from when things looked like they were going wrong:

> 
Dec  3 18:25:37 localhost kernel: [4294765.097000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
Dec  3 18:34:41 localhost kernel: [4295309.704000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 18:34:41 localhost kernel: [4295309.704000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 18:52:10 localhost kernel: [4296358.771000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 18:52:10 localhost kernel: [4296358.771000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 19:46:12 localhost kernel: [4299600.726000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 19:46:12 localhost kernel: [4299600.726000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 19:47:58 localhost kernel: [4299707.287000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 19:47:58 localhost kernel: [4299707.287000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 20:11:20 localhost kernel: [4301108.575000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 20:11:20 localhost kernel: [4301108.575000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 20:20:31 localhost kernel: [4301659.880000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 20:20:31 localhost kernel: [4301659.880000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 20:36:12 localhost kernel: [4302600.851000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Dec  3 20:36:12 localhost kernel: [4302600.851000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Dec  3 20:41:21 localhost kernel: [4302910.590000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.595000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.599000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.603000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.607000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.611000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.615000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.619000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.623000] i2c_adapter i2c-0: Error: command never completed
Dec  3 20:41:21 localhost kernel: [4302910.623000] Critical temperature reached (191 C), shutting down.
Dec  3 20:41:28 localhost kernel: [4302917.027000] apm: BIOS not found.
Dec  3 20:41:38 localhost kernel: Kernel logging (proc) stopped.
Dec  3 20:41:38 localhost kernel: Kernel log daemon terminating.


> 
Nov 27 20:54:15 localhost kernel: [4294764.516000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
Nov 27 20:55:48 localhost kernel: [4294858.033000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 27 20:55:48 localhost kernel: [4294858.033000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 27 20:57:15 localhost kernel: [4294944.284000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 27 20:57:15 localhost kernel: [4294944.284000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 27 20:57:24 localhost kernel: [4294953.551000] i2c_adapter i2c-0: Error: command never completed
Nov 27 20:57:24 localhost kernel: [4294953.555000] i2c_adapter i2c-0: Error: command never completed
Nov 27 20:57:24 localhost kernel: [4294953.559000] i2c_adapter i2c-0: Error: command never completed
Nov 27 20:57:24 localhost kernel: [4294953.561000] Critical temperature reached (127 C), shutting down.
Nov 27 20:57:24 localhost kernel: [4294953.566000] i2c_adapter i2c-0: Error: command never completed
Nov 27 20:57:24 localhost kernel: [4294953.681000] Critical temperature reached (47 C), shutting down.
Nov 27 20:57:30 localhost kernel: [4294959.948000] apm: BIOS not found.
Nov 27 20:57:40 localhost kernel: Kernel logging (proc) stopped.
Nov 27 20:57:40 localhost kernel: Kernel log daemon terminating.


> 
Nov 22 21:05:34 localhost kernel: [4294806.856000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:06:56 localhost kernel: [4294889.524000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:06:56 localhost kernel: [4294889.528000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:15:15 localhost kernel: [4295388.249000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 21:15:15 localhost kernel: [4295388.249000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 21:37:33 localhost kernel: [4296725.976000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:46:53 localhost kernel: [4297286.205000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:58:29 localhost kernel: [4297982.384000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:58:29 localhost kernel: [4297982.388000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:58:29 localhost kernel: [4297982.392000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:58:29 localhost kernel: [4297982.399000] i2c_adapter i2c-0: Error: command never completed
Nov 22 21:58:29 localhost kernel: [4297982.403000] i2c_adapter i2c-0: Error: command never completed
Nov 22 22:35:45 localhost kernel: [4300218.366000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 22:35:45 localhost kernel: [4300218.366000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 22:49:25 localhost kernel: [4301038.960000] i2c_adapter i2c-0: Error: command never completed
Nov 22 22:50:59 localhost kernel: [4301133.068000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 22:50:59 localhost kernel: [4301133.068000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 22:58:08 localhost kernel: [4301561.803000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 22:58:08 localhost kernel: [4301561.803000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 23:03:23 localhost kernel: [4301876.501000] i2c_adapter i2c-0: Error: command never completed
Nov 22 23:10:05 localhost kernel: [4302279.274000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 23:10:05 localhost kernel: [4302279.274000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 23:18:08 localhost kernel: [4302762.454000] i2c_adapter i2c-0: Error: command never completed
Nov 22 23:18:08 localhost kernel: [4302762.458000] i2c_adapter i2c-0: Error: command never completed
Nov 22 23:18:08 localhost kernel: [4302762.462000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:16:58 localhost kernel: [4306292.482000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 00:16:58 localhost kernel: [4306292.482000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 00:18:08 localhost kernel: [4306362.319000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:18:08 localhost kernel: [4306362.323000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:18:08 localhost kernel: [4306362.327000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:18:08 localhost kernel: [4306362.331000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:18:08 localhost kernel: [4306362.335000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:30:44 localhost kernel: [4307118.620000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 00:30:44 localhost kernel: [4307118.620000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 00:33:10 localhost kernel: [4307264.218000] i2c_adapter i2c-0: Error: command never completed
Nov 23 00:50:15 localhost kernel: [4308289.756000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 00:50:15 localhost kernel: [4308289.756000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 00:51:33 localhost kernel: [4308367.832000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 00:51:33 localhost kernel: [4308367.832000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 01:09:23 localhost kernel: [4309438.266000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 01:09:23 localhost kernel: [4309438.266000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 01:19:39 localhost kernel: [4310054.171000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 01:19:39 localhost kernel: [4310054.171000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 01:25:01 localhost kernel: [4310375.753000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 01:25:01 localhost kernel: [4310375.753000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 01:43:01 localhost kernel: [4311456.097000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 01:43:01 localhost kernel: [4311456.097000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 01:47:47 localhost kernel: [4311742.266000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 01:47:47 localhost kernel: [4311742.266000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 02:10:07 localhost kernel: [4313082.402000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 02:10:07 localhost kernel: [4313082.402000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 02:27:26 localhost kernel: [4314121.336000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 02:27:26 localhost kernel: [4314121.336000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 02:28:47 localhost kernel: [4314202.804000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 02:28:47 localhost kernel: [4314202.804000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 02:46:44 localhost kernel: [4315279.414000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 02:46:44 localhost kernel: [4315279.414000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 03:18:39 localhost kernel: [4317194.654000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 03:18:39 localhost kernel: [4317194.654000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 03:45:05 localhost kernel: [4318781.264000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 03:45:05 localhost kernel: [4318781.264000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 03:47:44 localhost kernel: [4318940.206000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 03:47:44 localhost kernel: [4318940.206000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 04:14:47 localhost kernel: [4320563.158000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:15:52 localhost kernel: [4320628.423000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:32:21 localhost kernel: [4321617.248000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 23 04:32:21 localhost kernel: [4321617.248000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 23 04:40:35 localhost kernel: [4322110.887000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:40:35 localhost kernel: [4322110.891000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:40:35 localhost kernel: [4322110.901000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:54:34 localhost kernel: [4322950.318000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:54:34 localhost kernel: [4322950.327000] i2c_adapter i2c-0: Error: command never completed
Nov 23 04:54:34 localhost kernel: [4322950.328000] Critical temperature reached (127 C), shutting down.
Nov 23 04:54:34 localhost kernel: [4322950.446000] Critical temperature reached (46 C), shutting down.


> 
Nov 21 18:05:14 localhost kernel: [4295470.137000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 18:05:14 localhost kernel: [4295470.137000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 18:24:20 localhost kernel: [4296616.374000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 18:24:20 localhost kernel: [4296616.374000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 18:32:58 localhost kernel: [4297134.181000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 18:32:58 localhost kernel: [4297134.181000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 20:13:29 localhost kernel: [4303166.507000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 20:13:29 localhost kernel: [4303166.507000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 20:49:34 localhost kernel: [4305331.752000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 20:49:34 localhost kernel: [4305331.752000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 21:03:49 localhost kernel: [4306185.916000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 21:03:49 localhost kernel: [4306185.916000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 22:22:07 localhost kernel: [4310884.808000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 22:22:07 localhost kernel: [4310884.808000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 22:39:45 localhost kernel: [4311943.376000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 22:39:45 localhost kernel: [4311943.376000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 23:13:25 localhost kernel: [4313963.437000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 23:13:25 localhost kernel: [4313963.437000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 23:13:39 localhost kernel: [4313977.634000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 23:13:39 localhost kernel: [4313977.634000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 21 23:14:30 localhost kernel: [4314028.030000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 21 23:14:30 localhost kernel: [4314028.030000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 00:09:10 localhost kernel: [4317308.424000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 00:09:10 localhost kernel: [4317308.424000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 00:36:46 localhost kernel: [4318964.435000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 00:36:46 localhost kernel: [4318964.435000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 00:45:15 localhost kernel: [4319473.482000] i2c_adapter i2c-0: Resetting entire SMB Bus to clear busy condition (08)
Nov 22 00:45:15 localhost kernel: [4319473.482000] i2c_adapter i2c-0: SMBus reset failed! (0x08) - controller or device on bus is probably hung
Nov 22 00:48:05 localhost kernel: [4319644.051000] i2c_adapter i2c-0: Error: command never completed
Nov 22 00:48:05 localhost kernel: [4319644.055000] i2c_adapter i2c-0: Error: command never completed
Nov 22 00:48:05 localhost kernel: [4319644.060000] Critical temperature reached (191 C), shutting down.
Nov 22 00:48:05 localhost kernel: [4319644.062000] i2c_adapter i2c-0: Error: command never completed
Nov 22 00:48:32 localhost kernel: [4319671.430000] apm: BIOS not found.
Nov 22 00:48:42 localhost kernel: Kernel logging (proc) stopped.
Nov 22 00:48:42 localhost kernel: Kernel log daemon terminating.


---

### Post by Limulus on 2005-12-04
BTW, the "i2c_adapter i2c-0" errors also happen in the logs without the system shutting down.

---

### Post by Limulus on 2005-12-04
I had a look around the forum and I noticed in an older thread, about a person with a similar problem, that someone asked "Do you have lm-sensors installed and configured correctly?"

This reminded me that I had indeed installed lm-sensors not all that long ago (Oct. 31 as per Synaptic; to get hardware-monitor working in the Gnome Panel) and I ran *sudo sensors-detect* to set it up, allowing it to modify my system settings...

I just had a look at lm-sensors in Synaptic and it suggests installing sensord, which contains "a daemon that logs hardware health status to the system log with optional warnings on potential system problems"  I'm going to install it to see if it will help me get some more details on the problem.

---

### Post by Limulus on 2005-12-04
here's what it now reads in /var/log/syslog

> 
Dec  4 14:58:05 localhost sensord: Chip: eeprom-i2c-0-51
Dec  4 14:58:05 localhost sensord: Adapter: SMBus ALI1535 adapter at d860
Dec  4 14:58:05 localhost sensord: Algorithm: Unavailable from sysfs
Dec  4 14:58:05 localhost sensord:   Memory type: DDR SDRAM DIMM SPD
Dec  4 14:58:05 localhost sensord:   Memory size (MB): Invalid 13 10 2 4
Dec  4 14:58:05 localhost sensord: Chip: eeprom-i2c-0-50
Dec  4 14:58:05 localhost sensord: Adapter: SMBus ALI1535 adapter at d860
Dec  4 14:58:05 localhost sensord: Algorithm: Unavailable from sysfs
Dec  4 14:58:05 localhost sensord:   Memory type: DDR SDRAM DIMM SPD
Dec  4 14:58:05 localhost sensord:   Memory size (MB): Invalid 13 10 2 4
Dec  4 14:58:05 localhost sensord: Chip: adm1032-i2c-0-4c
Dec  4 14:58:05 localhost sensord: Adapter: SMBus ALI1535 adapter at d860
Dec  4 14:58:05 localhost sensord: Algorithm: Unavailable from sysfs
Dec  4 14:58:05 localhost sensord:   M/B Temp: 45.00
Dec  4 14:58:05 localhost sensord:   -temp1_high: 127.00
Dec  4 14:58:05 localhost sensord:   -temp1_low: -65.00
Dec  4 14:58:05 localhost sensord:   -M/B Crit: 127.00
Dec  4 14:58:05 localhost sensord:   -hyst1: 122.00
Dec  4 14:58:05 localhost sensord:   CPU Temp: 46.25
Dec  4 14:58:05 localhost sensord:   -temp2_high: 50.00
Dec  4 14:58:05 localhost sensord:   -temp2_low: 45.00
Dec  4 14:58:05 localhost sensord:   -CPU Crit: 86.00
Dec  4 14:58:05 localhost sensord:   -hyst2: 81.00
Dec  4 14:58:05 localhost sensord:   alarms: 16.00


---

### Post by corax on 2006-07-19
I have the same problem sometimes (tipilcally when the system starts) the system shuts down itself saying : critical temperature reached: 
 Jul 19 20:20:14 localhost kernel: [17179608.300000] apm: BIOS not found.
Jul 19 20:20:16 localhost kernel: [17179609.872000] ttyS1: LSR safety check engaged!
Jul 19 20:20:16 localhost kernel: [17179610.308000] eth1: no IPv6 routers present
Jul 19 20:20:22 localhost kernel: [17179615.748000] Critical temperature reached ([COLOR="Red"]65535 C[/COLOR]), shutting down.

#(you are lucky with 191 C my notebook nearly killed me with 65535 C !!!! ;)  )

it is a sensor or lm-sensors fault for sure because it all get started when I installed that. I dont know the solution but i think i set my config file well here is the output of command "**sensors**" :
max6657-i2c-0-4c
Adapter: SMBus I801 adapter at 18e0
M/B Temp:    +52°C  (low  =   +20°C, high =   +55°C)   
CPU Temp:  +56.4°C  (low  = +20.0°C, high = +70.2°C)   
M/B Crit:    +70°C  (hyst =   +60°C)                   
CPU Crit:    +80°C  (hyst =   +70°C)                   

It is logical that if i have 65535 C then the system shuts down because i set the crit to 80 C

BUT 65535 should be ignored by system because it is a "bit" irrational so is the 191 C 

there should be a limit and if lm-sensors read a themp greater than 120 C for example (my cpu dies at 100 according to the intels specs) the value should be ignored.

anyway i dont know a solution and i dont thin there is a solution for this either ](*,)  but i ll post this to the lm-sensors developers.

bye

---

