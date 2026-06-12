---
title: "USB not recognized... provided &quot;dmsg | tail&quot;"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by Scott S. on 2007-12-23
Any help is appreciated, thanks....

So I was reading in the forums about similar problems but my "dmsg | tail" comes out a bit different than most. 

I'm no coder but I do manage to cobble together workarounds at times. The issue may center around the line that reads "unable to read config index 0 descriptor/start"...

Call it a hunch.

********
scott@scott-2:~$ dmesg | tail
[27839.890572] usb 4-1: new high speed USB device using ehci_hcd and address 10
[27845.021787] usb 4-1: unable to read config index 0 descriptor/start
[27845.021800] usb 4-1: chopping to 0 config(s)
[29347.671632] usb 4-1: no configuration chosen from 0 choices
[29347.671717] usb 4-1: USB disconnect, address 10
[29347.910646] ppdev0: registered pardevice
[29347.910678] ppdev0: unregistered pardevice
[29348.270215] ppdev0: registered pardevice
[29348.319307] ppdev0: unregistered pardevice
[29367.280140] usb 4-1: new high speed USB device using ehci_hcd and address 11
scott@scott-2:~$ 
********

Thanks again,

Scott

---

### Post by Scott S. on 2007-12-23
Folks? Can someone tell me anything about this? I re-tried it and maybe I hit the dmsg | tail a little fast the first time because a couple more lines came up. I have no idea how this hardware does it's handshaking so it's all Greek to me. Strangely, trying it in different USB ports doesn't seem to change the output of dmsg | tail at all.

Thanks,
Scott

scott@scott-2:~$ dmesg | tail
[27845.021800] usb 4-1: chopping to 0 config(s)
[29347.671632] usb 4-1: no configuration chosen from 0 choices
[29347.671717] usb 4-1: USB disconnect, address 10
[29347.910646] ppdev0: registered pardevice
[29347.910678] ppdev0: unregistered pardevice
[29348.270215] ppdev0: registered pardevice
[29348.319307] ppdev0: unregistered pardevice
[29367.280140] usb 4-1: new high speed USB device using ehci_hcd and address 11
[29372.411392] usb 4-1: unable to read config index 0 descriptor/start
[29372.411405] usb 4-1: chopping to 0 config(s)
scott@scott-2:~$

---

