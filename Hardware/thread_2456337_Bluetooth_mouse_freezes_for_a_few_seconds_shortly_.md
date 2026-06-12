---
title: "Bluetooth mouse freezes for a few seconds shortly after connecting but then works"
date: 2021-01-09
forum: Hardware
---

### Post by andylatham82 on 2021-01-09
I have a bluethooth mouse (Logitech Pebble) which works fine on my laptop with Ubuntu, except for one small issue. When I first boot up or wake the computer, the mouse works fine for maybe 30 seconds to a minute, but then freezes for a few seconds before then working again. After that it works perfectly until the next reboot or until the next time I wake the laptop from being suspended. I have searched around but can't find an answer to why this is happening.

A couple of bits of info that might be useful:

1. It's a dual boot machine with Ubuntu 20.10 and Windows 10, with the mouse paired in both (I had to find out the keys).

2. I had an old bluetooth mouse which did not have this problem. It was a cheap mouse and broke quickly.

Does anyone have any suggestions? It's not a huge deal, it's just irritating!

---

### Post by #&amp;thj^% on 2021-01-09
MUTUAL INTERFERENCE: 
A FHSS receiver cannot decode a DSSS transmission and vice versa; a transmission using one spread spectrum technique is nothing but interference to a receiver using another spread spectrum technique. 

In the case of Bluetooth and Wi-Fi, interference between two co-located or nearbydevices will occur approximately one quarter of the time, such aswhen a Bluetooth device hops to a frequency occupied by an active Wi-Fi channel.
> 
 22MHz wide Wi-Fi channel= collisions approximately 28%of the time
79 available Bluetooth frequencies
If this interference is sufficiently strong such that the Bluetooth or Wi-Fi receiver cannot decode a transmission, the transmission must be resent, resulting in a decrease in performance. 
Under the most extreme of circumstances, the Bluetooth or Wi-Fi device may completely lose connectivity.
Plus your using 20.10 which I assume is kernel 5.8.....had nothing but trouble with this kernel, with my tweaks.
I'm hesitant in offering any changes for you.
If you was using 20.04 LTS with kernel 5.4 default i'd have a suggestion or two.
I'm wishing good luck in your endeavor though.

---

### Post by andylatham82 on 2021-01-10
I don't know if it makes a difference, but I'm on kernal 5.10. I upgraded to try to solve a problem I was having with my laptop touchpad (sadly it didn't solve the problem).

---

