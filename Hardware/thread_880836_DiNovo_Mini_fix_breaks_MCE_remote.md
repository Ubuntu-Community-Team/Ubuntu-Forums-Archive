---
title: "DiNovo Mini fix breaks MCE remote"
date: 2008-08-05
forum: Hardware
---

### Post by phunqe on 2008-08-05
Hi,

I have managed to get the trackpad working on a Logitech DiNovi Mini by using the fixes posted in [http://ubuntuforums.org/showthread.php?t=727505&highlight=dinovo+mini](http://ubuntuforums.org/showthread.php?t=727505&highlight=dinovo+mini)

However, doing the modprobe options changes seems to break my MCE remote. Before the changes, my remote works perfectly and all button presses are registered when I test it with irw.
After applying the fix it's dead. Nothing even registers in the irw application.

The answer is most certainly in the tweak that you do to the modprobe option, however I know too little about those to be able to see what might be the issue.

Any ideas?

Thanks.

---

### Post by teaker1s on 2008-11-01
remove 
> options usbhid quirks=0x046d:0xc71f:0x00080000
from /etc/modprobe.d/options,
 Then look at my reply [here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5741842")

example of my 

# HID daemon
HIDD_ENABLED=1
sudo hciconfig hci0 down
sudo hciconfig hci0 up
HIDD_OPTIONS="-i hci0 --connect 046d:c71f --connect 046d:c71e --connect  046d:0b07

---

