---
title: "tv tuner help please!"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by metuwi on 2006-09-01
I have a tv card with chip saa7133, thus the saa7134 driver is needed. 

To determine the tuner number, I tried this script: 
```

#/bin/sh 
MAXTUNER=70 
i=0 
while [ $i -lt $MAXTUNER ]; 
do 
           rmmod tuner saa7134 
                       modprobe saa7134 card=2 tuner=$i 
                       echo "Actual tuner is:" $i 
                       sleep 1 
                       tvtime 
         i=$(($i+1)) 
done

```


And I get a picture when tuner=4. However it stays on one station no matter what I do (and I have tried everything I could think of); changing the channel has no effect at tuner=4. 

In the gentoo wiki it says the correct parameters for my card is card=2 tuner=2, but I get nothing with that. 

The card is working fine -- tested it in windows. 
Any help? 

(also according to [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134), tuner=4 is "NoTuner," which is... weird?)

---

