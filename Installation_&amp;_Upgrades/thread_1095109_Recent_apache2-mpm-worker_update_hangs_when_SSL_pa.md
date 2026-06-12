---
title: "Recent apache2-mpm-worker update hangs when SSL password required"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by plyte on 2009-03-13
3/13/09 apache2-mpm-worker update

Problem
The apache2-mpm-worker update hangs when the apache2 server is configured to require a pass phrase to start apache2 with SSL.

Description
When installing the apache2-mpm-worker update it requires that apache2 be restarted, this all happens in an internal terminal embedded within the software update, which can be made visible by expanding "Details." The update hangs when apache2 requires a pass phrase to start up configured with SSL, which my server requires by default.

Currently, there's no way to get the install to bypass this, and it must be forced closed, and I'm worried that it may have not installed the update properly.

---

### Post by plyte on 2009-03-13
RESOLVED

The "Details" terminal can accept user input and allowed me to type the password to start the server. Glad that this is not an issue.

---

