---
title: "Amarok fails to start up."
date: 2005-11-27
forum: General Help
---

### Post by Luggy on 2005-11-27
I'm having some trouble getting amarok to start up correctly. Even after I reset my computer or when I complete remove amarok and then re-install it. When I try and start amarok, I get the splash screen and then it goes away right away. 
Here is what I'm getting as my output when I try and run it in console.

```
paul@ubuntu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
paul@ubuntu:~$ SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3600037
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3600037
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3600037
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)


```

---

### Post by Bachstelze on 2005-11-27
Amarok is normally a KDE app, so it's normal you have some problems with GNOME. Perhaps you're missing some packages ? On my comp, it works fine...

---

### Post by Luggy on 2005-11-27
Well the problem is that it used to run fine on my computer until I ran swfplayer. Then it stopped working.

---

### Post by Luggy on 2005-11-27
I fixed the problem.
Aparently the swf (flash) decoders for gstreamer were screwing around with my gstreamer engine on amarok.

Once I removed that (and swfplayer) I was good to go.

---

### Post by Copter on 2005-12-22
[QUOTE=Luggy]I fixed the problem.
Aparently the swf (flash) decoders for gstreamer were screwing around with my gstreamer engine on amarok.

Once I removed that (and swfplayer) I was good to go.[/QUOTE]
i had the same problem with AmaroK 1.3.1 on Kubuntu Breezy 5.10. ive istalled Amarok 1.3.7 but it hasnt changed anything. i did as you said (just removed **gstreamer0.8-swfdec**) and now it works fine again.

thanks a lot Luggy! this forum rules!

copter :]

---

### Post by RSX311 on 2005-12-22
install amarok-xine, I think it sounds way better than gstreamer

```
sudo apt-get install amarok-xine
```

then go to the options and configure it for xine

---

### Post by Copter on 2005-12-24
[QUOTE=RSX311]install amarok-xine, I think it sounds way better than gstreamer

```
sudo apt-get install amarok-xine
```

then go to the options and configure it for xine[/QUOTE]
ive istalled amarok-xine but first i had to run amarok to change this option :). deleting ~/.kde/apps/amarok did not helped here also. btw removing gstreamer0.8-swfdec did not affect flash on my computer.

copter :]

---

### Post by pedrorolo on 2006-01-08
[QUOTE=Luggy]I'm having some trouble getting amarok to start up correctly. Even after I reset my computer or when I complete remove amarok and then re-install it. When I try and start amarok, I get the splash screen and then it goes away right away. 
Here is what I'm getting as my output when I try and run it in console.

```
paul@ubuntu:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
paul@ubuntu:~$ SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
SWFDEC: ERROR: swfdec_font.c(158): tag_func_define_font_2: langcode 2
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3600037
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3600037
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3600037
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)


```[/QUOTE]


I have more or less the same problem:

```
$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for job!

```

 I already removed gstreamer's swf-dec and it continues as shity as is was... :(

Ah! and the most funny thing is that after chashing, amarok opens mozilla thunderbird

---

