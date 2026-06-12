---
title: "VMWare Tools won't install fully on Jaunty Server 9.04"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by Dougga on 2009-10-06
I'm having quite a problem getting VMWare Tools installed on a VM with Jaunty server loaded.

There appears to be nothing I can do to get the memory management piece of VMWare tools to work.

I've run the install tool several times after installing various things I felt might help, but alas, nadda.

Details on error:


make[1]: Entering directory '/usr/src/linux-headers-2.6.28-15-server'
  CC [M] /tmp/vmware-config2/vmmemctl-only/backdoorGcc32.o
  CC [M] /tmp/vmware-config2/vmmemctl-only/os.o
/tmp/bmware-config2/vmmemctl-only/os.c: In function 'os_init':
/tmp/vmware-config2/vmmemctl-only/os.c:590: error: 'struct proc_dir_entry' has no member named 'get_info'

Can anyone help?

Thanks,

~Doug

---

