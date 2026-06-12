---
title: "Can't detect headphone removal in 19.04"
date: 2019-05-09
forum: Hardware
---

### Post by spiff666 on 2019-05-09
Hi. After someone kept 'borrowing' headphones from my desk at work, I wrote a short script to detect the removal of the device using **evtest** and send me a notification & a webcam photo of the perp using a **curl** call to Pushover.net. This worked great under 18.10 but since I upgraded to 19.04 I ca't seem to detect the headphones being removed.

*sudo evtest* lists the front headphone jack as being: 

/dev/input/event13:	HDA Intel PCH Front Headphone


I then use the following code in my script

[I]device='/dev/input/event13'
evtest --grab "$device" | while read line; do
    echo $line
    if [[ $line == *"value 0"* ]]; then

     #notification code goes here

    fi
[/I]

If I just do *evtest /dev/input/event13* at the command prompt, then I can see that nothing happens when I remove or insert the headphone jack. The status value just stays at '1' (device inserted)

Is this a problem with the new kernel in 19.04 or have I missed something obvious? Thanks.

---

