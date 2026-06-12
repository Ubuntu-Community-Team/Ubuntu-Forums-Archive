---
title: "apt-get problems after upgrade to 8.10"
date: 2008-11-06
forum: General Help
---

### Post by trewman on 2008-11-06
Hi Guys, 

Usually most problems I can nut out myself or use google but this one is really bugging me! I recently upgraded to the latest ubuntu from 8.4 - 8.10

Updates were working for a while but now when trying to update the system I get these errors:

```
luke@luke-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libgnomekbd-common (2.24.0-0ubuntu2) ...
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2339: parser error : StartTag: invalid element name
 &#2342;&#2367;&#2326;&#2366;&#2351;&#2375;&#2306; (&#2360;&#2367;&#2352;&#2381;&#2347; XFree &#2360;&#2350;&#2352;&#2381;&#2341;&#2367;&#2340; &#2348;&#2361;&#2369;a)<
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2339: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xE0 0xA4 0x20 0xE0
&#2342;&#2367;&#2326;&#2366;&#2351;&#2375;&#2306; (&#2360;&#2367;&#2352;&#2381;&#2347; XFree &#2360;&#2350;&#2352;&#2381;&#2341;&#2367;&#2340; &#2348;&#2361;&#2369;a)< 
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2344: parser error : Opening and ending tag mismatch: locale line 2342 and long
op (csi daz(&#2360;&#2367;többszaállítt&#65533;támogays&#65533; skupporihoz) minden ablakhoz</long
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2345: parser error : Opening and ending tag mismatch: schema line 2231 and locale
      </locale>
               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2348: parser error : expected '>'
/shortiiónassieme ai grupplongvecersiiiónassiene i de nomes de grupo</shortii
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2348: parser error : Opening and ending tag mismatch: locale line 2347 and shortii
/shortiiónassieme ai grupplongvecersiiiónassiene i de nomes de grupo</shortii
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2348: parser error : Opening and ending tag mismatch: schemalist line 3 and long
ep names (assie&#2360;&#2367;ort>rsions aa dme ai gruppiXFree sup)ati per finestra</long
                                                                               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2349: parser error : Opening and ending tag mismatch: gconfschemafile line 2 and locale
      </locale>
               ^
/usr/share/gconf/schemas/desktop_gnome_peripherals_keyboard_xkb.schemas:2351: parser error : Extra content at the end of the document
      <locale name="ja">
      ^
dpkg: error processing libgnomekbd-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomekbd3:
 libgnomekbd3 depends on libgnomekbd-common (= 2.24.0-0ubuntu2); however:
  Package libgnomekbd-common is not configured yet.
dpkg: error processing libgnomekbd3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbdui3:
 libgnomekbdui3 depends on libgnomekbd3; however:
  Package libgnomekbd3 is not configured yet.
dpkg: error processing libgnomekbdui3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libgnomekbd3; however:
  Package libgnomekbd3 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgnomekbd3; however:
  Package libgnomekbd3 is not configured yet.
 gnoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                            No apport report written because MaxReports is reached already
                                                                                                                          No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                        No apport report written because MaxReports is reached already
                                                          me-control-center depends on libgnomekbdui3; however:
  Package libgnomekbdui3 is not configured yet.
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd-dev:
 libgnomekbd-dev depends on libgnomekbd3 (= 2.24.0-0ubuntu2); however:
  Package libgnomekbd3 is not configured yet.
dpkg: error processing libgnomekbd-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbdui-dev:
 libgnomekbdui-dev depends on libgnomekbdui3 (= 2.24.0-0ubuntu2); however:
  Package libgnomekbdui3 is not configured yet.
 libgnomekbdui-dev depends on libgnomekbd-dev; however:
  Package libgnomekbd-dev is not configured yet.
dpkg: error processing libgnomekbdui-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomekbd-common
 libgnomekbd3
 libgnomekbdui3
 gnome-settings-daemon
 gnome-control-center
 gnome-panel
 libgnomekbd-dev
 libgnomekbdui-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
luke@luke-laptop:~$ 

```

Obviously the problem is with gnome but how do I go about solving this problem?

Cheers

---

### Post by tomthumb99 on 2009-01-27
This thread address prob to a point

[http://ubuntuforums.org/showthread.php?t=810176]("http://ubuntuforums.org/showthread.php?t=810176")

---

