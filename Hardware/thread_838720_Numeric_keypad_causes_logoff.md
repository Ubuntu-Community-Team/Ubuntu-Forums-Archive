---
title: "Numeric keypad causes logoff"
date: 2008-06-23
forum: Hardware
---

### Post by swguy on 2008-06-23
I have been running 8.04 on a Uniwell notebook (upgraded from 7.10) since April 24 and everything was working normally until a few days ago.

Now keys 1-9 on the numeric keypad cause automatic logoff on both the notebook keyboard and the external keyboard.

It is not a hardware issue as the numeric keypad works perfectly on the login screen.  Cold boot does not resolve the issue.

What do I need to check?

---

### Post by swguy on 2008-06-23
I found the answer to this one on Launchpad:

Some people have this problem on 8.04.  Here's the fix:

Go to System/Preferences/Keyboard/Mouse Keys. Uncheck "Allow to control the pointer using the keyboard"

:)

---

### Post by instinctive on 2008-07-21
OMG Thank you very much. This solution worked straight away. That was such an annoying bug.

---

