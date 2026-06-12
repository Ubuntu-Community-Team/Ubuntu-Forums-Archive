---
title: "virt-manager 0.7.0"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by mk6032 on 2009-03-29
I'm trying to upgrade to upgrade virt-manager to the latest version. From what I can tell, the package management is two versions behind at 0.5.4. 0.7.0 offers significant improvements from what I've read so I wanted to build a package for it. I first downloaded the source a ran ./configure. It failed with a python-gtk error so I apt installed the python-gtk2 and python-gtk2-dev packages and all was well. I then ran make and make install which also were successful, then sudo virt-manager. A screen pops up and says: 

Error starting Virtual Machine Manager: cannot import name Storage
Details ->
Traceback (most recent call last):
  File "/usr/local/share/virt-manager/virt-manager.py", line 368, in <module>
    main()
  File "/usr/local/share/virt-manager/virt-manager.py", line 309, in main
    from virtManager.engine import vmmEngine
  File "/usr/local/share/virt-manager/virtManager/engine.py", line 34, in <module>
    from virtManager.details import vmmDetails
  File "/usr/local/share/virt-manager/virtManager/details.py", line 36, in <module>
    from virtManager.addhardware import vmmAddHardware
  File "/usr/local/share/virt-manager/virtManager/addhardware.py", line 34, in <module>
    from virtManager.storagebrowse import vmmStorageBrowser
  File "/usr/local/share/virt-manager/virtManager/storagebrowse.py", line 29, in <module>
    import virtManager.host
  File "/usr/local/share/virt-manager/virtManager/host.py", line 27, in <module>
    from virtinst import Storage
ImportError: cannot import name Storage

---

### Post by mk6032 on 2009-04-02
I posted this on Launchpad tonight: 

[https://answers.launchpad.net/ubuntu/+question/66295](https://answers.launchpad.net/ubuntu/+question/66295)

---

