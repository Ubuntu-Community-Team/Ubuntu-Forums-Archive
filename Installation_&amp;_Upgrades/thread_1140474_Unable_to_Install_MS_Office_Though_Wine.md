---
title: "Unable to Install MS Office Though Wine"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Jimbo8927 on 2009-04-27
Hi,

I'm a recent convert to Ubuntu, and am having some trouble installing MS Office through Wine. I tried searching other posts but nothing anyone else recommended seemed to help. 

Right now, the installation freezes right after it begins the installation process--the installation/progress bar doesn't move at all before it crashes.

This is what I get when I try and install Office through the Terminal: 
[php]
brent@Brently:/media/cdrom0$ wine setup
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:CheckTokenMembership ((nil) 0x131250 0x326d3c) stub!
fixme:ole:NdrCorrelationInitialize (0x329940, 0x329540, 1024, 0x0): stub
fixme:ole:NdrCorrelationFree (0x329940): stub
fixme:ole:NdrCorrelationInitialize (0x329958, 0x329558, 1024, 0x0): stub
fixme:ole:NdrCorrelationFree (0x329958): stub
fixme:msxml:DllCanUnloadNow 
fixme:advapi:LookupAccountNameW (null) L"brent" (nil) 0x33f80c (nil) 0x33f810 0x33f804 - stub
fixme:advapi:LookupAccountNameW (null) L"brent" 0x1360f8 0x33f80c 0x136020 0x33f810 0x33f804 - stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:shell:DllCanUnloadNow stub
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:advapi:CheckTokenMembership ((nil) 0xe52c40 0xcee0b8) stub!
fixme:shell:DllCanUnloadNow stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 69 ignored L"Upgrade" table values
fixme:msxml:DllCanUnloadNow 
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:richedit:RTFCharSetToCodePage unknown charset -1000000
fixme:font:WineEngCreateFontInstance Untranslated charset 192
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:ACTION_CallDllFunction Custom action (L"C:\\windows\\temp\\msiac05.tmp":L"OfficeDataLockPermissions") caused a page fault: c0000005
err:ntdll:RtlpWaitForCriticalSection section 0x7ee4bef8 "handle.c: MSI_object_cs" wait timed out in thread 0062, blocked by 0037, retrying (60 sec)
wine: Critical section 7ee4bef8 wait failed at address 0x7bc34ac9 (thread 0062), starting debugger...
Unhandled exception: wait failed on critical section 0x7ee4bef8
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc34ac9
Process of pid=002b has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
brent@Brently:/media/cdrom0$ process  tid      prio (all id:s are in hex)
0000000c 
    0000001c    0
    0000000e    0
    0000000d    0
0000000f 
    00000010    0
00000019 
    0000001f    0
    0000001e    0
    0000001b    0
    0000001a    0
0000002c 
    00000031    0
0000004f 
    00000051    0
    00000052    0
00000027 
    00000045    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
brent@Brently:/media/cdrom0$ 
[/php]Is anyone able to understand what my problem is from this? If not, what details do I need to provide?

Thank you so much!

---

### Post by pparks1 on 2009-04-27
A friend of mine sent me this in another forum, it's for running Office 2007 on Ubuntu 8.10.  I've personally never tried it, as I just run Office under Windows...but it might be of interest to you.

[http://www.programmerfish.com/roffice-2007-in-linux](http://www.programmerfish.com/roffice-2007-in-linux)

---

