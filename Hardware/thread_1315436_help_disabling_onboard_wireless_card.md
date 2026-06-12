---
title: "help disabling onboard wireless card"
date: 2009-11-05
forum: Hardware
---

### Post by DataSpy on 2009-11-05
I recently bought a new external wireless card so that I could get extended range for wifi with my laptop.  Even though when I click on the network icon on the top right and I can see both network cards, it seems to favor my onboard card.  I was wondering if there was a way I can disable my onboard card and only have my external wifi card remain active?

I don't know if you need this but the output of iwconfig is:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Zen Master"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:9B:6E:0C   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=90/100  Signal level:-48 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Zen Master"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:9B:6E:0C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=16/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

You can see how wlan0 and wlan1 both say they're connected to "Zen Master" my wireless network.  The one I would like to exclusively use is wlan0.

Any help is greatly appreciated, thanks in advance!!!

---

### Post by sergio jose dias on 2009-11-05
Go to link: 
[http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html](http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html)
And try the solution.

---

