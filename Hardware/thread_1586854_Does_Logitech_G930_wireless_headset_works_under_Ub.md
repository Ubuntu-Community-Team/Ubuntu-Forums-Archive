---
title: "Does Logitech G930 wireless headset works under Ubuntu?"
date: 2010-10-02
forum: Hardware
---

### Post by cioma on 2010-10-02
I'm thinking about buying Logitech G930 wireless headset ([http://www.logitech.com/en-us/gaming/headsets/devices/7248](http://www.logitech.com/en-us/gaming/headsets/devices/7248)) and using in under Ubuntu.
Does anyone have it working good?

---

### Post by synthaxx on 2010-10-06
I'm looking for a new headset, and would like to know this as well.

It's a lot of money to spend on a guess.

/edit: just got off the phone with Logitech support, and their official line is "we don't officially support it but it *could* work" so not a big help there.

---

### Post by faceclot on 2010-10-10
I have these headphones and they work!

---

### Post by dext_krk on 2010-10-11
> **faceclot said:**
> I have these headphones and they work!

But is everything working? What about:
- microphone?
- 7.1 sound in movies?

Does it work out of the box, or you had to recompile the kernel? ;)

---

### Post by synthaxx on 2010-10-11
My old headset decided to throw one ear clean off, so i've taken the plunge and just ordered these at a store with good return policies (also not too sure about the size, i have a LARGE head).

Will update when they get here (hopefully tomorrow).

Also, this thread is the first result on a Google search of "Ubuntu G930", so we're kind of obligated to get a full answer in here ;)

---

### Post by faceclot on 2010-10-11
Mic working.  
Side volume roller is working perfectly -- better then windows 7 actually.
Volume is loud enough. Quality is perfect. Side G buttons working good, pause, next and previous, and mute worked good in all the condition I tested them in.
7.1 seems to be working pretty good but I want to run some more tests on actual files 
(I did the Halo 2 YouTube surround sound test ^^)

---

### Post by cioma on 2010-10-12
I'm going to order G930 and I'll also put my feedback here.

---

### Post by faceclot on 2010-10-12
Okay surround sound is running good.
Ran[ this ]("http://www.youtube.com/watch?v=qlwXv9VXY80")and it sounded great.
I am running Ubuntu 10.04. 

Any questions / custom requests?

---

### Post by synthaxx on 2010-10-12
Just got it in, and the good news is: I've got sound!

Here are a couple of the highlights so far.

Good:

-The sound quality is great
-A lot of range
-The earphones shut out sound really well
-The G buttons work, front most goes forward a track, rear goes back one, and the middle pauses.


Not good:

-Can't get the mic working. I'll try and find a windows machine somewhere to test if it works at all. **FIXED!** Turns out i had it muted in alsamixer for some reason...
-The surround button does nothing. I did notice a digital stereo output profile in the sound preferences, so i'll keep expirimenting.
-While there's enough travel to fit my (admittedly gigantic) mellon, the clamping force exerts a vice like grip that is almost headache inducing. Hopefully this will subside when they break in...

/edit: I also recommend [this]("http://ubuntuforums.org/showthread.php?t=1574337") as an addon. Thought it lacked a bit of bass, and the EQ cleared that right up.

---

### Post by synthaxx on 2010-10-16
Update (with a little something extra).

The size issue is pretty much fixed. It's still a little tight, but it's a hell of a lot better than it was.

The surround button is still a dud. I think this is as much a software implementation as anything, so it's bound not to work. I don't really miss it though.

Now however for something that i think is really cool.

I have a NAS, running Ubuntu server 10.04. In the spirit of experimentation i decided to plug in the headset, which worked.

Then i remembered that Ubuntu has pulse audio which can do audio over network. After installing that my NAS reported the headset back to every Ubuntu machine on my network (right in the sound preferences). Giving me whole house audio on every machine! Of course you can also run music on just the server without having to have another computer on.

Haven't figured out how to use the buttons or the volume control through the server yet, but audio and microphone work great.

---

### Post by cioma on 2010-11-15
Finally I got mine and I can confirm that everything works under Ubuntu 10.10 amd64
I haven't tested 7.1 yet, is there any demo available? The Halo 2 demo from YouTube is not really clear.

---

### Post by stevesherrie on 2011-03-31
Alright I've got Ubuntu 10.10 64 bit and the g930, but nothing is working.

I've installed gnome-alsamixer, and made sure nothing was muted, but in the sound dialog under the hardware tab, there is an entry for Logitech G930 Headset that says 'Analog Mono Input', so it looks like it's not picking up the speakers at all.

Audio still plays out of the laptop speakers or the analog headphones if they're plugged in.

