---
title: "which apach2 config files to backup?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Ascenti0n on 2009-11-06
I'm about to do a clean install of Ubuntu 9.10 due to various issues after an upgrade from 9.04.

I have a separate home partition and have backed up my sites in /var/www. I have also backup up my MySQL dbs, but I'm not sure which apache2 config files to backup.

I think there is probably only 2 apache.conf and another, but I can't remember.

Can someone confirm files I need to backup pls.

Thanks

---

### Post by pdoes on 2009-11-06
I would backup the /etc/apache2 directory
it holds your conf, enabled mods, enabled sites.

If you run PHP also backup your /etc/php5 directory.

---

### Post by Ascenti0n on 2009-11-06
thanks. I take it I can simply copy back the two folders AFTER installing the LAMP stack, under the new install, OVERWRITING default folders created at installation time?

PS you have a remarkable likeness to the singer from "the Doors" ;)

---

### Post by pdoes on 2009-11-06
As you already did an upgrade to Karmic, the files in the folders are updated as well, so I would say yes you can just copy them back.

Personally I would backup the directories after the fresh install, just to be safe.

Re P.S. I hear that a lot :lolflag: Your avatar seems to be from Jimmy Neutron, but I could be wrong

---

