---
title: "Continuous Log Entries"
date: 2008-10-11
forum: Hardware
---

### Post by shutslar on 2008-10-11
I am running Hardy 32bit.  I have a Canon MP130 printer connected via USB.  I get a continuous flow of log entries the entire time I have the printer plugged into the USB port.  As soon as I unplug it, the messages stop.  Here is a copy of the messages from /var/logs/messages:

```

[ 1215.400392] sd 11:0:0:0: [sdc] Unit Not Ready
[ 1215.400395] sd 11:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 1215.400398] sd 11:0:0:0: [sdc] Add. Sense: No additional sense information
[ 1216.175629] sd 11:0:0:0: [sdc] READ CAPACITY failed
[ 1216.175633] sd 11:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1216.175636] sd 11:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 1216.175638] sd 11:0:0:0: [sdc] Add. Sense: No additional sense information
[ 1216.436102] sd 11:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 1216.699123] sd 11:0:0:0: ioctl_internal_command return code = 8000002
[ 1216.699127]    : Sense Key : No Sense [current] 
[ 1216.699129]    : Add. Sense: No additional sense information

```

My 1st guess is the memory card readers are causing this because I don't have any memory cards to put into the slots.  I don't know for sure though.

Any suggestions on how I might keep my working printer connected without logging a continuous flow of messages?

Best Regards

---

