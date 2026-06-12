---
title: "acpi lid button script help"
date: 2010-08-08
forum: Hardware
---

### Post by otkaz on 2010-08-08
I have a hp elitebook 8530p running lucid with the Ati fglrx driver.
lspci output
```

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

```
I'm trying to change the lid button script so it will turn my display off, but not the HDMI connector output. Right now if I'm connected to a monitor or TV with HDMI and close the lid it puts both displays to sleep. I tried modifying the lid.sh to use radeontool to turn the light off, but it does not effect the behavior. While running the script I get this in my syslog.
```

logger[2975]: LID state closed
kernel: [  306.547838] radeontool:2977 conflicting memory types 80000000-90000000 uncached-minus<->write-combining
kernel: [  306.547841] reserve_memtype failed 0x80000000-0x90000000, track uncached-minus, req uncached-minus
logger[2985]: LID state open
[  307.248705] radeontool:2986 conflicting memory types 80000000-90000000 uncached-minus<->write-combining
kernel: [  307.248708] reserve_memtype failed 0x80000000-0x90000000, track uncached-minus, req uncached-minus
kernel: [  307.251576] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)

```
The script I'm using I wrote for an older laptop that was running jaunty with the open source driver and it worked great. Thanks for any input you can get or direction you can point me in.

---

