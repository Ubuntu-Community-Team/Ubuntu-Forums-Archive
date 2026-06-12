---
title: "Disable ATI card on Intel/ATI hybrid setup?"
date: 2014-07-14
forum: Hardware
---

### Post by Feby_Philip_Abraham on 2014-07-14
Hi.

My ATI GPU quit working one fine day. I have a dual boot (Win7+Ubuntu) setup. I am able to disable the ATI GPU in Windows from the Device Manager and I've installed the Intel HD 3000 drivers from Leshcat.

Is there any similar way to get ubuntu 14.04 running on the Intel GPU alone with the ATI card disabled. I use Windows most of the time (work), but I'm not a total newbie to Ubuntu. So if someone could guide me on how this can be done, I would be thankful.

Feby

---

### Post by QIII on 2014-07-14
Hello!

It might be easier to find a setting in your BIOS to do that.  Where that is is anyone's guess since we don't know what motherboard you have.

Do you still have your motherboard documentation?

Cheers!

---

### Post by Feby_Philip_Abraham on 2014-07-14
QIII, I've a HP dv6 notebook. I can't disable the ATI GPU (6770m) from the BIOS. All I can do is select dynamic GPU switching or Fixed GPU mode. I have selected the Fixed GPU mode. When the the ATI GPU was in proper working condition, I could switch between the two from the Catalyst window. But now can't install the ATI Catalyst drivers as there is some problem with the ATI card.

So my only option, I believe, is to explicitly disable the ATI GPU from within the OS. Can it be done (even if a bit difficult) from within ubuntu?

Feby

---

### Post by SeijiSensei on 2014-07-14
I recall that the only way to make my ATI/Intel hybrid see the ATI card was to use "Fixed Mode" in the BIOS.  Have you tried changing it back to the other setting?  

Another possibility might be futzing with the files in /etc/modprobe.d/ to blacklist the ATI driver(s) and just use Intel.  I've not done this myself, but maybe this will give you something to go on.

My ATI/Intel hybrid with the proprietary fglrx driver has a corresponding /etc/modprobe.d/fglrx file that looks like this:
```

blacklist radeon
alias fglrx fglrx_updates
alias radeon off
alias lbm-radeon off

```
Notice how it blacklists the open-source ATI driver module, called "radeon" here, so that the fglrx proprietary driver will be used instead.  I'd try deleting this file (should you have one), then create a new one called /etc/modprobe.d/noati.conf and add these lines:
```

blacklist radeon
blacklist fglrx
alias radeon off
alias ibm-radeon off
alias fglrx off

```
That should prohibit the two ATI drivers from loading.  Reboot after this and see if it helps.

You need to do all these functions as root with sudo.

---

### Post by Feby_Philip_Abraham on 2014-07-15
Thanks buddy!! Worked like a charm. Running on Intel Sandybridge.

Cheers.

PS: I guess you have mistyped ```
alias lbm-radeon off
``` as ```
alias ibm-radeon off
```

---

