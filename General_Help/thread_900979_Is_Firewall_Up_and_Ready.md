---
title: "Is Firewall Up and Ready"
date: 2008-08-25
forum: General Help
---

### Post by Storm Rider on 2008-08-25
I'd like to take another look at Ubuntu.  Can you tell me if the firewall is installed and configured as part of the initial install.

One of the reason I've stuck with SuSE and Fedora is that the firewall is up and running when the installation is finished.

:)

---

### Post by overdrank on 2008-08-25
> **Storm Rider said:**
> I'd like to take another look at Ubuntu.  Can you tell me if the firewall is installed and configured as part of the initial install.

One of the reason I've stuck with SuSE and Fedora is that the firewall is up and running when the installation is finished.

:)

Hi and this link may help
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by mssever on 2008-08-25
ufw is installed by default, but there's no firewall configured by default. There's no need, since no ports are open by default. Thus, a firewall would be pointless.

---

### Post by tuxxy on 2008-08-25
> **Storm Rider said:**
> I'd like to take another look at Ubuntu.  Can you tell me if the firewall is installed and configured as part of the initial install.

One of the reason I've stuck with SuSE and Fedora is that the firewall is up and running when the installation is finished.

:)

You may need to enable the firewall, open a terminal and type **ufw** for the commands

---

### Post by Storm Rider on 2008-08-26
Thanks very much for the quick replies.  I'll be flashing up Ubuntu 8.04 in the next few minutes.  Will post back sometime tomorrow.

---

### Post by Camilia on 2008-08-27
Alas something that was simple and easy to do!

---

### Post by Storm Rider on 2009-01-04
Here we are a few months later.  My system seems to be working well....never satisfied though lol.

How can I check to make sure my system is secure?  I have a router as well and many will say that's enough but I'm not betting my banking info on it.  

Are there any system security diagnostic checks that I can run?

Thanks:)

---

### Post by mssever on 2009-01-05
> **Storm Rider said:**
> Are there any system security diagnostic checks that I can run?
"System security" is a HUGE topic. The best thing is to be smart with what you do with your computer, and install all security updates that come out. Remember, systems are only as secure as their weakest link, and on Linux the weakest link is usually the user. Read up on how to secure Linux systems (Google knows a bit about this).

Without knowing what type of security diagnostics you're looking for, it's hard to make specific recommendations. tiger and chkrootkit are good for checking for ways that root can be compromised, but they by no means cover every way a system can be compromised (indeed, it's impossible to write such software).

EDIT: By the way, in case you're soncerned about someone remotely breaking into your machine over the network, that's pretty much possible in a default install. If you installed some server that listens on a remotely-accessible interface, either use your router's NAT to deny external access or read up on how to secure that particular software. People can't access your computer through closed ports, no matter what they try. Of course, there are potential ways to get you to install malware on your machine what opens up a back door, but good security practices as mentioned above will minimize that risk.

---

