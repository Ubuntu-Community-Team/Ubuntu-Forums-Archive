---
title: "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by honorguard on 2008-02-27
Hello,
I have Thinkpad R61i with graphic card Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller. I have a lot of problems with this card.
1) Lot of native linux games not runing. (for example planeshift of Sauerbraten). These games will write "core dumped" and fall. I can sent message from terminal. 
2) Game like asi Gridwars and other will stop computer completly. Display black like as changing resolution, after that i see mouse and tak black again and again. I can't restart X. I must reset computer. 
3)Lot of games what I can play under cedega I can't play for uknown reason. Thats games like as Need For Speed and others.
4) Every acelerated game under Wine (from CS 1.6 to NFS) will write this:

```
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
wine: Unhandled page fault on read access to 0x00000010 at address 0x7e1c86f5 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x7e1c86f5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e1c86f5 ESP:0034f3b8 EBP:0034f3bc EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7c0f8238 ECX:7c592a00 EDX:00000005
 ESI:0034f464 EDI:7ee36eef
Stack dump:
0x0034f3b8:  7ee548bc 0034f6ac 7edb7353 7c0f8238
0x0034f3c8:  00008620 7c592a00 7ee36e7c 7ee554cc
0x0034f3d8:  b7db88ac 00000320 00000021 00000001
0x0034f3e8:  7e38e4c0 b7db7541 7c11a088 7c0f8238
0x0034f3f8:  79800000 0034f42c 7e1a3906 7e38e4c0
0x0034f408:  b7db88ac b7db7541 0034f584 0000036c
Backtrace:
=>1 0x7e1c86f5 in i965_dri.so (+0x856f5) (0x0034f3bc)
  2 0x7edb7353 IWineD3DImpl_FillGLCaps+0x8115() in wined3d (0x0034f6ac)
  3 0x7edbf3a1 InitAdapters+0x1f16() in wined3d (0x0034faec)
  4 0x7ee2bdc6 WineDirect3DCreate+0x22() in wined3d (0x0034fb1c)
  5 0x7ee6cec1 Direct3DCreate9+0x77() in d3d9 (0x0034fb4c)
  6 0x00407c0c in speed (+0x7c0c) (0x0034ff08)
  7 0x7b86eb3d in kernel32 (+0x4eb3d) (0x0034ffe8)
  8 0xb7de22cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e1c86f5: movl        0x10(%eax),%eax
Modules:
Module  Address                 Debug info      Name (94 modules)
PE        400000-  785d98       Export          speed
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cb2f000-7cb44000       Deferred        midimap<elf>
  \-PE  7cb40000-7cb44000       \               midimap
ELF     7cb44000-7cb6a000       Deferred        msacm32<elf>
  \-PE  7cb50000-7cb6a000       \               msacm32
ELF     7cb6a000-7cb82000       Deferred        msacm32<elf>
  \-PE  7cb70000-7cb82000       \               msacm32
ELF     7cb82000-7cbbe000       Deferred        wineoss<elf>
  \-PE  7cb90000-7cbbe000       \               wineoss
ELF     7cbbe000-7cc84000       Deferred        libasound.so.2
ELF     7cc97000-7cccc000       Deferred        winealsa<elf>
  \-PE  7cca0000-7cccc000       \               winealsa
ELF     7cccc000-7ccf2000       Deferred        netapi32<elf>
  \-PE  7ccd0000-7ccf2000       \               netapi32
ELF     7ccf2000-7cd0f000       Deferred        tapi32<elf>
  \-PE  7cd00000-7cd0f000       \               tapi32
ELF     7cd0f000-7cd63000       Deferred        ddraw<elf>
  \-PE  7cd20000-7cd63000       \               ddraw
ELF     7cd63000-7cdad000       Deferred        dsound<elf>
  \-PE  7cd70000-7cdad000       \               dsound
ELF     7cdad000-7cdd8000       Deferred        ws2_32<elf>
  \-PE  7cdc0000-7cdd8000       \               ws2_32
ELF     7ce19000-7ce4b000       Deferred        uxtheme<elf>
  \-PE  7ce20000-7ce4b000       \               uxtheme
ELF     7ce4b000-7ce68000       Deferred        imm32<elf>
  \-PE  7ce50000-7ce68000       \               imm32
ELF     7ce68000-7ce70000       Deferred        libxrender.so.1
ELF     7e143000-7e39a000       Export          i965_dri.so
ELF     7e39a000-7e3a4000       Deferred        libdrm.so.2
ELF     7e3a4000-7e3a9000       Deferred        libxfixes.so.3
ELF     7e3a9000-7e3ac000       Deferred        libxdamage.so.1
ELF     7e3ac000-7e40d000       Deferred        libgl.so.1
ELF     7e40d000-7e412000       Deferred        libxdmcp.so.6
ELF     7e412000-7e415000       Deferred        libxau.so.6
ELF     7e415000-7e506000       Deferred        libx11.so.6
ELF     7e506000-7e514000       Deferred        libxext.so.6
ELF     7e514000-7e519000       Deferred        libxxf86vm.so.1
ELF     7e519000-7e531000       Deferred        libice.so.6
ELF     7e531000-7e539000       Deferred        libsm.so.6
ELF     7e53a000-7e543000       Deferred        libxcursor.so.1
ELF     7e543000-7e546000       Deferred        libxcomposite.so.1
ELF     7e546000-7e54c000       Deferred        libxrandr.so.2
ELF     7e54c000-7e5d6000       Deferred        winex11<elf>
  \-PE  7e560000-7e5d6000       \               winex11
ELF     7e636000-7e656000       Deferred        libexpat.so.1
ELF     7e656000-7e681000       Deferred        libfontconfig.so.1
ELF     7e681000-7e696000       Deferred        libz.so.1
ELF     7e696000-7e706000       Deferred        libfreetype.so.6
ELF     7e706000-7e7c5000       Deferred        comctl32<elf>
  \-PE  7e710000-7e7c5000       \               comctl32
ELF     7e7c5000-7e81d000       Deferred        shlwapi<elf>
  \-PE  7e7d0000-7e81d000       \               shlwapi
ELF     7e81d000-7e921000       Deferred        shell32<elf>
  \-PE  7e830000-7e921000       \               shell32
ELF     7e921000-7e935000       Deferred        shfolder<elf>
  \-PE  7e930000-7e935000       \               shfolder
ELF     7e935000-7e9c1000       Deferred        winmm<elf>
  \-PE  7e940000-7e9c1000       \               winmm
ELF     7e9c1000-7e9d4000       Deferred        libresolv.so.2
ELF     7e9e7000-7ea06000       Deferred        iphlpapi<elf>
  \-PE  7e9f0000-7ea06000       \               iphlpapi
ELF     7ea06000-7ea64000       Deferred        rpcrt4<elf>
  \-PE  7ea10000-7ea64000       \               rpcrt4
ELF     7ea64000-7eb03000       Deferred        ole32<elf>
  \-PE  7ea70000-7eb03000       \               ole32
ELF     7eb03000-7eb39000       Deferred        dinput<elf>
  \-PE  7eb10000-7eb39000       \               dinput
ELF     7eb39000-7eb52000       Deferred        dinput8<elf>
  \-PE  7eb40000-7eb52000       \               dinput8
ELF     7eb52000-7eb9b000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb9b000       \               advapi32
ELF     7eb9b000-7ec31000       Deferred        gdi32<elf>
  \-PE  7ebb0000-7ec31000       \               gdi32
ELF     7ec31000-7ed68000       Deferred        user32<elf>
  \-PE  7ec50000-7ed68000       \               user32
ELF     7ed68000-7ee57000       Export          wined3d<elf>
  \-PE  7ed80000-7ee57000       \               wined3d
ELF     7ee57000-7ee86000       Export          d3d9<elf>
  \-PE  7ee60000-7ee86000       \               d3d9
ELF     7efa5000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efed000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c61000-b7c65000       Deferred        libdl.so.2
ELF     b7c65000-b7daf000       Deferred        libc.so.6
ELF     b7db0000-b7dc8000       Deferred        libpthread.so.0
ELF     b7ddb000-b7eef000       Export          libwine.so.1
ELF     b7ef1000-b7f0d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000014
        00000016    0
        00000015    0
0000000c
        0000000f    0
        0000000e    0
        0000000d    0
0000000a
        0000000b    0
00000008 (D) Z:\home\jakub\hry-install\Need For Speed Underground [PC GAME] [Extract and Play)\Need For Speed Underground\Speed.exe
        00000013    2
        00000012    1
        00000011   15
        00000010    2
        00000009    0 <==
Backtrace:
=>1 0x7e1c86f5 in i965_dri.so (+0x856f5) (0x0034f3bc)
  2 0x7edb7353 IWineD3DImpl_FillGLCaps+0x8115() in wined3d (0x0034f6ac)
  3 0x7edbf3a1 InitAdapters+0x1f16() in wined3d (0x0034faec)
  4 0x7ee2bdc6 WineDirect3DCreate+0x22() in wined3d (0x0034fb1c)
  5 0x7ee6cec1 Direct3DCreate9+0x77() in d3d9 (0x0034fb4c)
  6 0x00407c0c in speed (+0x7c0c) (0x0034ff08)
  7 0x7b86eb3d in kernel32 (+0x4eb3d) (0x0034ffe8)
  8 0xb7de22cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

I can't run compiz....
Can somebody help me please!? I tried to find solvation on two czech forum's (I'm from Czech republic (central Europe)) and everybody don't know how to solve this.
Thank for every HINT!!!

---

### Post by Rocket2DMn on 2008-02-27
Have you tried reconfiguring X - try this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
You will want the "intel" drivers.  If you have more questions, post the contents of xorg.conf:
```
cat /etc/X11/xorg.conf
```

---

### Post by Yellow Pasque on 2008-02-27
> I can't run compiz....
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by honorguard on 2008-02-28
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "cz"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "EmulateWheel"          "on"
        Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheelButton"    "2"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        32000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Obecný monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Obecný monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```
