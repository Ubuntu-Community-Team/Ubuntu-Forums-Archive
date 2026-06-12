---
title: "ATI/AMD Proprietary drivers"
date: 2011-11-26
forum: Hardware
---

### Post by Mr.Plex on 2011-11-26
For some reason I can't install the proprietary drivers. I checked the log but don't know how to approach it. 
/var/log/jockey.log
> 2011-11-26 13:02:25,026 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:25,027 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:25,119 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:25,119 DEBUG: fglrx_updates is not the alternative in use
**2011-11-26 13:02:25,575 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver**
2011-11-26 13:02:25,697 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-11-26 13:02:25,873 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:25,873 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:25,953 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:25,953 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:29,047 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,048 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:29,141 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,142 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:29,273 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,274 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-26 13:02:29,461 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,462 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-26 13:02:29,785 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,786 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:29,874 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:29,874 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:30,016 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:30,016 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:30,091 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:30,092 DEBUG: fglrx_updates is not the alternative in use
2011-11-26 13:02:30,216 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:30,216 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-11-26 13:02:30,388 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-11-26 13:02:30,389 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

Has anyone ever conquered these kind of **2011-11-26 13:02:25,575 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver** errors yet and lived to tell the tale?

---

### Post by Redblade20XX on 2011-11-26
Take a look at this! Hopefully it will help clean up your system and clean install the proprietary!

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

- Red

---

