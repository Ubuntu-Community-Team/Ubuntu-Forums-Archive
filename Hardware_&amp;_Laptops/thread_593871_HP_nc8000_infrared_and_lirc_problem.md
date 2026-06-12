---
title: "HP nc8000 infrared and lirc problem"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by gillis on 2007-10-27
Hello.

i have a nc8000 and installed ubuntu on it. runs very well.
the only thing is that i spend already two days to get lirc working.
i followed all kind of tutorials, it just dont work. i dont know what to do anymore.
i can start lircd, but when i test it with IRW  nothing happens (it wont hang as it should be)
i am wondering if my infrared port is working. 
Someone know where i can see if it is working??
other people with nc6000 or 8000's??

btw this is my lirc hardware.conf


[php]
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SONY_RM-831"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="default"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
</php>


thanks

---

