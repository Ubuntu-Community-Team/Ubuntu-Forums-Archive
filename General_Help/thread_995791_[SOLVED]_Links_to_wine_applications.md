---
title: "[SOLVED] Links to wine applications"
date: 2008-11-28
forum: General Help
---

### Post by IanB2 on 2008-11-28
I've recently installed wine and have a couple of very old windows applications sort of running OK (printing problems etc)

I've been trying to create a link to either the desktop or menu as my wife won't be impressed having to launch an application from the terminal!

Hence the problem. If I create a link within the same folder as the application resides in, all is well (but this is not very useful). As soon as I move the link to another directory, the link refuses to work. I've tried various ways of pointing to the file including *wine "C:\Program Files\my application\application.exe"* but none have worked.

I can launch the application from the terminal but get an odd error message during launch: 
[I]fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
fixme:mmio:MMIO_InstallIOProc Global procedures not implemented[/I]

Any suggestions?

---

### Post by lovinglinux on 2008-11-28
Right click in the desktop, select "Create launcher" option and add a command like this:

"/home/[COLOR="Red"]**me**[/COLOR]/.wine/drive_c/Program Files/my application\application.exe"

Don't remove the quotes!

---

### Post by IanB2 on 2008-11-28
> **lovinglinux said:**
> Right click in the desktop, select "Create launcher" option and add a command like this:

"/home/[COLOR="Red"]**me**[/COLOR]/.wine/drive_c/Program Files/my application\application.exe"

Don't remove the quotes!

Thanks ..... partial success .... one application fine, the other is giving error messages because in windows the directory likes to reside under c:

I actually put 
*wine "/home/me/.wine/drive_c/Program Files/my app/app.exe"*
in the command line after experimenting in a terminal first.

---

### Post by IanB2 on 2008-11-28
> **IanB2 said:**
> Thanks ..... partial success .... one application fine, the other is giving error messages because in windows the directory likes to reside under c:

I actually put 
*wine "/home/me/.wine/drive_c/Program Files/my app/app.exe"*
in the command line after experimenting in a terminal first.

I've just had another look at how the shortcut is set up in windows and I have to set the 'start in' directory to point to the application. When the application tries to launch under wine, it cannot find the correct directory and I get a load of error messages. 

Is there a way of forcing the application to run from the correct directory from the command line (or using a program launcher)?

---

