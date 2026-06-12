---
title: "installation problem with ktorrent tar.gz file"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by keedaiit on 2009-03-01
i was able to extect the file using the tar -xvf command
now i am into the configuring part
but when i am trying to use the ./configure command
i am the error message of 
bash: ./configure: No such file or directory
dunno what to do can anybody help here?

---

### Post by taurus on 2009-03-01
After you unpacked it, does it create a new directory?  What's the output of this command from a terminal, assuming you are in the directory where you have just unpacked ktorrent?

```
ls -la
```

---

### Post by keedaiit on 2009-03-01
well the result was 
i was able to create a new folder on the desktop 
when i used the -ls la command the output was this .
total 108
drwxr-xr-x 14 pratik pratik  4096 2009-02-15 22:40 .
drwxr-xr-x  6 pratik pratik  4096 2009-03-01 19:49 ..
-rw-r--r--  1 pratik pratik 26844 2009-02-15 22:37 ChangeLog
drwxr-xr-x  3 pratik pratik  4096 2009-02-15 22:37 cmake
-rw-r--r--  1 pratik pratik  2118 2009-02-15 22:40 CMakeLists.txt
-rw-r--r--  1 pratik pratik 18273 2009-02-15 22:37 COPYING
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 ideal
drwxr-xr-x  3 pratik pratik  4096 2009-02-15 22:37 ktorrent
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 ktupnptest
drwxr-xr-x 15 pratik pratik  4096 2009-02-15 22:37 libbtcore
drwxr-xr-x  7 pratik pratik  4096 2009-02-15 22:37 libktcore
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 libktupnp
drwxr-xr-x  4 pratik pratik  4096 2009-02-15 22:37 plasma
drwxr-xr-x 17 pratik pratik  4096 2009-02-15 22:37 plugins
drwxr-xr-x 41 pratik pratik  4096 2009-02-15 22:40 po
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 scripts
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 templates


can somebody help me now

---

### Post by taurus on 2009-03-01
While you are in that newly created directory after you've unpacked ktorrent, change to ktorrent directory and post the output of this command.

```
cd ktorrent
ls -la
```

---

