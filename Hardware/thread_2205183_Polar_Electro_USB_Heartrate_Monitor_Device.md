---
title: "Polar Electro USB Heartrate Monitor Device"
date: 2014-02-12
forum: Hardware
---

### Post by Kirk Schnable on 2014-02-12
Hello Ubuntu Community!

I have been asked to get a device working on Ubuntu.  If this is not possible, we may have to fall back on a Windows machine as an alternative, but I'd like to think anything can be done on Ubuntu with a little bit of effort.  

The device is a heartrate monitor, but at the end of a workout, you scan it on a USB pad.  This USB pad is supposed to import the data from the personal fitness device.  The device is made by a company called Polar Electro.  [www.polarpersonaltrainer.com](www.polarpersonaltrainer.com)

I would like to achieve one of the following objectives:
[LIST]
[*]Get the manufacturer's software working in WINE.
[*]Find an open source alternative to the manufacturer's software.
[*]Find and install any drivers needed for the device to work.
[/LIST]

Here is the device USB identifier:
```
Bus 001 Device 005: ID 0da4:0003 Polar Electro OY
```

When I attempted to run the software installation of the manufacturer's software in WINE, here is my debug log:
```
err:menubuilder:init_xdg error looking up the desktop directory
fixme:clusapi:GetNodeClusterState ((null),0x33ec20) stub!
fixme:advapi:DecryptFileA "c:\\5a42e13ffb8f0e7ccc25c3\\" 00000000
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:advapi:RegisterEventSourceA ((null),""): stub
fixme:advapi:RegisterEventSourceW (L"",L""): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc00e1115,(nil),0x0003,0x00000000,0x33f240,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc00e1115,(nil),0x0003,0x00000000,0x1414c8,(nil)): stub
err:eventlog:ReportEventW L"Windows"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"Path not found\r\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" (nil) 0x33f160 (nil) 0x33f164 0x33f158 - stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" 0x166aa8 0x33f160 0x167610 0x33f164 0x33f158 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 7 ignored L"Upgrade" table values
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:clusapi:GetNodeClusterState ((null),0x33ec24) stub!
fixme:advapi:DecryptFileA "c:\\fefc19d4a981ea194fd110a7c95fd5\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:LsaOpenPolicy ((null),0x33f324,0x00000001,0x33f34c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" (nil) 0x7add98 (nil) 0x7add9c 0x7add90 - stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" 0x16cf78 0x7add98 0x16c818 0x7add9c 0x7add90 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:mscoree:LoadLibraryShim (0x4505fcac L"fusion.dll", (nil), (nil), 0x7ae570): semi-stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" (nil) 0x33f160 (nil) 0x33f164 0x33f158 - stub
fixme:advapi:LookupAccountNameW (null) L"dobbertinm" 0x1663c8 0x33f160 0x166080 0x33f164 0x33f158 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 3 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 3 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
wine: Unhandled page fault on read access to 0x00000000 at address 0x4a6ff2 (thread 0045), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004a6ff2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004a6ff2 ESP:00a2e960 EBP:00a2e960 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:683c5ff4 ECX:00a2e9c4 EDX:00000000
 ESI:00a2e9c4 EDI:00127a28
Stack dump:
0x00a2e960:  00a2e970 0035613e 00000000 00a2e9c4
0x00a2e970:  00a2e980 00357ec6 00000000 005232d8
0x00a2e980:  00a2ea18 101cdd3a 00000000 50ba1e47
0x00a2e990:  00127a28 001277b0 683c5ff4 7bc3525f
0x00a2e9a0:  00000010 00a2e9b8 7bc47dc6 000f85c8
0x00a2e9b0:  005232d8 7bc9cff4 00a2ea18 7bc48ce6
Backtrace:
=>0 0x004a6ff2 in msvcr90 (+0x36ff2) (0x00a2e960)
  1 0x0035613e in msvcp90 (+0x1613d) (0x00a2e970)
  2 0x00357ec6 in msvcp90 (+0x17ec5) (0x00a2e980)
  3 0x101cdd3a in libpolar (+0x1cdd39) (0x00a2ea18)
  4 0x683afca4 in advapi32 (+0x2fca3) (0x00a2ea68)
  5 0x7bc70480 call_thread_func+0xb() in ntdll (0x00a2ea78)
  6 0x7bc70650 call_thread_entry_point+0x6f() in ntdll (0x00a2eb48)
  7 0x7bc7a325 in ntdll (+0x6a324) (0x00a2f398)
  8 0x6802296e start_thread+0xbd() in libpthread.so.0 (0x00a2f498)
0x004a6ff2: movw    0x0(%eax),%cx
Modules:
Module    Address            Debug info    Name (90 modules)
PE      340000-  3cd000    Export          msvcp90
PE      400000-  468000    Deferred        polard
PE      470000-  513000    Export          msvcr90
PE    10000000-1035f000    Export          libpolar
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68036000    Export          libpthread.so.0
ELF    68036000-6803a000    Deferred        libdl.so.2
ELF    6803a000-68060000    Deferred        libm.so.6
ELF    68060000-68068000    Deferred        libnss_compat.so.2
ELF    68068000-68072000    Deferred        libnss_nis.so.2
ELF    68072000-6807e000    Deferred        libnss_files.so.2
ELF    6807e000-68083000    Deferred        libnss_lsass.so.2
ELF    68083000-6809f000    Deferred        liblsaclient.so.0
ELF    6809f000-680a3000    Deferred        liblsaauth.so.0
ELF    680a3000-680bf000    Deferred        liblwmsg_nothr.so.0
ELF    680bf000-680e0000    Deferred        liblwadvapi_nothr.so.0
ELF    680e0000-68103000    Deferred        liblsacommon.so.0
ELF    68103000-6810c000    Deferred        librt.so.1
ELF    6810c000-68177000    Deferred        liblwbase_nothr.so.0
ELF    68177000-6817b000    Deferred        libuuid.so.0
ELF    6817b000-681b3000    Deferred        winspool<elf>
  \-PE    68180000-681b3000    \               winspool
ELF    681b3000-682e5000    Deferred        user32<elf>
  \-PE    681d0000-682e5000    \               user32
ELF    682e5000-68371000    Deferred        gdi32<elf>
  \-PE    682f0000-68371000    \               gdi32
ELF    68371000-683cc000    Export          advapi32<elf>
  \-PE    68380000-683cc000    \               advapi32
ELF    683cc000-683e0000    Deferred        lz32<elf>
  \-PE    683d0000-683e0000    \               lz32
ELF    683e0000-68455000    Deferred        rpcrt4<elf>
  \-PE    683f0000-68455000    \               rpcrt4
ELF    68455000-68482000    Deferred        ws2_32<elf>
  \-PE    68460000-68482000    \               ws2_32
ELF    68482000-684f8000    Deferred        libfreetype.so.6
ELF    684f8000-6850d000    Deferred        libz.so.1
ELF    6850d000-6853d000    Deferred        libfontconfig.so.1
ELF    6853d000-68565000    Deferred        libexpat.so.1
ELF    68565000-68608000    Deferred        winex11<elf>
  \-PE    68570000-68608000    \               winex11
ELF    68608000-68611000    Deferred        libsm.so.6
ELF    68611000-68621000    Deferred        libxext.so.6
ELF    68621000-6873e000    Deferred        libx11.so.6
ELF    6873e000-68743000    Deferred        libuuid.so.1
ELF    68743000-68747000    Deferred        libxau.so.6
ELF    68747000-6874d000    Deferred        libxdmcp.so.6
ELF    6874d000-6876f000    Deferred        imm32<elf>
  \-PE    68750000-6876f000    \               imm32
ELF    6876f000-68773000    Deferred        libxinerama.so.1
ELF    68773000-68779000    Deferred        libxxf86vm.so.1
ELF    68779000-68783000    Deferred        libxrender.so.1
ELF    68783000-68787000    Deferred        libxcomposite.so.1
ELF    68787000-6878d000    Deferred        libxfixes.so.3
ELF    6878d000-68797000    Deferred        libxcursor.so.1
ELF    68797000-687de000    Deferred        libcups.so.2
ELF    687de000-6880d000    Deferred        libgssapi_krb5.so.2
ELF    6880d000-688a8000    Deferred        libgnutls.so.26
ELF    688a8000-688b9000    Deferred        libavahi-client.so.3
ELF    688b9000-6896a000    Deferred        libkrb5.so.3
ELF    6896a000-6898e000    Deferred        libk5crypto.so.3
ELF    6898e000-68992000    Deferred        libcom_err.so.2
ELF    68992000-6899a000    Deferred        libkrb5support.so.0
ELF    6899a000-689ae000    Deferred        libresolv.so.2
ELF    689ae000-689bf000    Deferred        libtasn1.so.3
ELF    689bf000-68a32000    Deferred        libgcrypt.so.11
ELF    68a32000-68a6b000    Deferred        libdbus-1.so.3
ELF    68a6b000-68a70000    Deferred        libgpg-error.so.0
ELF    68a70000-68a91000    Deferred        localspl<elf>
  \-PE    68a80000-68a91000    \               localspl
ELF    68a91000-68aac000    Deferred        spoolss<elf>
  \-PE    68aa0000-68aac000    \               spoolss
ELF    68b6f000-68b86000    Deferred        libnsl.so.1
ELF    68fab000-68faf000    Deferred        libkeyutils.so.1
ELF    69103000-6910b000    Deferred        libxrandr.so.2
ELF    6e182000-6e197000    Deferred        hid<elf>
  \-PE    6e190000-6e197000    \               hid
ELF    6e41a000-6e55a000    Deferred        libwine.so.1
ELF    6eb30000-6eb49000    Deferred        libice.so.6
ELF    72909000-72968000    Deferred        setupapi<elf>
  \-PE    72910000-72968000    \               setupapi
ELF    73c83000-73c9d000    Deferred        libxcb.so.1
ELF    784b4000-78615000    Export          libc.so.6
ELF    795e9000-795f5000    Deferred        libavahi-common.so.3
ELF    7b800000-7b97d000    Deferred        kernel32<elf>
  \-PE    7b810000-7b97d000    \               kernel32
ELF    7bc00000-7bcb9000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cf37000-7cf50000    Deferred        version<elf>
  \-PE    7cf40000-7cf50000    \               version
Threads:
process  tid      prio (all id:s are in hex)
00000008 websync_2.8.1.exe
    00000009    0
0000000e services.exe
    00000044    0
    00000043    0
    0000003d    0
    0000003c    0
    0000003b    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000019    0
    00000017    0
    00000013    0
    00000012    0
0000001a explorer.exe
    0000001b    0
00000021 msiexec.exe
    00000028    0
    00000026    0
    00000022    0
00000029 websync_2.8.1.exe
    0000002a    0
0000002b daemon_win32_2.2.2_distribution.exe
    0000002c    0
00000035 msiexec.exe
    00000036    0
0000003e (D) C:\Program Files\Polar\Daemon\polard.exe
    00000045    0 <==
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
Backtrace:
=>0 0x004a6ff2 in msvcr90 (+0x36ff2) (0x00a2e960)
  1 0x0035613e in msvcp90 (+0x1613d) (0x00a2e970)
  2 0x00357ec6 in msvcp90 (+0x17ec5) (0x00a2e980)
  3 0x101cdd3a in libpolar (+0x1cdd39) (0x00a2ea18)
  4 0x683afca4 in advapi32 (+0x2fca3) (0x00a2ea68)
  5 0x7bc70480 call_thread_func+0xb() in ntdll (0x00a2ea78)
  6 0x7bc70650 call_thread_entry_point+0x6f() in ntdll (0x00a2eb48)
  7 0x7bc7a325 in ntdll (+0x6a324) (0x00a2f398)
  8 0x6802296e start_thread+0xbd() in libpthread.so.0 (0x00a2f498)
err:msi:ITERATE_StartService Failed to start service L"Polar Daemon" (1053)
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
fixme:msi:msi_dialog_handle_event Unknown progress message 3
err:msi:custom_get_thread_return Invalid Return Code 2
err:msi:ITERATE_Actions Execution halted, action L"ISInstallPrerequisites" returned 1603
```

If anybody has any experience with this type of device or has any insights, please let me know!

Thanks,
Kirk

---

