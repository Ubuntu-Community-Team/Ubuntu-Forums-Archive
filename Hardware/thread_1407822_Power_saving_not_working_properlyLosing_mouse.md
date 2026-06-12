---
title: "Power saving not working properly/Losing mouse"
date: 2010-02-15
forum: Hardware
---

### Post by tastech on 2010-02-15
We've got a Gateway 6510gz with Ubuntu 9.10 installed. The problem we're currently experiencing is that it seems to get the power settings confused as to whether it's plugged in or not, and will randomly follow either of the schemes, or so it seems. Due to this we currently have it set to always on regardless and we can't put it into suspension at all because when it resumes we are left with no mouse, just a static cursor on the screen. Any ideas what to check? The only thing I've thought of is looking into updating the bios, but power saving works fine in Windows so I figured it shouldn't be much of an issue. Thanks for the help :p

---

### Post by tastech on 2010-02-17
A bump I feel is in need.

---

### Post by pi/roman on 2010-02-17
I just ran a test to see what happens in suspend:
```
xinput watch-props "SynPS/2 Synaptics TouchPad"
```Here was the output:
> Property 'Device Enabled' changed.
    Device Enabled (92):    0
Property 'Device Enabled' changed.
    Device Enabled (92):    1So it looks like the touchpad is disabled during suspend then re-enabled later but I'm guessing that your touchpad is not getting re-enabled.  So I have a script to toggle the touchpad through synclient in my touchpad guide but it looks like that won't work here because in this case it would involve xinput. So I made a script to toggle it that way which you can use by making an empty file called "syntoggle.sh" on your desktop then copy and paste this in it:
> # toggle synaptic touchpad on/off
# get current state
SYNSTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled | grep -o [10])
# change to other state
if [ $SYNSTATE = 0 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
elif [ $SYNSTATE = 1 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
else
    echo "nogo"
    exit 1
fi
exit 0now right click it and change it to executable on the permissions tab, then move it to /usr/bin:
```
sudo mv ~/Desktop/syntoggle.sh /usr/bin
```Now if your touchpad becomes disabled you should be able to press alt/f2 and type "syntoggle.sh" to re-enable it. You should be able to do the same thing with your mouse substituting it's name from xinput list. I know this is not the perfect solution to your problem but hopefully it will make it a little better.

---

### Post by tastech on 2010-02-18
Thanks friend. I was actually thinking of figuring out a script for this myself, but you've saved me the work :). You seem far more knowledgeable than myself.

---

### Post by pi/roman on 2010-02-18
Well I don't know much about linux, but I'm always learning and I had problems with my touchpad when I started so I've been focusing a lot on that. I've updated my script too because I didn't account for the numbers in parenthesis before so this one should work better:
> # toggle synaptic touchpad on/off
# get current state
SYNSTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled |  grep -Eo '.$')
# change to other state
if [ $SYNSTATE = 0 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
elif [ $SYNSTATE = 1 ]; then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
else
    echo "i give up"
    exit 1
fi
exit 0

---

