---
title: "Upstart service checklist"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Obfuscator on 2009-10-30
Hi,

Just upgraded to Karmic. I'd like to see the boot sequence, i.e

Starting postfix           ok
Starting nfs-common        fail
Starting postgres          ok

etc. I've removed 'splash' from the boot params, but this list is not present. I presume this is due to upstart, but where does this get logged and is it possible to get more detailed boot information somehow? I've googled for solutions and found upstart-logd but it seems to be phased out. What to do? I like to see which services are started, because I start in different environments and sometimes one or more fail, and I need to enable them manually once X is up. Then this is a great functionality. Secondly, the 'System->Admin->Services' utility is gone, where are all services listed ('/etc/event.d/'?).

Thanks

---

