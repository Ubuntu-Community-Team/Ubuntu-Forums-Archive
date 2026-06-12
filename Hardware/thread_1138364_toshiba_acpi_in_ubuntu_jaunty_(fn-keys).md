---
title: "toshiba_acpi in ubuntu jaunty? (fn-keys)"
date: 2009-04-26
forum: Hardware
---

### Post by Anfanglir on 2009-04-26
Hi
i need advice on how to enable fn-keys in Jaunty. It worked in Hardy, was broken in Intrepid and is still broken in Jaunty. 

According to this bug-report:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/261318](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/261318)
it is related to toshiba_acpi being replaced by tlsup in Intrepid and Jaunty. One post on that page (by Andy Whitcroft on 2009-01-05) has a link to patches that are supposed to fix this in Jaunty:
[http://people.ubuntu.com/~apw/lp269831-jaunty/](http://people.ubuntu.com/~apw/lp269831-jaunty/)

But I don't know how to apply the patches. Could anyone give some hints how to proceed?

thanx / Anfanglir

EDIT: btw, I have a Toshiba Libretto U100. END EDIT

---

### Post by Anfanglir on 2009-04-27
Got a reply from Andy Whitcroft:

[I]"Those patches are the patches I used to build the kernels which used
to be in the same directory. They have now expired. According to the bug
the fixes that they contained are already released in both Intrepid and
Jaunty kernels. If you are running those releases and are up to date
your should already have the fixes and those kernels would be of no use
to you. If you are seeing an issue it is likely a new one and needing a
new bug filed."[/I]


:\ Anfangflir

---