this is xorg.conf
I tried reconfiguring X, but I don't know how configure it good to good card function...

---

### Post by Rocket2DMn on 2008-02-28
Your xorg file looks OK, except that it only shows 1280x800 resolution.  While this might work natively, some games may be trying to run on less which can create problems.  Reconfigure again and select your monitor's max resolution and everything less.
As far as games go, you should check wine's website for compatibility, though I know games like CS 1.6 should work OK.  You will probably need to disable compiz when you run games though so you can get a decent framerate.  You can do this as follows:
```
metacity --replace
```
Then when you're finished, re-enable compiz with
```
compiz --replace
```
I would suggest just making desktop or panel shortcuts for these commands if you find yourself using them regularly.

---

### Post by honorguard on 2008-02-28
I needn't to disable compiz, because compiz doesn't function. If I run compiz, it change window decoration but it don't run efects.

---

### Post by Rocket2DMn on 2008-02-28
If you enable compiz and select the Custom radio button, you can hit Preferences and tell it which effects you want to enable.

---

### Post by honorguard on 2008-02-28
I know. I had compiz on my last computer, but after that I bought this computer and there it doesn't run...

---

### Post by Rocket2DMn on 2008-02-28
Ok, we're gonna need some more information.  Do you have a second video card in the computer by chance?  That can create problems.
What happens when you try to enable CF.  Post the output from running
```
compiz --replace
```
We need error messages and as much relevant data as possible.  Have you followed any guides to getting your intel card to work with CF?  Checked for other threads on the forum (I guarantee there are some.)?
Did you reconfigure so that the rest of the resolutions show in xorg.conf?

