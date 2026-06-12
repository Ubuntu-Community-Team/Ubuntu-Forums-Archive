---
title: "[SOLVED] Error removing file: Directory not empty"
date: 2008-08-24
forum: General Help
---

### Post by blah5754745 on 2008-08-24
Error removing file: Directory not empty

i get this and its really annoying lol, plz help if ya can thx :cry:

---

### Post by yabbadabbadont on 2008-08-24
Please provide more information.  What, exactly, are you trying to do?  What command did you run?  Which tool did you use?  That sort of stuff.  :)

---

### Post by blah5754745 on 2008-08-24
was just trying to right click/delete from trash and get this

---

### Post by yabbadabbadont on 2008-08-24
Are you saying that you were viewing the Trash, and tried to delete something that was already in the Trash?  Or did you get the error when you right clicked on the Trash and selected the Empty option?

---

### Post by blah5754745 on 2008-08-24
1st thing, but when i look in the trash bin there is still 3 files in there

---

### Post by yabbadabbadont on 2008-08-24
If you want to remove all of them, just right-click on the Trash and select the Empty option.  Does that work?

---

### Post by blah5754745 on 2008-08-24
it does not remove these three files because of that error
Error removing file: Directory not empty
(when i go into the trash bin and right click/delete them)

---

### Post by dexter.deepak on 2008-08-24
directories can be removed with the "-r" option of "rm"
```
sudo rm -rf /location/to/trash
```
dont try this code without knowing the exact location of your folder in trash.

---

### Post by blah5754745 on 2008-08-24
so i put in 
```

sudo rm -rf /location/to/trash/XFiDrv_Linux_US-1.18
```

and its still there, did i do it correctly? :confused:

---

### Post by dexter.deepak on 2008-08-24
no. the location of trash is ~/.local/share/Trash, so it should be ```
sudo rm -rf ~/.local/share/Trash/files/the_name_of_folder_here
```
 i have a doubt whether the location consistyes of files or Files, check it yourself, and replace the_name_of_folder_here with the folder you want to remove.

---

### Post by blah5754745 on 2008-08-24
i'm such a nub, i can't find where my trash bin is located lol

---

### Post by dexter.deepak on 2008-08-24
> **blah5754745 said:**
> i'm such a nub, i can't find where my trash bin is located lol

as i told before, your trash is in your home directory (denoted by ~)
```
cd ~/.local/share/Trash
```
this is your trash bin, where you would see 2 folders, 1 for files and other for the file-infos, just cd into the files folder and delete the folders present there. this is quite simple !!

---

### Post by blah5754745 on 2008-08-24
so, idk what to do i quit for now

[SIZE="3"][COLOR="Red"]Error removing file: Directory not empty[/COLOR][/SIZE]

DURRR i want the power to kill or save anything i click on!! :)

---

### Post by dexter.deepak on 2008-08-24
> **blah5754745 said:**
> so, idk what to do i quit for now

[SIZE="3"][COLOR="Red"]Error removing file: Directory not empty[/COLOR][/SIZE]

DURRR i want the power to kill or save anything i click on!! :)

i am surprised to see this response. can you please post the exact commends you used ?

---

### Post by blah5754745 on 2008-08-24
idk why i have to use a command to delete something completely out of the trash bin.

I've tried a bunch of commands none seem to work.

remember I'm a complete nub right now:popcorn:

---

### Post by kpatz on 2008-08-24
When you view the folder "haxfi" in the trash, what's in there?

This command:
```

rm -rf ~/.local/share/Trash

```

should empty the trash "completely".  It'll delete the entire trash folder, but it will be recreated next time you delete something into it.

---

