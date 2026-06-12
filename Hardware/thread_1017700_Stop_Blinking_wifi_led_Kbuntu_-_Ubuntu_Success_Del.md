---
title: "Stop Blinking wifi led Kbuntu - Ubuntu Success Dell D830"
date: 2008-12-21
forum: Hardware
---

### Post by firefox66 on 2008-12-21
Hi.
I try to config my wifi as guided on forum and i success to stop led blinking while while wifi led on as normal.so what i have done:

1- Make a script iwl-no-blink.sh and save it on desktop:

```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
        for dir in /sys/class/leds/iwl-phy*X; do
                echo none > $dir/trigger
        done
fi

```

2- Change line folowing like this : 
            echo none > $dir/trigger
        As like this:
            echo none > /sys/class/leds/iwl-phy0\:radio/trigger
            echo none > /sys/class/leds/iwl-phy0\:assoc/trigger
   so as final is:

```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
        for dir in /sys/class/leds/iwl-phy*X; do
              echo none > /sys/class/leds/iwl-phy0\:radio/trigger
              echo none > /sys/class/leds/iwl-phy0\:assoc/trigger
        done
fi

```

3- Copy it to system folder : /etc/network/if-up.d/
        Name it : iwl-no-blink
        Set executable for file : 
               chmod +x /etc/network/if-up.d/iwl-no-blink
               or
               chmod 755 iwl-no-blink

4- Try to open this cmd in terminal:
echo none > /sys/class/leds/iwl-phy0\:radio/trigger
echo none > /sys/class/leds/iwl-phy0\:assoc/trigger

5- Restart - Done

Hopy it helpfull.
thanks,Firefox66.:popcorn:

---

### Post by squaregoldfish on 2008-12-22
Thanks so much for this. My blinky network light has been driving me mad ](*,)

Steve.

---

### Post by joshuajtl on 2009-02-08
When I try to run:

echo none > $dir/trigger

I get: 

bash: /trigger: Permission denied

then I try:

sudo echo none > $dir/trigger

and I still get: 

bash: /trigger: Permission denied

So what's going on here? How can I get this to work.
Thanks

---

### Post by squaregoldfish on 2009-02-10
The first code chunk is a bit of a red herring. If you read the instructions carefully, you'll see that it's actually the second bit of code you need.

Steve.

---

### Post by framling on 2009-10-22
That for loop doesn't really do much with the full path inside it. 

Also, it's a double :: in the path on mine, so:

echo none >  /sys/class/leds/iwl-phy0\:\:radio/trigger 
echo none >  /sys/class/leds/iwl-phy0\:\:assoc/trigger 


thank you, this has been driving me nuts. I feel at peace now.

---

### Post by arslano on 2009-10-25
hello

i've tried this solution but nothing changed

what can the problem be?

thanks

i always get permission denied when i try with terminal

---

### Post by squaregoldfish on 2009-11-08
This issue is more actively being discussed in another thread:

[http://ubuntuforums.org/showthread.php?t=966511](http://ubuntuforums.org/showthread.php?t=966511)

---

