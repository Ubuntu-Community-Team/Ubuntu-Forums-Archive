---
title: "Low Graphics Mode error when logging out"
date: 2014-04-27
forum: Hardware
---

### Post by cranerja on 2014-04-27
I can boot fine and login fine, but when I log out I get this error (in title). My card is GTX 770 and I'm using the nvidia-331-updates from the repos. Also, I'm on 14.04. The only changes I've made in xorg.conf have been: 
```
**Option "ModeValidation" "AllowNon60hzmodesDFPModes,  NoEDIDDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoDFPNativeResolutionCheck,  NoMaxSizeCheck, NoMaxPClkCheck, AllowNonEdidModes, NoEdidMaxPClkCheck"**
```
 in the device section due to my monitor not having the correct edid. Any ideas?

---

### Post by cranerja on 2014-05-01
I've found a solution in a really old thread. The drivers weren't reloading during the restart of x. I fixed it with this command:
```
sudo nvidia-smi -pm 1
```

---

