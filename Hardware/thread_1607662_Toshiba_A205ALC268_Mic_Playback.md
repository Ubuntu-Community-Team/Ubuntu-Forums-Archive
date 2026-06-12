---
title: "Toshiba A205/ALC268 Mic Playback"
date: 2010-10-28
forum: Hardware
---

### Post by DOS Boot on 2010-10-28
I'm using a Toshiba A205 with a Realtek ALC268 soundcard and when a microphone or other sound source is plugged into the mic jack there is no live playback. Sound can be recorded and then played back using Sound Recorder, but it does not come through the speakers while you are recording. 

I've tried editing the options in the alsa-base.conf file and so far none of the options (the ones found in the HD-Audio-Models.txt file) have worked to enable live playback.

Does anyone know of a way to enable live playback?

---

### Post by lidex on 2010-10-30
> **DOS Boot said:**
> I'm using a Toshiba A205 with a Realtek ALC268 soundcard and when a microphone or other sound source is plugged into the mic jack there is no live playback. Sound can be recorded and then played back using Sound Recorder, but it does not come through the speakers while you are recording. 

I've tried editing the options in the alsa-base.conf file and so far none of the options (the ones found in the HD-Audio-Models.txt file) have worked to enable live playback.

Does anyone know of a way to enable live playback?

If your mic works to record, alsa-base.conf options aren't the problem. More likely a sound routing issue. Do you have pulseaudio preferences installed? If not, 
```
sudo apt-get install paprefs
```
On the multicast/RTP tab, select the two main options and below the second one also select 'loop back audio to local speaakers'

---

### Post by DOS Boot on 2010-11-01
> **lidex said:**
> If your mic works to record, alsa-base.conf options aren't the problem. More likely a sound routing issue. Do you have pulseaudio preferences installed? If not, 
```
sudo apt-get install paprefs
```On the multicast/RTP tab, select the two main options and below the second one also select 'loop back audio to local speaakers'

Thanks Lidex, that was definitely a step in the right direction. After configuring Pulseaudio Preferences like you described, mic output worked briefly but it was delayed, choppy, and after a few seconds it cut out entirely.

If I switch between "Send audio from local microphone" to one of the other two options below it and then back again, that will temporarily enable mic output but it still cuts out after a few seconds.

---

### Post by lidex on 2010-11-02
Remove your pulse config files and reboot. Reset the options in paprefs and see if they stick.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```

No joy? Post this output please:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by DOS Boot on 2010-11-03
> **lidex said:**
> Remove your pulse config files and reboot. Reset the options in paprefs and see if they stick.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```No joy? 

Running those commands seemed to delete the ".pulse" files but also returned these errors:

```
rm: cannot remove `/home/mint/.asound*': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory
```After rebooting I heard the mic kick in at startup for a few seconds then cut out. 

> **lidex said:**
> 
Post this output please:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

After running that command the mic output worked for a few seconds then cut out. Here's the output:

```
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is e32d5ba5baa78fe6f4792efb4cd0f7f0.
I: main.c: Session ID is e32d5ba5baa78fe6f4792efb4cd0f7f0-1288795976.210021-1177156621.
I: main.c: Using runtime directory /home/mint/.pulse/e32d5ba5baa78fe6f4792efb4cd0f7f0-runtime.
I: main.c: Using state directory /home/mint/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

---

### Post by DOS Boot on 2010-11-04
When I run the following command mic output becomes enabled without cutting out. 
 
```
pactl load-module module-loopback
```
 
The only issues that remain are the delay and some pitch shifting. Once that command is is run the output will begin working with about two seconds of delay, then the pitch will go high for a few seconds, return to normal, and the delay will be cut down to about one second.

---

### Post by lidex on 2010-11-04
> **DOS Boot said:**
> When I run the following command mic output becomes enabled without cutting out. 
 
```
pactl load-module module-loopback
```
 
The only issues that remain are the delay and some pitch shifting. Once that command is is run the output will begin working with about two seconds of delay, then the pitch will go high for a few seconds, return to normal, and the delay will be cut down to about one second.

