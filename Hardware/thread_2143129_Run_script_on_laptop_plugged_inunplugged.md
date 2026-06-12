---
title: "Run script on laptop plugged in/unplugged"
date: 2013-05-07
forum: Hardware
---

### Post by JaySeeJC on 2013-05-07
There are a couple programs that I would like to start in the background (mainly virtual machines) when my laptop is plugged in, and then paused when the laptop is unplugged/suspended/hibernated. Is it possible to run scripts that react to these power configuration changes?

---

### Post by JaySeeJC on 2013-05-24
OK for anyone out there who's actually come across this thread hoping for some actual answers, here's what I've come up with. It's only been tested on my laptop, but I see no reason why it wouldn't work with others as well.

```
#!/bin/bash

# The threshold in percentage of when to consider the battery charged.
charged="90"
# The time in seconds between checks
sleeptime="30"


function loop(){


        while true
        do
                state=$(acpi -b|sed 's/Battery 0: Unknown, //g'|sed 's/%//g') # I know it's not pretty, but it works
                if [ "$state" -gt "$charged" ]
                then
                        turnon
                else
                        turnoff
                fi
                sleep $sleeptime
        done
}


function turnon(){
        # Turn stuff on here
}


function turnoff(){
        # Turn stuff off here
}


loop &



```

What the above script does is checks to see if the battery is below a certain percentage, in this case 90%, and turns things off when below that threshold and turns stuff back on when above the threshold.

---

