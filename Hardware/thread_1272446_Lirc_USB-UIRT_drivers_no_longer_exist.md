---
title: "Lirc USB-UIRT drivers no longer exist?"
date: 2009-09-22
forum: Hardware
---

### Post by markdavidoff on 2009-09-22
Hi all!
I am trying to follow this guide here, but I have ran into a few problems, possibly with the newest version of lirc that ubuntu supports

[https://help.ubuntu.com/community/Lirc_USB-UIRT](https://help.ubuntu.com/community/Lirc_USB-UIRT)

1. The following lines do not exist by default in the hardware.conf:

```
# Arguments which will be used when launching lircd
LIRCD_ARGS=""
```

and

```
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""
```

Is this because the transmitter/sender has its own drivers now, like so: ?

```
TRANSMITTER="USB Transmitter"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

```

so that device, etc will be defined here instead of separate commands?

2. I noticed that the only driver that lircd knows is "default"
if you run this command:
```
lircd --driver=
```

I have been unsuccessful so far in getting the transmitter to work. I assume it is because of 2nd reason, but any help would be great.

EDIT:
I just installed lirc on another computer...and that one has multiple drivers, so what is going on with mine? Is there a way to get them back?
I tried completely removing lirc using synaptic, but that didn't help

---

### Post by markdavidoff on 2009-09-22
I fixed it.

1. I completely removed lirc using synaptic

2. did all the latest updates with sudo apt-get update and sudo apt-get upgrade using the main mirror

3. ran sudo depmod -a

---

