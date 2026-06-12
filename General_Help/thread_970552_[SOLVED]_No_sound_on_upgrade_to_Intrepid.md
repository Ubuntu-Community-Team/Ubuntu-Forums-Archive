---
title: "[SOLVED] No sound on upgrade to Intrepid"
date: 2008-11-04
forum: General Help
---

### Post by the bogs on 2008-11-04
I have just upgraded to Intrepid and on re-starting I get no sound and the loudspeaker icon has a red cross next to it.

When I try to open Volume Control I get the below error...

"No volume control GStreamer plugins and/or devices found."

if i try to open 'preferences' i get nothing.

If I go to 'Preference's', 'sound' and tryn to change any of the options there i get another error message.

How do i fix this?

---

### Post by the bogs on 2008-11-06
help!

---

### Post by Yellow Pasque on 2008-11-06
What kind of sound card do you have and do you have a driver loaded?
```
sudo lshw -C multimedia
```

---

### Post by the bogs on 2008-11-06
*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by tamias on 2008-11-06
I have the same problem on a Dell Inspiron 6000. I've found this potential solution, but I'm at work, so can't test at the moment: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Could you try it and let me know if it fixes your problem?

Mark

---

### Post by the bogs on 2008-11-06
Thanks tamias,


find /lib/modules/`uname -r` | grep snd

returned no results, so despite the page referring to upgrading to Heron

sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic

after reboot - all good.

---

### Post by tamias on 2008-11-06
That's good to know -- I'll try it when I'm home tonight, as well.

Interestingly, my wireless driver was also removed during the upgrade (ipw2200). It seems that, for some reason, the upgrader missed out some of the various modules packages.

I'll file a bug later.

---

### Post by tamias on 2008-11-06
Actually the problem in both cases (no sound and no wireless) was that linux-generic was not installed (or was removed) by the upgrade tool. This bug is already being tracked at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/268721](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/268721)

So, to summarise, anyone with sound or networking problems due to missing drivers after a Hardy->Intrepid install, make sure that linux-generic is installed!

---

