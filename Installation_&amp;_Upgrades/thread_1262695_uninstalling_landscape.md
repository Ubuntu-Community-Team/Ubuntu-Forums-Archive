---
title: "uninstalling landscape"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by klausmedk on 2009-09-10
Hello!

I want to uninstall landscape on my Ubuntu 9.04 headless NAS because I do not use it.

Running: "sudo aptitude -s remove landscape-client" produces:

...
The following packages will be REMOVED:
  acl{u} hal{u} hal-info{u} landscape-client landscape-common{u} libffi5{u} libhal-storage1{u} libhal1{u} libpolkit-dbus2{u} libpolkit-grant2{u} libsmbios2{u} pm-utils{u} policykit{u} powermgmt-base{u} python-dbus{u} python-gobject{u} python-pexpect{u} python-pycurl{u} python-smartpm{u} python-twisted-bin{u} python-twisted-core{u} python-twisted-web{u} python-zopeinterface{u} smartdimmer{u}
0 packages upgraded, 0 newly installed, 24 to remove and 3 not upgraded.
...

To me it seems that it want to uninstall support for acl among other things. But I don't want to remove support for acl as I use it on my files.
And also should "hal" be removed?

Can somebody explain to me whether it is safe to carry on with uninstalling landscape-client?

regards
Klaus

---

