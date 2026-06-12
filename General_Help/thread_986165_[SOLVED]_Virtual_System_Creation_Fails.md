---
title: "[SOLVED] Virtual System Creation Fails"
date: 2008-11-18
forum: General Help
---

### Post by beattyml1 on 2008-11-18
When I use the virtual machine manager(0.5.4, powered by libvirt, (C) Red Hat) to try to create a new  virtual desktop it will sucessfully create the file for the image for the virtual hard drive, and then fails and gives the following error message.

Unable to complete install: 'virDomainCreateLinux() failed internal error invalid domain type attribute'

Details:

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed internal error invalid domain type attribute
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 652, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 902, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 923, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 841, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed internal error invalid domain type attribute




I have limited experience in the terminal(cd, ls, cp, apt-get, and similar commands), but am willing to learn if neccessaary to fix the problem

---

### Post by Xyem on 2008-12-15
I'm having the same issue..

> Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed internal error invalid domain type attribute
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 652, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 902, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 923, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 841, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed internal error invalid domain type attribute
'

Will let you know if I find anything..

---

### Post by Xyem on 2008-12-15
I installed the 'qemu' package. Now 'qemu' appears as a hypervisor choice ( under i686 etc. ) and it seems to work..

I thought kvm was a direct replacement for qemu ( perhaps a symlink would have also fixed this? ) but I guess not.

All in all, it appears that an empty hypervisor selection causes the error.

Hope this helps you beattyml1!

---

