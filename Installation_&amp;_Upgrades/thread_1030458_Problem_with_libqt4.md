---
title: "Problem with libqt4"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by delphiexile on 2009-01-04
Hi every body;

     First , i've tried to install realplayer but an error occured always : "Cannot install lsb " ; i tracked the problem and i had this problem when i tried to install "libqt4" packages:

[IMG]http://img187.imageshack.us/img187/5448/screenshotwa5.png[/IMG]

      I tried using terminal ; and i have the same problem using this command: **sudo apt-get -f install libqt4-gui libqt4-core**

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libqt4-core: Depends: libqtcore4 (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
               Depends: libqt4-network (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
               Depends: libqt4-script (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
               Depends: libqt4-xml (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
               Depends: libqt4-dbus (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
               Depends: libqt4-test (= 4.4.3-0ubuntu1) but it is not going to be installed
  libqt4-gui: Depends: libqtgui4 (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
              Depends: libqt4-svg (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
              Depends: libqt4-opengl (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
              Depends: libqt4-designer (= 4.4.3-0ubuntu1) but 4.4.3-0ubuntu1.1 is to be installed
              Depends: libqt4-assistant (= 4.4.3-0ubuntu1) but it is not going to be installed
E: Broken packages

```

Thanks for helping me.

---

### Post by delphiexile on 2009-01-05
Is there anyone who encountered this problem ....

---

### Post by mc4man on 2009-01-05
To start go into System -> admin... -> software sources and see if under the 'updates' tab if 'Recommended Updates (intrepid-updates) is checked. If not checked, then enable and reload.

Post back as to whether it was enabled or not.

---

### Post by delphiexile on 2009-01-05
Thanks it works

---