[http://pulseaudio.org/wiki/Modules#module-loopback](http://pulseaudio.org/wiki/Modules#module-loopback)

---

### Post by DOS Boot on 2010-11-04
> **lidex said:**
> [http://pulseaudio.org/wiki/Modules#module-loopback](http://pulseaudio.org/wiki/Modules#module-loopback)

I manually set the sources and sinks as well as latency_msec and still got the same result. Would any of those other options help to reduce latency?

---

### Post by DOS Boot on 2010-11-05
One thing that seems to cut down on the latency is running the loopback module then opening PulseAudio Volume Control, selecting the "Input Devices" tab and then selecting "Show: All Input Devices". For some reason just having that open cuts down on the latency (although it's still noticeably delayed) and it also raises the pitch. When PulseAudio Volume Control is closed the pitch drops and the delay becomes longer.

---

### Post by lidex on 2010-11-05
A sampling rate change may help here. Open this file:
```
gksudo gedit /etc/pulse/daemon.conf
```
Scroll down to line ~76 "; default-sample-rate = 44100", uncomment it (remove semicolon)and change to 48000. Save and close. Logout and back in.

---

### Post by DOS Boot on 2010-11-05
> **lidex said:**
> A sampling rate change may help here. Open this file:
```
gksudo gedit /etc/pulse/daemon.conf
```Scroll down to line ~76 "; default-sample-rate = 44100", uncomment it (remove semicolon)and change to 48000. Save and close. Logout and back in.

After editing that file the latency is still about the same. Do you think it might be some kind of conflict between ALSA and PulseAudio and some other programs running in the background? This is all taking place on a clean install of Linux Mint 10 RC, but it also shows up in a Live USB of Mint 9 (Both are the GNOME version).

---

### Post by lidex on 2010-11-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by DOS Boot on 2010-11-05
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.

Here's the link to the output of that command:

[http://www.alsa-project.org/db/?f=e17606bf30c3ebcb641150aa3ae70ed873baf407](http://www.alsa-project.org/db/?f=e17606bf30c3ebcb641150aa3ae70ed873baf407)

---

### Post by lidex on 2010-11-05
> **DOS Boot said:**
> Here's the link to the output of that command:

[http://www.alsa-project.org/db/?f=e17606bf30c3ebcb641150aa3ae70ed873baf407](http://www.alsa-project.org/db/?f=e17606bf30c3ebcb641150aa3ae70ed873baf407)

Wish I'd asked for that sooner. Do this for me please as your alsa install is out of sorts. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Generic instructions for ubuntu, as for mint, not sure about gdm and ubuntu-desktop. Watch the removal process
to see what else needs to be re-installed.

---

### Post by DOS Boot on 2010-11-06
> **lidex said:**
> Wish I'd asked for that sooner. Do this for me please as your alsa install is out of sorts. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get purge linux-sound-base alsa-base alsa-utils

``````
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Generic instructions for ubuntu, as for mint, not sure about gdm and ubuntu-desktop. Watch the removal process
to see what else needs to be re-installed.

Running those commands, restarting, and running the loopback module enabled mic playback with noticeably less delay than normal. I also think the pitch changing issue is gone now.

Also, using the latency_msec command and setting it to "=1" or "=5" seems to provide even faster response, but there is still a fraction of a second of delay. It's almost gone, though. Is there anything else that can be tweaked to get rid of the latency?

---

### Post by lidex on 2010-11-06
There is a quirk specifically for your model. You can try it - it certainly won't hurt.
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Any other tweaks you may have made probably should be returned to default just to make certain they are needed. Your alsa version is stock for your distro but can be upgraded to the latest if you care to. I would also recommend purging your pulse configuration again (post #4).

EDIT: I am no expert on the mic lag but if it is a issue with monitoring you may need the realtime kernel??
Try posting in the ubuntu-studio forum: [http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

### Post by DOS Boot on 2010-11-06
> **lidex said:**
> There is a quirk specifically for your model. You can try it - it certainly won't hurt.
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Any other tweaks you may have made probably should be returned to default just to make certain they are needed. Your alsa version is stock for your distro but can be upgraded to the latest if you care to. I would also recommend purging your pulse configuration again (post #4).

EDIT: I am no expert on the mic lag but if it is a issue with monitoring you may need the realtime kernel??
Try posting in the ubuntu-studio forum: [http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

I did another clean install of Mint, ran an update, setup the alsa-base.conf options, setup alsamixer in the terminal, and ran the code:

```
pactl load-module module-loopback latency_msec=1
```That's basically what it takes to get the latency down to a usable level. There is still a very slight amount of latency, but in general mic output works pretty well. 

I've been thinking about trying an external soundcard, do you think that might improve performance?

Anywho, thank you for all your help, Lidex. I really appreciate it.

---

### Post by lidex on 2010-11-06
Everything I've read about pulseaudio states that it does not add any latency so I find it odd that loading that module has such an effect. It must be making up for an alsa issue. With your current setup, post the output of these commands please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
I also wonder if the tsched option would help:
[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

---

### Post by DOS Boot on 2010-11-06
> **lidex said:**
> Everything I've read about pulseaudio states that it does not add any latency so I find it odd that loading that module has such an effect. It must be making up for an alsa issue. With your current setup, post the output of these commands please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

``````
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```I also wonder if the tsched option would help:
[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

I've sent you the outputs for the "dmidecode" and "dmesg" commands in a private message.

I'm not quite sure how to get the "tsched" option to work. Should it be loaded with the alsa-sink module like this:

```
pactl load-module module-alsa-sink tsched=0
```

---

### Post by lidex on 2010-11-06
> **DOS Boot said:**
> I've sent you the outputs for the "dmidecode" and "dmesg" commands in a private message.

I'm not quite sure how to get the "tsched" option to work. Should it be loaded with the alsa-sink module like this:

```
pactl load-module module-alsa-sink tsched=0
```

If you were manually loading it, but I'm pretty sure that it's loaded at start up. That would mean editing "/etc/pulse/default.pa"

---

### Post by DOS Boot on 2010-11-06
> **lidex said:**
> If you were manually loading it, but I'm pretty sure that it's loaded at start up. That would mean editing "/etc/pulse/default.pa"

I found the alsa-sink module in the /etc/pulse/default.pa file but it was commented out with a "#". Should I remove the comment?

---

### Post by lidex on 2010-11-06
> **DOS Boot said:**
> I found the alsa-sink module in the /etc/pulse/default.pa file but it was commented out with a "#". Should I remove the comment?
So maybe it's not loaded at start up. Out of my depth here but it shouldn't hurt to try. I noted there are three other modules that take that option.

---

### Post by DOS Boot on 2010-11-06
> **lidex said:**
> So maybe it's not loaded at start up. Out of my depth here but it shouldn't hurt to try. I noted there are three other modules that take that option.

I removed the comment and added "tsched=0" to the alsa-sink module but that didn't seem to affect the latency too much.

---

