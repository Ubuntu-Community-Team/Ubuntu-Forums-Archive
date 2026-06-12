---
title: "Lenovo T530 Mute Button Mutes but doesn't un-mute"
date: 2013-03-06
forum: Hardware
---

### Post by itrogers on 2013-03-06
Hey All-

I have a Thinkpad T530. I noticed today that when I press the mute button that comes on the machine, everything mutes properly. When I press it again, to unmute, ubuntu doesn't recognize it and the machine stays muted. The light on the button turns off indicating that it is unmuted but the volume control in ubuntu indicates that it is still muted. Therefore I still need to uncheck the mute box in the volume control. Any ideas on how to make the mute button actually unmute? Thanks in advanced.

---

### Post by ajgreeny on 2013-03-06
I think this may be a Lubuntu or LXDE problem as I sometimes run Lubuntu on my desktop, which has a Trust Multimedia keyboard, and I have exactly the same problem as you describe, with the mute key just working in the one direction; to mute.  In Xubuntu and Ubuntu 12.04 it works without problem to both mute and unmute, so it is not a keyboard problem, hence my suspicion about Lubuntu/LXDE.

---

### Post by Mr. Shannon on 2013-03-06
I don't know about LXDE but in XFCE this can be fixed with:
```
xfconf-query -c xfce4-mixer -p /active-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
xfconf-query -c xfce4-mixer -p /sound-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
```
So finding the equivalent settings in LXDE might work.  If your LXDE environment is using the xfce-mixer then the above commands should actually solve the problem.

Essentially the sound mixer was not configured for Pulse Audio by default on my previous XFCE installation.

---

### Post by itrogers on 2013-03-07
> **Mr. Shannon said:**
> I don't know about LXDE but in XFCE this can be fixed with:
```
xfconf-query -c xfce4-mixer -p /active-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
xfconf-query -c xfce4-mixer -p /sound-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
```
So finding the equivalent settings in LXDE might work.  If your LXDE environment is using the xfce-mixer then the above commands should actually solve the problem.

Essentially the sound mixer was not configured for Pulse Audio by default on my previous XFCE installation.

It definitely has something to do with Pulse and Alsa, however, the code provided did not work for my particular setup. It seems that Alsa is unmuting but Pulse is not. I found [another thread]("http://askubuntu.com/questions/118675/mute-key-mutes-alsa-and-pulseaudio-but-unmutes-only-alsa") with the same issues but it seems that those don't work for me either. I'll keep looking around and will post back once I find a solution.

---

### Post by gordintoronto on 2013-03-07
It might be helpful if you said exactly what version of Ubuntu you are using.

---

### Post by itrogers on 2013-03-09
> **gordintoronto said:**
> It might be helpful if you said exactly what version of Ubuntu you are using.

Im running Lubuntu 12.10

---

### Post by protongradient on 2013-03-25
Hi!
I'm running in a HP mini 110-3000 with Ubuntu 12.04 + Ldxe and I'm having the same problem than you. 
Did you finally find a solution?
Thanks!

---

### Post by blackowaya on 2013-06-17
I found a workaround to this issue. I'm using Lubuntu 12.10.

1) Create an empty file (for example, mute.sh) wherever you want (example /home/user/scripts/).
2) Paste the following:

#!/bin/bash

SINK_NAME=$(pacmd dump | grep -m 1 -o "alsa.*stereo")
MUTE_STATE=`pacmd dump | grep -P "^set-sink-mute $SINK_NAME\s+" | perl -p -i -e 's/.+\s(yes|no)$/$1/'`
    if [ $MUTE_STATE = no ]
    then
            pactl set-sink-mute $SINK_NAME 1
    elif [ $MUTE_STATE = yes ]
    then
        pactl set-sink-mute $SINK_NAME 0
    fi

3) Save the file (in this example mute.sh) and give the proper execution permissions.
4) Open the openbox configuration file (by example /home/user/.config/openbox/lubuntu-rc.xml)
5) Search for the following lines:
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer -q sset Master toggle</command>
6) Change the text between <command> and </command> labels for the full path of the script. In this example, these lines are changed as follows:
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>/home/user/scripts/mute.sh</command>
7) Save the changes in configuration file and restart LXDE (or the PC).

---

### Post by kcn_viper on 2013-07-13
I have HP 430 laptop with Ubuntu 12.04 and LXDE. I solved it by simply replacing "amixer -q sset master toggle" with a shell script toggle_mute.sh in ~/.config/openbox/lxde-rc.xml. The shell script had the contents "amixer -q sset master toggle". I am not sure why you have to wrap in a shell script like this. This was not a problem with other display managers.

---

### Post by LycoLoco on 2013-12-15
> **Mr. Shannon said:**
> I don't know about LXDE but in XFCE this can be fixed with:
```
xfconf-query -c xfce4-mixer -p /active-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
xfconf-query -c xfce4-mixer -p /sound-card -s PlaybackBuiltinAudioAnalogStereoPulseAudioMixer
```
So finding the equivalent settings in LXDE might work.  If your LXDE environment is using the xfce-mixer then the above commands should actually solve the problem.

Essentially the sound mixer was not configured for Pulse Audio by default on my previous XFCE installation.

I'd just like to confirm that this works with LXDE using xfce4-mixer even on Fedora 19 on a Lenovo T430s as well as the OS and laptop described in the original post. Here's what xconf-query showed me initially, for future reference:

$ xfconf-query -c xfce4-mixer -p /active-card
HDAIntelPCHAlsamixer
$ xfconf-query -c xfce4-mixer -p /sound-card
HDAIntelPCHAlsamixer

Thank you so much!

---

