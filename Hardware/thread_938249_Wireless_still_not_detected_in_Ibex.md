---
title: "Wireless still not detected in Ibex"
date: 2008-10-04
forum: Hardware
---

### Post by carlolovearianne on 2008-10-04
I partitioned my laptop drive and installed Intrepid Ibex Beta. Sadly, my AR5007 (AR2425 chips) wireless still doesn't work out of the box. 

I managed to activate it by doing this:


In the Terminal:


```
sudo apt-get install build-essential
```


Download the tar from:


[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)


Move the tar to the Home folder and then extract it there


Open the Terminal:

```
cd madwifi-hal-0.10.5.6-r3861-20080903
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```


Worked for me. I hope this can help anybody out there with the same chip.

---

