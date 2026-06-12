---
title: "Installing Ubuntu"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by mrrinmoy on 2009-01-16
When i install ubuntu (6.10,7.04,7.10,8.04,8.10) its working fine but after some time
its hanged .

Intel P4 3.00 GHz, i386(32 bit)
RAM-512MB
Motherboard-Original Intel D101GGC
Graphic-ATI
Sound-Realtk.
SATA80GB

But Ubuntu recommd to install 256MB of ram 4GB free Space.

Tell some solution.

---

### Post by Sef on 2009-01-16
When does it hang exactly?

---

### Post by mrrinmoy on 2009-01-16
> **Sef said:**
> When does it hang exactly?

after 2 or 5 min .

---

### Post by mrrinmoy on 2009-01-16
> **mrrinmoy said:**
> after 2 or 5 min .

Pls Help me out

---

### Post by mrrinmoy on 2009-01-16
> **mrrinmoy said:**
> Pls Help me out

Any Solution?

---

### Post by linux_tech on 2009-01-16
try the alternate cd install
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
or [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

ubuntu-8.10-alternate-i386.iso

---

### Post by mrrinmoy on 2009-01-16
> **linux_tech said:**
> try the alternate cd install
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
or [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

ubuntu-8.10-alternate-i386.iso

I have this not only ubuntu-8.10-alternate-i386 i have all version of Ubuntu
but same problem.

---

### Post by Fuzzman on 2009-01-16
Does it hang after you do something specific or is it random?

---

### Post by abhilashm86 on 2009-01-17
have u installed ubuntu in separate drive and boot everything fine?maybe u need to partion using exe32(check while partioning)format.Are u able to use application programs and terminal?

---

### Post by abhilashm86 on 2009-01-17
can u post your boot file,through terminal type
 vim /boot/grub/menu.lst
check the partitions before u install,did u give correct mounting point?

---

### Post by mrrinmoy on 2009-01-18
> **abhilashm86 said:**
> can u post your boot file,through terminal type
 vim /boot/grub/menu.lst
check the partitions before u install,did u give correct mounting point?

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fdc26dcc-34ab-4f07-867c-4f8222e5b094 ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mrrinmoy on 2009-01-18
> **mrrinmoy said:**
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fdc26dcc-34ab-4f07-867c-4f8222e5b094 ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Pls help I love ubuntu very much because its faster than any linux disto....

---

### Post by mrrinmoy on 2009-01-19
> **mrrinmoy said:**
> Pls help I love ubuntu very much because its faster than any linux disto....

can any1 help me out :(:(:(:(:(:(

---

### Post by mrrinmoy on 2009-03-09
plsssssssssssssssssssssssssss

---

### Post by mrrinmoy on 2009-03-09
> **mrrinmoy said:**
> plsssssssssssssssssssssssssss

help:(:(:(:(:(:(:(

---

### Post by asteonaut on 2009-03-09
Try booting it in verbose mode.
It helped for me.

---

### Post by mrrinmoy on 2009-03-09
> **asteonaut said:**
> Try booting it in verbose mode.
It helped for me.
i tried this ways too but not works

---

### Post by mrrinmoy on 2009-08-28
Pls help

---

### Post by mrrinmoy on 2009-08-28
--------------------------------------------------------------------------------
                                     ***  Common Devices ***
--------------------------------------------------------------------------------

                         Processor Name:       Intel(R) Pentium(R) 4 CPU 3.00GHz
                         Videocard Name:       ATI RADEON XPRESS 200 Series
                       Installed Memory:       446.48 MB

--------------------------------------------------------------------------------
                                 ***  Installed Programs ***
--------------------------------------------------------------------------------

           Number of Installed Programs:       87 programs
            Number of Running Processes:       39 processes
              Internet Explorer Version:       7.0.5730.13 (0)
                        DirectX Version:       4.09.00.0904
                         Office Version:       12.0.4518.1014

--------------------------------------------------------------------------------
                                    ***  Windows Details ***
--------------------------------------------------------------------------------

                        Windows Version:       Windows XP (5.1.2600) Professional
          Latest Service Pack Installed:       Service Pack 3
                              Installed:       8/4/2009 7:14:28 PM
                            Last Reboot:       8/28/2009 1:16:44 PM
                Default Internet Client:       C:\Program Files\Internet Explorer\iexplore.exe
                             Product ID:       55274-640-8365391-23271
                            Product Key:       
                               Language:       English (United States) (ID: $0409)
                                Country:       United States (Country Code: 1)
                              Time zone:       (GMT+05:30) Chennai, Kolkata, Mumbai, New Delhi

--------------------------------------------------------------------------------
                                       ***  User Details ***
--------------------------------------------------------------------------------

                          Registered To:       ----------
                           Organization:       ----------
                              User Name:       sam
                          Computer Name:       ----------

--------------------------------------------------------------------------------
                                        ***  Environment ***
--------------------------------------------------------------------------------

                         ALLUSERSPROFILE       C:\Documents and Settings\All Users
                                 APPDATA       C:\Documents and Settings\sam\Application Data
                           ArmServerInfo       000C046E
                              CLIENTNAME       Console
                      CommonProgramFiles       C:\Program Files\Common Files
                            COMPUTERNAME       ----------
                                 ComSpec       C:\WINDOWS\system32\cmd.exe
                        FP_NO_HOST_CHECK       NO
                               HOMEDRIVE       C:
                                HOMEPATH       \Documents and Settings\sam
                             LOGONSERVER       \\----------
                    NUMBER_OF_PROCESSORS       2
                                      OS       Windows_NT
                                    Path       C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;
                                 PATHEXT       .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH
                  PROCESSOR_ARCHITECTURE       x86
                    PROCESSOR_IDENTIFIER       x86 Family 15 Model 6 Stepping 5, GenuineIntel
                         PROCESSOR_LEVEL       15
                      PROCESSOR_REVISION       0605
                            ProgramFiles       C:\Program Files
                             SESSIONNAME       Console
                             SystemDrive       C:
                              SystemRoot       C:\WINDOWS
                                    TEMP       C:\DOCUME~1\sam\LOCALS~1\Temp
                                     TMP       C:\DOCUME~1\sam\LOCALS~1\Temp
                              USERDOMAIN       ----------
                                USERNAME       sam
                             USERPROFILE       C:\Documents and Settings\sam
                                  windir       C:\WINDOWS
                          __COMPAT_LAYER       EnableNXShowUI

--------------------------------------------------------------------------------
                                     ***  System Folders ***
--------------------------------------------------------------------------------

                                 AppData       C:\Documents and Settings\sam\Application Data
                              CDBurnArea       C:\Documents and Settings\sam\Local Settings\Application Data\Microsoft\CD Burning
                        CommonAdminTools       C:\Documents and Settings\All Users\Start Menu\Programs\Administrative Tools
                        CommonDesktopDir       C:\Documents and Settings\All Users\Desktop
                           CommonAppData       C:\Documents and Settings\All Users\Application Data
                         CommonDocuments       C:\Documents and Settings\All Users\Documents
                         CommonFavorites       C:\Documents and Settings\All Users\Favorites
                             CommonMusic       C:\Documents and Settings\All Users\Documents\My Music
                          CommonPictures       C:\Documents and Settings\All Users\Documents\My Pictures
                         CommonStartMenu       C:\Documents and Settings\All Users\Start Menu
                           CommonStartup       C:\Documents and Settings\All Users\Start Menu\Programs\Startup
                         CommonTemplates       C:\Documents and Settings\All Users\Templates
                             CommonVideo       C:\Documents and Settings\All Users\Documents\My Videos
                                 Cookies       C:\Documents and Settings\sam\Cookies
                                 Desktop       C:\Documents and Settings\sam\Desktop
                              DesktopDir       C:\Documents and Settings\sam\Desktop
                               Favorites       C:\Documents and Settings\sam\Favorites
                                   Fonts       C:\WINDOWS\Fonts
                                 History       C:\Documents and Settings\sam\Local Settings\History
                           InternetCache       C:\Documents and Settings\sam\Local Settings\Temporary Internet Files
                            LocalAppData       C:\Documents and Settings\sam\Local Settings\Application Data
                                 NetHood       C:\Documents and Settings\sam\NetHood
                                 MyMusic       C:\Documents and Settings\sam\My Documents\My Music
                              MyPictures       C:\Documents and Settings\sam\My Documents\My Pictures
                                 MyVideo       C:\Documents and Settings\sam\My Documents\My Videos
                                Personal       C:\Documents and Settings\sam\My Documents
                               PrintHood       C:\Documents and Settings\sam\PrintHood
                                Programs       C:\Documents and Settings\sam\Start Menu\Programs
                                 Profile       C:\Documents and Settings\sam
                            ProgramFiles       C:\Program Files
                      ProgramFilesCommon       C:\Program Files\Common Files
                                  Recent       C:\Documents and Settings\sam\Recent
                                  SendTo       C:\Documents and Settings\sam\SendTo
                               StartMenu       C:\Documents and Settings\sam\Start Menu
                                 StartUp       C:\Documents and Settings\sam\Start Menu\Programs\Startup
                                  System       C:\WINDOWS\system32
                                 Windows       C:\WINDOWS
                               Templates       C:\Documents and Settings\sam\Templates

--------------------------------------------------------------------------------
                                        ***  CPU Details ***
--------------------------------------------------------------------------------

                    Physical Processors:       1
                     Logical Processors:       2
                       Processor Vendor:       Intel(R) Corporation
                         Processor Name:       Intel(R) Pentium(R) 4 CPU 3.00GHz
                        Additional Name:       x86 Family 15 Model 6 Stepping 5
                           Popular Name:       Pentium D
                              Frequency:       3420 MHz
                          Serial Number:       0000-0F65-BFEB-FBFF-0000-E59D

--------------------------------------------------------------------------------
                                  ***  CPU Cache Details ***
--------------------------------------------------------------------------------

                          Cache Level I:       16 KB
                         Cache Level II:       2,048 KB

--------------------------------------------------------------------------------
                                       ***  BIOS Details ***
--------------------------------------------------------------------------------

                            BIOS Vendor:       Award BIOS for Intel
                              BIOS Type:       AT/AT COMPATIBLE
                           BIOS Version:       GC11010N.86A.0311.2006.0420.1525
                              Copyright:       ATi - 42302e31
                                   Date:       04/20/2006
                                   Size:       512 KB

--------------------------------------------------------------------------------
                                ***  Motherboard Details ***
--------------------------------------------------------------------------------

                     Motherboard Vendor:       Intel Corporation
                      Motherboard Model:       D101GGC
                                Version:       AAD35788-310
                                 Serial:       BTGC634016ZJ
                                  Ports:       29
                           System Slots:       4

--------------------------------------------------------------------------------
                                     ***  Memory Modules ***
--------------------------------------------------------------------------------

                 Memory Devices Present:       2
                         Memory Device #       0
                         Device Locator:       A0
                           Bank Locator:       Bank0/1
                           Manufacturer:       None
                          Serial Number:       None
                            Part Number:       None
                     Memoty Device Type:       DDR
                            Total Width:       64 bits
                             Data Width:       64 bits
                                   Size:       512 MB
                                  Speed:       5 ns
                            Form Factor:       DIMM
                         Memory Device #       1
                         Device Locator:       A1
                           Bank Locator:       Bank2/3
                           Manufacturer:       None
                          Serial Number:       None
                            Part Number:       None
                     Memoty Device Type:       Unknown
                            Total Width:       65535 bits
                             Data Width:       65535 bits
                                   Size:       0 MB
                                  Speed:       0 ns
                            Form Factor:       DIMM
                        Total Installed:       512 MB

--------------------------------------------------------------------------------
                                   ***  Extented Details ***
--------------------------------------------------------------------------------

                             Technology:       90 nm
                           Architecture:       x86 Family
                               Stepping:       5
                                APIC ID:       0
                            Physical ID:       0
                             Logical ID:       0
                      Cores per Package:       1
              Logical Units per Package:       2

--------------------------------------------------------------------------------
                                     ***  CPU Properties ***
--------------------------------------------------------------------------------

                     Floating point unit       Supported
                  Virtual mode extension       Supported
                    Debugging extensions       Supported
                     Page size extension       Supported
                      Time stamp counter       Supported
              Machine specific registers       Supported
              Physical address extension       Supported
                 Machine check extension       Supported
             CMPXCHG8 instrucion support       Supported
                                    APIC       Supported
     Fast system call (SYSENTER/SYSEXIT)       Supported
             Memory type range registers       Supported
                   Page global extension       Supported
                Conditional move support       Supported
                    Page attribute table       Supported
              36-bit page size extension       Supported
                 Processor serial number       Not Supported
             CLFLUSH instruction support       Supported
                       Debug trace store       Supported
Thermal monitor and software controlled clock       Supported
                MMX architecture support       Supported
Fast floating point save (FXSAVE/FXRSTOR)       Supported
      Streaming SIMD instruction support       Supported
             Streaming SIMD extensions 2       Supported
                              Self snoop       Supported
              Hyper-Threading technology       Supported
                 Thermal monitor support       Supported
                             IA-64 Intel       Not Supported
                    Signal break on FERR       Supported
             Streaming SIMD extensions 3       Supported
                           MONITOR/MWAIT       Supported
               CPL qualified debug store       Supported
               Virtual machine extension       Not Supported
           Enhanced SpeedStep Technology       Supported
                       Thermal Monitor 2       Supported
                              Context Id       Supported
           CMPXCHG16B instrucion support       Supported
             Send task priority messages       Supported
                 Multiprocessing capable       Not Supported
              No execute page protection       Supported
               Extended MMX architecture       Not Supported
                             AMD64/EM64T       Supported
              Extended 3DNow! extensions       Not Supported
                       3DNow! extensions       Not Supported
                       LAHF/SAHF support       Supported
             Core multiprocessing legacy       Not Supported
                      Temperature sensor       Not Supported
                    Frequency id Control       Not Supported
                      Voltage id Control       Not Supported
                            Thermal trip       Not Supported
                Software thermal control       Not Supported
                           Invariant TSC       Not Supported

--------------------------------------------------------------------------------
                               ***  Videoadapter Details ***
--------------------------------------------------------------------------------

                     Video Adapter Name:       ATI RADEON XPRESS 200 Series
                           Video Memory:       256.00 MB
                           Chipset Name:       ATI display adapter (0x5A61)
                              BIOS Name:       BK-ATI VER008.046I.003.000
                              BIOS Date:       05/09/08
                     Current Resolution:       1024 x 768 pixels
                     Current Color Mode:       32 bits per pixel
                        DirectX Version:       4.09.00.0904

--------------------------------------------------------------------------------
                                    ***  Monitor Details ***
--------------------------------------------------------------------------------

                         Driver Version:       16384
                             Technology:       Raster Display
                           Refresh Rate:       75 Hz
                        Font Resolution:       96 dpi
        Width/Height/Diagonal in Pixels:       36/36/51
                        Horizontal Size:       330
                          Vertical Size:       250

--------------------------------------------------------------------------------
                              ***  Supported Resolutions ***
--------------------------------------------------------------------------------

                       320 x 200 - 8 bit       Supported
                      320 x 200 - 16 bit       Supported
                      320 x 200 - 32 bit       Supported
                       320 x 240 - 8 bit       Supported
                      320 x 240 - 16 bit       Supported
                      320 x 240 - 32 bit       Supported
                       400 x 300 - 8 bit       Supported
                      400 x 300 - 16 bit       Supported
                      400 x 300 - 32 bit       Supported
                       512 x 384 - 8 bit       Supported
                      512 x 384 - 16 bit       Supported
                      512 x 384 - 32 bit       Supported
                       640 x 400 - 8 bit       Supported
                      640 x 400 - 16 bit       Supported
                      640 x 400 - 32 bit       Supported
                       640 x 480 - 8 bit       Supported
                      640 x 480 - 16 bit       Supported
                      640 x 480 - 32 bit       Supported
                       800 x 600 - 8 bit       Supported
                      800 x 600 - 16 bit       Supported
                      800 x 600 - 32 bit       Supported
                      1024 x 768 - 8 bit       Supported
                     1024 x 768 - 16 bit       Supported
                     1024 x 768 - 32 bit       Supported
                      1152 x 864 - 8 bit       Supported
                     1152 x 864 - 16 bit       Supported
                     1152 x 864 - 32 bit       Supported
                      1280 x 768 - 8 bit       Supported
                     1280 x 768 - 16 bit       Supported
                     1280 x 768 - 32 bit       Supported
                      1280 x 960 - 8 bit       Supported
                     1280 x 960 - 16 bit       Supported
                     1280 x 960 - 32 bit       Supported
                     1280 x 1024 - 8 bit       Supported
                    1280 x 1024 - 16 bit       Supported
                    1280 x 1024 - 32 bit       Supported
                       640 x 480 - 4 bit       Supported
                       800 x 600 - 4 bit       Supported

--------------------------------------------------------------------------------
                                      ***  Text Features ***
--------------------------------------------------------------------------------

   Capable of Character Output Precision       Supported
      Capable of Stroke Output Precision       Supported
        Capable of Stroke Clip Precision       Supported
   Supports 90 Degree Character Rotation       Not Supported
Supports Character Rotation to Any Angle       Not Supported
               X And Y Scale Independent       Not Supported
      Supports Doubled Character Scaling       Not Supported
Supports Integer Multiples Only When Scaling       Not Supported
Supports Any Multiples For Exact Character Scaling       Not Supported
       Supports Double Weight Characters       Not Supported
                        Supports Italics       Not Supported
                     Supports Underlines       Supported
                     Supports Strikeouts       Supported
                   Supports Raster Fonts       Supported
                   Supports Vector Fonts       Supported
                Cannot Scroll Using Blts       Not Supported

--------------------------------------------------------------------------------
                                   ***  Polygon Features ***
--------------------------------------------------------------------------------

   Capable of Character Output Precision       Supported
      Capable of Stroke Output Precision       Supported
        Capable of Stroke Clip Precision       Supported
   Supports 90 Degree Character Rotation       Not Supported
Supports Character Rotation to Any Angle       Not Supported
               X And Y Scale Independent       Not Supported
      Supports Doubled Character Scaling       Not Supported
Supports Integer Multiples Only When Scaling       Not Supported
Supports Any Multiples For Exact Character Scaling       Not Supported
       Supports Double Weight Characters       Not Supported
                        Supports Italics       Not Supported
                     Supports Underlines       Supported
                     Supports Strikeouts       Supported
                   Supports Raster Fonts       Supported
                   Supports Vector Fonts       Supported
                Cannot Scroll Using Blts       Not Supported
                 Alternate Fill Polygons       Supported
                              Rectangles       Supported
                   Winding Fill Polygons       Supported
                        Single Scanlines       Supported
                            Wide Borders       Supported
                          Styled Borders       Supported
                 Wide and Styled Borders       Supported
                               Interiors       Supported

--------------------------------------------------------------------------------
                                    ***  Raster Features ***
--------------------------------------------------------------------------------

   Capable of Character Output Precision       Supported
      Capable of Stroke Output Precision       Supported
        Capable of Stroke Clip Precision       Supported
   Supports 90 Degree Character Rotation       Not Supported
Supports Character Rotation to Any Angle       Not Supported
               X And Y Scale Independent       Not Supported
      Supports Doubled Character Scaling       Not Supported
Supports Integer Multiples Only When Scaling       Not Supported
Supports Any Multiples For Exact Character Scaling       Not Supported
       Supports Double Weight Characters       Not Supported
                        Supports Italics       Not Supported
                     Supports Underlines       Supported
                     Supports Strikeouts       Supported
                   Supports Raster Fonts       Supported
                   Supports Vector Fonts       Supported
                Cannot Scroll Using Blts       Not Supported
                 Alternate Fill Polygons       Supported
                              Rectangles       Supported
                   Winding Fill Polygons       Supported
                        Single Scanlines       Supported
                            Wide Borders       Supported
                          Styled Borders       Supported
                 Wide and Styled Borders       Supported
                               Interiors       Supported
                        Requires Banding       Not Supported
                    Can Transfer Bitmaps       Supported
                  Supports Bitmaps > 64K       Supported
        Supports SetDIBits and GetDIBits       Supported
              Supports SetDIBitsToDevice       Supported
                  Can Perform Floodfills       Supported
           Supports Windows 2.0 Features       Supported
                           Palette Based       Not Supported
                                 Scaling       Not Supported
                     Supports StretchBlt       Supported
                  Supports StretchDIBits       Supported

--------------------------------------------------------------------------------
                                      ***  Line Features ***
--------------------------------------------------------------------------------

   Capable of Character Output Precision       Supported
      Capable of Stroke Output Precision       Supported
        Capable of Stroke Clip Precision       Supported
   Supports 90 Degree Character Rotation       Not Supported
Supports Character Rotation to Any Angle       Not Supported
               X And Y Scale Independent       Not Supported
      Supports Doubled Character Scaling       Not Supported
Supports Integer Multiples Only When Scaling       Not Supported
Supports Any Multiples For Exact Character Scaling       Not Supported
       Supports Double Weight Characters       Not Supported
                        Supports Italics       Not Supported
                     Supports Underlines       Supported
                     Supports Strikeouts       Supported
                   Supports Raster Fonts       Supported
                   Supports Vector Fonts       Supported
                Cannot Scroll Using Blts       Not Supported
                 Alternate Fill Polygons       Supported
                              Rectangles       Supported
                   Winding Fill Polygons       Supported
                        Single Scanlines       Supported
                            Wide Borders       Supported
                          Styled Borders       Supported
                 Wide and Styled Borders       Supported
                               Interiors       Supported
                        Requires Banding       Not Supported
                    Can Transfer Bitmaps       Supported
                  Supports Bitmaps > 64K       Supported
        Supports SetDIBits and GetDIBits       Supported
              Supports SetDIBitsToDevice       Supported
                  Can Perform Floodfills       Supported
           Supports Windows 2.0 Features       Supported
                           Palette Based       Not Supported
                                 Scaling       Not Supported
                     Supports StretchBlt       Supported
                  Supports StretchDIBits       Supported
                               Polylines       Supported
                                 Markers       Supported
                        Multiple Markers       Supported
                              Wide Lines       Supported
                            Styled Lines       Supported
                   Wide and Styled Lines       Supported

--------------------------------------------------------------------------------
                                     ***  Curve Features ***
--------------------------------------------------------------------------------

   Capable of Character Output Precision       Supported
      Capable of Stroke Output Precision       Supported
        Capable of Stroke Clip Precision       Supported
   Supports 90 Degree Character Rotation       Not Supported
Supports Character Rotation to Any Angle       Not Supported
               X And Y Scale Independent       Not Supported
      Supports Doubled Character Scaling       Not Supported
Supports Integer Multiples Only When Scaling       Not Supported
Supports Any Multiples For Exact Character Scaling       Not Supported
       Supports Double Weight Characters       Not Supported
                        Supports Italics       Not Supported
                     Supports Underlines       Supported
                     Supports Strikeouts       Supported
                   Supports Raster Fonts       Supported
                   Supports Vector Fonts       Supported
                Cannot Scroll Using Blts       Not Supported
                 Alternate Fill Polygons       Supported
                              Rectangles       Supported
                   Winding Fill Polygons       Supported
                        Single Scanlines       Supported
                            Wide Borders       Supported
                          Styled Borders       Supported
                 Wide and Styled Borders       Supported
                               Interiors       Supported
                        Requires Banding       Not Supported
                    Can Transfer Bitmaps       Supported
                  Supports Bitmaps > 64K       Supported
        Supports SetDIBits and GetDIBits       Supported
              Supports SetDIBitsToDevice       Supported
                  Can Perform Floodfills       Supported
           Supports Windows 2.0 Features       Supported
                           Palette Based       Not Supported
                                 Scaling       Not Supported
                     Supports StretchBlt       Supported
                  Supports StretchDIBits       Supported
                               Polylines       Supported
                                 Markers       Supported
                        Multiple Markers       Supported
                              Wide Lines       Supported
                            Styled Lines       Supported
                   Wide and Styled Lines       Supported
                                 Circles       Supported
                              Pie Wedges       Supported
                                  Chords       Supported
                                Ellipses       Supported
                      Rounded Rectangles       Supported


--------------------------------------------------------------------------------
                                           ***  Services ***
--------------------------------------------------------------------------------

       Application Layer Gateway Service       n/a
            avast! iAVS4 Control Service       n/a
                       Ati HotKey Poller       n/a
                           Windows Audio       n/a
                        avast! Antivirus       n/a
                     avast! Mail Scanner       n/a
                      avast! Web Scanner       n/a
                  Cryptographic Services       n/a
            DCOM Server Process Launcher       n/a
                             DHCP Client       n/a
                    Logical Disk Manager       n/a
                              DNS Client       n/a
                 Error Reporting Service       n/a
                               Event Log       n/a
                       COM+ Event System       n/a
       Fast User Switching Compatibility       n/a
                        Help and Support       n/a
                                  Server       n/a
                             Workstation       n/a
                   TCP/IP NetBIOS Helper       n/a
                     Network Connections       n/a
        Network Location Awareness (NLA)       n/a
                           Plug and Play       n/a
                          IPSEC Services       n/a
                       Protected Storage       n/a
        Remote Access Connection Manager       n/a
                         Remote Registry       n/a
             Remote Procedure Call (RPC)       n/a
               Security Accounts Manager       n/a
                          Task Scheduler       n/a
                         Secondary Logon       n/a
               System Event Notification       n/a
Windows Firewall/Internet Connection Sharing (ICS)       n/a
                Shell Hardware Detection       n/a
                           Print Spooler       n/a
                  SSDP Discovery Service       n/a
                               Telephony       n/a
                       Terminal Services       n/a
                                  Themes       n/a
        Distributed Link Tracking Client       n/a
                            Windows Time       n/a
                               WebClient       n/a
      Windows Management Instrumentation       n/a
                         Security Center       n/a
                       Automatic Updates       n/a
             Wireless Zero Configuration       n/a

--------------------------------------------------------------------------------
                                       ***  Applications ***
--------------------------------------------------------------------------------

                      Running Processes:       39
                                Windows:       467
                   Startup Applications:       21
                        Browser Plugins:       3

--------------------------------------------------------------------------------
                                           ***  Services ***
--------------------------------------------------------------------------------

                         Total Services:       96
                       Running Services:       46
                       Startup Services:       39

--------------------------------------------------------------------------------
                                            ***  Drivers ***
--------------------------------------------------------------------------------

                         Loaded Drivers:       125

--------------------------------------------------------------------------------
                                     ***  Volume Details ***
--------------------------------------------------------------------------------

                            Disk Letter:       C:
                            Volume Type:       Hard Disk Drive
                          Serial Number:       D02C-DC06
                            File System:       NTFS
                            Total Bytes:       15,726,702,592 bytes
                             Bytes Free:       4,056,690,688 bytes
                             Bytes Used:       11,670,011,904 bytes

--------------------------------------------------------------------------------
                                        ***  File System ***
--------------------------------------------------------------------------------

                File Compression Enabled       Yes
                    Volume is Compressed       No
                 Long File Names Enabled       Yes
              Unicode File Names Enabled       Yes
           Encrypted File System Support       Yes

--------------------------------------------------------------------------------
                                ***  Logical Information ***
--------------------------------------------------------------------------------

                     Number of Clusters:       3,839,527
                          Free Clusters:       990,403
                          Used Clusters:       2,849,124
                      Bytes per Cluster:       4,095 bytes
                    Sectors per Cluster:       8
                           Used Sectors:       22,792,992
                           Free Sectors:       7,923,224

--------------------------------------------------------------------------------
                              ***  Configuration Details ***
--------------------------------------------------------------------------------

                       Bytes per Sector:       512 bytes
                          Total Sectors:       30,716,216

--------------------------------------------------------------------------------
                                ***  General Information ***
--------------------------------------------------------------------------------

                                  Model:       ST380013AS
                      Firmware Revision:       3.00
                          Serial Number:       4MR3NRZZ
                            Device Type:       ATA device, hard drive
                        Drive Standards:       ATA-2, ATA-3, ATA/ATAPI-4, ATA/ATAPI-5, ATA/ATAPI-6
                            ATA Version:       ATA/ATAPI-6

--------------------------------------------------------------------------------
                                           ***  Geometry ***
--------------------------------------------------------------------------------

                              Cylinders:       9,729
                                  Heads:       255
                        Bytes per Track:       32,256 bytes
                       Bytes per Sector:       512 bytes
                      Sectors per Track:       63
                    Addressable Sectors:       156,296,385

--------------------------------------------------------------------------------
                                          *** Properties ***
--------------------------------------------------------------------------------

                            Buffer Size:       8,192 KB
                               ECC Code:       4
                            Temperature:       44
                                    LUN:       0
                                 Target:       0

--------------------------------------------------------------------------------
                                 ***  S.M.A.R.T. Details ***
--------------------------------------------------------------------------------

                     S.M.A.R.T. Support:       Yes
                      S.M.A.R.T. Active:       Yes

--------------------------------------------------------------------------------
                                              ***  Ports ***
--------------------------------------------------------------------------------

                              PortSlot_0       Other
                              PortSlot_1       Other
                              PortSlot_2       8251 FIFO Compatible
                              PortSlot_3       Serial Port 16450 Compatible
                              PortSlot_4       Parallel Port ECP/EPP
                              PortSlot_5       Keyboard Port
                              PortSlot_6       Mouse Port
                                    USB1       USB
                                    USB2       USB
                                    USB3       USB
                                    USB4       USB
                                    USB5       USB
                                    USB6       USB
                                    USB7       USB
                                    USB8       USB
                                   VIDEO       Video Port
                                 Line In       Audio Port
                                Line Out       Audio Port
                                  Mic In       Audio Port
                                   CD In       Audio Port
                             Front Panel       Audio Port
                                ETHERNET       Network Port
                             PortSlot_22       Other
                             PortSlot_23       Other
                             PortSlot_24       Other
                             PortSlot_25       Other
                             PortSlot_26       None
                             PortSlot_27       None
                             PortSlot_28       None

--------------------------------------------------------------------------------
                                        ***  USB Devices ***
--------------------------------------------------------------------------------


--------------------------------------------------------------------------------
                                           ***  Printers ***
--------------------------------------------------------------------------------

                         No items found.       n/a

--------------------------------------------------------------------------------
                                      ***  Audio Devices ***
--------------------------------------------------------------------------------

             Realtek HD Audio input v5.5       Wave Input
                 Bluetooth AV Audio v1.1       Wave Input
                Bluetooth SCO Audio v1.1       Wave Input

--------------------------------------------------------------------------------
                                  ***  Bluetooth Devices ***
--------------------------------------------------------------------------------

                         No items found.       n/a

--------------------------------------------------------------------------------
                                  ***  Installed Engines ***
--------------------------------------------------------------------------------

                             IE Version:       7.0.5730.13 (0)
                        DirectX Version:       4.09.00.0904
                Windows Installer (MSI):       4.5.6001.22159
                         OpenGL Version:       5.1.2600.5512 (xpsp.080413-0845)
                           .Net Version:       2.0.50727.1433 (REDBITS.050727-1400)
                            ADO Version:       2.81.1132.0 (xpsp.080413-0852)
                            DAO Version:       03.60.9512.0
                           ODBC Version:       3.525.1132.0 (xpsp.080413-0852)

--------------------------------------------------------------------------------
                                ***  DirectX Information ***
--------------------------------------------------------------------------------

Microsoft Direct3D Hardware acceleration through Direct3D HAL       Direct3D
Microsoft Direct3D Mono(Ramp) Software Emulation       Direct3D
Microsoft Direct3D RGB Software Emulation       Direct3D
          Microsoft Software Synthesizer       DirectMusic
   WinSock TCP Connection For DirectPlay       DirectPlay
   WinSock IPX Connection For DirectPlay       DirectPlay
         Modem Connection For DirectPlay       DirectPlay

--------------------------------------------------------------------------------
                        ***  Microsoft Office Components ***
--------------------------------------------------------------------------------

              Microsoft Word Application       12.0.4518.1014



--------------------------------------------------------------------------------
                                  ***  Installed Drivers ***
--------------------------------------------------------------------------------

                            ntkrnlpa.exe       \WINDOWS\system32\
                                 hal.dll       \WINDOWS\system32\
                               KDCOM.DLL       \WINDOWS\system32\
                             BOOTVID.dll       \WINDOWS\system32\
                              WMILIB.SYS       \WINDOWS\system32\DRIVERS\
                             PCIIDEX.SYS       \WINDOWS\system32\DRIVERS\
                            CLASSPNP.SYS       \WINDOWS\system32\DRIVERS\
                            intelppm.sys       \SystemRoot\system32\DRIVERS\
                            ati2mtag.sys       \SystemRoot\system32\DRIVERS\
                            VIDEOPRT.SYS       \SystemRoot\system32\DRIVERS\
                             usbohci.sys       \SystemRoot\system32\DRIVERS\
                             USBPORT.SYS       \SystemRoot\system32\DRIVERS\
                             usbehci.sys       \SystemRoot\system32\DRIVERS\
                               imapi.sys       \SystemRoot\system32\DRIVERS\
                               cdrom.sys       \SystemRoot\system32\DRIVERS\
                             redbook.sys       \SystemRoot\system32\DRIVERS\
                                  ks.sys       \SystemRoot\system32\DRIVERS\
                            HDAudBus.sys       \SystemRoot\system32\DRIVERS\
                             RTL8139.SYS       \SystemRoot\system32\DRIVERS\
                              serial.sys       \SystemRoot\system32\DRIVERS\
                             serenum.sys       \SystemRoot\system32\DRIVERS\
                             parport.sys       \SystemRoot\system32\DRIVERS\
                            i8042prt.sys       \SystemRoot\system32\DRIVERS\
                            mouclass.sys       \SystemRoot\system32\DRIVERS\
                            kbdclass.sys       \SystemRoot\system32\DRIVERS\
                            VcommMgr.sys       \SystemRoot\System32\Drivers\
                        blueletaudio.sys       \SystemRoot\system32\DRIVERS\
                             portcls.sys       \SystemRoot\system32\DRIVERS\
                                drmk.sys       \SystemRoot\system32\DRIVERS\
                     BlueletSCOAudio.sys       \SystemRoot\system32\DRIVERS\
                             audstub.sys       \SystemRoot\system32\DRIVERS\
                             RootMdm.sys       \SystemRoot\System32\Drivers\
                               Modem.SYS       \SystemRoot\System32\Drivers\
                             rasl2tp.sys       \SystemRoot\system32\DRIVERS\
                            ndistapi.sys       \SystemRoot\system32\DRIVERS\
                             ndiswan.sys       \SystemRoot\system32\DRIVERS\
                            raspppoe.sys       \SystemRoot\system32\DRIVERS\
                             raspptp.sys       \SystemRoot\system32\DRIVERS\
                                 TDI.SYS       \SystemRoot\system32\DRIVERS\
                              psched.sys       \SystemRoot\system32\DRIVERS\
                               msgpc.sys       \SystemRoot\system32\DRIVERS\
                             ptilink.sys       \SystemRoot\system32\DRIVERS\
                              raspti.sys       \SystemRoot\system32\DRIVERS\
                            pcouffin.sys       \SystemRoot\System32\Drivers\
                               VComm.sys       \SystemRoot\system32\DRIVERS\
                               rdpdr.sys       \SystemRoot\system32\DRIVERS\
                              termdd.sys       \SystemRoot\system32\DRIVERS\
                              swenum.sys       \SystemRoot\system32\DRIVERS\
                              update.sys       \SystemRoot\system32\DRIVERS\
                            mssmbios.sys       \SystemRoot\system32\DRIVERS\
                             NDProxy.SYS       \SystemRoot\System32\Drivers\
                              usbhub.sys       \SystemRoot\system32\DRIVERS\
                                USBD.SYS       \SystemRoot\system32\DRIVERS\
                            RtkHDAud.sys       \SystemRoot\system32\drivers\
                              Fs_Rec.SYS       \SystemRoot\System32\Drivers\
                                Null.SYS       \SystemRoot\System32\Drivers\
                                Beep.SYS       \SystemRoot\System32\Drivers\
                                 vga.sys       \SystemRoot\System32\drivers\
                               mnmdd.SYS       \SystemRoot\System32\Drivers\
                              RDPCDD.sys       \SystemRoot\System32\DRIVERS\
                                Msfs.SYS       \SystemRoot\System32\Drivers\
                                Npfs.SYS       \SystemRoot\System32\Drivers\
                              rasacd.sys       \SystemRoot\system32\DRIVERS\
                               ipsec.sys       \SystemRoot\system32\DRIVERS\
                               tcpip.sys       \SystemRoot\system32\DRIVERS\
                              aswTdi.SYS       \SystemRoot\System32\Drivers\
                               ipnat.sys       \SystemRoot\system32\DRIVERS\
                               netbt.sys       \SystemRoot\system32\DRIVERS\
                              wanarp.sys       \SystemRoot\system32\DRIVERS\
                                 afd.sys       \SystemRoot\System32\drivers\
                             netbios.sys       \SystemRoot\system32\DRIVERS\
                              SCDEmu.SYS       \SystemRoot\System32\Drivers\
                               rdbss.sys       \SystemRoot\system32\DRIVERS\
                              mrxsmb.sys       \SystemRoot\system32\DRIVERS\
                                Fips.SYS       \SystemRoot\System32\Drivers\
                               aswSP.SYS       \SystemRoot\System32\Drivers\
                            Aavmker4.SYS       \SystemRoot\System32\Drivers\
                              btcusb.sys       \SystemRoot\System32\Drivers\
                                Cdfs.SYS       \SystemRoot\System32\Drivers\
                          dump_atapi.sys       \SystemRoot\System32\Drivers\
                         dump_WMILIB.SYS       \SystemRoot\System32\Drivers\
                              win32k.sys       \SystemRoot\System32\
                               Dxapi.sys       \SystemRoot\System32\drivers\
                            watchdog.sys       \SystemRoot\System32\
                                 dxg.sys       \SystemRoot\System32\drivers\
                              dxgthk.sys       \SystemRoot\System32\drivers\
                            ati2dvag.dll       \SystemRoot\System32\
                            ati2cqag.dll       \SystemRoot\System32\
                            atikvmag.dll       \SystemRoot\System32\
                            ati3duag.dll       \SystemRoot\System32\
                            ativvaxx.dll       \SystemRoot\System32\
                            aswFsBlk.sys       \SystemRoot\system32\DRIVERS\
                             ndisuio.sys       \SystemRoot\system32\DRIVERS\
                             aswMon2.SYS       \SystemRoot\System32\Drivers\
                              mrxdav.sys       \SystemRoot\system32\DRIVERS\
                              ParVdm.SYS       \SystemRoot\System32\Drivers\
                              wdmaud.sys       \SystemRoot\system32\drivers\
                            sysaudio.sys       \SystemRoot\system32\drivers\
                                 srv.sys       \SystemRoot\system32\DRIVERS\
                              aswRdr.SYS       \SystemRoot\System32\Drivers\
                                HTTP.sys       \SystemRoot\System32\Drivers\
                            asyncmac.sys       \SystemRoot\system32\DRIVERS\
                              kmixer.sys       \SystemRoot\system32\drivers\
                               ntdll.dll       \WINDOWS\system32\

--------------------------------------------------------------------------------
                                ***  General Information ***
--------------------------------------------------------------------------------

                              Host Name:       ----------
                          Proxy Enabled:       Disabled
                            DNS Enabled:       Disabled
                        Routing Enabled:       Disabled

--------------------------------------------------------------------------------
                                    ***  WinSock Details ***
--------------------------------------------------------------------------------

                            Description:       WinSock 2.0
                                Version:       2.2
                                 Status:       Running

--------------------------------------------------------------------------------
                                           ***  Adapters ***
--------------------------------------------------------------------------------

Realtek RTL8139 Family PCI Fast Ethernet NIC - Packet Scheduler Miniport       0.0.0.0

--------------------------------------------------------------------------------
                                    ***  Network Details ***
--------------------------------------------------------------------------------

                  Found IP Addresses #1:       127.0.0.1
         Installed Physical Adapters #1:       Realtek RTL8139 Family PCI Fast Ethernet NIC
          Installed Virtual Adapters #1:       WAN Miniport (IP)
          Installed Virtual Adapters #2:       WAN Miniport (PPPOE)
          Installed Virtual Adapters #3:       WAN Miniport (PPTP)
          Installed Virtual Adapters #4:       WAN Miniport (Network Monitor)
          Installed Virtual Adapters #5:       RAS Async Adapter
          Installed Virtual Adapters #6:       WAN Miniport (L2TP)
          Installed Virtual Adapters #7:       Realtek RTL8139 Family PCI Fast Ethernet NIC - Packet Scheduler Miniport
          Installed Virtual Adapters #8:       Direct Parallel
          Installed Virtual Adapters #9:       Bluetooth PAN Network Adapter
         Installed Virtual Adapters #10:       WAN Miniport (Network Monitor) - Packet Scheduler Miniport
         Installed Virtual Adapters #11:       WAN Miniport (IP) - Packet Scheduler Miniport
         Installed Virtual Adapters #12:       Bluetooth PAN Network Adapter - Packet Scheduler Miniport
                 Supported Protocols #1:       Message-oriented TCP/IP Protocol (SMB session)
                 Supported Protocols #2:       Layer 2 Tunneling Protocol
                 Supported Protocols #3:       Remote Access NDIS WAN Driver
                 Supported Protocols #4:       NDIS Usermode I/O Protocol
                 Supported Protocols #5:       Network Monitor Driver
                 Supported Protocols #6:       Internet Protocol (TCP/IP)
                 Supported Protocols #7:       Point to Point Protocol Over Ethernet
                 Supported Protocols #8:       WINS Client(TCP/IP) Protocol
                 Supported Protocols #9:       Point to Point Tunneling Protocol
                  Supported Services #1:       Generic Packet Classifier
                  Supported Services #2:       Remote Access Connection Manager
                  Supported Services #3:       Dial-Up Server
                  Supported Services #4:       Dial-Up Client
                  Supported Services #5:       Wireless Zero Configuration
                  Supported Services #6:       Application Layer Gateway
                  Supported Services #7:       Steelhead
                  Supported Services #8:       File and Printer Sharing for Microsoft Networks
                  Supported Services #9:       NetBIOS Interface
                 Supported Services #10:       QoS RSVP
                 Supported Services #11:       QoS Packet Scheduler
                        Found Client #1:       WebClient
                        Found Client #2:       Client for Microsoft Networks

---

### Post by mrrinmoy on 2009-08-28
my full sysyem infroation

---

### Post by directhex on 2009-08-28
> **mrrinmoy said:**
> my full sysyem infroation

Can you try again with a recent release? You old messages relate to an old version of Ubuntu.

---

### Post by bahawks2 on 2009-08-28
Get a new cheap computer. I have a desk top that wouldn't run the demo/install Ubuntu so I bought a laptop for $500 and not only is it better then old desktop but it will run the demo of Ubuntu but I am just waiting till I upgrade to windows 7 till I create the duel boot environment.:)

---

