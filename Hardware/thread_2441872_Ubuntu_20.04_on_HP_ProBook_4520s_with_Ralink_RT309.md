---
title: "Ubuntu 20.04 on HP ProBook 4520s with Ralink RT3090 wireless (802.11n) card"
date: 2020-04-27
forum: Hardware
---

### Post by 1n6w3 on 2020-04-27
Howdy,

Just wanted to post my findings after spending some time to resolve an issue.

Was running Ubuntu 18.04 on HP ProBook 4520s with Ralink RT3090 wireless card without problems - connected to TV, used mostly to stream Netflix and YouTube.

Decided to install Ubuntu 20.04 and it went well, except has issues with poor wireless performance. High latency/dropped packets when pinging the box. There were repeated messages in /var/log/syslog:

```
wpa_supplicant[123]: wlo1: CTRL-EVENT-BEACON-LOSS
```

After trying a lot of things, this post finally put me on the right path:

[https://ubuntuforums.org/showthread.php?t=2387392&p=13749530#post13749530](https://ubuntuforums.org/showthread.php?t=2387392&p=13749530#post13749530)

More specifically this command solved my problem:

```
[COLOR=#000000][FONT=&amp]sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf[/FONT][/COLOR]
```


I first used this command to confirm power management was in fact "on" for the card:

```
iwconfig wlo1
```


I used this command to update the setting to confirm that power management was the culprit:

```
sudo iwconfig wlo1 power off
```

I saw an immediate improvement. I then updated the [COLOR=#000000][FONT=&amp]default-wifi-powersave-on.conf[/FONT][/COLOR] file as per above to make it persistent.


I still see the odd "CTRL-EVENT-BEACON-LOSS" message in the syslog file, but no longer see any dropped packets and latency is good.

Hope this helps someone else. :)

---

