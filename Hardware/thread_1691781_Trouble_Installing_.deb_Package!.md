---
title: "Trouble Installing .deb Package!"
date: 2011-02-20
forum: Hardware
---

### Post by dave2001 on 2011-02-20
I have recently moved to 10.04 since support for 8.04 is ending soon. I am attempting to install a very necessary debian package, but it returns an error message and fails.



Here is the portion of terminal output from gdebi. tpfan is what i'm attempting to install.

```
Setting up tpfand (0.95-ubuntu2)...
Reloading thinkpad_acpi module...
FATAL; Module thinkpad_acpi is in use.
dpkg: error processing tpfan (--install):
  subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db...
Processing triggers for ureadahead...
Errors were encountered while processing:
  tpfand

```It seems to me that the problem is the thinkpad_acpi module is not able to be reloaded, and thus dpkg can't configure tpfan correctly.

Any suggestions for getting this .deb to install correctly?

The .deb is for fan control on a thinkpad, and it's the only thing that  worked for me on 8.04. (I've tried using "thinkfan" from the  10.04 ubuntu repository- no good). If anyone has any other suggestions for a fan control application or script that works on thinkpads, I'd love to hear that too.

---

