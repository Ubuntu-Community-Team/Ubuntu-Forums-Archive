---
title: "Audio device switch"
date: 2010-01-02
forum: Hardware
---

### Post by tsvetan on 2010-01-02
I have a system with a graphic card with HDMI output and I'm often using my TV to watch movies and listen music though HDMI. Unfortunately Ubuntu doesn't switch the sound output automatically upon HDMI device connection and I had to do it manually everytime. After some research and experiments I made a little bash script that switches the output audio devices. 

The script assumes that **pulseaudio** is used and was tested with Karmic. It is pretty generic and actually has nothing to do with any HDMI device – it simply iterates over the sound devices and switches the output to the next one.

Here is how to make it work:
[LIST=1]
[*]# [FONT="Courier New"]sudo gedit /usr/local/bin/audio-device-switch.sh[/FONT]
[*]Copy and paste the source code bellow in the gedit editor
[*]Save it and close gedit
[*]# [FONT="Courier New"]sudo chmod 755 /usr/local/bin/audio-device-switch.sh[/FONT]
[*]System -> Preferences -> Keyboard Shortcuts
[*]Press „Add“ and enter „Switch between audio devices“ as name and [FONT="Courier New"]audio-device-switch.sh[/FONT] as command and press „Apply“.
[*]Select the newly added shortcut row and click on the „shortcut“ column. Choose a shortcut combination – e.g. Win + F12.
[*]That's all - now you can plug in your plug in your HDMI device and switch the audio output by pressing the chosen shortcut combination.
[/LIST]
```
#!/bin/bash

declare -i sinks_count=`pacmd list-sinks | grep -c index:[[:space:]][[:digit:]]`
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i major_sink_index=$sinks_count-1
declare -i next_sink_index=0

if [ $active_sink_index -ne $major_sink_index ] ; then
	next_sink_index=active_sink_index+1
fi

#change the default sink
pacmd "set-default-sink ${next_sink_index}"

#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
	pacmd "move-sink-input $app $next_sink_index"
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
	if [ $next_sink_index -eq $ndx ] ; then
		notify-send -i notification-audio-volume-high "Sound output switched to" "$line"
		exit
	fi
	ndx+=1
done;

```

Hope that this is helpful.

---

### Post by MarcusAntonius on 2010-01-10
Hi,
That was exactly what I was looking for. I now have a desktop-starter linked to the script, and I can move audio with just one click. That was exactly what I was looking for :-)

---

### Post by nutsy.ben on 2010-06-19
Simply brillant .... 
I was looking for this for a while !!!



THANK YOU

---

### Post by fbscarel on 2010-07-28
I, too, was looking all over the place for some kind of script/command that would accomplish this simple task... thanks a lot, it works like a charm!

---

### Post by worldofbill on 2010-08-19
Fantastic!  Thanks for this script.  It works great to switch audio outputs on-the-fly for a Logitech USB headset for Skype.

---

### Post by yanber on 2010-08-27
I modified tsvetan's script slightly to allow for an (odd ?) behaviour on my machine where sinks often do not get assigned consecutive index numbers (e.g. I would get indexes 2 and 4 rather than 0 and 1, as the script expected).

I'll include it here in case someone else has the same issue.

```

#!/bin/bash

declare -i sinks=(`pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sinks_count=${#sinks
[*]}
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_sink_index=${sinks[0]}

#find the next sink (not always the next index number)
declare -i ord=0
while [ $ord -lt $sinks_count ];
do
    echo ${sinks[$ord]}
    if [ ${sinks[$ord]} -gt $active_sink_index ] ; then
        next_sink_index=${sinks[$ord]}
        break
    fi
    let ord++
done

#change the default sink
pacmd "set-default-sink ${next_sink_index}"

#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $(( $ord % $sinks_count )) -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high --hint=string:x-canonical-private-synchronous: "Sound output switched to" "$line"
        exit
    fi
    let ndx++
done;

