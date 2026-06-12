---
title: "Audio device switch with selected devices"
date: 2015-05-14
forum: Hardware
---

### Post by jeff-artik on 2015-05-14
Good evening,

I'm trying to get a little script that allow me to switch between 2 audio devices. I found [a script]("http://ubuntuforums.org/showthread.php?t=1370383") that switch between all devices, but I have at least 7, and I only use 2.
I actually got 2 scripts that I wrote with what I found on forums, one to switch to my 1st device, the second to switch to my 2nd device. Here are the scripts:

1st device :

```
#!/bin/bash

#change the default sink
pacmd "set-default-sink 2"


#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
pacmd "move-sink-input $app 2"
done
```

2nd device :

```
#!/bin/bash

#change the default sink
pacmd "set-default-sink 3"


#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
pacmd "move-sink-input $app 3"
done
```

And I apply these scripts to 2 shortcuts.

Unfortunatly I'm not good enough in bash, and what i would like is a script that switch between both. If one is active, so the script switch to the other and vice e versa. A little notification to tell me wich device is loaded could be really great.
Thank for help !

---

### Post by jeff-artik on 2015-05-15
A friend of mine helped me. thx !

```
#!/bin/bash

SINK_INDEX1=2
SINK_INDEX2=3
ACTIVE_SINK=$(pacmd list-sinks | grep '* index:' | grep -o '[0-9]*')


if [ "$ACTIVE_SINK" = $SINK_INDEX1 ] ; then
    pacmd set-default-sink $SINK_INDEX2
    pacmd list-sink-inputs | awk '/index:/{print $2}' | xargs -r -I{} pacmd move-sink-input {} $SINK_INDEX2
    notify-send "PC Audio"
else
    pacmd set-default-sink $SINK_INDEX1
    pacmd list-sink-inputs | awk '/index:/{print $2}' | xargs -r -I{} pacmd move-sink-input {} $SINK_INDEX1
	notify-send "NuForce USB Audio"
fi


done;
```

---

