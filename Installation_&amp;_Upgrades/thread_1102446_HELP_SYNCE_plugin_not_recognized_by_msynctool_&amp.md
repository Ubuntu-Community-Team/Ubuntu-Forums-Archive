---
title: "HELP: SYNCE plugin not recognized by msynctool &amp; multisync"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by awechris on 2009-03-21
Hello & thanks for your time on reading / helping me solve this issue:

1) Everything was working fine (had synce-opensync-plugin & evo2 plugin working perfectly fine thru usb cable and bluetooth using msynctool and multisync) until python packages updated in the main repositories and broke the dependencies. I played around with reinstalling the pluging and the dependencies in order to get the combination of synce and evo2 plugin to exchange data.

2) My evo2-sync plugin works fine and it's traced with msynctool --listplugins. But --listplugins does not trace the synce-opensync-plugin which is essential for syncing WM6.1 devices. I have synce-multisync-plugin 0.9.0-4.1 universe & opensync-plugin-synce 0.13-0ubuntu0~ppa~intrepid1 universe packages installed from Synaptic (universe).

My question is : Why is the msynctool unaware of the synce plugin existance ? What do i have to do ?

a)I'm using the Ubuntu Jaunty 9.04.
b)My 'Python-rra', 'python-rapi2' & 'python-rtfcomp' are stuck to 0.11.1-1ubuntu1 instead of the latest version which is 0.13-0ubuntu0~ppa~inrepid1 because if i try to upgrade to 0.13 version it comes up with: 
python-rra:  Depends: python (<2.6) but 2.6.1-0ubuntu3 is to be installed.

I'll provide any additional info on request.

---

### Post by Zubrania on 2009-05-08
> **awechris said:**
> Hello & thanks for your time on reading / helping me solve this issue:

1) Everything was working fine (had synce-opensync-plugin & evo2 plugin working perfectly fine thru usb cable and bluetooth using msynctool and multisync) until python packages updated in the main repositories and broke the dependencies. I played around with reinstalling the pluging and the dependencies in order to get the combination of synce and evo2 plugin to exchange data.

2) My evo2-sync plugin works fine and it's traced with msynctool --listplugins. But --listplugins does not trace the synce-opensync-plugin which is essential for syncing WM6.1 devices. I have synce-multisync-plugin 0.9.0-4.1 universe & opensync-plugin-synce 0.13-0ubuntu0~ppa~intrepid1 universe packages installed from Synaptic (universe).

My question is : Why is the msynctool unaware of the synce plugin existance ? What do i have to do ?

a)I'm using the Ubuntu Jaunty 9.04.
b)My 'Python-rra', 'python-rapi2' & 'python-rtfcomp' are stuck to 0.11.1-1ubuntu1 instead of the latest version which is 0.13-0ubuntu0~ppa~inrepid1 because if i try to upgrade to 0.13 version it comes up with: 
python-rra:  Depends: python (<2.6) but 2.6.1-0ubuntu3 is to be installed.

I'll provide any additional info on request.

I have the same problem. Have you found any solution ?

---