```Credit to tsvetan for creating the initial script and posting instructions on how to easily switch audio device! Thank you!

---

### Post by daniferi on 2010-09-11
Nice script, it is very useful to change my audio output when I want watch film in TV and use 2nd sound card for this :)

---

### Post by dark-triad on 2010-09-15
Thanks, works perfect for me too, but does anyone know how to alter the script  to change the sound input too? would be nice if it could change the output and input all in one go for use with my bluetooth headset and skype.

---

### Post by Takky on 2010-12-10
I've found the script very Useful and I used it with "xrandr" to enable/disable TV output.
But now it's stopped working!

Default sink changes, but inputs created after the switch aren't affected by this change!
Someone else got this behaviour? Any solution? I haven't found any command to refresh or something similar.

The Cool thing is it seems to play something on one sink while playing something else on other sink... :P

However, Thanks a lot for the script..

---

### Post by jambel on 2010-12-18
can anyone help me with my problem here?
[http://ubuntuforums.org/showthread.php?p=10244899#post10244899](http://ubuntuforums.org/showthread.php?p=10244899#post10244899)
 I want to change only the sound input

Thanks

---

### Post by helmerj on 2011-01-18
Thanks!

Exactly what I was looking for. Works like charm!

Cheers J.

---

### Post by pickle79 on 2011-01-19
Finding and implementing this script made my night.

---

### Post by bcg30506 on 2011-03-03
Awesome!  Thank you.  Note:  I did have to install libnotify-bin in order for the popup notification to work.

---

### Post by Rimus on 2011-03-19
The script works just fine by itself, but the keyboard shortcut won't function in my 10.10, it only says "launching the application attached to the keyboard shortcut failed". Anyone have ideas for a workaround?

For the time being I put a launcher to Gnome panel and it works from there.

---

### Post by icouldmakeyousmile on 2011-03-29
Installing libnotify-bin and getting the popup was the icing on the cake (I was testing it by looking at the radio buttons in Preferences > Sound jump up and down).

Rimus: It worked for me in 10.10. Have you done the very stupidly obvious thing of checking the path in the shortcut, and file permissions?

---

### Post by Chodid on 2011-04-08
Great script, that is what I was looking for, thanks a lot! But is there any way to implement an OSD notification quickly showing the name of the device which just got activated? Best regards.

---

### Post by icouldmakeyousmile on 2011-04-09
> **Chodid said:**
> Great script, that is what I was looking for, thanks a lot! But is there any way to implement an OSD notification quickly showing the name of the device which just got activated? Best regards.

Have you installed libnotify-bin?

---

### Post by kortas on 2011-04-14
My script was not working, because I was using only
pacmd "set-default-sink ..."

this is what I was missing:
pacmd "move-sink-input $app $next_sink_index"

thanks A LOT!

---

### Post by kiaran on 2011-05-22
Works great!

Ubuntu developers, please do this automatically when an HDMI cable is plugged/unplugged!! PLEASE!

---

### Post by TIIUNDER on 2011-06-03
Really great, thx for this script. Also works on Natty and with my Bluetooth-Headset ;-)

PS: This would be awesome for the sound indicator :rolleyes:

---

### Post by PsyWolf on 2011-07-28
Awesome script!  This really should be installed as a default hotkey (and happen automatically when you plug in usb or hdmi cables)

---

### Post by definetti on 2011-09-10
Nice script, but is there a way to modify it so that I can switch not only the output of current application, but the output device -so to say- system-wide(that is the option in "output" menu of gnome-volume-control)?

---

### Post by pierocol on 2011-10-29
Fantastic. I am ver grateful. I have been looking for this for quite a while,

---

### Post by Mars11 on 2011-12-29
This is awesome, but when I use it in GNOME-Shell the notifications just build up. I commented out the line with "notify-send", but I kinda liked the notification, does anyone know how to fix the build up?

---

### Post by Rubadubdub on 2012-01-27
If you are using Gnome Shell instead of Unity you can install the extension below. You'll then be able to switch from the volume short-cut in the top panel. [https://extensions.gnome.org/extension/142/output-device-chooser-on-volume-menu/](https://extensions.gnome.org/extension/142/output-device-chooser-on-volume-menu/)

---

### Post by dar270785 on 2012-01-31
I have a script to change audio devices automatically if any one is interested.
```

mkdir ~/bin
cd bin
gedit audio_switch.sh

```Copy the following into the text editor:
```

#!/bin/bash

status="$(cat /sys/class/drm/card0-HDMI-A-1/status)"

