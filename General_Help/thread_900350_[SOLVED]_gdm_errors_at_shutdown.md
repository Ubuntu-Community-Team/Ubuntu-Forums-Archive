---
title: "[SOLVED] gdm errors at shutdown"
date: 2008-08-25
forum: General Help
---

### Post by Riffer on 2008-08-25
When I'm shutting down I get these 2 messages;

gdm[4478]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 

gdm[4478]: WARNING: Request for invalid configuration key xdmcp/Enable=false 

Any clues on what they are and how to fix them.

---

### Post by Riffer on 2008-08-25
There seems to be a bug in GDM thats been fixed upstream.  So its just a matter of time and the fix will be here, so I'm marking this solved.

---

### Post by rocketero2008 on 2008-09-01
I am also experiencing this problem:

 GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed

But somehow is aggravating because it keeps hanging at restarting for a minute or two, and on top of this error I am also suffering from the "CIFS VFS server connection error" witch adds up another minute or two to the re-starting process :(:(

---

### Post by vijaym on 2009-01-08
I am not sure that this is solved. This still seems to affect Hardy.

---

