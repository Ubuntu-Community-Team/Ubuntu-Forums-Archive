---
title: "Installing Adobe CS4 in Wine"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Face_Man on 2009-10-23
i try this guide [http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/](http://www.sucka.net/2009/08/installing-adobe-cs4-in-wine/)


I got this error when i try to install Adobe CS4 in Wine 



```


wine Setup.exeApplication tried to create a window, but no driver could be loaded. 
Make sure that your X server is running and that $DISPLAY is set correctly. 
Application tried to create a window, but no driver could be loaded. 
Make sure that your X server is running and that $DISPLAY is set correctly. 
err:ole:apartment_createwindowifneeded CreateWindow failed with error 0 
fixme:console:AttachConsole stub ffffffff 
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svg" 4 4 (nil) (nil) 0x14b248 (nil) 
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svgz" 4 4 (nil) (nil) 0x14b248 (nil) 
Begin Adobe Setup 
UI mode: Full GUI 
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger... 
Application tried to create a window, but no driver could be loaded. 
Make sure that your X server is running and that $DISPLAY is set correctly. 
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000). 
Register dump: 
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b 
 EIP:00000000 ESP:0033f890 EBP:0033fabc EFLAGS:00010202(  R- --  I   - - - ) 
 EAX:00000000 EBX:00000000 ECX:0033f8b8 EDX:00000079 
 ESI:00000006 EDI:00000000 
Stack dump: 
0x0033f890:  00434f9f 00000006 00000000 00000000 
0x0033f8a0:  00000000 0033f8b8 3831f630 0069a340 
0x0033f8b0:  0033fd08 00000000 00000030 00000000 
0x0033f8c0:  00000007 00110014 0014b1b8 00000000 
0x0033f8d0:  7bc95ff4 0014b168 00000000 0000011c 
0x0033f8e0:  00000006 00000000 00001770 00000002 
Backtrace: 
=>0 0x00000000 (0x0033fabc) 
  1 0x0045d382 in setup (+0x5d382) (0x0033fb00) 
  2 0x0042b0b5 in setup (+0x2b0b5) (0x0033fb78) 
  3 0x536e6957 (0x02020002) 
0x00000000: -- no code accessible -- 
Modules: 
Module   Address         Debug info   Name (73 modules) 
PE     400000-  6fe000   Export          setup 
PE   70bd0000-70c35000   Deferred        shlwapi 
ELF   7b800000-7b972000   Deferred        kernel32<elf> 
  \-PE   7b820000-7b972000   \               kernel32 
ELF   7bc00000-7bcb2000   Deferred        ntdll<elf> 
  \-PE   7bc10000-7bcb2000   \               ntdll 
ELF   7bf00000-7bf04000   Deferred        <wine-loader> 
ELF   7e179000-7e17d000   Deferred        libgpg-error.so.0 
ELF   7e17d000-7e1e6000   Deferred        libgcrypt.so.11 
ELF   7e1e6000-7e1f8000   Deferred        libtasn1.so.3 
ELF   7e1f8000-7e1fc000   Deferred        libkeyutils.so.1 
ELF   7e1fc000-7e205000   Deferred        libkrb5support.so.0 
ELF   7e205000-7e229000   Deferred        libk5crypto.so.3 
ELF   7e229000-7e2bb000   Deferred        libkrb5.so.3 
ELF   7e2bb000-7e358000   Deferred        libgnutls.so.26 
ELF   7e358000-7e383000   Deferred        libgssapi_krb5.so.2 
ELF   7e383000-7e3ba000   Deferred        libcups.so.2 
ELF   7e3d6000-7e40a000   Deferred        uxtheme<elf> 
  \-PE   7e3e0000-7e40a000   \               uxtheme 
ELF   7e445000-7e46c000   Deferred        libexpat.so.1 
ELF   7e46c000-7e499000   Deferred        libfontconfig.so.1 
ELF   7e499000-7e4af000   Deferred        libz.so.1 
ELF   7e4af000-7e526000   Deferred        libfreetype.so.6 
ELF   7e526000-7e52a000   Deferred        libcom_err.so.2 
ELF   7e542000-7e557000   Deferred        system.drv16.so 
PE   7e550000-7e557000   Deferred        system.drv16 
ELF   7e557000-7e56d000   Deferred        psapi<elf> 
  \-PE   7e560000-7e56d000   \               psapi 
ELF   7e56d000-7e652000   Deferred        oleaut32<elf> 
  \-PE   7e580000-7e652000   \               oleaut32 
ELF   7e652000-7e6c0000   Deferred        rpcrt4<elf> 
  \-PE   7e660000-7e6c0000   \               rpcrt4 
ELF   7e6c0000-7e7bd000   Deferred        ole32<elf> 
  \-PE   7e6e0000-7e7bd000   \               ole32 
ELF   7e7bd000-7e7e6000   Deferred        oledlg<elf> 
  \-PE   7e7c0000-7e7e6000   \               oledlg 
ELF   7e7e6000-7e81a000   Deferred        winspool<elf> 
  \-PE   7e7f0000-7e81a000   \               winspool 
ELF   7e81a000-7e8e4000   Deferred        comctl32<elf> 
  \-PE   7e820000-7e8e4000   \               comctl32 
ELF   7e8e4000-7ea74000   Deferred        shell32<elf> 
  \-PE   7e8f0000-7ea74000   \               shell32 
ELF   7ea74000-7eb26000   Deferred        comdlg32<elf> 
  \-PE   7ea80000-7eb26000   \               comdlg32 
ELF   7eb26000-7eb3c000   Deferred        libresolv.so.2 
ELF   7eb3e000-7eb58000   Deferred        version<elf> 
  \-PE   7eb40000-7eb58000   \               version 
ELF   7eb58000-7eb78000   Deferred        iphlpapi<elf> 
  \-PE   7eb60000-7eb78000   \               iphlpapi 
ELF   7eb78000-7eba2000   Deferred        ws2_32<elf> 
  \-PE   7eb80000-7eba2000   \               ws2_32 
ELF   7eba2000-7ebbd000   Deferred        wsock32<elf> 
  \-PE   7ebb0000-7ebbd000   \               wsock32 
ELF   7ebbd000-7ed09000   Deferred        user32<elf> 
  \-PE   7ebe0000-7ed09000   \               user32 
ELF   7ed09000-7ed60000   Deferred        advapi32<elf> 
  \-PE   7ed20000-7ed60000   \               advapi32 
ELF   7ed60000-7ee00000   Deferred        gdi32<elf> 
  \-PE   7ed70000-7ee00000   \               gdi32 
ELF   7ee00000-7ee6f000   Deferred        msvcrt<elf> 
  \-PE   7ee10000-7ee6f000   \               msvcrt 
ELF   7ef99000-7efa5000   Deferred        libnss_files.so.2 
ELF   7efa5000-7efbe000   Deferred        libnsl.so.1 
ELF   7efbe000-7efe4000   Deferred        libm.so.6 
ELF   7efe5000-7eff9000   Deferred        lz32<elf> 
  \-PE   7eff0000-7eff9000   \               lz32 
ELF   f7c70000-f7c7b000   Deferred        libnss_nis.so.2 
ELF   f7c7c000-f7c80000   Deferred        libdl.so.2 
ELF   f7c80000-f7de3000   Deferred        libc.so.6 
ELF   f7de4000-f7dfd000   Deferred        libpthread.so.0 
ELF   f7e10000-f7e19000   Deferred        libnss_compat.so.2 
ELF   f7e19000-f7f55000   Deferred        libwine.so.1 
ELF   f7f57000-f7f78000   Deferred        ld-linux.so.2 
Threads: 
process  tid      prio (all id:s are in hex) 
00000008 (D) Z:\Setup.exe 
   00000009    0 <== 
0000000e  
   00000016    0 
   00000015    0 
   00000014    0 
   00000010    0 
   0000000f    0 
00000011  
   00000018    0 
   00000017    0 
   00000013    0 
   00000012    0 
Backtrace: 
=>0 0x00000000 (0x0033fabc) 
  1 0x0045d382 in setup (+0x5d382) (0x0033fb00) 
  2 0x0042b0b5 in setup (+0x2b0b5) (0x0033fb78) 
  3 0x536e6957 (0x02020002) 

```

---

