---
title: "Skype installing in intrepid"
date: 2008-11-06
forum: General Help
---

### Post by Yumi on 2008-11-06
I try to install Skype in Ubuntu 8.10 from repositories. Skype seem to require some dependencies which do not load, maybe they are absent in Intrepid. Any advice on howto install?

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.4.3-0ubuntu1_i386.deb)
  Could not connect to cn.archive.ubuntu.com:80 (222.73.255.64), connection timed out

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-gui_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.4.3-0ubuntu1_i386.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qt4-qtconfig_4.4.3-0ubuntu1_i386.deb)
  Unable to connect to cn.archive.ubuntu.com http:

---

### Post by Mark_in_Hollywood on 2008-11-06
Open

System / Administration / Synaptic Package Manager

Once SPM is on-screen, open

Settings

Pull down:

Server for and select either main or United States 

and try to d/l Skype again.

I just installed it. WOW! I did have to select the hardware sound devices, 2 times before skype remembered them.

If the above doesn't work for you, I'll be watching this post for a few days. If it does, please mark the thread solved under red-letter "thread tools"

---

### Post by Yumi on 2008-11-07
You where quite right! I installed in Lhasa, Tibet and the repository server got set to China. Changing to Main solved the problem and Skype downloaded and installed without problem.
Now I have to go to the same process as you and try to set Skype so the sound works.

Thanks a lot
Michael

---

