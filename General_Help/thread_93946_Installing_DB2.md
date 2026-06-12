---
title: "Installing DB2"
date: 2005-11-23
forum: General Help
---

### Post by pecanov on 2005-11-23
I've tried to install DB2 Personal Edition on Ubuntu Breezy, but unseccessefully.
Everytime I start db2install it freezes my computer at some stage (ussually after installing a dozen rpms.
Has anyone installed it successefully?

---

### Post by zenaan on 2005-11-24
I don't get a segfault etc, but the db2setup programs tells me:

"Installing DB2 file sets:.......Failure
ERROR:A major error occurred while installing "IBM DB2 Universal Database 
Express Edition" on this computer. The installation can not continue. If the 
problem persists please contact your technical service representative."

Tried custom and standard installs, same problem both times.

I installed the IBMJava2-SDK-1.4.1-2.0.i386.rpm using alien, and it seems to work fine - basic java binaries run, and the db2setup program runs.

I'm trying to install DB2UDB 8.2 on breezy/5.10 desktop edition on a DELL 700m latptop.

I'm wondering whether DB2 installs (and runs) on 5.10 or just 5.04? Not that I've tried 5.04, but I'd assume that _some_ release works, given the announcements.

Does Ubuntu server run on power boxes?

BTW, should I post my error in a new thread, or will it get addressed if in this thread?

ta
zenaan

---

### Post by suRoot on 2005-11-24
DB2 installs usually log to /tmp/db2setuplog, at least on the DB2 systems I've set up.  You may want to have a look at that for a more descriptive error.  If you find it, feel free to post it & maybe I can help you.

Part of my job involves installing, configuring & maintaining IBM software (mainly WebSphere products) & I can tell you from experience that unless you do everything *EXACTLY* right, things will *not* install - especially on Linux.  You can't count on the Infocenters being correct, either (in fact, a lot of times they're just outright wrong).

---

### Post by pecanov on 2005-11-25
My problem is that my computer freezes when installing db2 (with alien ofcourse). No installation crash, nothing in logs ...

---

