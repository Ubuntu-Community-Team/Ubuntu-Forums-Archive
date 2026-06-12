---
title: "External Power Manager - Not running on Linux - Please help!"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-03-22
Hi There,

Just bought a "Power Manager" from Gembird:

Silver Shield Power Manager - SIS-PM

It's a power-socket with 4 outlets, fully controlable from the pc, via USB. - A really nice piece of hardware...

Running pm2.exe gives me this:

[email]lea@lealap:~/.wine[/email]/drive_c/Program Files/Power Manager$ wine pm2.exe
fixme:ole:CoRegisterMessageFilter stub
fixme:setupapi:SetupDiGetClassDevsW ({4d1e55b2-f16f-11cf-88cb-001111000030}): stub
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 000a, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 000a, blocked by 0009, retrying (60 sec)
fixme:setupapi:SetupDiGetClassDevsW ({4d1e55b2-f16f-11cf-88cb-001111000030}): stub
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 000a, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 000a, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 000a, retrying (60 sec)
[email]lea@lealap:~/.wine[/email]/drive_c/Program Files/Power Manager$ wine pm2.exe
fixme:ole:CoRegisterMessageFilter stub
fixme:setupapi:SetupDiGetClassDevsW ({4d1e55b2-f16f-11cf-88cb-001111000030}): stub
fixme:setupapi:SetupDiGetClassDevsW ({4d1e55b2-f16f-11cf-88cb-001111000030}): stub
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 000a, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 000a, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7fd70020 "heap.c: main process heap section" wait timed out in thread 0009, blocked by 000a, retrying (60 sec)
[email]lea@lealap:~/.wine[/email]/drive_c/Program Files/Power Manager$

And then an error pops up:

"Cannot retrieve HID devices list." 

Any ideas on how to fix this?

You can download the application here:

[http://dumazz.dk/ubuntu/PM/PM.zip](http://dumazz.dk/ubuntu/PM/PM.zip) (Also including the needed DLL-files!)

I've heard that some people is writing drivers/applications for unsupported hardware, just by sending them the hardware... Is that true? - And how do I get in touch with them?

---

### Post by daller on 2006-04-03
This project is nice:

[http://sourceforge.net/projects/sispm](http://sourceforge.net/projects/sispm)

...It solved my problems!

---

### Post by daller on 2006-04-04
If you have any idea about what Windows-versions supports this device, please post them here.

I know WinXP does, but what about 98, Me and 2000???

(I'm not running Windows, but my costumers are!)

---