if [ "${status}" = disconnected ]
then
pactl set-card-profile 0 output:analog-stereo+input:analog-stereo
notify-send -i notification-audio-volume-high "Sound output switched to Laptop Speakers"
exit
elif [ "${status}" = connected ]
then
pactl set-card-profile 0 output:hdmi-stereo+input:analog-stereo
notify-send -i notification-audio-volume-high "Sound output switched to HDMI"
exit
fi

```To get the settings name of your card profile you will have to run
```

pacmd list-cards

```If you scroll up to where there are a lot of 'output:'. These are the profile names. The zero is the card number this should be whatever it says for alsa.card.

Save and close

Open up terminal and type:
```

sudo gedit /etc/udev/rules.d/100-hdmi.rules

```In the text editor copy:
```

USER="$(who | grep :0\) | cut -f 1 -d ' ')"
KERNEL=="card0", ACTION=="change", RUN+="/home/$USER/bin/audio_switch.sh"

```Save and close

Finally in terminal type:
sudo chmod +x ~/bin/audio_switch.sh

With a bit more tweaking you can get this to change setting for your HDMI. i.e. resolution, position, primary display etc.

In my script I use it to also change the resolution of my HDTV to its maximum when it is plugged in, as it is not correctly detected.

Enjoy!

---

### Post by nandok_it on 2012-02-06
> **dar270785 said:**
> I have a script to change audio devices automatically if any one is interested.


Great job!

\\:D/

---

### Post by max3903 on 2012-05-29
@dar270785
Great script. I used it to switch between my USB audio device and laptop speakers when I plug/unplug the laptop from its dock station. Very convenient when using a softphone like [http://www.sflphone.org](http://www.sflphone.org).

---

### Post by psmbfuer on 2012-09-22
For anyone on Ubuntu 12.04 and wishing to add a shortcut key to switch between two audio cards/profiles, I hope this helps. I give credit to the first and last code post as these were my starting point. I only post this as the original post (from 2010) does not appear to work on Ubuntu 12.04. That said, I'm no expert and I might have mis-interpretted the results of my testing or just overlooked something. Either way, the following does work for me.

This script uses the "pacmd list-cards" command to first get a listing of the available sound cards/profile present in my system. It again uses the "pacmd set-card-profile" command to set the desired profile. 

The pacmd output that you see below represents a piece of the output from "pacmd list-cards". Since there are so many, and since the names do not exactly match to the names seen in the GUI "Sound" tool available in Ubuntu, I ran the above command twice, while manually changing from my "HDMI/ DisplayPort 2" to "Analog Output" via  the "Sound" application.

The key line below is the "active profile:" line where you see "<output:analog-stereo+input:analog-stereo>". 

Using this technique, and instead of writing a more complex script, I simply use these two as logic flags in the script below. Change the script to use your profiles and you should be good to go, at least if you are toggling between two profiles.

[SIZE="2"][COLOR="Sienna"]#	profiles:
output:analog-stereo: Analog Stereo Output (priority 6000)
[COLOR="DarkSlateBlue"]output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)[/COLOR]
output:analog-surround-40: Analog Surround 4.0 Output (priority 700)
output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (priority 760)
output:analog-surround-41: Analog Surround 4.1 Output (priority 800)
output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (priority 860)
output:analog-surround-50: Analog Surround 5.0 Output (priority 700)
output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (priority 760)
output:analog-surround-51: Analog Surround 5.1 Output (priority 800)
output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (priority 860)
output:analog-surround-71: Analog Surround 7.1 Output (priority 700)
output:analog-surround-71+input:analog-stereo: Analog Surround 7.1 Output + Analog Stereo Input (priority 760)
output:iec958-stereo: Digital Stereo (IEC958) Output (priority 5500)
output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (priority 5560)
output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5460)
output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 300)
output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 360)
output:hdmi-stereo-extra1: Digital Stereo (HDMI) Output (priority 5200)
[COLOR="DarkSlateBlue"]output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI) [/COLOR]Output + Analog Stereo Input (priority 5260)
input:analog-stereo: Analog Stereo Input (priority 60)
off: Off (priority 0)
[COLOR="DarkSlateBlue"]active profile: <output:analog-stereo+input:analog-stereo>
active profile: <output:hdmi-stereo-extra1+input:analog-stereo> (I added this one to this listing, but it is from the second[/COLOR]
                                                                       (run of pacmd when the HDMI card was active.)
	sinks:
		alsa_output.pci-0000_00_1b.0.analog-stereo/#10: Built-in Audio Analog Stereo

[/COLOR][/SIZE]Of the available "cards" / "profiles" listed, I only use two, the HDMI and Anolog cards. So all I want to do is toggle from one to the other.

```
#!/bin/bash

