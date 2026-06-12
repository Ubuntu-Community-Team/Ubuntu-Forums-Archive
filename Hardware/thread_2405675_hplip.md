---
title: "hplip"
date: 2018-11-09
forum: Hardware
---

### Post by pfd272 on 2018-11-09
I stupidly installed hplip from hp's page to get my printer working in 18.10. It warned me 18.10 wasn't supported but would install
18.04 instead. I'm now getting errors when trying to do "apt upgrade". Is there a way to roll back to the hplip that came default with 18.10?

  ```
rob@Lenny:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up python3 (3.6.7-1~18.10) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/deviceuricombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr_ext.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabgrouptable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabnametable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/filetable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/loadpapergroupbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printernamecombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettings_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingstoolbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/queuesconf.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/readonlyradiobutton.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systemtray.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/ui_utils.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog_base.py'
error running python rtupdate hook hplip-data
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-pyqt5:
 python3-pyqt5 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-pyqt5 depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-pyqt5 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pyqt5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-notify2:
 python3-notify2 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg:o apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                    No apport report written because MaxReports is reached already
                                              m error processing package python3-notify2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-sip:
 python3-sip depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-sip depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-sip depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-sip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.6.6-1~); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
        dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent processing triggers for gnome-menus:
 gnome-menus depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-menus (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-dbus.mainloop.pyqt5:
 python3-dbus.mainloop.pyqt5 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-dbus.mainloop.pyqt5 depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-dbus.mainloop.pyqt5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on python3-dbus.mainloop.pyqt5; however:
  Package python3-dbus.mainloop.pyqt5 is not configured yet.
 hplip-gui depends on python3-pyqt5; however:
  Package python3-pyqt5 is not configured yet.

dpkg: error processing package hplip-gui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:18.10.11.1); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:18.10.11.1); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python3
 python3-pyqt5
 ubuntu-release-upgrader-core
 python3-notify2
 python3-sip
 python3-gdbm:amd64
 gnome-menus
 python3-dbus.mainloop.pyqt5
 python3-distupgrade
 hplip-gui
 ubuntu-release-upgrader-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ajgreeny on 2018-11-09
What printer are you having trouble with, and does it really need the hplip version from their own website.
How did you install hplip; was it using the method shown at [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index) which is how I have installed sometimes in the past when using a very new printer model?
Please also check that you have python3 installed; I suspect it is a default in new Ubuntu versions but it's worth checking that it's installed and which version you have.  It looks as if you need version 3.6 but lower than 3.8 according to the error shown
```
python3-dbus.mainloop.pyqt5 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-dbus.mainloop.pyqt5 depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
```

Cosmic's default hplip version is 3.18.7+dfsg1-2ubuntu2 and the hplip site itself has 3.18.10, not very different.
It may be worth trying to remove hplip and then install using the normal apt remove/install commands but it looks as if your attempt to install direct has also brought in a lot of python versions that are not compatible with cosmic, so you may still have problems.

---

### Post by slickymaster on 2018-11-09
*Thread moved to **Hardware**.*

---

### Post by pfd272 on 2018-11-10
I tried what you suggested, but was still getting errorsso I ended up going back to 18.04. I'll stick with the lts for now

Thanks

---

