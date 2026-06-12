---
title: "Automatically setting a USB headset as default when plugging it in?"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by stee on 2007-05-22
I've got a USB Headset and an internal soundcard. Whenever I plug in the USB headset, I use **asoundconf set-default-card 1** to set the headset as the default soundcard. I set it back to the internal (0) when I unplug. Now my question is this; is it possible to write a script that automatically does this for me - i.e. detects that the headset is connected and changes the default card to it? Or is there perhaps another way to achieve the same?

I hope you understand what I'm asking, and that this is the right subforum.

EDIT: I taught myself bash scripting and wrote the following daemon. Now I have to find out how to load it automatically.

```
#! /bin/bash

defcard=0

while [ "true" ]
do
        # If the internal card is default, check if the USB card is found
        # and if it is, set it to the new default
        if [ "$defcard" -eq 0 ]
        then
                if [ `aplay -l | grep USB | wc -l` -gt 0 ]
                then
                        echo "USB soundcard was found"
                        echo "Setting default soundcard to USB"
                        asoundconf set-default-card 1
                        defcard=1
                fi
        # If the USB card is default, check if the USB card is found
        # and if it isn't, set the internal to the new default
        elif [ "$defcard" -eq 1 ]
        then
                if [ `aplay -l | grep USB | wc -l` -eq 0 ]
                then
                        echo "USB soundcard was not found"
                        echo "Setting default soundcard to internal"
                        asoundconf set-default-card 0
                        defcard=0
                fi
        fi
        sleep 1
done

```

---

