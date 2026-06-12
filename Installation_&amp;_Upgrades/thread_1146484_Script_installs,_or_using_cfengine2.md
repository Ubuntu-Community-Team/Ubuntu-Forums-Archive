---
title: "Script installs, or using cfengine2"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by blingerlive on 2009-05-02
Hi All,

I was trying to script install NIS and ubuntu-restricted-extras

e.g.
#!/bin/sh
apt-get -y install nis

The problem is that the installer requires user input.  For example, for java, it needs the user to agree to the license agreement.  So if you run the above script, it will just "hang" until the user enters an input.

Is there a straight forward way to automate the input?  So it doesn't stall the script installer.

thanks,

---

