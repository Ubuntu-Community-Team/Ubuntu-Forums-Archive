---
title: "Logitech G9 Mouse Led (Useful feature)"
date: 2011-08-15
forum: Hardware
---

### Post by Mr.Anarchy on 2011-08-15
Hello fellow forum readers,

I've been looking for a practical use for Logitech G9 mouse LED and considering Logitech isn't going to release any software for it I've written a little script to monitor your system load with it.

I've used the following program (also included in the zip) and I am NOT the author of the original software so no credits for me there:

[http://als.regnet.cz/logitech-g9-linux-led-color.html](http://als.regnet.cz/logitech-g9-linux-led-color.html)

What the script does is monitor your system load en change the LED color accordingly. The following is the script (also included in the zip file):

```

#!/bin/bash
#
# Creator:	Mr.Anarchy
# Version:	2.0
# Doel:		Logitech G9 Load Monitoring
#
# Script author notes:
# This is a script wrapped around a program I found on the net, it can be found here:
#   - http://als.regnet.cz/logitech-g9-linux-led-color.html
# I did not write the original program and all credits go the original writer, If you like it
# you could let him know ofcourse.
#
# I did however write this (very tiny) script to do something usefull with the G9 mouse led.
# Monitor you system, explanation:
#
# The led color will change by five minute load average (checked every 1 second):
# Black/off 0.* - Green 1.* - Blue 2.* - Orange 3.* - Red 4.* and over.
#
# Use, adapt and spread as you see fit (No selling the sctipt for money though!)!

# Working directory
wd="/home/<username>/logitech9colors" # Where the script and program reside on you system change "<username>".
# The actual program
chcolor="./g9led"

# Some nifty colors for the 'wow' factor...
black="000000"
green="00FF00"
blue="000099"
orange="FF9900"
red="F70000"

cd $wd

while true
do
  # Grab the 5 min average load as a single digit.
  cload=`uptime | awk -F " " '{ print $8 }' | sed 's/\(.*\)./\1/' | awk -F "." '{print $1}'`
  # Based on load give a nifty color to your mouse. 
  case $cload in
   0)
     $chcolor $black 
    ;;
   1)
     $chcolor $green
    ;;
   2)
     $chcolor $blue
    ;;
   3)
     $chcolor $orange
    ;;
   *)
     $chcolor $red
    ;;
  esac
  # Wait one second before restarting the sequence.
  sleep 1
done

```

The script will need to be editted to your working directory and can only be run as root. If you have any questions, let me know!

EDIT: I've added the script to /etc/rc.local (start up) with the following line (without quotes): "sh /home/<username>/logitech9colors/load_monitor.sh &"

---

### Post by Gen2ly on 2011-12-19
Pretty nice Mr. Anarchy.  I wrote one that changes the color ever so minutes.  I can be found here:

[http://linuxtidbits.wordpress.com/2010/01/08/logitech-g9x-laser-mouse/](http://linuxtidbits.wordpress.com/2010/01/08/logitech-g9x-laser-mouse/)

Putting:

```
"nohup bash /home/<username>/pathtoscripts/g9led-random-color &> /dev/null &"
```

should load in on boot.

---

