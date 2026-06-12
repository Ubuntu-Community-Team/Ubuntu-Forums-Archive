---
title: "Update Manager items Out of Date?"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2009-01-31
Hello

Im using Ubuntu 810 everything seems to be running just fine except when I do a system update.  I not a major issue I guess but it is anoying, What I get is this:  


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

******** 
Before I make things worse and do the wrong thing I though I would ask you all.

If you need more information I would be happy to supply it.

Thank you.

---

### Post by taurus on 2009-01-31
I see that you are running intrepid but how come you have a hardy repo (wine)?  Shouldn't you be using the intrepid as well?

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by kostkon on 2009-01-31
And, check [this helpful script]("http://ubuntuforums.org/showpost.php?p=6638010&postcount=42") from [this thread]("http://ubuntuforums.org/showthread.php?t=1047743"). It will install all the PPA keys for you automatically.

---

### Post by sandman3838 on 2009-01-31
Hey thanks for the help!
Its getting better.

After setting up the CORRECT "Wine" source line and running the "Scott Ritchie script file" I was down to just three issues instead of the five.

Next I unchecked all of the third party options and one at a time I activated them.

OH!  If it helps I have added a screen shot as how things atand at the moment.

What I found was this:

1.
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)
THIS ISSUE IS FROM OPEN OFFICE:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF


2.
[http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu)
THIS ISSUE IS FROM FIREFOX:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6


3.
[http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu)
THIS ISSUE IS FROM SCREENLETS:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513


Any suggestions?  I have to ask... but could I just leave them as they are now unchecked?

---

### Post by taurus on 2009-01-31
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by sandman3838 on 2009-02-01
SOLVED - Firefox does its own updated.
Office Archive is down do to update issues.
Seceenlets - I don't care!  :)

---

