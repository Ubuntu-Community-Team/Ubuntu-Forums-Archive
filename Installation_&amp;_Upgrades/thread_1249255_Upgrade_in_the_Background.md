---
title: "Upgrade in the Background"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by mikeblah on 2009-08-25
Hi everyone

I am new to Ubuntu, and loving it. 

I would like to get a friend started on Ubuntu (9.04) but need to configure it to be simpler to use. I have set software sources to 'Important security updates only' and 'install security updates without confirmation' on a test machine. My problem is the Update Manager still appears asking to install, which is what I don't want. That is with an admin account. With a normal account Update Manager doesn't appear but I'm not sure if the updates are installed.

Any suggestions?

Thanks

---

### Post by ad_267 on 2009-08-25
You can prevent the update manager from opening by pressing Alt+F2 and running "gconf-editor" then going to apps - update-notifier and disabling "auto_launch".

Hopefully the "install in the backround" feature will work then too. This seems like a bug to me so I'm reporting it on launchpad as I've experienced the same behaviour.

---

### Post by mikeblah on 2009-08-25
Thanks, I'll give that a try.

---

