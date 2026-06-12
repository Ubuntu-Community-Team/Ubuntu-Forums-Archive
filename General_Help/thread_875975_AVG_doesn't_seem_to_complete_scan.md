---
title: "AVG doesn't seem to complete scan"
date: 2008-07-31
forum: General Help
---

### Post by CrusaderAD on 2008-07-31
I get this error when using the AVG scanner:

Cannot Open; Not Checked! Resource temporarily unavailable.

What does that mean? Is it not finishing it's scan?

---

### Post by dexter.deepak on 2008-07-31
when exactly do you get this error? and please post the complete post. run it through the terminal.

---

### Post by tuxxy on 2008-07-31
Maybe its to do with open apps or privileges

---

### Post by CrusaderAD on 2008-07-31
I ran it in terminal with sudo. Here's the error:

avggui: /opt/grisoft/avggui/prog/fsh.py:145: WARNING: OSError: [Errno 13] Permission denied: '/home/user/.gvfs'

---

### Post by dexter.deepak on 2008-07-31
> **raptormanad said:**
> I ran it in terminal with sudo. Here's the error:

avggui: /opt/grisoft/avggui/prog/fsh.py:145: WARNING: OSError: [Errno 13] Permission denied: '/home/user/.gvfs'

this is strange,i have full permissions to this.
have you tried this without sudo ??
add yourself to the fuse group.
alternatively go system -> user & groups and there see if you are having a permission to play with fuse filesystems.

---

### Post by CrusaderAD on 2008-07-31
When I run without sudo, I get a ton of errors cause it won't search certain areas without sudo. As for your other idea, yes, I am in the fuse group. Thanks looking at this.

---

