---
title: "Sound problems - Ubuntu 22.04 LTS"
date: 2023-08-16
forum: Hardware
---

### Post by araujo-phys on 2023-08-16
Hi everyone,

I recently had some issues with the arch linux and I change my distro to ubuntu. However, when installing it and other distros in my laptop (arch linux, bodhi linux, etc) I have been facing severe sound problems. All of them only show as output device "dummy output". I've tried several options to solve the problem, including adding the lines:

[COLOR=#2C001E][FONT=Ubuntu]options snd-hda-intel dmic_detect=0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]options snd-hda-intel model=auto[/FONT][/COLOR]

at the end of the /etc/modprobe.d/alsa-base.conf file, reinstall the kernel, reinstall alsamixer. Nothing works. Does anyone have an idea how I could resolve this?

This is my output from the inxi -F command:

[COLOR=#2C001E][FONT=Ubuntu]Audio:[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]    driver: snd_hda_intel[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  Sound Server-1: ALSA v: k6.2.0-26-generic running: yes[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  Sound Server-2: PulseAudio v: 15.99.1 running: yes[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]  Sound Server-3: PipeWire v: 0.3.48 running: yes[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]CPU: dual core Intel Celeron N4020 (-MCP-) speed/min/max: 1056/800/2800 MHz[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Kernel: 6.2.0-26-generic x86_64 Up: 8m Mem: 1783.7/3740.7 MiB (47.7%)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]Storage: 447.13 GiB (12.3% used) Procs: 229 Shell: Bash inxi: 3.3.13

Thanks[/FONT][/COLOR]

---

