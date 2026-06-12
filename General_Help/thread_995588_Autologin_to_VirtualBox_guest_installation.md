---
title: "Autologin to VirtualBox guest installation?"
date: 2008-11-28
forum: General Help
---

### Post by jw29 on 2008-11-28
Hello,

I manage a lab at a university and we've been dualbooting Windows and Ubuntu for years.  Every course (primarily comp. sci. and math, along with some engineering) that uses the lab uses Linux, with the exception of one course or so per semester from a computer-illiterate area outside of our department like business, education, psychology, etc., which uses Windows.

During the winter break, we're going to be switching from the dualboot setup to running Ubuntu 8.04 with Virtualbox installed to run Windows XP for that one class.

To avoid as much confusion as possible, this is basically what I want to do: Create a user, say, 'winxp', so that when somebody logs in with that account, Virtualbox automatically starts up and loads the Windows XP guest installation.

Right now, the classes outside our department are confused just rebooting the machines to get back into Windows, so I want to keep it as simple as possible.  And ideally, with the setup I posted in the previous paragraph, it would be to tell the instructor: "Have the students type this username and password on the orangy-brown screen and wait for the Windows desktop to load".

Any ideas?

Thank you!

---

### Post by Peter09 on 2008-11-28
You can run a virtual box machine from the command line. So you would just need to put that command into your session information.

You can get the manual, which describes the command line interface here

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

