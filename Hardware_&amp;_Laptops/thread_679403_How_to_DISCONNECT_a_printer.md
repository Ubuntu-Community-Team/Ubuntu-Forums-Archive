---
title: "How to ?DISCONNECT? a printer"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by shutslar on 2008-01-26
I have a dual boot (Ubuntu 7.10/Win XP).  I have a locally installed Cannon MP130 that my wife uses on the Win XP side.  I had tried to install some drivers to use it on the Ubuntu side of the world without any luck (I hate Cannon).  I have removed the printer from cups.  But while it is connected to the USB port, my syslog is constantly getting the errors below.  The only way I have found to stop the constant barrage of errors (and you can really tell a difference in response time when it's connected vs. disconnected) is to physically unplug the printer from the USB port.  Is there any way that I can keep the printer plugged in but have Ubuntu ignore it completely and stop trying to use the memory card reader?

Thanks,

> Jan 26 07:36:09 localhost kernel: [34514.916000] sd 3:0:0:0: [sdc] Unit Not Ready
Jan 26 07:36:09 localhost kernel: [34514.916000] sd 3:0:0:0: [sdc] Sense Key : No Sense [current] 
Jan 26 07:36:09 localhost kernel: [34514.916000] sd 3:0:0:0: [sdc] Add. Sense: No additional sense information
Jan 26 07:36:10 localhost kernel: [34515.688000] sd 3:0:0:0: [sdc] READ CAPACITY failed
Jan 26 07:36:10 localhost kernel: [34515.688000] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan 26 07:36:10 localhost kernel: [34515.688000] sd 3:0:0:0: [sdc] Sense Key : No Sense [current] 
Jan 26 07:36:10 localhost kernel: [34515.688000] sd 3:0:0:0: [sdc] Add. Sense: No additional sense information
Jan 26 07:36:11 localhost kernel: [34515.944000] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
Jan 26 07:36:11 localhost kernel: [34515.944000] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Jan 26 07:36:11 localhost kernel: [34516.188000] sd 3:0:0:0: ioctl_internal_command return code = 8000002
Jan 26 07:36:11 localhost kernel: [34516.188000]    : Sense Key : No Sense [current] 
Jan 26 07:36:11 localhost kernel: [34516.188000]    : Add. Sense: No additional sense information

---

