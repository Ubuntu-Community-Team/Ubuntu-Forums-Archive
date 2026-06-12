---
title: "Printer setup issue Ubuntu 15.10 and HP MFP M127 printer"
date: 2015-11-08
forum: Hardware
---

### Post by dave205 on 2015-11-08
I recently tried to install my HP HP_LaserJet_Pro_MFP_M127fw&#8221; printer on Ubuntu 15.10 desktop and ran into an issue.  Hopefully I'll outline my steps and it will help someone else and at least point them in the right direction.  


I started with trying to use the gui add printer tool and it actually DID find the printer. Everything looked correct except when I printed I would seethe error in the error_log found in /var/log/cups/error_log.
```


D[05/Nov/2015:18:59:49 -0600] [Job 4] prnt/hpcups/Hbpl1.cpp 52: Hbpl1constructor : m_szLanguage = HBPL1STATE: +hplip.plugin-error
D[05/Nov/2015:18:59:49 -0600] [Job 4] prnt/hpcups/HPCupsFilter.cpp486: m_Job initialization failed with error = 48
D[05/Nov/2015:18:59:49 -0600] [Job 4] prnt/backend/hp.c 919: ERROR:null print job total=0
D[05/Nov/2015:18:59:49 -0600] [Job 4] PID 3046(/usr/lib/cups/filter/hpcups) stopped with status 1.
D[05/Nov/2015:18:59:49 -0600] [Job 4] Hint: Try setting the LogLevelto "debug" to find out more.
```


From researching abit, I determined that the hplip package that was being automatically applied was incorrect (I guess?).  Here is the current HP page for the hplip package. 
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

The automatic method only worked (for me) after updating the OS via update-manager -d

during the install of hplip, I also had to download the Hp binary (link provided during hte install of the package).

---

### Post by dave205 on 2015-11-08
interesting!  I wrote up the post offline in LibreOffice Writer, connected to the forum, copy/pasted the entire text and several of my words were connected like "instructionsfor" and "notmore".  Maybe a bug in Libre?

---

