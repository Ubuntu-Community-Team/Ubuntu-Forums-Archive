---
title: "KUbuntu 6.10, ECIADLS and Atlantisland I-Storm"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by elegos on 2007-02-15
Hi there!

I've just succeded convincing my brother to install KUbuntu on his machine... I've got a flat-ethernet connection, while he has a USB ADSL...

Here start the problems:

He cannot install his Atlantisland I-Storm...

Procedures:
1. Downloaded pppoe package
2. Downloaded eciadsl-usermode_0.11-1_i386.deb

installed pppoe
installed eciadsl

launched eciadsl-config-text

He can insert username, but there is a strange error: there are some unexpected operators... so I decided to test myself... and this is what I have:
```

Password:
[: 26: ==: unexpected operator
[: 36: 0: unexpected operator
-e
===== Welcome to the EciAdsl Linux driver configuration =====

-e At any time, press Ctrl+C to quit this script without saving modifications.

-e Tip: you can run eciadsl-config-text with a .bin file as parameter to change
your .bin quickly.

[: 26: ==: unexpected operator
[: 36: 0: unexpected operator
-e Your choice:

1) Configure all settings
2) Remove dabusb module
3) Change synch .bin file
-en
Enter your choice (1-3, default is 1):
1
-e
===> EciAdsl driver setup <===

Type in your user name (given by your provider): test

Type in your password (given by your provider):
[: 905: ==: unexpected operator
Type in your password again (for verification):
[: 905: ==: unexpected operator
-e ** passwords don't match, try again

Type in your password (given by your provider):    
```

What's wrong with this package? Maybe corrupted version?

What must he do? He cannot continuing passing through windows-linux-windows-linux... :S

Please help us :(

Notice that he can download single packages from Windows...

---

