---
title: "problem with evolution mail"
date: 2008-10-14
forum: General Help
---

### Post by jsally on 2008-10-14
When I click on a link in an email in evolution mail nothing happens.
How do I fix this?

---

### Post by AreEK on 2008-10-14
What's the value for http and https under /desktop/gnome/url-handlers when viewed with gconf-editor?
This command will set firefox as url-handler for https:
su - ume -c "gconftool-2 -s -t string /desktop/gnome/url-handlers/https/command 'firefox %s'".

Links to anchors inside the html-mail should of course not open in an external browser..

---

