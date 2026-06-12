---
title: "Acer Aspire 7720 Subwoofer"
date: 2008-05-24
forum: Hardware
---

### Post by ebirkenes on 2008-05-24
Hi

I have an Acer Aspire 7720 and have been trying to get the subwoofer to work with 8.04, with no luck so far. The other two speakers works just fine.

Has anyone been able to do this? Or does anyone have any good ideas?


-E

---

### Post by xanthe on 2008-06-22
I have exactly the same problem. The sound would be great if only the subwoofer worked- as it is I'm stuck without any bass.

---

### Post by koleoptera on 2008-07-29
Hi I also have an aspire 7720 G and can't get the subwoofer working. I ve heard other people having the same problem with this laptop in any version of ubuntu. Is there any solution out there?

---

### Post by willywortel on 2008-08-21
Same problem here. Sound is ok but with the woofer it would be better.

---

### Post by xanthe on 2008-10-31
Has anyone had a chance to test this model on intrepid? I've had no luck with suggested fixes for similar laptop models.

---

### Post by BB88 on 2008-11-21
The problem is the same in Interpid, I have no sub woofer. Having to use my Sennheiser Headset for bass :D

I was using an Acer Aspire 5920 before and the sub woofer worked fine, but why not in the Acer Aspire 7720?

---

### Post by Mokou on 2009-01-31
Same problem , i have an acer 7520g ,the sound is fine but no bass.

---

### Post by Daedhel on 2009-03-06
Same problem here. I am not an expert at this, but I believe there should be a bug report on this problem.

Should it be reported to alsa?

Daedhel

---

### Post by WinterWeaver on 2009-03-23
I dont have one of these, but I'm looking to purchase one soon. So I found this thread doing some research.

Have any of you tried messing with the different audio settings?
Check the Audio preferences, an under Channel Mode, enable Surround sound.
There may also be other sliders associated with the bass.

ta,

WW

---

### Post by Daedhel on 2009-04-21
The problem has disapeared for me since I use the kernel 2.6.29-1 (I am using archlinux) I guess you just have to wait for ubuntu to releases that kernel.

Daedhel

---

### Post by hcooh on 2009-08-23
> **Daedhel said:**
> The problem has disapeared for me since I use the kernel 2.6.29-1 (I am using archlinux) I guess you just have to wait for ubuntu to releases that kernel.

Daedhel

Do you mean that you have a working subwoofer on Archlinux ?
Because I am on arclinux with the 2.26.30 kernel.
I installed ALSA but the subwoofer is not working.
Do you have anything to configure ?

---

### Post by sanso on 2010-07-21
> **xanthe said:**
> Has anyone had a chance to test this model on intrepid? I've had no luck with suggested fixes for similar laptop models.

I'm having the same issue on lucid. Has this been solved anywhere? -- please?

---

### Post by pavelf on 2012-07-15
It seems the thread is dead but there is a workaround :)

Download HDA-Analyzer
```
wget http://www.alsa-project.org/hda-analyzer.py
```

Change it to executable:
```
chmod +x ./hda-analyzer.py
```
then run
```
sudo ./hda-analyzer.py
```

Now select PIN 0x16 and check "OUT" checkbox (under the Widget Control) then uncheck "Mute" checkbox.

Voila. Now subwoofer works. You may close HDA Analyzer & answer No when it ask to revert changes.

---

### Post by Menno124875 on 2012-09-24
ThanKs Pavelf, 

Your workaround using hda-analyzer did the trick for me!
:KS:KS:KS:KS:KS

---

### Post by pavelf on 2012-09-28
> **Menno124875 said:**
> ThanKs Pavelf, 

Your workaround using hda-analyzer did the trick for me!
:KS:KS:KS:KS:KS

This tool provides a feature to save your actions to the py script.
So this is a script in attached file to enable subwoofer on our model.

Save it to some location, say to the ~/bin/subwoofer_fix and change it to executable (chmod +x ~/bin/subwoofer_fix)
Now edit /etc/rc.local (kdesudo kate /etc/rc.local in my kubuntu, smth like gksudo gedit /etc/rc.local in gnome ununtu)
Add a line before "exit 0" to make it look like:
```

/home/YOUR_USERNAME/bin/subwoofer_fix

exit 0

```Now 7720 subwoofer will turn on on every boot. Another problem is wakeups. Subwoofer is turned off when laptop goes sleep. So we need to run this script again on wakeups. I created a file /etc/pm/sleep.d/99-custom.sh
```

#!/bin/bash
case "$1" in
    thaw|resume)
        /home/YOUR_USERNAME/bin/subwoofer_fix
        ;;
    *)
        ;;
esac
exit $?

```Do not forget to change it to the executable too. Now the subwoofer should turn on on every wakeup too.

The only issue is when you plug in a headphone, subwoofer won't not turn off and will continue to produce a sound. So you should go to the applet to turn it off manually. I was too lazy to find a hook to this event.

P.S. Ok I'm giving up about attachments so there is the contents of the subwoofer_fix file:
> 
#!/usr/bin/env python

import os
import struct
from fcntl import ioctl

def __ioctl_val(val):
  # workaround for OverFlow bug in python 2.4
  if val & 0x80000000:
    return -((val^0xffffffff)+1)
  return val

IOCTL_INFO = __ioctl_val(0x80dc4801)
IOCTL_PVERSION = __ioctl_val(0x80044810)
IOCTL_VERB_WRITE = __ioctl_val(0xc0084811)

def set(nid, verb, param):
  verb = (nid << 24) | (verb << 8) | param
  res = ioctl(FD, IOCTL_VERB_WRITE, struct.pack('II', verb, 0))  

FD = os.open("/dev/snd/hwC0D0", os.O_RDONLY)
info = struct.pack('Ii64s80si64s', 0, 0, '', '', 0, '')
res = ioctl(FD, IOCTL_INFO, info)
name = struct.unpack('Ii64s80si64s', res)[3]
if not name.startswith('HDA Codec'):
  raise IOError, "unknown HDA hwdep interface"
res = ioctl(FD, IOCTL_PVERSION, struct.pack('I', 0))
version = struct.unpack('I', res)
if version < 0x00010000:    # 1.0.0
  raise IOError, "unknown HDA hwdep version"

# initialization sequence starts here...

set(0x16, 0x300, 0xb000) # 0x1603b000 (SET_AMP_GAIN_MUTE)
set(0x16, 0x707,   0x40) # 0x16070740 (SET_PIN_WIDGET_CONTROL)

os.close(FD)


---

### Post by Gandalf the White on 2012-11-14
Kudos to pavelf. This trick finally solved my Aspire 7720g subwoofer problem!!
:KS:KS:KS:KS:KS

The only annoying thing still, is the fact that plugging in headphones leaves the subwoofer activated. Still, way better than before!

Thanks again. Cheers!!!

---

