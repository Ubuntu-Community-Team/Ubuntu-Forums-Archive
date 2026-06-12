---
title: "[Solved] Openoffice.org 2.4.1 and Java Extensions"
date: 2008-08-07
forum: General Help
---

### Post by botmind on 2008-08-07
Hopefully others can profit from my labor in figuring this out.  I tried to install an extension in OO.O 2.4.1 (Thessalonica) and got the following error:

Could not create Java implementation loader 

To fix this:

1. open System >> Administration >> Synaptic

2. search "openoffice"

3. install the "openoffice.org" package and its dependencies.  This installs the Java JRE for OO.O that makes Java extensions work.

4. install your extension.

It worked for me, but your mileage may vary.

NB: it might be a good idea to clear your OO.O settings before trying this:

At the terminal:

>> mv ~/.openoffice.org2/user ~/.openoffice.org2/user_old

---