### Post by keedaiit on 2009-03-01
total 708
drwxr-xr-x  3 pratik pratik  4096 2009-02-15 22:37 .
drwxr-xr-x 14 pratik pratik  4096 2009-02-15 22:40 ..
-rw-r--r--  1 pratik pratik  2537 2009-02-15 22:37 addpeersdlg.cpp
-rw-r--r--  1 pratik pratik  2095 2009-02-15 22:37 addpeersdlg.h
-rw-r--r--  1 pratik pratik  3957 2009-02-15 22:37 addpeersdlg.ui
-rw-r--r--  1 pratik pratik  3592 2009-02-15 22:37 advancedpref.cpp
-rw-r--r--  1 pratik pratik  2288 2009-02-15 22:37 advancedpref.h
-rw-r--r--  1 pratik pratik 14630 2009-02-15 22:37 advancedpref.ui
-rw-r--r--  1 pratik pratik  2400 2009-02-15 22:37 app.cpp
-rw-r--r--  1 pratik pratik  1756 2009-02-15 22:37 app.h
-rw-r--r--  1 pratik pratik 12640 2009-02-15 22:37 btpref.ui
-rw-r--r--  1 pratik pratik  1781 2009-02-15 22:37 CMakeLists.txt
-rw-r--r--  1 pratik pratik 30414 2009-02-15 22:37 core.cpp
-rw-r--r--  1 pratik pratik  9778 2009-02-15 22:37 core.h
-rw-r--r--  1 pratik pratik 10517 2009-02-15 22:37 fileselectdlg.cpp
-rw-r--r--  1 pratik pratik  2562 2009-02-15 22:37 fileselectdlg.h
-rw-r--r--  1 pratik pratik  9453 2009-02-15 22:37 fileselectdlg.ui
-rw-r--r--  1 pratik pratik  8039 2009-02-15 22:37 generalpref.ui
-rw-r--r--  1 pratik pratik  2432 2009-02-15 22:37 groupfiltermodel.cpp
-rw-r--r--  1 pratik pratik  2324 2009-02-15 22:37 groupfiltermodel.h
-rw-r--r--  1 pratik pratik  2973 2009-02-15 22:37 grouppolicydlg.cpp
-rw-r--r--  1 pratik pratik  1916 2009-02-15 22:37 grouppolicydlg.h
-rw-r--r--  1 pratik pratik  8676 2009-02-15 22:37 grouppolicydlg.ui
-rw-r--r--  1 pratik pratik 14901 2009-02-15 22:37 groupview.cpp
-rw-r--r--  1 pratik pratik  4123 2009-02-15 22:37 groupview.h
-rw-r--r--  1 pratik pratik 22868 2009-02-15 22:37 gui.cpp
-rw-r--r--  1 pratik pratik  6304 2009-02-15 22:37 gui.h
drwxr-xr-x  2 pratik pratik  4096 2009-02-15 22:37 icons
-rw-r--r--  1 pratik pratik 11102 2009-02-15 22:37 importdialog.cpp
-rw-r--r--  1 pratik pratik  2893 2009-02-15 22:37 importdialog.h
-rw-r--r--  1 pratik pratik  3587 2009-02-15 22:37 importdialog.ui
-rw-r--r--  1 pratik pratik  5230 2009-02-15 22:37 ipfilterlist.cpp
-rw-r--r--  1 pratik pratik  2894 2009-02-15 22:37 ipfilterlist.h
-rw-r--r--  1 pratik pratik  5727 2009-02-15 22:37 ipfilterwidget.cpp
-rw-r--r--  1 pratik pratik  2183 2009-02-15 22:37 ipfilterwidget.h
-rw-r--r--  1 pratik pratik  3085 2009-02-15 22:37 ipfilterwidget.ui
-rw-r--r--  1 pratik pratik  3603 2009-02-15 22:37 ktorrent.desktop
-rw-r--r--  1 pratik pratik 14813 2009-02-15 22:37 ktorrent.notifyrc
-rw-r--r--  1 pratik pratik  1106 2009-02-15 22:37 ktorrentplugin.desktop
-rw-r--r--  1 pratik pratik  2735 2009-02-15 22:37 ktorrentui.rc
-rw-r--r--  1 pratik pratik  8189 2009-02-15 22:37 main.cpp
-rw-r--r--  1 pratik pratik  5249 2009-02-15 22:37 missingfilesdlg.cpp
-rw-r--r--  1 pratik pratik  2570 2009-02-15 22:37 missingfilesdlg.h
-rw-r--r--  1 pratik pratik  4815 2009-02-15 22:37 missingfilesdlg.ui
-rw-r--r--  1 pratik pratik  3267 2009-02-15 22:37 networkpref.cpp
-rw-r--r--  1 pratik pratik  2004 2009-02-15 22:37 networkpref.h
-rw-r--r--  1 pratik pratik 12762 2009-02-15 22:37 networkpref.ui
-rw-r--r--  1 pratik pratik  2393 2009-02-15 22:37 pastedialog.cpp
-rw-r--r--  1 pratik pratik  1978 2009-02-15 22:37 pastedialog.h
-rw-r--r--  1 pratik pratik  1841 2009-02-15 22:37 pastedlgbase.ui
-rw-r--r--  1 pratik pratik  6324 2009-02-15 22:37 prefdialog.cpp
-rw-r--r--  1 pratik pratik  2792 2009-02-15 22:37 prefdialog.h
-rw-r--r--  1 pratik pratik  3290 2009-02-15 22:37 proxypref.cpp
-rw-r--r--  1 pratik pratik  2037 2009-02-15 22:37 proxypref.h
-rw-r--r--  1 pratik pratik 13577 2009-02-15 22:37 proxypref.ui
-rw-r--r--  1 pratik pratik 11767 2009-02-15 22:37 qmpref.ui
-rw-r--r--  1 pratik pratik 10386 2009-02-15 22:37 queuemanagermodel.cpp
-rw-r--r--  1 pratik pratik  3661 2009-02-15 22:37 queuemanagermodel.h
-rw-r--r--  1 pratik pratik  5714 2009-02-15 22:37 queuemanagerwidget.cpp
-rw-r--r--  1 pratik pratik  2570 2009-02-15 22:37 queuemanagerwidget.h
-rw-r--r--  1 pratik pratik  1842 2009-02-15 22:37 queuemanagerwidget.ui
-rw-r--r--  1 pratik pratik  9385 2009-02-15 22:37 recommendedsettingsdlg.cpp
-rw-r--r--  1 pratik pratik  2487 2009-02-15 22:37 recommendedsettingsdlg.h
-rw-r--r--  1 pratik pratik 10537 2009-02-15 22:37 recommendedsettingsdlg.ui
-rw-r--r--  1 pratik pratik  5727 2009-02-15 22:37 scandlg.cpp
-rw-r--r--  1 pratik pratik  3200 2009-02-15 22:37 scandlg.h
-rw-r--r--  1 pratik pratik  7668 2009-02-15 22:37 scandlg.ui
-rw-r--r--  1 pratik pratik  5612 2009-02-15 22:37 speedlimitsdlg.cpp
-rw-r--r--  1 pratik pratik  2173 2009-02-15 22:37 speedlimitsdlg.h
-rw-r--r--  1 pratik pratik  4152 2009-02-15 22:37 speedlimitsdlg.ui
-rw-r--r--  1 pratik pratik  7590 2009-02-15 22:37 speedlimitsmodel.cpp
-rw-r--r--  1 pratik pratik  2942 2009-02-15 22:37 speedlimitsmodel.h
-rw-r--r--  1 pratik pratik  3184 2009-02-15 22:37 spinboxdelegate.cpp
-rw-r--r--  1 pratik pratik  2331 2009-02-15 22:37 spinboxdelegate.h
-rw-r--r--  1 pratik pratik  3998 2009-02-15 22:37 statusbar.cpp
-rw-r--r--  1 pratik pratik  2822 2009-02-15 22:37 statusbar.h
-rw-r--r--  1 pratik pratik 10332 2009-02-15 22:37 torrentcreatordlg.cpp
-rw-r--r--  1 pratik pratik  2586 2009-02-15 22:37 torrentcreatordlg.h
-rw-r--r--  1 pratik pratik 10764 2009-02-15 22:37 torrentcreatordlg.ui
-rw-r--r--  1 pratik pratik  5075 2009-02-15 22:37 torrentmigratordlg.cpp
-rw-r--r--  1 pratik pratik  2660 2009-02-15 22:37 torrentmigratordlg.h
-rw-r--r--  1 pratik pratik  1776 2009-02-15 22:37 torrentmigratordlg.ui
-rw-r--r--  1 pratik pratik 11965 2009-02-15 22:37 trayicon.cpp
-rw-r--r--  1 pratik pratik  4372 2009-02-15 22:37 trayicon.h
-rw-r--r--  1 pratik pratik 13622 2009-02-15 22:37 view.cpp
-rw-r--r--  1 pratik pratik  4730 2009-02-15 22:37 view.h
-rw-r--r--  1 pratik pratik 17182 2009-02-15 22:37 viewmanager.cpp
-rw-r--r--  1 pratik pratik  5839 2009-02-15 22:37 viewmanager.h
-rw-r--r--  1 pratik pratik 18623 2009-02-15 22:37 viewmodel.cpp
-rw-r--r--  1 pratik pratik  5793 2009-02-15 22:37 viewmodel.h
-rw-r--r--  1 pratik pratik  3396 2009-02-15 22:37 viewselectionmodel.cpp
-rw-r--r--  1 pratik pratik  2247 2009-02-15 22:37 viewselectionmodel.h

