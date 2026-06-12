---
title: "Realtime Wi-Fi strength/noise-meter"
date: 2008-11-17
forum: Hardware
---

### Post by daller on 2008-11-17
Hi there,

I'm setting up a network between an apartment on the second floor, and an apartment on the ground floor. I didn't think this would cause any problems - but it does!

Unfortunately I'm not able to use cables in this setup! And I can't mount the antennas outside, since I'm not allowed to mount anything on the outside of the building.

I have set up 2 directional antennas pointing at each other (not perfectly, yet) - But the signal is horrible.

Is there a tool in linux to measure the strength of a not yet connected network, in order to align the antennas?

Thank you in advance!

---

### Post by olejorgen on 2008-11-17
Not sure if this is the best solution, but this is what I used when I was hunting for open networks in my flat.
```

# general:
sudo watch -n <delay between updates> iwlist <wireless interface> scan
# on my system:
sudo watch -n 1 iwlist wlan0 scan

```

EDIT: Just found out: you can filter the result by essid like this:
```

iwlist scan wlan0 essid <essid>

```

---

### Post by daller on 2008-11-17
Wow, iwlist seems effective! :)

It seems that iwlist doesn't respect the essid setting, though:

```
watch -n 1 'sudo iwlist wlan0 scan essid jazzen'
```

Note that I had to write the device before 'scan' for some odd reason.

That command outputs this: (among other)

```

          Cell 02 - Address: 00:17:9A:58:DC:2F
                    ESSID:"Ropemaster"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/100  Signal level:-75 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000018e4afd179
                    Extra: Last beacon: 1420ms ago

```

And that essid has nothing to do with 'jazzen' - which is the essid I'm interested in.

Any ideas?

UPDATE:

I fixed it ad-hoc, though it's not that nice:

> watch -n 1 'sudo iwlist wlan1 scan | grep -B 1 -A 15 "jazzen"'

But the response is not that good:

> Quality=45/100  Signal level:-86 dBm

I've moved the antenna 20 meters - still on the ground-floor, so that it's directly below the apartment, and it increased the quality dramatically, but I still can't connect:

> Quality=88/100  Signal level:-45 dBm  Noise level=-127 dBm

What is the Signal level and Noise level readings? - and what should I be aiming at?

---

