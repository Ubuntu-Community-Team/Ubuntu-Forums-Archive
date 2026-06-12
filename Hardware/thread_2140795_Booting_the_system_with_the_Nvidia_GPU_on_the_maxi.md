---
title: "Booting the system with the Nvidia GPU on the maximum clock, and fanspeed at 70%"
date: 2013-04-30
forum: Hardware
---

### Post by eduardofgd on 2013-04-30
[COLOR=#000000][FONT=verdana]After some research and experimentation, I found a solution to start the Nvidia GPUs, on Linux, with the maximum clock and fan speed by 70%, preventing overheating. Just follow the steps below:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]1. Install the proprietary driver for your Nvidia card:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]a) On Debian-derived systems, open a terminal and run the command "$ sudo apt-get update && sudo apt-get install nvidia-current -y";[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]b) On Red Hat-derived systems, open a terminal and run the command "# yum install akmod-nvidia";[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]c) In Slackware systems, you're by yourself. I have no business with the devil.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2. Open the terminal and run the command "$ sudo gedit /etc/X11/xorg.conf" (this command will open the xorg.conf configuration file for editing);[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]3. In the "Device" section, paste the following:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]# added manually:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Option "Coolbits" "4"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]4. Save and exit gedit;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]5. Then open gedit again and paste the following shell script:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]# read the current fan speed from nvidia-settings[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]current_speed=`nvidia-settings -t -q [fan:0]/GPUCurrentFanSpeed`[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]new_speed=0[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]#read arguments from command line[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]case "$1" in[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#if argument is "up", increase fan speed by 10%, unless already at 100%[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]"up") let "new_speed = $current_speed + 40"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]if [ $new_speed -gt 100 ][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]then[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]new_speed=100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]fi[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]eval "nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=$new_speed"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana];;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#if argument is "down", decrease fan speed by 10%, unless already at 35[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]"down") let "new_speed = $current_speed - 10"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]if [ $new_speed -lt 35 ][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]then[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]new_speed=35[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]fi[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]eval "nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=$new_speed"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana];;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#if "min", set fan speed to 35%[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]"min") nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=35[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana];;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#if "maX2, set fan speed to 100%[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]"max") nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=100[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana];;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#if "mid", set fan speed to 60%[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]"mid") nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=60[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana];;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]esac[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]exit 0[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]6. Save the file with the name "nvfanspeedadjust" and exit gedit;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]7. In the terminal, run the command "$ chmod +x nvfanspeedadjust" to make it executable;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]8. Copy the newly created file to the folder "~/.nvfanspeedautoadjust";[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]9. Then open gedit again and paste the following:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana][Desktop Entry][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Type=Application[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Exec=/home/user/.nvfanspeedadjust/nvfanspeedadjust up[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Hidden=false[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]X-GNOME-Autostart-enabled=true[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Name[pt_BR]=NvidiaFanAutoAdjust[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Name=NvidiaFanAutoAdjust[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Comment[pt_BR]=NvidiaFanAutoAdjust[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Comment=NvidiaFanAutoAdjust[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]10. On the third line of the newly created file, change the username to your username;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]11. Save the file with the name "nvautoadjust.desktop";[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]12. Copy this file to the folder "~/.config/autostart";[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]13. Restart the system.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]14. Now, You are ready, and your Nvidia GPU will start with the maximum clock speed and fan speed will be locked in 70%, preventing overheating of the device.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]P.S.: This page helped me with scripts and other things: [/FONT][/COLOR][http://crunchbang.org/forums/viewtopic.php?id=18919](http://crunchbang.org/forums/viewtopic.php?id=18919)

---

