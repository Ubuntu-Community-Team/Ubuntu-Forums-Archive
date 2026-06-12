---
title: "Ubuntu 10.10 (maverick) Floppy not working"
date: 2010-10-22
forum: Hardware
---

### Post by cparke on 2010-10-22
I have a traditional floppy diskette drive on my computer via an onboard MFM controller (i.e. I am not using a USB floppy drive).  However, I can't mount the drive no matter what diskette I put in the drive.  I can boot off the floppy drive, so I don't think it is the drive or diskette's fault (and I have tried several diskettes too).  I get no error messages, mount just accesses the drive briefly, then returns without the mount completed, or it complains there is no media in the drive even when there is.  Is this another thing broken in 10.10? (makes me want to consider going back to 10.04, at least from a stability standpoint.

---

### Post by cparke on 2010-10-23
Same problem using wine-1.3.  Same problem using Ubuntu 10.10 32-bit.  In the console window, these messages appear:

larissa@DELL:~$ wineconsole cmd.exe
fixme:shell: Dde_OnRequest returning fake program groups list
err:ddeml: DdeAccessData Failed on GlobalLock(0xdeb2)
fixme:shell: Dde_OnRequest returning fake program groups list
err:ddeml: DdeAccessData Failed on GlobalLock(0xb12a)
fixme: Dle:LoadTypeLib16 ("C:\\windows\\SYSTEM\\OC25.DLL",0x43f722): stub
wine: Unhandled page fault on read access to 0xffffffff at address 0x12bf:0x00000ded (thread 001f), starting debugger...
fixme:dbghelp:addr_to_linear Failed to linearize address 6f33:b809 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address 6f33:114 (mode 0)
err:ntdll:RtlpWaitForCriticalSection section 0x7eb56700 "syslevel.c: Win16Mutex" wait timed out in thread 0020, blocked by 001f, retrying (60 sec)
err:syslevel:_LeaveSysLevel (0x7eb56700, level 1): Invalid state: count 0 mutex (nil).

---

### Post by mhgsys on 2010-10-23
coincidence while scrolling the forums


read ;
[http://ubuntuforums.org/showthread.php?t=1599639](http://ubuntuforums.org/showthread.php?t=1599639)

---

### Post by cparke on 2010-10-23
> **cparke said:**
> Same problem using wine-1.3. Same problem using Ubuntu 10.10 32-bit. In the console window, these messages appear:
 
larissa@DELL:~$ wineconsole cmd.exe
fixme:shell: Dde_OnRequest returning fake program groups list
err:ddeml: DdeAccessData Failed on GlobalLock(0xdeb2)
fixme:shell: Dde_OnRequest returning fake program groups list
err:ddeml: DdeAccessData Failed on GlobalLock(0xb12a)
fixme: Dle:LoadTypeLib16 ("C:\\windows\\SYSTEM\\OC25.DLL",0x43f722): stub
wine: Unhandled page fault on read access to 0xffffffff at address 0x12bf:0x00000ded (thread 001f), starting debugger...
fixme:dbghelp:addr_to_linear Failed to linearize address 6f33:b809 (mode 0)
fixme:dbghelp:addr_to_linear Failed to linearize address 6f33:114 (mode 0)
err:ntdll:RtlpWaitForCriticalSection section 0x7eb56700 "syslevel.c: Win16Mutex" wait timed out in thread 0020, blocked by 001f, retrying (60 sec)
err:syslevel:_LeaveSysLevel (0x7eb56700, level 1): Invalid state: count 0 mutex (nil).
The above error messages above have _nothing_ to do with Ubuntu 10.10, sorry my mistake adding it here (it is related to a problem I am having using WINE with a 16-bit app., was supposed to be posted to WINEHQ).
 
The floppy drive problem though is real, I can use the drive works in Ubuntu 10.04 but not in 10.10.
 
Thank you mhgsys for the link, good to know that I'm not the only one seeing this problem and maybe there is a workaround.

---

### Post by cparke on 2010-10-24
> **mhgsys said:**
> coincidence while scrolling the forums


read ;
[http://ubuntuforums.org/showthread.php?t=1599639](http://ubuntuforums.org/showthread.php?t=1599639)

Yes - this link did workaround fix my problem, thank you very much!

I already had the /etc/fstab entry for /dev/fd0.  But in Ubuntu 10.10 (as well as 10.04.1) a normal mount on /dev/fd0 does not work.  This was working in 10.04, BTW.  

While a normal mount doesn't work, this command does:
```
udisks --mount /dev/fd0
```I'm not sure what the differences are, but that's good enough for me for now.


CP

---

