---
title: "Problem Starting Up WoW with wine in 8.04"
date: 2008-07-25
forum: General Help
---

### Post by ohmycar on 2008-07-25
I am running ubuntu 8.04 and I have the latest wine installed.
I was able to install World of Warcraft and all its patches successfully, but when I try to run the game, I get this error:

```
Error #132 (0x85100084) Fatal Exception
Exception: 0xC0000005 (Access_Violation) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000"
The memory could not be "read"
```

Then it pops up with the WoWerror Windows and it prints this:

```
==============================================================================
World of WarCraft (build 8606)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jul 25, 2008  2:40:51.709 PM
User:     ashkan
Computer: Devastator
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 8606
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0033F074  EBX=7E04FDCC  ECX=00000000  EDX=00000000  ESI=00000000
EDI=7E031B25  EBP=0033F094  ESP=0033EC08  EIP=00000000  FLG=00210246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 3/3 threads...

--- Thread ID: 40 ---
7BC6909B 7D5D282C 0001:0005809B C:\windows\system32\ntdll.dll
7BC69372 7D5D285C 0001:00058372 C:\windows\system32\ntdll.dll
7B88BF82 7D5D29AC 0001:0006AF82 C:\windows\system32\KERNEL32.dll
7B88C17C 7D5D29CC 0001:0006B17C C:\windows\system32\KERNEL32.dll

--- Thread ID: 39 ---
7B88E1C4 7D6E39B4 0001:0006D1C4 C:\windows\system32\KERNEL32.dll
7B88E215 7D6E39D4 0001:0006D215 C:\windows\system32\KERNEL32.dll
0065EF34 7D6E3A30 0001:0025DF34 C:\Program Files\World of Warcraft\Wow.exe
0075FDD4 7D6E3A48 0001:0035EDD4 C:\Program Files\World of Warcraft\Wow.exe
7BC6B6B2 7D6E3AE8 0001:0005A6B2 C:\windows\system32\ntdll.dll
7BC6B8E2 7D6E43D8 0001:0005A8E2 C:\windows\system32\ntdll.dll
B7E524FB 7D6E44C8 0000:00000000 <unknown>

--- Thread ID: 38 [Current Thread] ---
00000000 0033F094 0000:00000000 C:\Program Files\World of Warcraft\Wow.exe
7E022E42 0033F0C4 0001:000C1E42 C:\windows\system32\wined3d.dll
7E0674C7 0033F0F4 0001:000064C7 C:\windows\system32\d3d9.dll
005A437A 0033F108 0001:001A337A C:\Program Files\World of Warcraft\Wow.exe
0059EB57 0033F730 0001:0019DB57 C:\Program Files\World of Warcraft\Wow.exe
0064107A 0033FB64 0001:0024007A C:\Program Files\World of Warcraft\Wow.exe
0063D57F 0033FC14 0001:0023C57F C:\Program Files\World of Warcraft\Wow.exe
0040673D 0033FE5C 0001:0000573D C:\Program Files\World of Warcraft\Wow.exe
00406846 0033FE6C 0001:00005846 C:\Program Files\World of Warcraft\Wow.exe
00406898 0033FF08 0001:00005898 C:\Program Files\World of Warcraft\Wow.exe
7B8776A7 0033FFE8 0001:000566A7 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 3/3 threads...

--- Thread ID: 40 ---
7BC6909B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7D5D2894,0x00000004,0x00000000)
7BC69372 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7D5D2894,0x00000000,0x00000000)
7B88BF82 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7D5D29D4,0x00000000,0xFFFFFFFF)
7B88C17C KERNEL32.dll WaitForSingleObject+60 (0x000020BC,0xFFFFFFFF,0x7BC89464,0x0075FD55)

--- Thread ID: 39 ---
7B88E1C4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7D6E39D4,0x7B854F97)
7B88E215 KERNEL32.dll Sleep+37 (0x00000064,0x0075FD55,0x7BC89464,0x01200BD8)
0065EF34 Wow.exe      <unknown symbol>+0 (0x01200C10,0x7BC6B01E,0x01200C10,0x01200C10)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x01200C10,0x10012A03,0x00000000)
7BC6B6B2 ntdll.dll    <unknown symbol>+0 (0x7D6E3B1C,0x00000000,0x00000000,0x00000000)
7BC6B8E2 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7D6E4490,0x7D6E4490,0x7D6E4490)
B7E524FB              start_thread+203 (0x7D6E4B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 [Current Thread] ---
7E022E42 wined3d.dll  WineDirect3DCreate+34 (0x00000020,0x00000009,0x001389E0,0x7B867E0D)
7E0674C7 d3d9.dll     Direct3DCreate9+119 (0x00000020,0x00D68F4C,0x00000000,0x0033F730)
005A437A Wow.exe      <unknown symbol>+0 (0x0033F128,0x0033F130,0x00D68F4C,0x00D68F4E)
0059EB57 Wow.exe      <unknown symbol>+0 (0x00D68F4C,0x00D68F4E,0x00D68F50,0x00D68F54)
0064107A Wow.exe      <unknown symbol>+0 (0x00D68F4C,0x00D6925D,0x008C9048,0x008C9054)
0063D57F Wow.exe      <unknown symbol>+0 (0x0033FC28,0x00000001,0x00000001,0x6C726F57)
0040673D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x00406898)
00406846 Wow.exe      <unknown symbol>+0 (0x0040A4E9,0x00400000,0x00000000,0x00111A3C)
00406898 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B8776A7 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EC8000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B931000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA5000  C:\windows\system32\ntdll.dll
0x7D470000 - 0x7D479000  C:\windows\system32\psapi.dll
0x7D480000 - 0x7D4C3000  C:\windows\system32\dbghelp.dll
0x7D710000 - 0x7D73C000  C:\windows\system32\uxtheme.dll
0x7D7C0000 - 0x7D7CD000  C:\windows\system32\midimap.dll
0x7D7D0000 - 0x7D7E4000  C:\windows\system32\msacm32.drv
0x7D8C0000 - 0x7D8E9000  C:\windows\system32\winealsa.drv
0x7D920000 - 0x7D9A9000  C:\windows\system32\winex11.drv
0x7DAE0000 - 0x7DB30000  C:\windows\system32\rpcrt4.dll
0x7DB40000 - 0x7DBD4000  C:\windows\system32\ole32.dll
0x7DBE0000 - 0x7DBFA000  C:\windows\system32\msacm32.dll
0x7DC20000 - 0x7DC38000  C:\windows\system32\iphlpapi.dll
0x7DC40000 - 0x7DC64000  C:\windows\system32\ws2_32.dll
0x7DC70000 - 0x7DD24000  C:\windows\system32\comctl32.dll
0x7DD30000 - 0x7DE39000  C:\windows\system32\shell32.dll
0x7DE50000 - 0x7DE92000  C:\windows\system32\shlwapi.dll
0x7DEA0000 - 0x7DEB3000  C:\windows\system32\mpr.dll
0x7DEC0000 - 0x7DF02000  C:\windows\system32\wininet.dll
0x7DF10000 - 0x7DF22000  C:\windows\system32\imm32.dll
0x7DF30000 - 0x7DF36000  C:\windows\system32\lz32.dll
0x7DF40000 - 0x7DF4F000  C:\windows\system32\version.dll
0x7DF60000 - 0x7E052000  C:\windows\system32\wined3d.dll
0x7E060000 - 0x7E082000  C:\windows\system32\d3d9.dll
0x7EB40000 - 0x7EBAC000  C:\windows\system32\opengl32.dll
0x7EBC0000 - 0x7EBFE000  C:\windows\system32\advapi32.dll
0x7EC10000 - 0x7EC9C000  C:\windows\system32\gdi32.dll
0x7ECC0000 - 0x7EDE3000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE75000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000000)

00000000: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0033EC08)

* = addr                            **                                *       
0033EC00: 00 00 00 00  00 00 00 00  ED 1A FB 7D  01 00 00 00  ...........}....
0033EC10: 74 F0 33 00  08 19 00 00  04 00 00 00  04 00 00 00  t.3.............
0033EC20: 00 00 00 00  E1 80 00 00  67 83 00 00  00 00 00 00  ........g.......
0033EC30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EC40: 10 ED 33 00  64 94 C8 7B  00 04 00 00  C4 A2 D7 7E  ..3.d..{.......~
0033EC50: 90 EC 33 00  20 03 00 00  FC 15 03 7E  78 F0 33 00  ..3. ......~x.3.
0033EC60: 74 F0 33 00  44 F0 33 00  1C F0 33 00  C0 EC 33 00  t.3.D.3...3...3.
0033EC70: 44 00 00 00  C8 3B CA 7B  70 0A 05 7E  DC EF 33 00  D....;.{p..~..3.
0033EC80: 20 03 00 00  A8 A6 13 00  C8 3B CA 7B  0C 3C CA 7B   ........;.{.<.{
0033EC90: 00 00 00 00  48 03 00 00  5C 00 5C 00  2E 00 5C 00  ....H...\.\...\.
0033ECA0: 44 00 49 00  53 00 50 00  4C 00 41 00  59 00 31 00  D.I.S.P.L.A.Y.1.
0033ECB0: 00 00 33 00  80 ED 33 00  1E 00 00 00  C4 A2 D7 7E  ..3...3........~
0033ECC0: F0 EC 33 00  00 4E C3 7B  C4 A2 D7 7E  48 ED 33 00  ..3..N.{...~H.3.
0033ECD0: E1 88 DA 7E  2C ED 33 00  58 00 31 00  31 00 20 00  ...~,.3.X.1.1. .
0033ECE0: 57 00 69 00  6E 00 64 00  6F 00 77 00  69 00 6E 00  W.i.n.d.o.w.i.n.
0033ECF0: 67 00 20 00  53 00 79 00  73 00 74 00  65 00 6D 00  g. .S.y.s.t.e.m.
0033ED00: 00 00 FD 7F  E0 89 13 00  48 ED 33 00  AC 44 F9 B7  ........H.3..D..
0033ED10: E0 89 13 00  64 ED 33 00  CF 30 C4 7B  00 00 00 00  ....d.3..0.{....
0033ED20: 70 ED 33 00  20 1C 00 00  14 00 11 00  20 8B 13 00  p.3. ....... ...
0033ED30: 30 A7 13 00  00 00 11 00  22 A3 E7 B7  AC 44 F9 B7  0......."....D..
0033ED40: 68 00 00 00  64 ED 33 00  34 AA E7 B7  48 00 00 00  h...d.3.4...H...
0033ED50: 00 00 03 00  58 1D 00 00  14 00 11 00  E8 89 13 00  ....X...........
0033ED60: 10 8B 13 00  00 00 11 00  64 94 C8 7B  D8 89 13 00  ........d..{....
0033ED70: 38 01 00 00  C4 ED 33 00  A6 27 C4 7B  04 00 00 00  8.....3..'.{....
0033ED80: 00 00 00 00  40 00 00 00  85 0F C4 7B  40 1A C9 7B  ....@......{@..{
0033ED90: 64 94 C8 7B  C4 ED 33 00  4E 18 C4 7B  8C 8A 13 00  d..{..3.N..{....
0033EDA0: F4 09 23 00  14 00 11 00  C1 3E C3 7B  2E 00 5C 00  ..#......>.{..\.
0033EDB0: 44 00 49 00  14 00 11 00  6F 38 C3 7B  14 00 11 00  D.I.....o8.{....
0033EDC0: 64 94 C8 7B  04 EE 33 00  37 2A C4 7B  48 00 11 00  d..{..3.7*.{H...
0033EDD0: 00 00 00 00  00 00 00 00  15 00 00 00  00 00 00 00  ................
0033EDE0: 00 00 0A FF  DD 6A C4 7B  6F 38 C3 7B  00 00 00 00  .....j.{o8.{....
0033EDF0: 00 00 11 00  02 00 00 00  88 48 8B 7B  00 00 00 00  .........H.{....
0033EE00: A4 F0 33 00  24 EE 33 00  FF 0E 85 7B  00 00 11 00  ..3.$.3....{....
0033EE10: 00 00 00 00  E0 89 13 00  88 48 8B 7B  00 00 00 00  .........H.{....
0033EE20: A4 F0 33 00  84 F0 33 00  43 7A 86 7B  00 00 11 00  ..3...3.Cz.{....
0033EE30: 00 00 00 00  E0 89 13 00  74 F0 33 00  83 4F D6 B7  ........t.3..O..
0033EE40: EC F3 33 00  EC F3 33 00  D8 F5 33 00  F4 7F E4 B7  ..3...3...3.....
0033EE50: 74 F0 33 00  00 00 00 00  E0 89 13 00  CF B7 D3 B7  t.3.............
0033EE60: 94 F4 33 00  31 3D D7 7E  00 00 00 00  00 00 00 00  ..3.1=.~........
0033EE70: 31 3D D7 7E  00 00 00 00  00 00 00 00  D4 FF FF FF  1=.~............
0033EE80: D4 FF FF FF  D4 FF FF FF  D4 FF FF FF  D4 FF FF FF  ................
0033EE90: FF CF D3 B7  46 00 00 00  90 02 22 00  FF CF D3 B7  ....F.....".....
0033EEA0: 00 00 00 00  EC F3 33 00  BC EE 33 00  66 18 C8 7B  ......3...3.f..{
0033EEB0: F8 F3 33 00  CE 01 00 00  00 00 00 00  70 02 00 00  ..3.........p...
0033EEC0: 5C 00 50 00  28 F5 33 00  6E 02 00 00  61 00 6D 00  \.P.(.3.n...a.m.
0033EED0: 34 F5 33 00  6F 38 C3 7B  00 8C FD 7F  00 00 C8 7B  4.3.o8.{.......{
0033EEE0: F0 EE 33 00  A0 8C C5 7B  15 00 00 00  00 00 FF FF  ..3....{........
0033EEF0: 03 00 00 00  31 3D D7 7E  2F 3D D7 7E  00 00 00 00  ....1=.~/=.~....
0033EF00: EC F3 33 00  00 00 00 00  19 00 00 00  00 00 00 00  ..3.............
0033EF10: 00 00 00 00  00 00 00 00  0A 00 00 00  E9 F3 33 00  ..............3.
0033EF20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EF30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033EF40: 00 00 00 00  00 00 00 00  20 00 00 00  00 00 00 00  ........ .......
0033EF50: 00 00 00 00  20 00 00 00  70 F1 33 75  94 EF 33 00  .... ...p.3u..3.
0033EF60: A4 99 E5 B7  2C 00 00 75  91 7D D2 B7  04 00 00 00  ....,..u.}......
0033EF70: 70 F1 33 00  2C 00 00 00  64 94 C8 7B  00 00 06 7E  p.3.,...d..{...~
0033EF80: 50 F0 33 00  B7 5B C4 7B  A8 EF 33 00  00 00 00 00  P.3..[.{..3.....
0033EF90: A8 EF 33 00  64 F0 33 00  08 3D C6 7B  F8 FE 33 00  ..3.d.3..=.{..3.
0033EFA0: B0 6E C4 7B  00 00 00 00  64 94 C8 7B  00 00 06 7E  .n.{....d..{...~
0033EFB0: 00 00 00 00  50 F0 33 00  FE 11 DF 73  09 6F B7 9C  ....P.3....s.o..
0033EFC0: 00 00 00 00  90 FE 8B 00  00 00 00 00  F0 92 E4 B7  ................
0033EFD0: A4 8D E7 B7  70 F5 33 00  64 94 C8 7B  28 00 01 00  ....p.3.d..{(...
0033EFE0: 2D 00 00 00  00 20 08 10  08 08 08 00  00 00 40 10  -.... ........@.
0033EFF0: 10 10 10 18  08 04 00 00  00 00 00 00  00 00 00 00  ................
0033F000: 00 00 00 00  2A 00 00 00  64 94 C8 7B  10 00 00 00  ....*...d..{....


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3851

Percent memory used:    12
Total physical memory:  2124455936
Free Memory:            1848373248
Page file:              4047757312
Total virtual memory:   2147352575
```

