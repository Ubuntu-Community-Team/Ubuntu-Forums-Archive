---
title: "touchpad does not work on MSI Prestige"
date: 2024-08-24
forum: Hardware
---

### Post by tolosa524 on 2024-08-24
Hello community,

I just bought a MSI Prestige Laptop and after install ubuntu 22.04 I get this issue. When I log in on my ubuntu session I can use the touchpad for a few seconds but then stops magically and I am not able to use it again. Could you give me some advice. Thanks in advance.

---

### Post by currentshaft on 2024-08-25
Check system logs with "sudo dmesg" and "journalctl -b" for errors.

---

### Post by tea for one on 2024-08-25
> **tolosa524 said:**
> I just bought a MSI Prestige Laptop and after install ubuntu 22.04 I get this issue. When I log in on my ubuntu session I can use the touchpad for a few seconds but then stops magically and I am not able to use it again. Could you give me some advice. Thanks in advance.
Is this laptop a 2024 model?
Download and try Ubuntu 24.04 - new PC often requires recent kernels.

---

### Post by guiverc on 2024-08-25
This may not be helpful, but you've asked this question in the *official flavors - Lubuntu* section of Ubuntu Forums, so I'll answer to that part.

Lubuntu doesn't include all *closed source **kernel modules* and differs (*as do all flavors*) to Ubuntu Desktop in regards the default kernel stack depending on ISO used for LTS releases (*flavors  still follow the defaults of Ubuntu Desktop 18.04 and earlier as per  HWE kernel stack defaults, Ubuntu Desktop 20.04 LTS & later now  always use HWE*), but these can be changed/added post-install as per the Lubuntu manual

[https://manual.lubuntu.me/lts/4/4.3/software_sources.html](https://manual.lubuntu.me/lts/4/4.3/software_sources.html)

Refer the* Additional Drivers* tab for any drivers for your hardware that aren't included in the reduced size (*lighter*) Lubuntu ISOs.

Ubuntu Desktop ISOs (*which include the Ubuntu Session; Lubuntu won't*) is installed from a larger ISO which contains *optional*  kernel modules that can be installed if your hardware will benefit from them. Lubuntu ISOs are smaller as they don't contain these.

---

### Post by tolosa524 on 2024-08-27
Thank you guys and I so sorry about make the question in the incorrect place. I am currently using Ubuntu 24.04 LTS. 

I run:

$ sudo dmesg | grep pad
[    1.676755] input: MSNB0001:00 06CB:CEBD Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-MSNB0001:00/0018:06CB:CEBD.0001/input/input5
[    1.749367] input: MSNB0001:00 06CB:CEBD Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-MSNB0001:00/0018:06CB:CEBD.0001/input/input8

and 

$ journalctl -b | grep -i touchpad
ago 27 08:35:33 matias-Prestige-14H-B12UCX kernel: input: MSNB0001:00 06CB:CEBD Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-MSNB0001:00/0018:06CB:CEBD.0001/input/input5
ago 27 08:35:33 matias-Prestige-14H-B12UCX kernel: input: MSNB0001:00 06CB:CEBD Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-MSNB0001:00/0018:06CB:CEBD.0001/input/input8
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) config/udev: Adding input device MSNB0001:00 06CB:CEBD Touchpad (/dev/input/event5)
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (**) MSNB0001:00 06CB:CEBD Touchpad: Applying InputClass "libinput touchpad catchall"
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) Using input driver 'libinput' for 'MSNB0001:00 06CB:CEBD Touchpad'
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (**) MSNB0001:00 06CB:CEBD Touchpad: always reports core events
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: is tagged by udev as: Touchpad
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device is a touchpad
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device removed
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) XINPUT: Adding extended input device "MSNB0001:00 06CB:CEBD Touchpad" (type: TOUCHPAD, id 13)
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) selected scheme none/0
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) acceleration factor: 2.000
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) acceleration threshold: 4
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: is tagged by udev as: Touchpad
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device is a touchpad
ago 27 08:35:39 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) config/udev: Adding input device MSNB0001:00 06CB:CEBD Touchpad (/dev/input/mouse1)
ago 27 08:35:52 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[1501]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device removed
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) config/udev: Adding input device MSNB0001:00 06CB:CEBD Touchpad (/dev/input/event5)
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (**) MSNB0001:00 06CB:CEBD Touchpad: Applying InputClass "libinput touchpad catchall"
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) Using input driver 'libinput' for 'MSNB0001:00 06CB:CEBD Touchpad'
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (**) MSNB0001:00 06CB:CEBD Touchpad: always reports core events
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: is tagged by udev as: Touchpad
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device is a touchpad
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device removed
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) libinput: MSNB0001:00 06CB:CEBD Touchpad: Step value 0 was provided, libinput Fallback acceleration function is used.
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) XINPUT: Adding extended input device "MSNB0001:00 06CB:CEBD Touchpad" (type: TOUCHPAD, id 13)
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) selected scheme none/0
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) acceleration factor: 2.000
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (**) MSNB0001:00 06CB:CEBD Touchpad: (accel) acceleration threshold: 4
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: is tagged by udev as: Touchpad
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) event5  - MSNB0001:00 06CB:CEBD Touchpad: device is a touchpad
ago 27 08:35:54 matias-Prestige-14H-B12UCX /usr/libexec/gdm-x-session[2467]: (II) config/udev: Adding input device MSNB0001:00 06CB:CEBD Touchpad (/dev/input/mouse1)

