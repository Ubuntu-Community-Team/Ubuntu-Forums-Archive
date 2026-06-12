---
title: "Magic Online III on Wine 1.0.1"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Giacecco on 2009-08-04
All, I am trying using Wizard of the Coast's Magic Online III software for Windows on my Dell Mini 9 running Ubuntu 9.04 Netbook Remix.

I have read in several other (but older) threads that the application worked fine on older versions of wine, once a minor issues with some fonts was managed. 

In my case, and using the latest Ubuntu wine package, I had no issues with fonts, the installation completes gracefully, but then launching the actual software ends in a big crash of the application. The output is pasted below.

Any advice? Thank you in advance,

Giacecco


giacecco@giacecco-mini:~$ env WINEPREFIX="/home/giacecco/.wine" wine "C:\Program Files\Wizards of the Coast\Magic Online III\Renamer.exe" 
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:advapi:CheckTokenMembership (0x134 0x147890 0x32d73c) stub!

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object.
   at System.Resources.ResourceManager.GetSatelliteAssembliesFromConfig()
   at System.Resources.ResourceManager.TryLookingForSatellite(CultureInfo lookForCulture)
   at System.Resources.ResourceManager.InternalGetResourceSet(CultureInfo culture, Boolean createIfNotExists, Boolean tryParents)
   at System.Resources.ResourceManager.GetString(String name, CultureInfo culture)
   at System.Environment.ResourceHelper.GetResourceStringCode(Object userDataIn)
   at System.Environment.GetResourceFromDefault(String key)
   at System.TypeInitializationException..ctor(String fullTypeName, Exception innerException)
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)
wine: Unhandled page fault on read access to 0x00000000 at address 0x2dd297f (thread 0033), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x02dd297f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:02dd297f ESP:0032e6c0 EBP:0032e70c EFLAGS:00010293(   - 00      RISA1C)
 EAX:00000000 EBX:00852360 ECX:00851234 EDX:0000040c
 ESI:00000000 EDI:0032e6ec
Stack dump:
0x0032e6c0:  00000000 00000000 00000000 00000000
0x0032e6d0:  00000000 00000000 00000000 00000000
0x0032e6e0:  00000000 00000000 00000000 0032e744
0x0032e6f0:  02dd2885 00000000 0185101c 00852360
0x0032e700:  00852360 0185101c 00000000 0032e744
0x0032e710:  02dd2885 00000000 00853a40 00852360
Backtrace:
=>1 0x02dd297f (0x0032e70c)
  2 0x02dd2885 (0x0032e744)
  3 0x02d38eee (0x0032e798)
  4 0x02d38a77 (0x00851f00)
  5 0x00000018 (0x00399310)
  6 0x00000010 (0x02440002)
  7 0x00000000 (0x00000000)
0x02dd297f: cmpl	%eax,0x0(%esi)
Modules:
Module	Address			Debug info	Name (68 modules)
PE	  400000-  408000	Deferred        renamer
PE	5e380000-5e409000	Deferred        diasymreader
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Deferred        mscorwks
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e39f000-7e3b4000	Deferred        lz32<elf>
  \-PE	7e3a0000-7e3b4000	\               lz32
ELF	7e3b4000-7e3cf000	Deferred        version<elf>
  \-PE	7e3c0000-7e3cf000	\               version
ELF	7e3cf000-7e475000	Deferred        oleaut32<elf>
  \-PE	7e3e0000-7e475000	\               oleaut32
ELF	7e475000-7e48b000	Deferred        libresolv.so.2
ELF	7e49d000-7e4bc000	Deferred        iphlpapi<elf>
  \-PE	7e4a0000-7e4bc000	\               iphlpapi
ELF	7e4bc000-7e51f000	Deferred        rpcrt4<elf>
  \-PE	7e4d0000-7e51f000	\               rpcrt4
ELF	7e51f000-7e5c5000	Deferred        ole32<elf>
  \-PE	7e530000-7e5c5000	\               ole32
ELF	7e7e7000-7e853000	Deferred        msvcrt<elf>
  \-PE	7e800000-7e853000	\               msvcrt
ELF	7e853000-7e85c000	Deferred        libxcursor.so.1
ELF	7e85c000-7e861000	Deferred        libxfixes.so.3
ELF	7e861000-7e865000	Deferred        libxcomposite.so.1
ELF	7e865000-7e86d000	Deferred        libxrandr.so.2
ELF	7e86d000-7e877000	Deferred        libxrender.so.1
ELF	7e877000-7e87a000	Deferred        libxinerama.so.1
ELF	7e87a000-7e89b000	Deferred        imm32<elf>
  \-PE	7e880000-7e89b000	\               imm32
ELF	7e89b000-7e8a0000	Deferred        libxdmcp.so.6
ELF	7e8a0000-7e8ba000	Deferred        libxcb.so.1
ELF	7e8ba000-7e8be000	Deferred        libxau.so.6
ELF	7e8be000-7e8c3000	Deferred        libuuid.so.1
ELF	7e8c3000-7e9b2000	Deferred        libx11.so.6
ELF	7e9b2000-7e9c2000	Deferred        libxext.so.6
ELF	7e9c2000-7e9c8000	Deferred        libxxf86vm.so.1
ELF	7e9c8000-7e9e0000	Deferred        libice.so.6
ELF	7e9e0000-7e9e9000	Deferred        libsm.so.6
ELF	7e9fb000-7ea96000	Deferred        winex11<elf>
  \-PE	7ea10000-7ea96000	\               winex11
