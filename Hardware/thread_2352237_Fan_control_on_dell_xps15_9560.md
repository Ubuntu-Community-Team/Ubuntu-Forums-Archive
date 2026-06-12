---
title: "Fan control on dell xps15 9560"
date: 2017-02-10
forum: Hardware
---

### Post by saroele on 2017-02-10
I have installed Ubuntu 16.04 in dual boot with windows 10 on my dell xps15 9560 (7th gen core-i7, 4K touch display). One of the issues that I find very annoying is the (almost) constant fan  noise.
  I upgraded to 16.10  as suggested in [this]("https://ubuntuforums.org/showthread.php?t=2301071") thread but that did  not solve anything. 

I don't know what the expected fan noise / fan speed should be as a function of cpu temperature?  I installed psensor for measuring the temperatures and even for cpu temperatures around 43°C the fan is constantly working. 

So I guess my questions are:
[LIST]
[*]How can i see the fan speed in order to do better logging of the relation between fan noise and cpu temperatures? 
[*]How can I reduce the fan speed and still be safe? 
[/LIST]

Thanks.

---

### Post by poorguy on 2017-02-10
This may help.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by howefield on 2017-02-10
This Dell, nowhere near as nice as yours :) was ok with fglrx but since 16.04 runs hot and noisy with the open source drivers. What worked for me was to install the i8kutils package and create a file at /etc/i8kmon.conf...

```
sudo apt install i8kutils
```

```
sudo nano /etc/i8kmon.conf
```

and paste in the following contents...

```
# Run as daemon, override with --daemon option
set config(daemon)      0

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose) 1

# Status check timeout (seconds), override with --timeout option
set config(timeout) 20

# For computer with 2 fans, use a variant of this instead:
# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0) {{-1 0}  -1  47  -1  60}
#set config(1) {{-1 1}  36  61  50  70}
#set config(2) {{-1 1}  50  75  60  80}
#set config(3) {{-1 2}  65 128  70 128}

set config(0) {{0 0}  -1  55  -1  55}
set config(1) {{1 1}  36  60  36  60}
set config(2) {{1 1}  52  70  52  70}
set config(3) {{2 2}  65  78  65  78}
set config(4) {{2 2}  75 128  75 128}


# end of file
```

Doesn't usually need a daemon restart but it doesn't hurt..

```
sudo /etc/init.d/i8kmon restart
```

Runs pretty well now but I try not to tax it too hard.

---

### Post by saroele on 2017-02-12
I installed lm-sensors and ran the sensors-check. But I don't think any fans are found, here's the final output:

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)
```


And for the installation of i8kutils, I have also a problem: I can't install the package.  Here' s the output of the command:

```
Job for i8kmon.service failed because the control process exited with error code.
See "systemctl status i8kmon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript i8kmon, action "start" failed.
&#9679; i8kmon.service - LSB: Dell fan/cpu-temperature monitor
   Loaded: loaded (/etc/init.d/i8kmon; generated; vendor preset: enabled)
   Active: failed (Result: exit-code) since Son 2017-02-12 12:46:16 CET; 13ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 6573 ExecStart=/etc/init.d/i8kmon start (code=exited, status=1/FAILURE)

Feb 12 12:46:16 roel-XPS-15-9560 systemd[1]: Starting LSB: Dell fan/cpu-temp....
Feb 12 12:46:16 roel-XPS-15-9560 i8kmon[6573]:  * Starting Dell fan/cpu-temp...n
Feb 12 12:46:16 roel-XPS-15-9560 i8kmon[6573]:    ...fail!
Feb 12 12:46:16 roel-XPS-15-9560 systemd[1]: i8kmon.service: Control process...1
Feb 12 12:46:16 roel-XPS-15-9560 systemd[1]: Failed to start LSB: Dell fan/c....
Feb 12 12:46:16 roel-XPS-15-9560 systemd[1]: i8kmon.service: Unit entered fa....
Feb 12 12:46:16 roel-XPS-15-9560 systemd[1]: i8kmon.service: Failed with res....
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package i8kutils (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 i8kutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas what I should do? Thanks a lot.

---

### Post by howefield on 2017-02-12
> **saroele said:**
> And for the installation of i8kutils, I have also a problem: I can't install the package.  Here' s the output of the command:

Hmm.. sorry to hear that, it works perfectly for me.

There is this bug on launchpad with a verified solution that might help you : [https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/1364503](https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/1364503)

---

### Post by poorguy on 2017-02-12
I have found very few prebuilds that display all of the results when using hardware monitoring software and if not displayed in bios than I doubt it will be available by OS software although not always the case.

---

### Post by saroele on 2017-02-12
ok, with the solution in that lunchpad bug report I can install i8kutils. Thanks @howefield.

Is it possible that the installation only, without any configuration done, changes my fan control?  Since I installed it, the fan  works in 'cyclic burst' mode: it blows hard for a very short time (like half a second), than stops for about 2-3 seconds, and then the next thrust. It starts doing that when the cpu temperatures are around 50°C and then stops doing it when they are around 44°C.

---

### Post by howefield on 2017-02-12
There is no problem with not having a config file as it will use some defaults. The benefit of having one is that you can tweak the settings.

---

### Post by cmuell89 on 2017-03-11
This is likely because the i8k module is competing with BIOS control. 

See [https://www.reddit.com/r/Dell/comments/5y3rii/xps_9560_battery_life_optimization_and_fan/](https://www.reddit.com/r/Dell/comments/5y3rii/xps_9560_battery_life_optimization_and_fan/)
Scroll to i8k utils how to. Proceed at your own risk.

cheers

---

### Post by The musmula on 2017-08-03
Any other developments here?

---

### Post by The musmula on 2017-08-06
So I tried getting educated on the matter of thermals and how I can get rid of the fan noise, you too are reporting. Turns out not even a single smartass wanted to school me so I eventually ended up finding this: [https://gist.github.com/whizzzkid/37c0d365f1c7aa555885d102ec61c048](https://gist.github.com/whizzzkid/37c0d365f1c7aa555885d102ec61c048)

A problem I've had was the inability to select the intel prime profile from the nvidia settings thing and reboot. I'd be stuck at the plymouth screen and couldn't even enter tty. I would avoid the issue by going into recovery mode, mounting the filesystem to rw and running ```
prime-select intel
``` which would just make my cmoputer usable aagain but it didn't solve the problem. What did it for me was this part of the guide mentioned above:

```

# Add command line params:sudo nano /etc/default/grub
# Make the following look like this, do not ask why.
GRUB_CMDLINE_LINUX_DEFAULT='pcie_port_pm=off acpi_backlight=none acpi_osi=Linux acpi_osi=! acpi_osi="Windows 2009"'
sudo update-grub2

```

---