---

### Post by honorguard on 2008-02-29
I didn't changed it. I have 15.4 monitor on ntb. This is the highteset resolution I think...

---

### Post by honorguard on 2008-02-29
```
jakub@honorguard:~$ compiz --replace
Checking for Xgl: not present.
Blacklisted PCIID '8086:2a02' found
aborting and using fallback: /usr/bin/metacity
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

Not initializing the Gtk-Qt theme engine

```
this is the log of compiz.
The only thing what it do is chenge tittles of windows for some old style...

---

### Post by Rocket2DMn on 2008-02-29
OK, according to this thread - [http://ubuntuforums.org/showthread.php?t=619099](http://ubuntuforums.org/showthread.php?t=619099) - your card doesn't support xgl, so it sounds like you may have to do without compiz.

But wait, there *might* be hope.  Have a look at this sticky - [http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112) which is from the Desktop Effects & Customization forum at [http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)
You may have to try and install xgl first though, I think the package is called "xserver-xgl".

In all reality, compiz is flashy, but for the most part useless.  I don't know how fast your computer is, but it can slow it down on some older machines (including my own laptop).  Try installing xgl and running the workaround in that post and see what happens.  If it doesn't work, you can try talking to the developer who posted that sticky, "Amaranth".  Please do post back your results though.
Good luck.

---

### Post by honorguard on 2008-03-02
This package would to kill my computer...
I have ntb with 1.5ghz intel core 2 duo, 1024 Rams and intel graphic.
After the instalation of this package everything was really slow (re-drawing K menu and others)...
I started one of the problem games and X-server fallen down...
I don't need compiz. I have 2 users. One for games and one for work.... Work user has KDE4 with akcelerated Kwin... It's fine and better than compiz I think. But compiz isn't problem.
Problems have "all" Open GL aplications (some not). Some stop activity of pc and I must restart, some kill x. Some Kill kwin, some not running... and some works fine. (Open arena, Alien Arena)...
If I understand, after final release of HH where is new X-server and new intel drivers, it may be everything OK, or no?

---

### Post by Rocket2DMn on 2008-03-02
I don't know exactly what's in store for Hardy, you'll have to look it up.  Others have been able to get your card to function normally, I don't really understand what the problem is, and I've never heard of Kwin.
Also, you never mentioned that you were using KDE for anything.  Is that all you use or do you use GNOME as well?  I don't think KDE4 has been exhaustively tested with (K)ubuntu yet, although they did release a disc with it I believe.

---

### Post by honorguard on 2008-03-03
I had KDE3 long time and i have that problems too... :'-(
Can it be a hardware problem?

---

### Post by Rocket2DMn on 2008-03-03
I think it's mostly that the support for your card isn't very good for situations that require a lot of processing power (like movies and games). Your card should be working OK otherwise (though without CF).  Do you at least have the correct screen resolution?
Also, running windows games under wine and cedega is far from perfect, and your linux games may just be too powerful for your card to handle (depends on your RAM since an integrated card shares memory with your RAM instead of having its own memory).  One of the advantages of setting up a dual boot with windows is that you can reboot into windows to play your favorites games in their native environment.

---

### Post by honorguard on 2008-03-04
I'm sorry, but I'm really hate windows... My friends have Win Vista, and asking me for problems every day... I have windows only on VirtualBox and there I have Borland delphi, MS Office 2007 (for learning it) and Macromedia Flash. I like linux. I think I have PCI-Express slot in my ntb, but I'm not sure. I will buy new card after summer holiday, but there is a question...
I don't like ATI corporation, because I had problems with it on windows. I like NVidia Geeforce chips, but before month there was a bug in restricted driver and it was bug on KDE4 kwin...
Can you suggest some card please?
Really thanks for your help!

---

### Post by Rocket2DMn on 2008-03-04
I thought you said you were using a laptop (Thinkpad) - are you really going to replace the card in your laptop?  Most nvidia cards work well and the majority of ATI cards made in the last few years work OK.  If you find a card you think you like, you can search and see if there are any problems with it in linux.  It's difficult to suggest a specific card as there are so many options, and what's available in your area within your price range limits the options - but only you can know that info.

---

### Post by lukus on 2008-03-24
I also have the GM965/GL960 graphics card.  If you're just interested in running compiz with this card, I found executing the folllowing command in terminal to work:

SKIP_CHECKS=yes compiz --replace ccp &

You should then be able to start compiz by going to System>preferences>appearance and enabling the effects from there.

try and put it in a nice shell script if you like....I think you may need to run it as root though...

hope that helps

Lukus

---

### Post by Yellow Pasque on 2008-03-24
> **lukus said:**
> I also have the GM965/GL960 graphics card.  If you're just interested in running compiz with this card, I found executing the folllowing command in terminal to work:

SKIP_CHECKS=yes compiz --replace ccp &

You should then be able to start compiz by going to System>preferences>appearance and enabling the effects from there.

try and put it in a nice shell script if you like....I think you may need to run it as root though...

hope that helps

Lukus
An easier way would be to edit /usr/bin/compiz and remove your card from the blacklist. See my link a few posts back.

---

### Post by yakuzaarakaki on 2008-05-19
hey guys!
look at this:

[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

cya!

---

