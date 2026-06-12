---
title: "Installing"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by xoxkamatayanxox on 2009-01-12
Hi everyone!
I am new to linux and I am having a problem with installing anything in Synaptic Package Manager. Every time I tried to install a program it never completes and give me an error message.

The error message is:

E: libghc6-highlighting-kate-dev: subprocess post-installation script returned error exit status 1
E: libghc6-highlighting-kate-prof: dependency problems - leaving unconfigured

Thanks for you help!

---

### Post by shafi on 2009-01-12
> **xoxkamatayanxox said:**
> Hi everyone!
I am new to linux and I am having a problem with installing anything in Synaptic Package Manager. Every time I tried to install a program it never completes and give me an error message.

The error message is:

E: libghc6-highlighting-kate-dev: subprocess post-installation script returned error exit status 1
E: libghc6-highlighting-kate-prof: dependency problems - leaving unconfigured

Thanks for you help!

Did you check marked the tab under software sources?
if no follow:
System -> Administration -> Software Sources , then click on the ubuntu software and tick the check boxes and click Revert.
and then type the following command in a terminal:
[HTML]
sudo apt-get update
[/HTML]
after that you should be able to install.

---

### Post by xoxkamatayanxox on 2009-01-12
Sorry its not working. I tried updating and its giving me the same error.

---

### Post by oldos2er on 2009-01-12
Tru 'sudo dpkg --configure -a'

---