i am not getting the conf file nor am getting ther read me file in software.

---

### Post by taurus on 2009-03-01
Where exactly did you download ktorrent.tar.gz?  It's probably faster for me to have a look at it on my system instead of asking you to run every command and post the result!

---

### Post by keedaiit on 2009-03-01
wee,i told you it was download by the archive manger on my desktop

---

### Post by keedaiit on 2009-03-02
i have downloaded it no my desktop.

---

### Post by oldos2er on 2009-03-02
From which website did you download it?

---

### Post by keedaiit on 2009-03-02
i have downloaded it from softpedia could you help me please

---

### Post by oldos2er on 2009-03-02
This is from the developer's website:

To compile KTorrent : 
 cd directory_where_ktorrent_source_code_is
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
make
sudo make install

---

### Post by maybeway36 on 2009-03-02
It migh be easier jus to go into Synaptic (or Adept) and install the ktorrent package from there.

---

### Post by oldos2er on 2009-03-02
The repositories only have 3.12.

---

### Post by keedaiit on 2009-03-03
where the source code is means.........
i have extracted ktorretn on my desktop
in that folder there is another ktorretn folder in which thre are two ktorretn files..........

---

### Post by stoeptegel on 2009-03-03
Try to compile with the wiki's faq, see this:
[http://ktorrent.org/wiki/index.php/FAQ](http://ktorrent.org/wiki/index.php/FAQ)

---