# My debug "echo" statements are still embedded, but feel fee to remove.

hdmiprof="<output:hdmi-stereo-extra1+input:analog-stereo>"   # to ease my parsing below, I keep the < and > on the string here.
analogprof="<output:analog-stereo+input:analog-stereo>"      # to ease my parsing below, I keep the < and > on the string here.

currentprof=$(pacmd list-cards | grep "active profile: " | cut -d" " -f3) # Query pacmd to see what profile is active
echo "$currentprof"

if [ "$currentprof" = "$analogprof" ] ; then
  echo about to switch to HDMI Audio
  pacmd set-card-profile 0 output:hdmi-stereo-extra1+input:analog-stereo
else
  echo about to swith to Analog Audio
  pacmd set-card-profile 0 output:analog-stereo+input:analog-stereo
fi

```

Save the script whereever you save them (hopefully somewhere in your PATH, chmod +x, add a shortcut key via the "Keyboard" application and it should be working.

---

### Post by rainwalker on 2012-09-24
> **psmbfuer said:**
> For anyone on Ubuntu 12.04 and wishing to add a shortcut key to switch between two audio cards/profiles, I hope this helps. I give credit to the first and last code post as these were my starting point. I only post this as the original post (from 2010) does not appear to work on Ubuntu 12.04. That said, I'm no expert and I might have mis-interpretted the results of my testing or just overlooked something. Either way, the following does work for me.

This script uses the "pacmd list-cards" command to first get a listing of the available sound cards/profile present in my system. It again uses the "pacmd set-card-profile" command to set the desired profile. 

-- snip --

```
#!/bin/bash

# My debug "echo" statements are still embedded, but feel fee to remove.

hdmiprof="<output:hdmi-stereo-extra1+input:analog-stereo>"   # to ease my parsing below, I keep the < and > on the string here.
analogprof="<output:analog-stereo+input:analog-stereo>"      # to ease my parsing below, I keep the < and > on the string here.

currentprof=$(pacmd list-cards | grep "active profile: " | cut -d" " -f3) # Query pacmd to see what profile is active
echo "$currentprof"

if [ "$currentprof" = "$analogprof" ] ; then
  echo about to switch to HDMI Audio
  pacmd set-card-profile 0 output:hdmi-stereo-extra1+input:analog-stereo
else
  echo about to swith to Analog Audio
  pacmd set-card-profile 0 output:analog-stereo+input:analog-stereo
fi

```

Save the script whereever you save them (hopefully somewhere in your PATH, chmod +x, add a shortcut key via the "Keyboard" application and it should be working.

Do you have any idea how to modify this for not only setting the different profiles, but setting them on different cards? I only have one sound card, but ```
pactl list cards
``` lists HDMI as card 0 and the regular laptop speakers as card 1.

---

### Post by psmbfuer on 2012-09-27
I'm new to all of this as well, and only came up with my solution through testing, trial, and error (and of course the starting point that the previous posts provided). I have looked into your question a bit, but I only have one card, so I cannot test through this as I did for my issue.

That said, I started up a pacmd session, than enter "help" (without the quotes). From this you will see an entire list of what is possible and I wonder whether the profile names are identical between your cards, and if not whether you could still use the profile switch that I used above. If not, there is a "set-card-profile" command that would be my next area of research.

Sorry I'm not able to be more helpful.

---

### Post by alesr on 2013-04-23
Here is the code for switching audio INPUTS.

```
#!/bin/bash
## This code is for switching audio inputs.

