---
title: "Sharing a wine Shortcut to other users"
date: 2008-10-01
forum: General Help
---

### Post by the_master on 2008-10-01
I have installed Ubuntu on a classroom computer in a High School Physics room.  I installed a program called "Logger Pro"  through wine and it seems to work.  However i need to Share the Icon on the administrator account to the student account so when students login to the student account they can use logger pro right from the desktop.  I've tried making a shortcut and then moving it to the Student Desktop Folder but no luck.  I have disabled the taskbar so that students couldn't screw it up and open up applications i didn't want them opening up, so thats out of the question.  That'd be great if someone could explain how to do this, a screenshot wouldn't hurt either :)

---

### Post by pytheas22 on 2008-10-02
You should be able to do it by following these steps:

1. log into the student account, right-click on the desktop, select "Create Launcher," and in the "Command" field, enter a command like:
```

wine '/path/to/logger.exe'
```

(see attached screenshot.  I'm not sure of the name of your admin account or the exact patch to the Windows executable that you need wine to run, but I think it should be simple enough to figure out where you need to substitute the relevant information; if not, let me know.)

2. you should also make sure that the student account has read, write and executable permissions on the necessary file (and probably the directory that it's in).  If you don't know how to set permissions, let me know.  By default I think that the students would only have read access to the wine files in the admin account, so this could have been part of the problem.

If it still doesn't work, open up a terminal and enter the command that you put into the launcher.  That should hopefully give you some feedback regarding why it doesn't work.

Let us know how it goes.

---

### Post by the_master on 2008-10-02
Yeah i don't know how to change permissions for a certain file, i bet thats why it didn't work before.  how would you do that?

---

### Post by pytheas22 on 2008-10-02
You can change permissions using the graphical interface by right-clicking on the folder or file that you want to modify, selecting 'Properties', navigating to the 'Permissions' tab, and setting the permissions as desired for each of the three categories of users--owner, group and other.  The easiest thing to do is probably just to give read and write permissions to other for the folder in which the Logger Pro .exe is located (you could create a group and add the students to it, but that's more complicated and probably not necessary for your situation).  After you set the permissions, check on them to verify that they were set correctly; sometimes it doesn't work when you do it graphically.

To set permissions using the command-line, you use the [chmod]("http://www.ss64.com/bash/chmod.html") command.  To give everyone read, write and execute permissions to the Logger Pro directory, you'd run a command like:
```

chmod -R 777 /home/admin/.wine/drive_c/Program\ Files/Logger\ Pro
```

(Remember that you need to escape white spaces with \ on the command line.  Also, Unix puritans generally frown harshly on giving '777' permissions; I only recommend it because it's the simplest solution, but it would be better to scale the permissions back a bit, or to use groups, etc.).

Let me know if this helps.  You should also probably try just running on the command-line the command that you want to use for the students to start Logger Pro, just to see if that works.  If there's a problem with permissions or something, it might tell you.

---

### Post by the_master on 2008-10-06
Alright i changed the permissions but it is still doing the same thing, i tried to take a screenshot but thats not working either, i'm guessing because i don't have permissions for that either.  Any other Ideas?

---

### Post by pytheas22 on 2008-10-06
Everyone should have permissions to take a screenshot of their desktop.  It doesn't work if you press alt-printscreen or use the Applications>Accessories>Take Screenshot utility?

Also, what is the output that you get in the terminal if you try running your command to launch Logger Pro under the student account?

Also, maybe you have a reason not to do this, but could you just install Logger Pro a second time within the student account, then create a desktop launcher for them to start their version of Logger Pro?  In other words, is there a reason that Logger Pro needs to be installed (and only installed) under the admin account?  It would bypass all of the permissions issues if you just installed a second copy under the student account.

---

### Post by the_master on 2008-10-07
Well the screenshot application pops up but when i save it to the Desktop it never shows up.

It won't even let me Launch it, i'm not sure why.  It shows up as a link to logger pro and i type that in but it just says the command is not there.

No there is no reason for me just installing it in the admin account i just don't see why you should have to install it twice?  Thats a waste of space, however if that works it will be a much easier way so i'll try that.

edit:  I installed it in the user account but when i launch it the screen goes black other then the taskbars at the top and bottom and it crashes.  : (

Here is what it outputs
```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
fixme:win:EnumDisplayDevicesW ((null),0,0x33dd80,0x00000000), stub!
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\QTFont.for",L"C:\\windows\\QTFont.qfn",(null)): stub
fixme:setupapi:CMP_WaitNoPendingInstallEvents 0
wine: Call from 0x7b841738 to unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName, aborting
wine: Unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName called at address 0x7b841738 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipCreateFontFamilyFromName called in 32-bit code (0x7b8417b2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8417b2 ESP:0033ee0c EBP:0033ee70 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82c1a9 EBX:7b8ae97c ECX:00000000 EDX:0033ee88
 ESI:0033ee88 EDI:0033f098
Stack dump:
0x0033ee0c:  0033ee88 00000008 0033ee44 80000100
0x0033ee1c:  00000001 00000000 7b841738 00000002
0x0033ee2c:  7e684ae0 7e684f28 00003444 7ecd9ce8
0x0033ee3c:  00000000 0033eec8 0033ee84 0000000a
0x0033ee4c:  00000000 0033ee6c 007e4586 0033ef00
0x0033ee5c:  0033f0c4 0000000a 7b841742 00000000
Backtrace:
=>1 0x7b8417b2 RaiseException+0x7a() in kernel32 (0x0033ee70)
  2 0x7e684a79 in gdiplus (+0x14a79) (0x0033ee90)
  3 0x7e671934 in gdiplus (+0x1934) (0x0033ef2c)
  4 0x006b6ff0 in loggerpro (+0x2b6ff0) (0x0033f270)
  5 0x0060454f in loggerpro (+0x20454f) (0x00000000)
0x7b8417b2 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (147 modules)
PE        400000-  b3c000       Export          loggerpro
PE      10000000-10062000       Deferred        ngio_lib
PE      66800000-67591000       Deferred        quicktime.qts
PE      675a0000-6766f000       Deferred        quicktimestreaming.qtx
PE      676c0000-6777b000       Deferred        quicktimevr.qtx
PE      67840000-67924000       Deferred        quicktimeinternetextras.qtx
PE      67930000-67b11000       Deferred        quicktimeauthoring.qtx
PE      67b20000-67b6e000       Deferred        quicktimecapture.qtx
PE      67b70000-67bf7000       Deferred        quicktimeeffects.qtx
PE      67c10000-67cf8000       Deferred        quicktimeimage.qtx
PE      67d00000-67d8b000       Deferred        quicktimemusic.qtx
PE      67d90000-67dc3000       Deferred        quicktimeqd3d.qtx
PE      67dd0000-67e3b000       Deferred        quicktimempeg.qtx
PE      67e40000-67e9a000       Deferred        quicktimeessentials.qtx
PE      67ea0000-67eef000       Deferred        quicktimempeg4.qtx
PE      67ef0000-67f77000       Deferred        quicktimempeg4authoring.qtx
PE      67f80000-67fd2000       Deferred        quicktime3gpp.qtx
PE      67fe0000-68052000       Deferred        quicktime3gppauthoring.qtx
PE      68180000-681d5000       Deferred        quicktimestreamingauthoring.qtx
PE      681e0000-68201000       Deferred        quicktimestreamingextras.qtx
PE      68210000-6853d000       Deferred        quicktimeh264.qtx
PE      68540000-687c6000       Deferred        quicktimeaudiosupport.qtx
PE      687d0000-6880c000       Deferred        corevideo.qtx
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d065000-7d07e000       Deferred        wsock32<elf>
  \-PE  7d070000-7d07e000       \               wsock32
ELF     7d9f5000-7d9ff000       Deferred        libdrm.so.2
ELF     7d9ff000-7da60000       Deferred        libgl.so.1
ELF     7da6b000-7db6d000       Deferred        wined3d<elf>
  \-PE  7da80000-7db6d000       \               wined3d
ELF     7db6d000-7dbc3000       Deferred        ddraw<elf>
  \-PE  7db70000-7dbc3000       \               ddraw
ELF     7dcd4000-7dcf5000       Deferred        mpr<elf>
  \-PE  7dce0000-7dcf5000       \               mpr
ELF     7dcf5000-7dd42000       Deferred        wininet<elf>
  \-PE  7dd00000-7dd42000       \               wininet
ELF     7dd42000-7dd55000       Deferred        msimg32<elf>
  \-PE  7dd50000-7dd55000       \               msimg32
ELF     7dd55000-7dd6c000       Deferred        spoolss<elf>
  \-PE  7dd60000-7dd6c000       \               spoolss
ELF     7dd6c000-7dd85000       Deferred        localspl<elf>
  \-PE  7dd70000-7dd85000       \               localspl
ELF     7dd85000-7de2f000       Deferred        comdlg32<elf>
  \-PE  7dd90000-7de2f000       \               comdlg32
ELF     7de2f000-7de78000       Deferred        riched20<elf>
  \-PE  7de40000-7de78000       \               riched20
ELF     7de78000-7de8b000       Deferred        riched32<elf>
  \-PE  7de80000-7de8b000       \               riched32
ELF     7de8b000-7dedc000       Deferred        libgcrypt.so.11
ELF     7dedc000-7df0a000       Deferred        libcrypt.so.1
ELF     7df0a000-7df7a000       Deferred        libgnutls.so.13
ELF     7df7a000-7df9f000       Deferred        libk5crypto.so.3
ELF     7df9f000-7e027000       Deferred        libkrb5.so.3
ELF     7e027000-7e050000       Deferred        libgssapi_krb5.so.2
ELF     7e050000-7e085000       Deferred        libcups.so.2
ELF     7e085000-7e09c000       Deferred        msacm32<elf>
  \-PE  7e090000-7e09c000       \               msacm32
ELF     7e09c000-7e162000       Deferred        libasound.so.2
ELF     7e164000-7e168000       Deferred        libgpg-error.so.0
ELF     7e168000-7e178000       Deferred        libtasn1.so.3
ELF     7e178000-7e180000       Deferred        libkrb5support.so.0
ELF     7e180000-7e183000       Deferred        libcom_err.so.2
ELF     7e183000-7e197000       Deferred        midimap<elf>
  \-PE  7e190000-7e197000       \               midimap
ELF     7e1ec000-7e21f000       Deferred        uxtheme<elf>
  \-PE  7e1f0000-7e21f000       \               uxtheme
ELF     7e21f000-7e228000       Deferred        libxcursor.so.1
ELF     7e228000-7e22d000       Deferred        libxfixes.so.3
ELF     7e22d000-7e230000       Deferred        libxcomposite.so.1
ELF     7e230000-7e236000       Deferred        libxrandr.so.2
ELF     7e236000-7e23e000       Deferred        libxrender.so.1
ELF     7e23e000-7e25e000       Deferred        imm32<elf>
  \-PE  7e240000-7e25e000       \               imm32
ELF     7e25e000-7e263000       Deferred        libxdmcp.so.6
ELF     7e263000-7e266000       Deferred        libxau.so.6
ELF     7e266000-7e357000       Deferred        libx11.so.6
ELF     7e357000-7e365000       Deferred        libxext.so.6
ELF     7e365000-7e36a000       Deferred        libxxf86vm.so.1
ELF     7e36a000-7e382000       Deferred        libice.so.6
ELF     7e382000-7e38a000       Deferred        libsm.so.6
ELF     7e390000-7e393000       Deferred        libxdamage.so.1
ELF     7e395000-7e429000       Deferred        winex11<elf>
  \-PE  7e3a0000-7e429000       \               winex11
ELF     7e4a6000-7e4c6000       Deferred        libexpat.so.1
ELF     7e4c6000-7e4f1000       Deferred        libfontconfig.so.1
ELF     7e4f1000-7e4f3000       Deferred        libkeyutils.so.1
ELF     7e4fc000-7e511000       Deferred        libz.so.1
ELF     7e511000-7e581000       Deferred        libfreetype.so.6
ELF     7e581000-7e5ac000       Deferred        ws2_32<elf>
  \-PE  7e590000-7e5ac000       \               ws2_32
ELF     7e5ac000-7e5e2000       Deferred        winspool<elf>
  \-PE  7e5b0000-7e5e2000       \               winspool
ELF     7e5e2000-7e5f6000       Deferred        hid<elf>
  \-PE  7e5f0000-7e5f6000       \               hid
ELF     7e5f6000-7e65b000       Deferred        setupapi<elf>
  \-PE  7e600000-7e65b000       \               setupapi
ELF     7e65b000-7e692000       Export          gdiplus<elf>
  \-PE  7e670000-7e692000       \               gdiplus
ELF     7e692000-7e733000       Deferred        oleaut32<elf>
  \-PE  7e6a0000-7e733000       \               oleaut32
ELF     7e733000-7e75b000       Deferred        msvfw32<elf>
  \-PE  7e740000-7e75b000       \               msvfw32
ELF     7e75b000-7e781000       Deferred        msacm32<elf>
  \-PE  7e760000-7e781000       \               msacm32
ELF     7e781000-7e794000       Deferred        libresolv.so.2
ELF     7e79f000-7e7bd000       Deferred        iphlpapi<elf>
  \-PE  7e7b0000-7e7bd000       \               iphlpapi
ELF     7e7bd000-7e81c000       Deferred        rpcrt4<elf>
  \-PE  7e7d0000-7e81c000       \               rpcrt4
ELF     7e81c000-7e8bd000       Deferred        ole32<elf>
  \-PE  7e830000-7e8bd000       \               ole32
ELF     7e8bd000-7e907000       Deferred        dsound<elf>
  \-PE  7e8c0000-7e907000       \               dsound
ELF     7e907000-7e974000       Deferred        quartz<elf>
  \-PE  7e910000-7e974000       \               quartz
ELF     7e974000-7e988000       Deferred        lz32<elf>
  \-PE  7e980000-7e988000       \               lz32
ELF     7e988000-7e9a1000       Deferred        version<elf>
  \-PE  7e990000-7e9a1000       \               version
ELF     7e9a1000-7ea31000       Deferred        winmm<elf>
  \-PE  7e9b0000-7ea31000       \               winmm
ELF     7ea31000-7eaf1000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eaf1000       \               comctl32
ELF     7eaf1000-7eb48000       Deferred        shlwapi<elf>
  \-PE  7eb00000-7eb48000       \               shlwapi
ELF     7eb48000-7ec59000       Deferred        shell32<elf>
  \-PE  7eb60000-7ec59000       \               shell32
ELF     7ec59000-7ecf2000       Deferred        gdi32<elf>
  \-PE  7ec70000-7ecf2000       \               gdi32
ELF     7ecf2000-7ee33000       Deferred        user32<elf>
  \-PE  7ed10000-7ee33000       \               user32
ELF     7ee33000-7ee82000       Deferred        advapi32<elf>
  \-PE  7ee40000-7ee82000       \               advapi32
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efb8000       Deferred        libnss_nis.so.2
ELF     7efb8000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c43000-b7c47000       Deferred        libdl.so.2
ELF     b7c47000-b7d91000       Deferred        libc.so.6
ELF     b7d91000-b7da9000       Deferred        libpthread.so.0
ELF     b7db4000-b7ee9000       Deferred        libwine.so.1
ELF     b7eeb000-b7f07000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Vernier Software\Logger Pro 3\LoggerPro.exe
        0000001d   15
        0000001c    1
        0000001b    2
        0000001a    1
        00000009    0 <==
0000000c 
        00000015    0
        00000014    0
        00000013    0
        00000012    0
        0000000e    0
        0000000d    0
0000000f 
        00000017    0
        00000016    0
        00000011    0
        00000010    0
00000018 
        00000019    0
Backtrace:
=>1 0x7b8417b2 RaiseException+0x7a() in kernel32 (0x0033ee70)
  2 0x7e684a79 in gdiplus (+0x14a79) (0x0033ee90)
  3 0x7e671934 in gdiplus (+0x1934) (0x0033ef2c)
  4 0x006b6ff0 in loggerpro (+0x2b6ff0) (0x0033f270)
  5 0x0060454f in loggerpro (+0x20454f) (0x00000000)
wine: Call from 0x7b841738 to unimplemented function gdiplus.dll.GdipCreateHICONFromBitmap, aborting
wine: Call from 0x7b841738 to unimplemented function gdiplus.dll.GdipCreateHalftonePalette, aborting
Killed

```

It says Permissions denied at first but it has something to do with ALSA which i think is something to do with sound and i don't need sound so that wouldn't really matter.  However i could be wrong.  what do you think?

---

### Post by geirha on 2008-10-07
First of all, don't ever use chmod 777. 

Secondly, install it somewhere other than your admin's home folder. You can select a different "homefolder" for wine (called wineprefix) by installing it with for example:
```
WINEPREFIX=/opt/wine/ wine /media/cdrom/install.exe
``` Of course you need to first create /opt/wine and give it proper permissions.
```

sudo mkdir /opt/wine/
sudo chown admin:admin /opt/wine

```

After it is installed, make sure the student account has read access and not write access to the logger application. Assuming student account is named **student** and has gid **student**, and also assuming here it got installed in "C:\Program Files\Logger".
```

sudo chgrp -R student "/opt/wine/drive_c/Program Files/Logger"
sudo chmod -R g-w "/opt/wine/drive_c/Program Files/Logger"

```
You might have to give some folders inside /opt/wine/drive_c/ write access, but it's hard to know which ones it wants to write things to.

As for the launcher, copying it from the desktop now, to the student's desktop should work fine. If the launcher has an icon, open the launcher-file (something.desktop) in an editor and read the value of Icon=, you should find that icon under /home/admin/.local/share/icons/ . Copy it to /usr/share/icons and it should be used automatically by the launcher at the student's desktop too.

Lastly, windows does things substantially different than linux. It really is easier to install it twice, than doing all of the above. 

Also, why disable the terminal?

---

### Post by geirha on 2008-10-07
> **the_master said:**
> 
It says Permissions denied at first but it has something to do with ALSA which i think is something to do with sound and i don't need sound so that wouldn't really matter.  However i could be wrong.  what do you think?

Try adding the student to the audio group and see if it makes any difference.
```
sudo adduser student audio
```

If the student is logged in when you add it to the group, you need to log out and back in again for it to take effect. Run "groups" in a terminal to confirm that it is in the audio group.

---

### Post by the_master on 2008-10-07
> Secondly, install it somewhere other than your admin's home folder. You can select a different "homefolder" for wine (called wineprefix) by installing it with for example:
Why shuld i install it somewhere other than the admin home folder?

> Lastly, windows does things substantially different than linux. It really is easier to install it twice, than doing all of the above.

I did install it twice, once in the admin account and another in the student account and the student account Logger pro is not working, see my post above for the output.
> Also, why disable the terminal?
If a user using the student account can use the terminal it isn't very locked down, so i disabled it.

Thanks for the reply, i'll try all this tomorrow and see if it fixes it.

---

### Post by the_master on 2008-10-07
> **geirha said:**
> Try adding the student to the audio group and see if it makes any difference.
```
sudo adduser student audio
```

If the student is logged in when you add it to the group, you need to log out and back in again for it to take effect. Run "groups" in a terminal to confirm that it is in the audio group.

The computer doesn't even have speakers so it really doesn't matter if any sound works at all.

---

### Post by pytheas22 on 2008-10-07
What else have you done to lock down the student account?  If logger pro works in the admin account but not in the student account, then there must be some problem with the students.  Which privileges have you reduced for the students?

It might help to give the students permission to use audio devices (go to System>Administration>Users and Groups to do this)--even if there are no speakers, the program could be crashing because of this; wine can do strange things sometimes.

Just to help diagnose the issue, you may want to create a new user account with default settings, installer logger pro (for a third time) under that account, and see if it works there under all of the default settings.  Then you can experiment with privileges to see what makes logger pro fail to work.

Also, as I'm sure geirha will tell you, you can't really do anything bad in the terminal if you don't have root access (and anyway, a clever student would know to press control-alt-F[1-6] to get to a command line anyway, unless you've also disabled that feature).

By the way, not to go off on a tangent, but have you checked to see if there's a free alternative to logger pro (provided you're not obligated by your school to use only logger pro)?  I don't know what exactly you need to do with it, but if it's just basic graphing and things, there are some free/open-source statistical programs these days that are quite sophisticated and user-friendly--I use them for my PhD work and pity my peers paying hundreds of dollars to do the same kinds of things.

---

### Post by geirha on 2008-10-08
> **the_master said:**
> Why shuld i install it somewhere other than the admin home folder?

I did install it twice, once in the admin account and another in the student account and the student account Logger pro is not working, see my post above for the output.

Since you wanted to run from the same installation with a different user. It will work having it in the home folder of admin, but it's bad practise. Though since you ended up installing it once for each user, then the home folder for admin is good. For the student account however, it should be moved to a different location, if not, they'll be able to delete the wineprefix, and consequently, logger pro ...

> **the_master said:**
> 
If a user using the student account can use the terminal it isn't very locked down, so i disabled it.

Thanks for the reply, i'll try all this tomorrow and see if it fixes it.

As pytheas22 pointed out, I don't see the point, they'll manage to get around it one way or another if they want to, but they can't do much harm. At least it shouldn't be regarded as a security measure. Anyway, this is getting off topic.

---

### Post by the_master on 2008-10-13
> **pytheas22 said:**
> What else have you done to lock down the student account?  If logger pro works in the admin account but not in the student account, then there must be some problem with the students.  Which privileges have you reduced for the students?
the only thing i've disabled so far is they aren't the administer of the system and they can't send and receive faxes, and they are a limited account.

> **pytheas22 said:**
> It might help to give the students permission to use audio devices (go to System>Administration>Users and Groups to do this)--even if there are no speakers, the program could be crashing because of this; wine can do strange things sometimes.
I did give them permissions now, didn't fix anything though, but just to prevent anything else to happening i added them.

> **pytheas22 said:**
> Just to help diagnose the issue, you may want to create a new user account with default settings, installer logger pro (for a third time) under that account, and see if it works there under all of the default settings.  Then you can experiment with privileges to see what makes logger pro fail to work.
I'll try this as a final solution

> **pytheas22 said:**
> Also, as I'm sure geirha will tell you, you can't really do anything bad in the terminal if you don't have root access (and anyway, a clever student would know to press control-alt-F[1-6] to get to a command line anyway, unless you've also disabled that feature).
Ya i didn't think of that so i did enable the terminal again.[/QUOTE]



> **pytheas22 said:**
> By the way, not to go off on a tangent, but have you checked to see if there's a free alternative to logger pro (provided you're not obligated by your school to use only logger pro)?  I don't know what exactly you need to do with it, but if it's just basic graphing and things, there are some free/open-source statistical programs these days that are quite sophisticated and user-friendly--I use them for my PhD work and pity my peers paying hundreds of dollars to do the same kinds of things.
Yes i did look, but i just searched for a "logger Pro alternative" not really just a graphing program because i'm not sure what the teacher is going to need to do that logger pro can do and an alternative might not.  However i never found an alternative.

> **geirha said:**
> Since you wanted to run from the same installation with a different user. It will work having it in the home folder of admin, but it's bad practise. Though since you ended up installing it once for each user, then the home folder for admin is good. For the student account however, it should be moved to a different location, if not, they'll be able to delete the wineprefix, and consequently, logger pro ...
Okay i installed logger pro in /opt/wine/...  and gave the student all ther permissions and all that stuff that you told me to do.  However its still doing the same thing (it tries to load but all i can see are the toolbars and everything else is black) so i think it is installed properly but something is preventing it to run correctly.  I can't figure out what it would be though.  Anyone have any ideas?

---

### Post by geirha on 2008-10-13
> **the_master said:**
> the only thing i've disabled so far is they aren't the administer of the system and they can't send and receive faces, and they are a limited account.

What's "faces"?

> **the_master said:**
> Okay i installed logger pro in /opt/wine/...  and gave the student all ther permissions and all that stuff that you told me to do.  However its still doing the same thing (it tries to load but all i can see are the toolbars and everything else is black) so i think it is installed properly but something is preventing it to run correctly.  I can't figure out what it would be though.  Anyone have any ideas?

Sounds like the only difference between the admin and student users are the groups they are a member of, so I'd second pytheas22's suggestion of creating a standard desktop user and see what the results are when you run it. Or possibly add the student user to all groups a desktop user is added to by default.

---

### Post by pytheas22 on 2008-10-13
Have you tried disabling desktop effects (System>Preferences>Appearance menu)?  There's a possibility that the black screen could be caused by that.  Also make sure that all other users on the system are logged off except for the account that's running Logger Pro; sometimes having multiple users logged in at the same time can cause weird video issues.

Please try installing Logger Pro a third time under a new account and let us know if it helps.

> What's "faces"?


I'm guessing he meant 'faxes' :)

---

