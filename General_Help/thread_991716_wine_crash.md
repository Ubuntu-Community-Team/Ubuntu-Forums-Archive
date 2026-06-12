---
title: "wine crash"
date: 2008-11-24
forum: General Help
---

### Post by topanda on 2008-11-24
sorry for my english.
i always get a final crash when i use dvdshrink 3.2 under wine 1.1.9 on my ubuntu 8.10.
the backups are well, i've got no problem for this, but - always - when i click on "ok"-button from "backup finished.. saved in folder ecc.." wine crashes.
thanks in advice
bye

this is the code from the terminal

```
cammello@cammello-desktop:~$ wine '/home/cammello/w/DVD Shrink/DVD Shrink 3.2.exe' 
fixme:iphlpapi:NotifyAddrChange (Handle 0x7da589f8, overlapped 0x7da589dc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/cammello/.wine' has been updated.
err:listview:LISTVIEW_WindowProc unknown msg 1044 wp=00000000 lp=0032dd30
fixme:quartz:Videowindow_HideCursor (0x154588/0x154590)->(0): stub !!!
fixme:shell:BrsFolder_OnCreate flags 20 not implemented
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
wine: Unhandled page fault on read access to 0x7dc70c40 at address 0x4325bf (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x7dc70c40 in 32-bit code (0x004325bf).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004325bf ESP:0032fad4 EBP:0032fb0c EFLAGS:00210206(   - 00      - RIP1)
 EAX:00154030 EBX:00000001 ECX:7dc70c40 EDX:0032fae8
 ESI:007c7d10 EDI:007c7d10
Stack dump:
0x0032fad4:  00154030 005087a0 0032fae8 0032fbe8
0x0032fae4:  0050f0c4 00000000 00000000 0032fb60
0x0032faf4:  004ce848 00000001 004b24e9 0032fbe8
0x0032fb04:  004d9830 00000111 0032fb3c 004b260a
0x0032fb14:  007c7d10 00000134 ffffffff 00432550
0x0032fb24:  0032fbe8 0000002c 00000000 007c7d10
Backtrace:
=>1 0x004325bf in dvd shrink 3.2 (+0x325bf) (0x0032fb0c)
  2 0x004b260a in dvd shrink 3.2 (+0xb260a) (0x0032fb3c)
  3 0x004b78b8 in dvd shrink 3.2 (+0xb78b8) (0x0032fb6c)
  4 0x004c2205 in dvd shrink 3.2 (+0xc2205) (0x0032fba4)
  5 0x004b2898 in dvd shrink 3.2 (+0xb2898) (0x0032fbd0)
  6 0x004bb9cd in dvd shrink 3.2 (+0xbb9cd) (0x0032fc24)
  7 0x004bc485 in dvd shrink 3.2 (+0xbc485) (0x0032fcb8)
  8 0x004b015c in dvd shrink 3.2 (+0xb015c) (0x0032fcd8)
  9 0x004bbfd6 in dvd shrink 3.2 (+0xbbfd6) (0x0032fcf8)
  10 0x004af0a1 in dvd shrink 3.2 (+0xaf0a1) (0x0032fd58)
  11 0x004b0a72 in dvd shrink 3.2 (+0xb0a72) (0x0032fd7c)
  12 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fda4)
  13 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fdcc)
  14 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fdf4)
  15 0x004b4998 in dvd shrink 3.2 (+0xb4998) (0x00000000)
0x004325bf: call	*0x0(%ecx)
Modules:
Module	Address			Debug info	Name (106 modules)
PE	  400000-  598000	Export          dvd shrink 3.2
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcac000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcac000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ce37000-7ce46000	Deferred        libgcc_s.so.1
ELF	7db9b000-7dbbc000	Deferred        devenum<elf>
  \-PE	7dba0000-7dbbc000	\               devenum
ELF	7dbbc000-7dc08000	Deferred        dsound<elf>
  \-PE	7dbc0000-7dc08000	\               dsound
ELF	7dcc0000-7dcd5000	Deferred        avicap32<elf>
  \-PE	7dcd0000-7dcd5000	\               avicap32
ELF	7dd36000-7dd5f000	Deferred        msacm32<elf>
  \-PE	7dd40000-7dd5f000	\               msacm32
ELF	7dd5f000-7dd78000	Deferred        msacm32<elf>
  \-PE	7dd60000-7dd78000	\               msacm32
ELF	7dd91000-7dde1000	Deferred        libpulse.so.0
ELF	7dde1000-7ddf6000	Deferred        midimap<elf>
  \-PE	7ddf0000-7ddf6000	\               midimap
ELF	7ddf6000-7ddff000	Deferred        librt.so.1
ELF	7ddff000-7dec7000	Deferred        libasound.so.2
ELF	7ded1000-7ded5000	Deferred        libcap.so.1
ELF	7ded5000-7dedc000	Deferred        libasound_module_pcm_pulse.so
ELF	7dedc000-7df13000	Deferred        winealsa<elf>
  \-PE	7def0000-7df13000	\               winealsa
ELF	7df13000-7dfa7000	Deferred        winmm<elf>
  \-PE	7df20000-7dfa7000	\               winmm
ELF	7dfa7000-7dfc2000	Deferred        version<elf>
  \-PE	7dfb0000-7dfc2000	\               version
ELF	7dfc2000-7dfeb000	Deferred        oledlg<elf>
  \-PE	7dfd0000-7dfeb000	\               oledlg
ELF	7dfeb000-7e0d8000	Deferred        oleaut32<elf>
  \-PE	7e000000-7e0d8000	\               oleaut32
ELF	7e0d8000-7e0dc000	Deferred        libgpg-error.so.0
ELF	7e0dc000-7e145000	Deferred        libgcrypt.so.11
ELF	7e145000-7e157000	Deferred        libtasn1.so.3
ELF	7e157000-7e15b000	Deferred        libkeyutils.so.1
ELF	7e15b000-7e18d000	Deferred        libcrypt.so.1
ELF	7e18d000-7e22a000	Deferred        libgnutls.so.26
ELF	7e22a000-7e24e000	Deferred        libk5crypto.so.3
ELF	7e24e000-7e2e0000	Deferred        libkrb5.so.3
ELF	7e2e0000-7e30a000	Deferred        libgssapi_krb5.so.2
ELF	7e30a000-7e340000	Deferred        libcups.so.2
ELF	7e340000-7e355000	Deferred        lz32<elf>
  \-PE	7e350000-7e355000	\               lz32
ELF	7e379000-7e38d000	Deferred        libresolv.so.2
ELF	7e390000-7e399000	Deferred        libkrb5support.so.0
ELF	7e3a2000-7e3c2000	Deferred        iphlpapi<elf>
  \-PE	7e3b0000-7e3c2000	\               iphlpapi
ELF	7e3c2000-7e429000	Deferred        rpcrt4<elf>
  \-PE	7e3d0000-7e429000	\               rpcrt4
ELF	7e429000-7e53c000	Deferred        ole32<elf>
  \-PE	7e450000-7e53c000	\               ole32
ELF	7e53c000-7e540000	Deferred        libcom_err.so.2
ELF	7e555000-7e58c000	Deferred        winspool<elf>
  \-PE	7e560000-7e58c000	\               winspool
ELF	7e58c000-7e5e9000	Deferred        shlwapi<elf>
  \-PE	7e5a0000-7e5e9000	\               shlwapi
ELF	7e5e9000-7e715000	Deferred        shell32<elf>
  \-PE	7e600000-7e715000	\               shell32
ELF	7e715000-7e7c3000	Deferred        comdlg32<elf>
  \-PE	7e720000-7e7c3000	\               comdlg32
ELF	7e7c3000-7e7f6000	Deferred        uxtheme<elf>
  \-PE	7e7d0000-7e7f6000	\               uxtheme
ELF	7e7f6000-7e7ff000	Deferred        libxcursor.so.1
ELF	7e7ff000-7e804000	Deferred        libxfixes.so.3
ELF	7e804000-7e808000	Deferred        libxcomposite.so.1
ELF	7e808000-7e80f000	Deferred        libxrandr.so.2
ELF	7e80f000-7e819000	Deferred        libxrender.so.1
ELF	7e819000-7e81f000	Deferred        libxxf86vm.so.1
ELF	7e81f000-7e822000	Deferred        libxinerama.so.1
ELF	7e822000-7e843000	Deferred        imm32<elf>
  \-PE	7e830000-7e843000	\               imm32
ELF	7e843000-7e848000	Deferred        libxdmcp.so.6
ELF	7e848000-7e861000	Deferred        libxcb.so.1
ELF	7e861000-7e864000	Deferred        libxcb-xlib.so.0
ELF	7e864000-7e867000	Deferred        libxau.so.6
ELF	7e867000-7e956000	Deferred        libx11.so.6
ELF	7e956000-7e965000	Deferred        libxext.so.6
ELF	7e965000-7e97d000	Deferred        libice.so.6
ELF	7e97d000-7e986000	Deferred        libsm.so.6
ELF	7e99b000-7ea37000	Deferred        winex11<elf>
  \-PE	7e9b0000-7ea37000	\               winex11
ELF	7ea81000-7eaa8000	Deferred        libexpat.so.1
ELF	7eaa8000-7ead5000	Deferred        libfontconfig.so.1
ELF	7ead5000-7eaeb000	Deferred        libz.so.1
ELF	7eaeb000-7eb61000	Deferred        libfreetype.so.6
ELF	7eb76000-7ec16000	Deferred        gdi32<elf>
  \-PE	7eb90000-7ec16000	\               gdi32
ELF	7ec16000-7ed64000	Deferred        user32<elf>
  \-PE	7ec30000-7ed64000	\               user32
ELF	7ed64000-7ee2b000	Deferred        comctl32<elf>
  \-PE	7ed70000-7ee2b000	\               comctl32
ELF	7ee2b000-7ee80000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee80000	\               advapi32
ELF	7efa0000-7efac000	Deferred        libnss_files.so.2
ELF	7efac000-7efc5000	Deferred        libnsl.so.1
ELF	7efc5000-7efeb000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7d97000-b7d9b000	Deferred        libdl.so.2
ELF	b7d9b000-b7ef9000	Deferred        libc.so.6
ELF	b7efa000-b7f13000	Deferred        libpthread.so.0
ELF	b7f28000-b805f000	Deferred        libwine.so.1
ELF	b8061000-b807e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\DVD Shrink\DVD Shrink 3.2.exe
	00000019    0
	00000041    0
	0000002d    0
	00000026   15
	00000025   15
	00000024    0
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x004325bf in dvd shrink 3.2 (+0x325bf) (0x0032fb0c)
  2 0x004b260a in dvd shrink 3.2 (+0xb260a) (0x0032fb3c)
  3 0x004b78b8 in dvd shrink 3.2 (+0xb78b8) (0x0032fb6c)
  4 0x004c2205 in dvd shrink 3.2 (+0xc2205) (0x0032fba4)
  5 0x004b2898 in dvd shrink 3.2 (+0xb2898) (0x0032fbd0)
  6 0x004bb9cd in dvd shrink 3.2 (+0xbb9cd) (0x0032fc24)
  7 0x004bc485 in dvd shrink 3.2 (+0xbc485) (0x0032fcb8)
  8 0x004b015c in dvd shrink 3.2 (+0xb015c) (0x0032fcd8)
  9 0x004bbfd6 in dvd shrink 3.2 (+0xbbfd6) (0x0032fcf8)
  10 0x004af0a1 in dvd shrink 3.2 (+0xaf0a1) (0x0032fd58)
  11 0x004b0a72 in dvd shrink 3.2 (+0xb0a72) (0x0032fd7c)
  12 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fda4)
  13 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fdcc)
  14 0x004b0aa6 in dvd shrink 3.2 (+0xb0aa6) (0x0032fdf4)
  15 0x004b4998 in dvd shrink 3.2 (+0xb4998) (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

---