declare -i sources=(`pacmd list-sources | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sources_count=${#sources
[*]}
declare -i active_source_index=`pacmd list-sources | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_source_index=${sources[0]}


#find the next source (not always the next index number)
declare -i ord=0
while [ $ord -lt $sources_count ];
do
    echo ${sources[$ord]}
    if [ ${sources[$ord]} -gt $active_source_index ] ; then
        next_source_index=${sources[$ord]}
        break
    fi
    let ord++
done


#change the default source
pacmd "set-default-source ${next_source_index}"


#move all outputs to the new source
for app in $(pacmd list-source-outputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-source-output $app $next_source_index"
done


#display notification
declare -i ndx=0
pacmd list-sources | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $(( $ord % $sources_count )) -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high --hint=string:x-canonical-private-synchronous: "Sound input switched to" "$line"
        exit
    fi
    let ndx++
done;
```

Basically it's the same code as from the original, just using *pacmd list-sources (for input devices) instead of pacmd list-sinks (for output devices).*

---

### Post by rainwalker on 2013-04-23
This is my output from ```
pacmd list-cards
```

```
2 card(s) available.
    index: 0
	name: <alsa_card.pci-0000_01_05.1>
	driver: <module-alsa-card.c>
	owner module: 4
	properties:
		alsa.card = "1"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xd0410000 irq 19"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:01:05.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "RS880 HDMI Audio [Radeon HD 4200 Series]"
		device.string = "1"
		device.description = "RS880 HDMI Audio [Radeon HD 4200 Series]"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5400)
		off: Off (priority 0)
	active profile: <output:hdmi-stereo>
	sinks:
		alsa_output.pci-0000_01_05.1.hdmi-stereo/#0: RS880 HDMI Audio [Radeon HD 4200 Series] Digital Stereo (HDMI)
	sources:
		alsa_output.pci-0000_01_05.1.hdmi-stereo.monitor/#0: Monitor of RS880 HDMI Audio [Radeon HD 4200 Series] Digital Stereo (HDMI)
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, available: unknown)
			properties:
				
    index: 1
	name: <alsa_card.pci-0000_00_14.2>
	driver: <module-alsa-card.c>
	owner module: 5
	properties:
		alsa.card = "0"
		alsa.card_name = "HDA ATI SB"
		alsa.long_card_name = "HDA ATI SB at 0xd0a00000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "SBx00 Azalia (Intel HDA)"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	profiles:
		output:analog-stereo: Analog Stereo Output (priority 6000)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060)
		input:analog-stereo: Analog Stereo Input (priority 60)
		off: Off (priority 0)
	active profile: <output:analog-stereo+input:analog-stereo>
	sinks:
		alsa_output.pci-0000_00_14.2.analog-stereo/#1: Built-in Audio Analog Stereo
	sources:
		alsa_output.pci-0000_00_14.2.analog-stereo.monitor/#1: Monitor of Built-in Audio Analog Stereo
		alsa_input.pci-0000_00_14.2.analog-stereo/#2: Built-in Audio Analog Stereo
	ports:
		analog-output-speaker: Speakers (priority 10000, available: unknown)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, available: no)
			properties:
				
		analog-input-microphone: Microphone (priority 8700, available: no)
			properties:

```

I can't quite figure out how to work with this. The card at index 0 is my ATI graphics card (ugh), which is apparently responsible for sound via HDMI out. The card at index 1 is my actual sound card.

---

### Post by futureboy on 2013-09-08
I found this thread very helpful, but for my needs, I just set up this simple script that switches between my monitor+desktop audio and HDMI tv+HDMI audio.
Since I mostly use my TV with XBMC, I included that in the script, and mapped [Super+Enter (keypad)] to run it.
Now everything switches to my TV when I want to watch something, and switches back when I exit XBMC.

```
#!/bin/bash

if xrandr | grep -q ', current 1440'

	then
		xrandr --output HDMI-0 --mode 1920x1080 --output DVI-0 --off
		xbmc
		pacmd set-default-sink 0

	while pgrep -u root xbmc > /dev/null; do sleep 1; done
		xrandr --output DVI-0 --mode 1440x900 --output HDMI-0 --off
		pacmd set-default-sink 1

	else
		xrandr --output DVI-0 --mode 1440x900 --output HDMI-0 --off
		pacmd set-default-sink 1

fi
```

Now if I could only get Igor Cesko's COM receiver to work with lirc...

---

