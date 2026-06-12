---
title: "Cedega, steam won't start"
date: 2008-10-26
forum: General Help
---

### Post by Naatan on 2008-10-26
Hi, I just installed the demo version of cedega to try out team fortress 2, I got it running with steam earlier but it didn't run well at all.

Anyway the installation of steam went fine, but upon launching steam (I'm pressing Play in Cedega) the "Connection to steam account" message appears, after a few seconds it goes away and that's about it.

When I run the log and tail it I get the following error messages at the end:

```

0016:Ret (0) kernel32.GetThreadContext() retval=00000001 ret=4042e041 fs=0043   
Unhandled exception: 0016:Call(0) kernel32.ReadProcessMemory(00000044,7704bdc0,004a1fcc,00000020,004a1f54) ret=4042dcb8 fs=400f0043                             
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042dcb8 fs=0043  
0016:Call(0) kernel32.ReadProcessMemory(00000044,7706bc8b,004a1f8c,00000040,004a1f44) ret=4042dcb8 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042dcb8 fs=0043  
unimplemented function kernel32.FoldStringW called0016:Call(0) kernel32.WriteProcessMemory(00000044,4000f3e0,004a1f13,00000001,00000000) ret=404187a5 fs=400f0043                                                                               
0016:Ret (0) kernel32.WriteProcessMemory() retval=00000001 ret=404187a5 fs=0043 
 in 32-bit code (0x77036052).                                                   
In 32-bit mode.                                                                 
Register dump:                                                                  
 CS:0073 SS:007b DS:007b ES:007b FS:0043 GS:003b                                
 EIP:77036052 ESP:0f51e1cc EBP:0f51e224 EFLAGS:00200212(   - 00  I   -A- 1 )    
 EAX:41f071f4 EBX:770833bc ECX:41f4006e EDX:00000080                            
 ESI:0f51e1cc EDI:0f51e260                                                      
Stack dump:                                                                     
0016:Call(0) kernel32.GetThreadSelectorEntry(00000068,0000007b,004a1f0c) ret=4042361e fs=400f0043                                                               
0016:Ret (0) kernel32.GetThreadSelectorEntry() retval=00000001 ret=4042361e fs=0043                                                                             
0x0f51e1cc (Steam.exe..rsrc+0xefcb1cc): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1cc,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 800001000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1d0,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000010016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1d4,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1d8,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 41f071f4                                                                       
0x0f51e1dc (Steam.exe..rsrc+0xefcb1dc): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1dc,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000020016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1e0,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 7704bdc00016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1e4,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 7706bc8b0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1e8,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 00000000                                                                       
0x0f51e1ec (Steam.exe..rsrc+0xefcb1ec): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1ec,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1f0,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1f4,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1f8,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 00000000                                                                       
0x0f51e1fc (Steam.exe..rsrc+0xefcb1fc): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e1fc,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e200,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e204,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 0f55405c0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e208,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 ffffffff                                                                       
0x0f51e20c (Steam.exe..rsrc+0xefcb20c): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e20c,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e210,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e214,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 000000000016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e218,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 ffffffff                                                                       
0x0f51e21c (Steam.exe..rsrc+0xefcb21c): 0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e21c,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 770833bc0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e220,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 0f51e3a00016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e224,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 0f51e2340016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e228,004a1ed0,00000004,00000000) ret=40423ed5 fs=400f0043                                         
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40423ed5 fs=0043  
 7703663c                                                                       
0x0f51e22c (Steam.exe..rsrc+0xefcb22c):                                         

0016:Call(0) kernel32.GetThreadSelectorEntry(00000068,00000047,004a1f10) ret=40423040 fs=400f0043                                                               
0016:Ret (0) kernel32.GetThreadSelectorEntry() retval=00000000 ret=40423040 fs=0043                                                                             
Backtrace:                                                                      
=>0 0x77036052 (KERNEL32.DLL..text+0x52 in C:\WINDOWS\SYSTEM32\KERNEL32.DLL) (ebp=0f51e224)                                                                     
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f553070,004a1bd4,00000004,00000000) ret=4042b2c4 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b2c4 fs=0043  
0016:Call(0) kernel32.GetThreadSelectorEntry(00000068,000023c7,004a1b70) ret=4042371d fs=400f0043                                                               
0016:Ret (0) kernel32.GetThreadSelectorEntry() retval=00000001 ret=4042371d fs=0043                                                                             
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f552fd0,004a1ef0,00000030,00000000) ret=4042b780 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b780 fs=0043  
0016:Call(0) kernel32.ReadProcessMemory(00000044,00000000,004a1bcb,00000001,00000000) ret=4042b366 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b366 fs=0043  
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e224,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b03e fs=0043  
  1 0x7703663c (KERNEL32.DLL.FreeLSCallback in C:\WINDOWS\SYSTEM32\KERNEL32.DLL) (ebp=0f51e234)                                                                 
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e234,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b03e fs=0043  
  2 0x41f071f4 (VSTDLIB_S.DLL.?Normalize@CStringNormalization@@SAH_NPBGPAGH@Z+0x144 in C:\PROGRAM FILES\STEAM\VSTDLIB_S.DLL) (ebp=0f51e378)                     
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e378,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b03e fs=0043  
  3 0x41f0729c (VSTDLIB_S.DLL.?Normalize@CStringNormalization@@SAH_NPBDPADH@Z+0x7c in C:\PROGRAM FILES\STEAM\VSTDLIB_S.DLL) (ebp=0f51e49c)                      
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e49c,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b03e fs=0043  
  4 0x4333fa3d (STEAMCLIENT.DLL.Steam_FreeLastCallback+0xa50fd in C:\PROGRAM FILES\STEAM\STEAMCLIENT.DLL) (ebp=0f51e718)                                        
0016:Call(0) kernel32.ReadProcessMemory(00000044,0f51e718,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042b03e fs=0043  
  5 0x6e61696e (CSERHELPER.DLL..reloc+0xe5f796e) (ebp=69766944)                 
0016:Call(0) kernel32.ReadProcessMemory(00000044,69766944,004a1b58,0000000c,00000000) ret=4042b03e fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000000 ret=4042b03e fs=0043  
*** Invalid address 0x69766944 (CSERHELPER.DLL..reloc+0x9747944)                

0x77036052 (KERNEL32.DLL..text+0x52 in C:\WINDOWS\SYSTEM32\KERNEL32.DLL): 0016:Call(0) kernel32.ReadProcessMemory(00000044,77036052,004a1f1b,00000001,00000000) ret=4042860d fs=400f0043                                                        
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=4042860d fs=0043  
0016:Call(0) kernel32.ReadProcessMemory(00000044,77036052,004a1e88,00000001,00000000) ret=40419fc5 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40419fc5 fs=0043  
jmp     0016:Call(0) kernel32.ReadProcessMemory(00000044,77036053,004a1e88,00000001,00000000) ret=40419fc5 fs=400f0043                                          
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40419fc5 fs=0043  
0x7703604c (KERNEL32.DLL..text+0x4c in C:\WINDOWS\SYSTEM32\KERNEL32.DLL)        
0016:Call(0) kernel32.ReadProcessMemory(00000044,77036052,004a1f3b,00000001,00000000) ret=40419bf5 fs=400f0043                                                  
0016:Ret (0) kernel32.ReadProcessMemory() retval=00000001 ret=40419bf5 fs=0043  
0016:Call(0) kernel32.WriteProcessMemory(00000044,4000f3e0,004a1f03,00000001,00000000) ret=404187a5 fs=400f0043                                                 
0016:Ret (0) kernel32.WriteProcessMemory() retval=00000001 ret=404187a5 fs=0043 
Modules:                                                                        
Address                 Module  Name                                            
0x00400000-0055e000     (PE)    C:\Program Files\Steam\Steam.exe                
0x10000000-10303000     (PE)    C:\PROGRAM FILES\STEAM\STEAMUI.DLL              
0x21100000-211ad000     (PE)    C:\PROGRAM FILES\STEAM\BIN\MSS32_S.DLL          
0x30000000-302f0000     (PE)    C:\PROGRAM FILES\STEAM\STEAM.DLL                
0x40060000-40062000     (PE)    C:\WINDOWS\SYSTEM32\NTDLL.DLL                   
0x40220000-40222000     (PE)    C:\WINDOWS\SYSTEM32\IPHLPAPI.DLL                
0x40417000-40419000     (PE)    C:\WINDOWS\SYSTEM32\WS2_32.DLL                  
0x4045b000-4045d000     (PE)    C:\WINDOWS\SYSTEM32\USER32.DLL                  
0x4056c000-4056e000     (PE)    C:\WINDOWS\SYSTEM32\GDI32.DLL                   
0x405d7000-405d9000     (PE)    C:\WINDOWS\SYSTEM32\ADVAPI32.DLL                
0x405f6000-405f8000     (PE)    C:\WINDOWS\SYSTEM32\WINSPOOL.DRV                
0x40616000-40618000     (PE)    C:\WINDOWS\SYSTEM32\COMDLG32.DLL                
0x4068f000-40691000     (PE)    C:\WINDOWS\SYSTEM32\SHELL32.DLL                 
0x40710000-40712000     (PE)    C:\WINDOWS\SYSTEM32\OLEDLG.DLL                  
0x40716000-40718000     (PE)    C:\WINDOWS\SYSTEM32\VERSION.DLL                 
0x40720000-40722000     (PE)    C:\WINDOWS\SYSTEM32\LZ32.DLL                    
0x4075f000-40761000     (PE)    C:\WINDOWS\SYSTEM32\OLE32.DLL                   
0x407ca000-407cc000     (PE)    C:\WINDOWS\SYSTEM32\RPCRT4.DLL                  
0x4080d000-4080f000     (PE)    C:\WINDOWS\SYSTEM32\SHLWAPI.DLL                 
0x4083f000-40841000     (PE)    C:\WINDOWS\SYSTEM32\COMCTL32.DLL                
0x408db000-408dd000     (PE)    C:\WINDOWS\SYSTEM32\OLEAUT32.DLL                
0x40b20000-40b22000     (PE)    C:\WINDOWS\SYSTEM32\X11DRV.DLL                  
0x41b84000-41b86000     (PE)    C:\WINDOWS\SYSTEM32\MSACM.DRV                   
0x41b8b000-41b8d000     (PE)    C:\WINDOWS\SYSTEM32\MIDIMAP.DRV                 
0x41bbc000-41bfa000     (PE)    C:\PROGRAM FILES\STEAM\TIER0_S.DLL              
0x41bff000-41c01000     (PE)    C:\WINDOWS\SYSTEM32\MSACM32.DLL                 
0x41d07000-41d09000     (PE)    C:\WINDOWS\SYSTEM32\PSAPI.DLL                   
0x41d0d000-41d0f000     (PE)    C:\WINDOWS\SYSTEM32\MSIMG32.DLL                 
0x41eab000-41ead000     (PE)    C:\WINDOWS\SYSTEM32\WINMM.DLL                   
0x41ef3000-41f6e000     (PE)    C:\PROGRAM FILES\STEAM\VSTDLIB_S.DLL            
0x41f7f000-41f81000     (PE)    C:\WINDOWS\SYSTEM32\WINEALSA.DRV                
0x41f9c000-41f9e000     (PE)    C:\WINDOWS\SYSTEM32\IMM32.DLL                   
0x4207a000-420acc00     (PE)    C:\PROGRAM FILES\STEAM\BIN\FILESYSTEM_STEAM.DLL 
0x420ad000-42142000     (PE)    C:\PROGRAM FILES\STEAM\BIN\VGUI2.DLL            
0x431f6000-434ae000     (PE)    C:\PROGRAM FILES\STEAM\STEAMCLIENT.DLL          
0x434b9000-434bb000     (PE)    C:\WINDOWS\SYSTEM32\WININET.DLL                 
0x434db000-434dd000     (PE)    C:\WINDOWS\SYSTEM32\CRYPT32.DLL                 
0x43505000-43507000     (PE)    C:\WINDOWS\SYSTEM32\SECUR32.DLL                 
0x43511000-4363f000     (PE)    C:\PROGRAM FILES\STEAM\BIN\P2PVOICE.DLL         
0x43641000-436f4000     (PE)    C:\PROGRAM FILES\STEAM\BIN\STEAMSERVICE.DLL     
0x436f4000-43808800     (PE)    C:\PROGRAM FILES\STEAM\DBGHELP.DLL              
0x43809000-4384f000     (PE)    C:\WINDOWS\SYSTEM32\MSVCRT.DLL                  
0x43856000-43858000     (PE)    C:\WINDOWS\SYSTEM32\RSAENH.DLL                  
0x43876000-43878000     (PE)    C:\WINDOWS\SYSTEM32\IMAADP32.ACM                
0x4387c000-4387e000     (PE)    C:\WINDOWS\SYSTEM32\MSG711.ACM                  
0x438cc000-438ce000     (PE)    C:\WINDOWS\SYSTEM32\DSOUND.DLL                  
0x438e5000-438e7000     (PE)    C:\WINDOWS\SYSTEM32\WINEMP3.ACM                 
0x4392b000-4392d000     (PE)    C:\WINDOWS\SYSTEM32\POWRPROF.DLL                
0x60000000-60021000     (PE)    C:\PROGRAM FILES\STEAM\CSERHELPER.DLL           
0x77035000-77037000     (PE)    C:\WINDOWS\SYSTEM32\KERNEL32.DLL                
Threads:                                                                        
0016:Call(0) kernel32.CreateToolhelp32Snapshot(00000004,00000000) ret=40422eba fs=400f0043                                                                      
0016:Ret (0) kernel32.CreateToolhelp32Snapshot() retval=000000d0 ret=40422eba fs=0043                                                                           
0016:Call(0) kernel32.Thread32First(000000d0,004a20f4) ret=40422ef9 fs=400f0043 
0016:Ret (0) kernel32.Thread32First() retval=00000001 ret=40422ef9 fs=0043      
process  tid      prio                                                          
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
00000001 (D) C:\Program Files\Steam\Steam.exe                                   
        00000012    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000014    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000013    1                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000011    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000d   15                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000e    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000010    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000f    0 <==                                                       
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000c    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000b    1                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        0000000a    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000009    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000008    0                                                           
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043  
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043       
        00000007    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043
        00000006    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043
        00000005    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043
        00000004    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043
        00000003    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000001 ret=40422fa6 fs=0043
        00000002    0
0016:Call(0) kernel32.Thread32Next(000000d0,004a20f4) ret=40422fa6 fs=400f0043
0016:Ret (0) kernel32.Thread32Next() retval=00000000 ret=40422fa6 fs=0043
0016:Call(0) kernel32.CloseHandle(000000d0) ret=40422fb0 fs=400f0043
0016:Ret (0) kernel32.CloseHandle() retval=00000001 ret=40422fb0 fs=0043
WineDbg terminated on pid 1
0016:Call(0) kernel32.ExitProcess(00000000) ret=404183dd fs=400f0043
0016:Call(1) PE DLL (proc=0x40473f5c,module=C:\WINDOWS\SYSTEM32\advapi32.dll(40470000),type=0,res=0x1)
0016:Call(2) ntdll.RtlDeleteCriticalSection(404869cc) ret=4047402b fs=400f0043
0016:Ret (2) ntdll.RtlDeleteCriticalSection() retval=00000000 ret=4047402b fs=0043
0016:Call(2) kernel32.CloseHandle(00000040) ret=4047d825 fs=400f0043
0016:Ret (2) kernel32.CloseHandle() retval=00000001 ret=4047d825 fs=0043
0016:Ret (1) PE DLL (proc=0x40473f5c,module=C:\WINDOWS\SYSTEM32\advapi32.dll(40470000),type=0,res=0x1) retval=1
0016:Call(1) PE DLL (proc=0x77044a9c,module=C:\WINDOWS\SYSTEM32\kernel32.dll(77035000),type=0,res=0x1)
0016:Ret (1) PE DLL (proc=0x77044a9c,module=C:\WINDOWS\SYSTEM32\kernel32.dll(77035000),type=0,res=0x1) retval=1

```

Also, before the errors occur, I get a LOT of the following:

```

000b:Call(0) ntdll.RtlLeaveCriticalSection(0ee41824) ret=30028582 fs=400f0043   
000b:Ret (0) ntdll.RtlLeaveCriticalSection() retval=00000000 ret=30028582 fs=0043                                                                               
000b:Call(0) ntdll.RtlEnterCriticalSection(0ee41824) ret=3004bbc2 fs=400f0043   
000b:Ret (0) ntdll.RtlEnterCriticalSection() retval=00000000 ret=3004bbc2 fs=0043                                                                               
000b:Call(0) ntdll.RtlLeaveCriticalSection(0ee41824) ret=30028582 fs=400f0043   
000b:Ret (0) ntdll.RtlLeaveCriticalSection() retval=00000000 ret=30028582 fs=0043                                                                               
000b:Call(0) ntdll.RtlEnterCriticalSection(0ee41824) ret=3004bbc2 fs=400f0043   
000b:Ret (0) ntdll.RtlEnterCriticalSection() retval=00000000 ret=3004bbc2 fs=0043                                                                               
000b:Call(0) ntdll.RtlLeaveCriticalSection(0ee41824) ret=30028582 fs=400f0043   
000b:Ret (0) ntdll.RtlLeaveCriticalSection() retval=00000000 ret=30028582 fs=0043                                                                               
000b:Call(0) ntdll.RtlEnterCriticalSection(0ee41824) ret=3004bbc2 fs=400f0043   
000b:Ret (0) ntdll.RtlEnterCriticalSection() retval=00000000 ret=3004bbc2 fs=0043                                                                               
000b:Call(0) ntdll.RtlLeaveCriticalSection(0ee41824) ret=30028582 fs=400f0043   
000b:Ret (0) ntdll.RtlLeaveCriticalSection() retval=00000000 ret=30028582 fs=0043                     

```

Does anyone know how I can solve this?

---

### Post by Naatan on 2008-10-26
bump

---

