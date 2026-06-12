---
title: "Get root privilege in X-window environnement"
date: 2008-09-15
forum: General Help
---

### Post by DavidB123 on 2008-09-15
How do I get root privilege in X-window environment?

For example, I would like to be able to create a folder in a root folder using the file browser.

I know I can use "sudo ..." to get temporary privilege or "sudo su" to get permanent privilege but the privilege are limited to the terminal. It doen't granted privilege for the X-Window.

Any help would be appreciated.

---

### Post by snowpine on 2008-09-15
Hi David, 'gksu nautilus' will give you a graphical file browser with root privilages. Be careful! :)

---

### Post by DavidB123 on 2008-09-15
Thank you snowpine. It works.

---

### Post by snowpine on 2008-09-15
gksu is the graphical alternative to sudo; for example 'gksu synaptic' vs 'sudo apt-get'.

---