Any ideas on how to fix this? I tried disabling desktop effects and rolling back from nvidia-glx-new to just nvidia-glx and still no luck.

I have got the cinematics before the login screen to play through, but after that I get this error. Any help or suggestions would be greatly appreciated. :)

Edit: My computer specs are in my signature

---

### Post by tye959 on 2008-07-25
YES! I have 7.10 hardy and it does almost the exact same thing. Wont let me open wow AT ALL. Although, I haven't installed the patch yet but I don't think that has anything to do with it. Unfortunately, I am still looking for a solution too. =(

---

### Post by ohmycar on 2008-07-27
Yeah, it is very annoying heh. I am still seeking a resolution to this. I have to go back to the nvidia-glx-new also since my resolution now is at a horrific 640x480!! Any help would be appreciated.

Edit: So I rolled back to nvidia-glx-new and my resolution could not go higher than 640x480, so I went back to just nvidia-glx and I enabled the prop. drivers for the card and still no luck with the resoltuon. :( any suggestions?

---

### Post by faceonkeyboard on 2008-08-01
I have this exact same issue, exact same error on the situation.

Error #132 (0x85100084) Fatal Exception
Exception: 0xC0000005 (Access_Violation) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000"
The memory could not be "read"

---

### Post by trickyD on 2008-08-18
The only way I could get it to work was to run it directly from my Windows NTFS drive; seemed to work fine then.

Copy it to a linux filesystem and try and run it from there and it wasn't having it at all; failed with the a similar error to above. Very bizarre indeed.

---

### Post by Dark Hornet on 2008-08-18
The best and easiest way I have found to install and play WoW is to simply copy the entire WoW folder from a windows install, and paste it to your WINE directory.  From there, just do a couple of edits to your "config.wtf" file, and you should be good to go.  In fact, I get much better frame rates now than I ever did under Win XP.

Good luck!

---

### Post by triphazard on 2008-09-24
I've just tried installing WoW on Ybuntu 8.04 and am experiencing exactly the same problem.  I don't suppose anyone out there has a working solution do they?

Copying from a Windows installation is a little tricky when you don't have one.

---