Any ideas??

Steve

---

### Post by stevesherrie on 2011-04-01
Very sensual update time.

It works!

The problem I was having was to do with the device being plugged into a USB3.0 port, and activating some bug in the XHCI driver in Ubuntu 10.10.
While plugged into that port it reported only a single profile in the hardware profile of the System->Preferences->Sound dialog, which denoted a single 'Analog Mono Input'.

After plugging it into a USB2.0 all the subsequent profiles were available.

What a waste of a day!

Steve

---

### Post by optics on 2011-04-27
I have gotten the Headset and Mic to work right after plugging it in, but I have not been able to get the G buttons to work, i'm also don't think surround sound is working completely as of now. Im going to try to get these 2 things working hopefully soon.

This is expected but the voice changer doesn't work on Ubuntu although there are several other programs out there that can do this, I'll list what I used when i find something that works well.

---

### Post by optics on 2011-04-27
Ok i got surround sound working, I had Alsa installed and what I had to do was edit what it said to edit for pulse audio at [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
and then it worked after restarting the computer, although im not completely sure why it worked, or if it is working at 7.1 level or just 5.1 as im not completely sure about the 7.1 tests.

---

### Post by timinator94 on 2011-05-01
> **optics said:**
> Ok i got surround sound working, I had Alsa installed and what I had to do was edit what it said to edit for pulse audio at [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)
and then it worked after restarting the computer, although im not completely sure why it worked, or if it is working at 7.1 level or just 5.1 as im not completely sure about the 7.1 tests.
How exactly did you get it working? I did the steps for pulse audio and now my soundcard has the 7.1 option but the headphones dont

---

### Post by optics on 2011-05-01
thats ok the headphones don't actually need the 7.1 option enabled to play 7.1 sound, or at least 5.1 sound (most applications seem to like to output 5.1 easier than 7.1) but just try a 5.1 or 7.1 audio test with digital stereo and that is what worked for me after changing the pulse to allow surround.

edit:
btw don't use youtube for surround sound tests as i'm pretty sure youtube only supports stereo..I used the 5.1 surround test at [http://www.lynnemusic.com/surround.html](http://www.lynnemusic.com/surround.html) if you want to test with that, as its surprisingly hard to find surround sound tests that actually work well.
also make sure to enable 5.1/7.1 in the music player your using it should be under options but if its not you might have to look up how to enable if 5.1 isn't working to make sure its not just the player.

---

### Post by r109chaos on 2011-05-20
My Logitech g930's in uBuntu 11.04 seems to be working fine plug and play. I can't figure out how to test the 7.1.

---

### Post by clobercow on 2011-09-12
I'm on Linux Mint 11 and the audio quality is very bad. Its breaking up quite a bit and actually sounds slow on my G930. Works fine in windows though...

Has anyone been using the Logitech software via Wine?

---

### Post by whinis on 2011-10-04
On 11.10, the programmable buttons now register as keyboard presses instead of separate keys ( used to be prog_01 prog_02 prog_03 ) making it hard to map them to programs like teamspeak.

---

### Post by vilwarin on 2012-01-23
Got myself also one of theses headsets and bilmey they work.
But those scurvy buttons made me marooned. So me decided to share some help and scripts with ya bunch of landlubbers. harrr

[LIST=1]
[*]**xmodmap**
  If the buttons don't register as XF86 keys, you just make 'em with xmodmap. Find out the keycode with **xev** and edit ~/.xmodmaprc to map them to the corresponding XF86 key. If you don't have these, install them with: 
```
sudo apt-get install x11-xserver-utils
```
Now edit ~/.xmodmaprc (create the file if it doesn't exist)
```

keycode 121 = XF86AudioMute
keycode 122 = XF86AudioLowerVolume
keycode 123 = XF86AudioRaiseVolume
keycode 124 = XF86AudioPlay
keycode 125 = XF86AudioPrev
keycode 126 = XF86AudioNext

```

[*]**xbindkeys**
  Now that we got the keys triggering the XF86 keys, we need to decide what to do with them. We can define the triggered action via xbindkeys. 
```
sudo apt-get install xbindkeys
```
The file to edit is ~/.xbindkeysrc.
```

"amixer -q set Master 2- unmute && ~/scripts/pulseaudiomodify.sh decrease"
XF86AudioLowerVolume

"amixer -q set Master 2+ unmute && ~/scripts/pulseaudiomodify.sh increase"
XF86AudioRaiseVolume

"~/scripts/alsa-sound.sh mute && ~/scripts/pulseaudiomodify.sh mute"
XF86AudioMute

"~/scripts/audio_control.sh --play-pause"
XF86AudioPlay

"~/scripts/audio_control.sh --stop"
XF86AudioStop

"~/scripts/audio_control.sh -r"
XF86AudioPrev

"~/scripts/audio_control.sh -f"
XF86AudioNext

```
Alas most commands don't work directly and need a little workaround. So we need some extra scripts to make everything work. Here's an example for these scripts.  Run 
```
mkdir ~/scripts
``` and create them in this folder with your favorite editor.

[*]**pulseaudiomodify.sh**
This script helps us to make the volume wheel also affect pulse. As you can see in the .xbindkeysrc above, in the end it will actually affect both alsa (amixer -q set Master 2- unmute) and pulse (pulseaudiomodify.sh). If you decide on one of those sound system, you won't be needing both.
```
#!/bin/bash
#### Create ~/.pulse/mute if not exists
ls ~/.pulse/mute &> /dev/null
if [[ $? != 0 ]]
then
    echo "false" > ~/.pulse/mute
fi

####Create ~/.pulse/volume if not exists
ls ~/.pulse/volume &> /dev/null
if [[ $? != 0 ]]
then
    echo "65536" > ~/.pulse/volume
fi

CURVOL=`cat ~/.pulse/volume`     #Reads in the current volume
MUTE=`cat ~/.pulse/mute`          #Reads mute state

if [[ $1 == "increase" ]]
then
    CURVOL=$(($CURVOL + 1024)) #3277 is 5% of the total volume, you can change this to suit your needs.
    if [[ $CURVOL -ge 65536 ]]
    then
        CURVOL=65536
    fi
elif [[ $1 == "decrease" ]]
then
    CURVOL=$(($CURVOL - 1024))
    if [[ $CURVOL -le 0 ]]
    then
        CURVOL=0
    fi
elif [[ $1 == "mute" ]]
then
    if [[ $MUTE == "false" ]]
    then
        pactl set-sink-mute 1 1
        echo "true" > ~/.pulse/mute
    exit
    else
        pactl set-sink-mute 1 0
        echo "false" > ~/.pulse/mute
    exit
    fi
fi

pactl set-sink-volume 1 $CURVOL
echo $CURVOL > ~/.pulse/volume # Write the new volume to disk to be read the next time the script is run.
```
Please change this value **1024** in the above script, if you want to change the step size the volume will go up and down.

[*]**alsa-sound.sh**
Muting alsa doesn't work under ubuntu for some time without a little tinkeing. So here's a script to tinker:
```
#!/bin/bash
device="alsa_output.pci-0000_00_14.2.analog-stereo"
case "$1" in
    "up")    # increase volume by 1000
        pacmd dump | awk --non-decimal-data '$1~/set-sink-volume/{if ($2~/'${device}'/) {if ($3+1000 > 65535) {system ("pactl "$1" '${device}' "65535)} else {system ("pactl "$1" '${device}' "$3+1000)}}}'
        ;;
    "down")  # decrease volume by 1000
        pacmd dump | awk --non-decimal-data '$1~/set-sink-volume/{if ($2~/'${device}'/) {if ($3-1000 < 0) {system ("pactl "$1" '${device}' "0)} else {system ("pactl "$1" '${device}' "$3-1000)}}}'
        ;;
    "mute")  # toggle mute
        pacmd dump|awk --non-decimal-data '$1~/set-sink-mute/{if ($2~/'${device}'/) {system ("pactl "$1" '${device}' "($3=="yes"?"no":"yes"))}}'
        ;;
esac
```

[*]**audio_control.sh**
Next we need a way to tell the running media player to pause or play the next/previous song. For that we need another script to a) support more than one player and b) address the correct DBUS
```
#!/bin/bash --login

# Usage
if test $# -lt 1
    then echo "$0 -f/-r/--play-pause/--stop"; exit;
fi

audioplayers=( /usr/bin/amarok /usr/bin/audacious2 )

for i in ${audioplayers|*|}
do
    pid=`pidof $i`
    #set dbus address
    export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$pid/environ | tr '\0' '\n' | grep DBUS | cut -d '=' -f2-`
    if [ "$pid" != "" ]
        then `$i $1`; break;
    fi
done

```
**Note:**Replace audioplayers|*| in the above script with square brackets [ * ] without spaces. I couldn't use square brackets, because they would be rendered as another list item in this post.

Fortunately most media players 
a) use the same command line options for these actions (-f/-r/-t) and 
b) use the DBUS as communication interface.

I tested the script with amarok and audacious2. If you use another player, simply add it to the **audioplayers** array and it should be supported as well.
[/LIST]

Savvy?

---

