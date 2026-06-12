---
title: "microsoft Office 2003 install fails on ubuntu 9"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by psylvester on 2009-06-14
Hi,
I am trying to install office 2003 on ubuntu however the setupfails each time, this is the error I am getting. I was using wine version 1.1.23, after that downgraded to 1.1.19. both doesnt seems to work. Kindly help.

Misha.

pr@prbltp:~/Office2003Prof$ wine SETUPPRO.EXE 
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:CheckTokenMembership ((nil) 0x1330d0 0x326d3c) stub!
fixme:ole:NdrCorrelationInitialize (0x329940, 0x329540, 1024, 0x0) : stub
fixme:advapi:CheckTokenMembership ((nil) 0x1491e8 0x321b78) stub!
fixme:ole:NdrCorrelationInitialize (0x329940, 0x329540, 1024, 0x0) : stub
fixme:ole:NdrCorrelationInitialize (0x329920, 0x329520, 1024, 0x0): stub
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:ole:NdrCorrelationFree (0x329920): stub
fixme:advapi:LookupAccountNameW (null) L"prabha" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"prabha" 0x138650 0x33f80c 0x139240 0x33f810 0x33f804 - stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:CheckTokenMembership ((nil) 0xf243d8 0x8be0b8) stub!
fixme:shell:DllCanUnloadNow stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 76 ignored L"Upgrade" table values
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msib158.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7ee51eb8 "handle.c: MSI_object_cs" wait timed out in thread 0020, blocked by 0046, retrying (60 sec)
wine: Critical section 7ee51eb8 wait failed at address 0x7bc34ac9 (thread 0020), starting debugger...
Unhandled exception: wait failed on critical section 0x7ee51eb8
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34ac9
Process of pid=001f has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
0000001a 
	0000001c    0
	0000001b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

---

### Post by cph05a on 2009-06-14
I've been using crossover 7 with Office 2003 and it makes life a little less stressful.  I'm not sure if you're a student, but they do have educational discounts.

other than that, I've heard good things about the winetricks tool, but haven't used it personally.

---

### Post by Mark Phelps on 2009-06-14
Crossover tends to work better than wine.  If you're going to use wine, you need to familiarize yourself with the CodeWeavers application compatibility database.  The rating for Office 2003 is "garbage", meaning it won't work.  See below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=31")

---

