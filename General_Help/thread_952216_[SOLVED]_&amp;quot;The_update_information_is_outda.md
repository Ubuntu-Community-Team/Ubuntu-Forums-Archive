---
title: "[SOLVED] &amp;quot;The update information is outdated&amp;quot;"
date: 2008-10-18
forum: General Help
---

### Post by Timmeh02 on 2008-10-18
Hello, 

Is there anything I can do about getting a repeated message (orange triangle with exclamation mark) which appears in the top toolbar telling me to manually check for updates.  I have attached a screenshot with the update manager error message.  Thanks.

---

### Post by drs305 on 2008-10-18
Added: It could be the server is just offline. You may wish to re-enable the repository at a later time to see if it is online.

You can open your sources.list via Synaptic (Settings, Repositories) or System, Administration, Software Sources and disable this repository. Go to the "Third Party Updates" tab, find the referenced repository and untick it. Then hit the Reload button or run "sudo apt-get update" to refresh the listing.

---

### Post by Timmeh02 on 2008-10-18
Thanks drs05, I have done that.  Appreciate you help.

---

