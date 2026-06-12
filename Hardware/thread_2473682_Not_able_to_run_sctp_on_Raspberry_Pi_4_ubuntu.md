---
title: "Not able to run sctp on Raspberry Pi 4 ubuntu"
date: 2022-04-10
forum: Hardware
---

### Post by coinoperated on 2022-04-10
I've been unable to get sctp connections established on the latest version of ubuntu desktop (21.10 RPI/400).  I've tried all the web recommendations i can find but nothing seem to work. 

The sctp module doesn't appear to be available modprobe as it is complaining that it can't be found.
When I grep /lib/modules/ on the Pi4 i only get alias entries for ip6t_sctp & ipt_sctp where i find an number of other sctp alias on my ubuntu pc. 

I am able to establish sctp connections on my ubuntu pc and have used the lksctp-tools without issue there as well -- no joy with the Raspberry ubuntu disto and i haven't found a way to extend the distro from what is provided using the Pi Imager or identify what if anything needs to be added to the kernel.

I have found that the Raspberry Pi OS Full bullseye distro is able to support sctp after loading the libsctp-dev & lksctp-tools without a hitch -- however i would prefer to use ubuntu if possible.
 
Any help is much appreciated.

---

