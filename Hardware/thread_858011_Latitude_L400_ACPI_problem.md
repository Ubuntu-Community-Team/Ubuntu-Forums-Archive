---
title: "Latitude L400 ACPI problem"
date: 2008-07-13
forum: Hardware
---

### Post by Diskdoc on 2008-07-13
I have a Dell Latitude L400 laptop. There is a problem using it with ACPI enabled. (See following links for discussion)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/75704]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/75704")
[http://www.nabble.com/-Bug-38374--acpid,-REOPENED:-System-auto-suspends-without-"noapic-acpi%3Doff"-into-grub--Dell-Latitude-L400--td17689804.html]("http://www.nabble.com/-Bug-38374--acpid,-REOPENED:-System-auto-suspends-without-"noapic-acpi%3Doff"-into-grub--Dell-Latitude-L400--td17689804.html")

Removing the sleep-function in Ubuntu (by removing or moving the relevant ACPI scripts) solves the problem for me - except for one thing. The screensaver fails to switch on. As the key-event for sleep is repeatedly triggered (this is the problem with the L400) the timer for the screesaver is reset.

Turning off ACPI (acpi=off) boots the system and the screensaver works normally.

My first question is: what important functionality do I lose by turning off ACPI? Sleep and hibernate didn't work properly to begin with but what else? Temperature sensors? Battery?

My second question: Is it possible to block the sleep key event from being registered by the kernel or screensaver?

*later*

Hmm. At least automatic power off seems to require ACPI support :-/

---

