---
title: "CPU scaling settings in jaunty"
date: 2009-07-20
forum: Hardware
---

### Post by spidermagicat on 2009-07-20
When I start up my laptop it automatically sets itself to "Perfomance" mode.
This means it uses more power and creates more heat, which means with my model of laptop (HP TX1000) it will break.

I currently set it to "Ondemand". Then I find that the up threshold is at 95% meaning any flash video for example lags as it doesn't go up quick enough.

I therefore run the command "echo 45 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold" to make the cpu scale up in good time.

Is there any way I can change the default settings so I don't have to do this when I start up?

I am starting to find it intolerably irritating and I want to do something about it :-)

---

### Post by GoldenSun on 2009-07-20
Can't you just make a script that runs that command on startup?

---

### Post by spidermagicat on 2009-07-20
I would also need a command to set the CPU to ondemand first, as the file doesn't exist until that is done so I would be willing to try it if someone could help me with that :-)

But I have also found that the second command only works when logged in as root, e.g. "sudo echo 45 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold" does not work.

I am really looking to change the default settings, something which I believe from posts could be done with gconf-editor under apps/gnome-power-manager/cpufreq in earlier versions of ubuntu

---

### Post by nelio2k on 2009-10-21
The "ondemand" script sleeps for 60 seconds, and then activates cpufreq to use the "ondemand" profile.

This script I wrote will be able to activate after ondemand has finished, and lower the threshold.

Use vim and copy an paste the following into the file 
```
/etc/init.d/update_up_threshold
```

```

#!/bin/bash

# This script will update the threshold of the 2 cpu's ondemand to be 55
# This will aid the computer in feeling less sluggish
# requires ondemand to be present
# Author: Neil Huang
# Oct 21, 2009



if [[ ! -e /etc/init.d/ondemand ]];then
   echo "ERROR: ondemand is not found in /etc/init.d/. This script will not run"
   exit 1
fi

case $1 in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/update_up_threshold -- background
        ;;
    background)
      declare -i maxTime
      maxTime=120 # ondemand script sleeps 60, 120 will avoid race condition
      declare -i secCount
      secCount=0

      sleep $maxTime

      cpuFile='/sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold'
      cpu0File='/sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold'

      while (( $secCount < $maxTime ));do
         if [[ -e "$cpu0File" ]];then
            for newCPUFREQ in $cpuFile;do
               [ -f $newCPUFREQ ] || continue
               echo "55" > $newCPUFREQ
            done
            break
         else
            secCount=$(( secCount + 1 ))
            sleep 1
         fi
      done
      ;;
   restart|reload|force-reload)
      echo "Error: argument '$1' not supported" >&2
      exit 3
      ;;
   stop)
      ;;
   *)
      echo "Usage: $0 start|stop" >&2
      exit 3
      ;;
esac

```

Make the file executable
```
sudo chmod a+x /etc/init.d/update_up_threshold
```

Then initialize it by using a tool called *sysv-rc-conf*
```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

and check boxes 2-5 for the line update_up...

Restart, and you should be good to go.

---

### Post by spidermagicat on 2009-10-21
Yes! Thankyou so much this works perfectly :-). I was slowly putting something like this together but couldn't get it to work. Now I'm in a good mood for the whole day, probably even a whole week :-D

---