I am quite new, so I can not see any error.

The wierd thing is that when I start the session it works for 15 seconds and then stops.

Thank you

---

### Post by tea for one on 2024-08-27
I can't help you with an exact solution.
After a quick search for your hardware MSNB0001:00 06CB:CEBD, it appeared that many distros have difficulty with this touchpad.

However, there seems to be a hack that keeps the touchpad available although the script was not published in the thread.
> But then I realized that, somehow, running lshw or lspci makes the touchpad run again, for a short while. So I have created an ugly, inelegant script, the kind that probably thinks "Not again!" often, to run lspci every 10 seconds
See here [https://forums.somethingawful.com/showthread.php?threadid=4044841](https://forums.somethingawful.com/showthread.php?threadid=4044841)

---

### Post by currentshaft on 2024-08-27
What happens if you

modprobe -r i2c_hid
modprobe i2c_hid

---

### Post by tolosa524 on 2024-09-08
Thank you so much for your help. actually that was super useful. It is quite expensive to have that script all the time running but at least I have my touchpad when I need it. What is [COLOR=#000000]modprobe -r i2c_hid  ?[/COLOR]

---

### Post by guiverc on 2024-09-08
> **tolosa524 said:**
> What is [COLOR=#000000]modprobe -r i2c_hid  ?[/COLOR]

Before I execute any commands I see, or am giving by someone I don' t know I can trust (*even then, as everyone makes mistakes*), I'll look what commands are likely to do myself first.

To explore that I'd just 

```

man modprobe

```

ie. view the quick reference manual page for modprobe..  Reading the first bit tells me a bit, then I scan scan down manually (*or with search; standard POSIX/vi etc search*) for the -r or remove option.

You can actually see much of that by inserting "man modprobe" in a search engine too using any browser, however by doing it at a command level, you'll be seeing the correct manual for your OS & release, instead of whatever OS/release the search engine provides, as options do change over time.

This doesn't directly help, but hopefully allows you to find the answer (*and next time too*).

---

### Post by tolosa524 on 2024-09-10
Hello guys, I found a more effitient and resource usage firendly solution than using a WHILE loop. This is from our dear friend ChatGPT, it works as a work around, but it is not the final solution:

[h=3]**Using systemd Timers (Precise Control)**[/h]For a more robust and system-integrated solution, you can use systemd to create a timer that triggers every 10 seconds.
[h=4]Steps to set up a systemd service and timer:[/h]
[LIST=1]
[*]**Create a systemd service file:**


sudo nano /etc/systemd/system/touchpad-rescan.service



[*]**Add the following content:**


[Unit]
Description=Touchpad Rescan Service

[Service]
Type=oneshot
ExecStart=/bin/bash -c 'echo 1 | sudo tee /sys/bus/pci/rescan'



[*]**Create the corresponding timer file:**


sudo nano /etc/systemd/system/touchpad-rescan.timer



[*]**Add the following content to run every 10 seconds:**


[Unit]
Description=Run touchpad rescan every 10 seconds

[Timer]
OnBootSec=10s
OnUnitActiveSec=10s
AccuracySec=1s

[Install]
WantedBy=timers.target



[*]**Enable and start the timer:**


sudo systemctl enable touchpad-rescan.timer
sudo systemctl start touchpad-rescan.timer



[*]**Check the status of the timer:**


sudo systemctl status touchpad-rescan.timer


[/LIST]

---

### Post by iiwiars on 2024-09-11
Crazy to have to install a service dedicated to keep your touchpad alive :o MSI should definitively improve that themselves...

---

