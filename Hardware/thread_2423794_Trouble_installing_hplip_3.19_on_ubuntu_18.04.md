---
title: "Trouble installing hplip 3.19 on ubuntu 18.04"
date: 2019-07-29
forum: Hardware
---

### Post by lance bermudez on 2019-07-29
I have download the new deb packages from ubuntu packages the error I receive during install is below.
```

# dpkg -i *.deb
Selecting previously unselected package hplip.
(Reading database ... 348855 files and directories currently installed.)
Preparing to unpack hplip_3.19.1+dfsg0-1_amd64.deb ...
Unpacking hplip (3.19.1+dfsg0-1) ...
Preparing to unpack hplip-data_3.19.1+dfsg0-1_all.deb ...
Unpacking hplip-data (3.19.1+dfsg0-1) over (3.19.1+dfsg0-1) ...
Preparing to unpack hplip-doc_3.19.1+dfsg0-1_all.deb ...
Unpacking hplip-doc (3.19.1+dfsg0-1) over (3.19.1+dfsg0-1) ...
Preparing to unpack libhpmud0_3.19.1+dfsg0-1_amd64.deb ...
Unpacking libhpmud0:amd64 (3.19.1+dfsg0-1) over (3.19.1+dfsg0-1) ...
Preparing to unpack libsane-hpaio_3.19.1+dfsg0-1_amd64.deb ...
Unpacking libsane-hpaio:amd64 (3.19.1+dfsg0-1) over (3.19.1+dfsg0-1) ...
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.19.1+dfsg0-1); however:
  Version of printer-driver-hpcups on system is 3.17.10+repack0-5.
 hplip depends on python3 (>= 3.7~); however:
  Version of python3 on system is 3.6.7-1~18.04.

dpkg: error processing package hplip (--install):
 dependency problems - leaving unconfigured
Setting up hplip-data (3.19.1+dfsg0-1) ...
Setting up hplip-doc (3.19.1+dfsg0-1) ...
Setting up libhpmud0:amd64 (3.19.1+dfsg0-1) ...
Setting up libsane-hpaio:amd64 (3.19.1+dfsg0-1) ...
Processing triggers for dbus (1.12.2-1ubuntu1.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 hplip

```

python 3.6 is also installed on this box it came as the default. to fix python 3 problems i did
```

# apt install idle-python3.7 libpython3.7 libpython3.7-dbg libpython3.7-dev libpython3.7-minimal libpython3.7-stdlib libpython3.7-testsuite python3.7 python3.7-dbg python3.7-dev python3.7-doc python3.7-examples python3.7-minimal python3.7-venv

```

to set python3.7 as the default i did
```

sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 0
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 1
sudo update-alternatives --config python3
here are 2 choices for the alternative python3 (providing /usr/bin/python3).

  Selection    Path                Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python3.7   1         auto mode
  1            /usr/bin/python3.6   0         manual mode
  2            /usr/bin/python3.7   1         manual mode


```

---

### Post by brian_p on 2019-07-29
Why do you need hplip 3.19? What device are you using?

---

### Post by lance bermudez on 2019-07-30
Network printer at work hp officejet pro x451dw

---

### Post by ajgreeny on 2019-07-30
That printer will work with full support using the version of hplip avaiable in the repos of 18.04 so why not use that; it will install in the usual manner with software centre or ***sudo apt install hplip***

---