### Post by blah5754745 on 2008-08-24
```
malay@malay-desktop:~$ rm -rf ~/.local/share/Trash
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/dummy.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/modules.order': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/ctalsa_main.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/amixer.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/pcm.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/emupia/modules.order': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/emupia/emupia_guids.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/emupia/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/emupia/emupia_main.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/plugins/cthwiut': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/plugins/pluginutils.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/plugins/ctexfifx': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/plugins/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/plugins/ct20xut': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/haxfi/modules.order': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/haxfi/haxfi_main.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/haxfi/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/ctossrv_main.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/modules.order': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/LinuxSys.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/osutils.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ossrv/LinuxReg.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/sfman/ctsfman_main.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/sfman/modules.order': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/sfman/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/utils/alsaver/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/utils/alsaver/alsaver.c': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ctbas2w.dat': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ctdlang.dat': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/settingsbkup.sfm': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ct_reg.dat': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/lang': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ctxficm.rfx': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/creative.state': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/settings.sfm': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ctdaught.dat': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/data': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/ctstatic.dat': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/CT1MGM.ROM': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/Default4.sfm': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/creative/CT2MGM.SF2': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/haxfi.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/cthwiut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ctsfman.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ct20xut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ctdriver.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ctexfifx.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/begin.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/cthwiut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/utils.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ctexfifx_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/emupia.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/end.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ct20xut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc3/ctossrv.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/haxfi.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/cthwiut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ctsfman.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ct20xut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ctdriver.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ctexfifx.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/begin.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/cthwiut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/utils.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ctexfifx_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/emupia.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/end.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ct20xut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/x86_64/gcc4/ctossrv.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/haxfi.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/cthwiut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ctsfman.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ct20xut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ctdriver.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ctexfifx.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/begin.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/cthwiut.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/utils.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ctexfifx_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/emupia.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/end.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ct20xut_ar.o': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/arch/i386/gcc4/ctossrv.a': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/linux': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/x86math.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/FeatureScale.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctioctl.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IasKernelModule.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/sfmain.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/osutils.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctdrv.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/cttypes.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctossrv.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IhwReg.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctdef.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IasDevReg.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IPluginManager.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/hwinfo.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/typedefs.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/PluginLinux.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/wintypes.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IasCtString.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/haxfi.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/plugindll.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IasOSSrv.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctcomdef.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/IasSystem.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/drvutils.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctalsa.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/PIAMain.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/asm': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctcomerr.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/PIAServ.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/include/ctstddef.h': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/configure': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/Makefile.conf.in': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/ctsound': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/ChangeLog': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/file_structure': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/src': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/creative.tar.gz': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/install-sh': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/globalrules.mk': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/README': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/AUTHORS': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/NEWS': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/arch': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/Makefile.build': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers (2)/include': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/configure': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/Makefile.conf.in': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/ctsound': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/ChangeLog': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/file_structure': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/src': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/creative.tar.gz': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/install-sh': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/globalrules.mk': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/README': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/AUTHORS': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/Makefile': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/NEWS': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/arch': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/Makefile.build': Permission denied
rm: cannot remove `/home/malay/.local/share/Trash/files/XFiDrv_Linux_US-1.2.18/drivers/include': Permission denied
malay@malay-desktop:~$ 

```

---

### Post by mssever on 2008-08-24
> **blah5754745 said:**
> ```
malay@malay-desktop:~$ rm -rf ~/.local/share/Trash
rm: cannot remove `/home/malay/.local/share/Trash/files/drivers/src/ctalsa/dummy.c': Permission denied

```
OK. You have a permissions problem. You can either fix the permissions, or (since you're deleting the files anyway), do ```
sudo rm -rf ~/.local/share/Trash
```I'm guessing that you extracted those files as root. That's why you can't empty the trash, though Nautilus really should display a better error message.

---

### Post by panayk on 2008-08-24
To fix the permissions:

> sudo chown -R $USER:$USER ~/.local/share/Trash && chmod -R u+w ~/.local/share/Trash

Then try again to empty the trash bin.

---

### Post by blah5754745 on 2008-08-24
> **mssever said:**
> OK. You have a permissions problem. You can either fix the permissions, or (since you're deleting the files anyway), do ```
sudo rm -rf ~/.local/share/Trash
```I'm guessing that you extracted those files as root. That's why you can't empty the trash, though Nautilus really should display a better error message.

holy crap i love you, 
```

sudo rm -rf ~/.local/share/Trash

```
fixed it

...if i'm not mistaken did ubuntu call me a dummy? :D

---

### Post by mssever on 2008-08-24
> **blah5754745 said:**
> holy crap i love you, 
```

sudo rm -rf ~/.local/share/Trash

```fixed it

...if i'm not mistaken did ubuntu call me a dummy? :D
To prevent these problems in the future, only operate as root (such as sudo or gksudo) when absolutely necessary. Some people think that you pretty much need to use sudo all the time, but that's not true, and you can mess up your permissions by doing that if you don't know what you're doing.

---

### Post by blah5754745 on 2008-08-25
thanks for the tip, command acknowledged.

---

### Post by tk1269 on 2008-09-08
I had a similar problem deleting a backup file that I had created but cancelled before it finished.  I could put it in the trash ok, but I couldn't get it back out.  Anyways, this helped me too.  Thanks.

---

