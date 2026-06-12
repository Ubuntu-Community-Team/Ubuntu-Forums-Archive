---
title: "ATI HD series fan speed control script"
date: 2010-07-22
forum: Hardware
---

### Post by taqkavar on 2010-07-22
Hello, I had this problem with my Radeon 5870 always overheating whenever I load up a game or do anything demanding on the card on Ubuntu and Windows. For windows I was able to find a program from MSI that dynamically controls the fanspeed to keep the card cool, for Ubuntu I wrote this short script which has worked fine for me. I didn't have time to write anything proper, so don't laugh... if the temp goes above 99 it messes up, so beware.

save the following to a file named ATI.py:
```

import os
import time

minTemp = 45.00
maxTemp = 50.00
minSpeed = 15
maxSpeed = 100
updateInterval = 4
fanSpeed = 25

while True:
    
    f = os.popen('aticonfig --od-gettemperature | grep "Sensor 0" | cut -c43-47')
    currentTemp = eval(str(f.readlines())[2:7])
    
    if currentTemp > maxTemp:
        if fanSpeed < maxSpeed:
            fanSpeed = fanSpeed + 1
    if currentTemp < minTemp:
        if fanSpeed > minSpeed:
            fanSpeed = fanSpeed - 1

    os.system('aticonfig --pplib-cmd "set fanspeed 0 ' + str(fanSpeed) + '"')

    print fanSpeed
    print currentTemp
    time.sleep(updateInterval)
```

then add it to your startup programs:

```
python ATI.py
```

also if you use conky you can add this to your .conkyrc to see the temp:

```
${voffset 4}${font Liberation Sans:style=Bold:size=8}${execi 30 aticonfig --od-gettemperature | grep 'Sensor 0' | cut -c43-49}
```


Almost forgot, I thing you need to have the proprietary ATI drivers installed for "aticonfig" not sure thought.

---

