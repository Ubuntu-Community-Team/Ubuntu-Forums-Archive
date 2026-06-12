---
title: "Ubuntu 10.04 not starting"
date: 2010-05-26
forum: Hardware
---

### Post by Moose32315 on 2010-05-26
Yesterday I got a new laptop, an Asus G51JX, and installed ubuntu 10.04 on it.  It didn't startup the first time after I installed it, but after a restarted it was quickly up and running.  While it was I updated it and everything.  Then I restarted it, but it doesn't want to startup.  This is what it shows on the screen.  

   [           9.077370] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
  [           9.077511] [drm] nouveau 0000:01:00.0: BDB I2C entry invalid
  [           9.247513] pciport 0000:00:03.0: PCIE Bus Error: severity=Uncorrected (Non-Fatal), type = =Transaction Layer, id=0018(Requester ID)
  [           9.286881] pcieport 0000:00:03.0:        device [8086:d138] error status/mask=000040000/00000000
  [           9.286998] pcieport 0000:00:03.0:        [14] Completion Timout (First)
  

I have very little knowledge of ubunbu; only a little experience with 9.10.  So I am unsure of what I should do.  I tried running it in recovery mode, but it just stopped on the same Timeout line.

---

### Post by Veren on 2010-05-26
It's just like if I saw myself this time yesterday. It' almost funny, if you check my post.
After 3 hours of total frustration I came up with this solution: (it will install all from scratch)
1. Press F2 to see BIOS when starting (restart with ctrl+alt+del)
2. In BOOT section put the 1st priority to CDROM and next one to hardware(it doesnt matter thought, the first one matters)
3. put LiveCD in
save&exit, let it restart.
Just reinstall Ubuntu. I am a second day Ubuntu user, I too have Asus (N61 series though), I think there is something wrong with the proprietary graphics driver (dont trust it!)
Hope I helped :)

---

### Post by Moose32315 on 2010-05-26
Thanks it helped.

---

### Post by grumpy.medic on 2010-05-26
> **Moose32315 said:**
> Yesterday I got a new laptop, an Asus G51JX, and installed ubuntu 10.04 on it.  It didn't startup the first time after I installed it, but after a restarted it was quickly up and running.  While it was I updated it and everything.  Then I restarted it, but it doesn't want to startup.  This is what it shows on the screen.  

   [           9.077370] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
  [           9.077511] [drm] nouveau 0000:01:00.0: BDB I2C entry invalid
  [           9.247513] pciport 0000:00:03.0: PCIE Bus Error: severity=Uncorrected (Non-Fatal), type = =Transaction Layer, id=0018(Requester ID)
  [           9.286881] pcieport 0000:00:03.0:        device [8086:d138] error status/mask=000040000/00000000
  [           9.286998] pcieport 0000:00:03.0:        [14] Completion Timout (First)
  

I have very little knowledge of ubunbu; only a little experience with 9.10.  So I am unsure of what I should do.  I tried running it in recovery mode, but it just stopped on the same Timeout line.

Looks like you are getting a load fail of some kind... when you ran updates, did you:

[LIST]
[*]Install Proprietary Drivers? 
[*]Run regular Update through Update Manager
[*]If so, was the update interrupted during install?
[/LIST]

The good thing here is, just like **Veren **said above, you can always reinstall the OS with minimal data loss since you just started using it.

Cheers

---