ELF	7eae0000-7eb07000	Deferred        libexpat.so.1
ELF	7eb07000-7eb34000	Deferred        libfontconfig.so.1
ELF	7eb34000-7eb4a000	Deferred        libz.so.1
ELF	7eb4a000-7ebc1000	Deferred        libfreetype.so.6
ELF	7ebd3000-7ec73000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec73000	\               gdi32
ELF	7ec73000-7edbf000	Deferred        user32<elf>
  \-PE	7ec90000-7edbf000	\               user32
ELF	7edbf000-7ee1a000	Deferred        shlwapi<elf>
  \-PE	7edd0000-7ee1a000	\               shlwapi
ELF	7ee1a000-7ee6d000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee6d000	\               advapi32
ELF	7ef98000-7efa4000	Deferred        libnss_files.so.2
ELF	7efa4000-7efaf000	Deferred        libnss_nis.so.2
ELF	7efaf000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efee000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7e12000-b7e16000	Deferred        libdl.so.2
ELF	b7e16000-b7f79000	Deferred        libc.so.6
ELF	b7f7a000-b7f93000	Deferred        libpthread.so.0
ELF	b7fa5000-b80dc000	Deferred        libwine.so.1
ELF	b80de000-b80fc000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001f    2
	0000001e    0
0000000c 
	0000001a    0
	0000000e    0
	0000000d    0
00000015 
	0000001d    0
	0000001c    0
	00000019    0
	00000016    0
00000027 
	00000028    0
0000002c 
	0000002f    2
	0000002e    0
00000032 (D) C:\Program Files\Wizards of the Coast\Magic Online III\Renamer.exe
	00000035    2
	00000034    0
	00000033    0 <==
Backtrace:
=>1 0x02dd297f (0x0032e70c)
  2 0x02dd2885 (0x0032e744)
  3 0x02d38eee (0x0032e798)
  4 0x02d38a77 (0x00851f00)
  5 0x00000018 (0x00399310)
  6 0x00000010 (0x02440002)
  7 0x00000000 (0x00000000)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object.
   at System.Resources.ResourceManager.GetSatelliteAssembliesFromConfig()
   at System.Resources.ResourceManager.TryLookingForSatellite(CultureInfo lookForCulture)
   at System.Resources.ResourceManager.InternalGetResourceSet(CultureInfo culture, Boolean createIfNotExists, Boolean tryParents)
   at System.Resources.ResourceManager.GetString(String name, CultureInfo culture)
   at System.Environment.ResourceHelper.GetResourceStringCode(Object userDataIn)
   at System.Environment.GetResourceFromDefault(String key)
   at System.TypeInitializationException..ctor(String fullTypeName, Exception innerException)
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)

Unhandled Exception: System.Threading.SynchronizationLockException: Object synchronization method was called from an unsynchronized block of code.
   at System.Resources.ResourceManager.TryLookingForSatellite(CultureInfo lookForCulture)
   at System.Resources.ResourceManager.InternalGetResourceSet(CultureInfo culture, Boolean createIfNotExists, Boolean tryParents)
   at System.Resources.ResourceManager.GetString(String name, CultureInfo culture)
   at System.Environment.ResourceHelper.GetResourceStringCode(Object userDataIn)
   at System.Environment.GetResourceFromDefault(String key)
   at System.TypeInitializationException..ctor(String fullTypeName, Exception innerException)
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)

---

### Post by Mark Phelps on 2009-08-04
If you're talking about version 3, you're out of luck -- the following CodeWeavers Application Compatibility page shows it's rating as Gargage: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1413]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1413")

---

### Post by Giacecco on 2009-08-05
Thanks Mark, very bad news then. I've checked on Cedega, too, and it is declared as 'working with issues'... sounds like lost of headache.

---

### Post by rvndrk3233 on 2011-03-26
you need Mono 1.2 or .Net 2.0 and wine 1.3. .NET 3.5 will crash(DO NOT INSTALL) and so will LIVE downloader from within winetricks.

There is a missing C library i might be able to attach.Goes into c:/windows/system

furthermore, configure(had to do by hand b/c of winetricks alpha/redraw issues) opengl instead of gdi and enable the few video tweaks that playonlinux does.need to get into regedit to do this.

I got Steam to run Crysis 2 on INTEL hardware with this trick..NOT BAD,EH?
..and it runs fine.

Im getting the Magick card updates now, but its a big SECOND download..almost as slow as ShowUP /5Street, which runs with the C package, but not on this screen size, as does another steam game.

HIGHLY recommend STEAM if your gonna play games on linux.PlayonLinux also.
i have gotten COD4 to work by hand with wine, but PlayonLinux saves time and hassle, so check there FIRST if an install is available.

DO NOT add in GDI or GDI+ modules, and start fresh.(BEST ADVICE)
.NET does not seem to work for me, Im limited to MONO compatible apps.

I run other apps also(Adobe/nook...), and have a valid config now after hours of headache.

---

