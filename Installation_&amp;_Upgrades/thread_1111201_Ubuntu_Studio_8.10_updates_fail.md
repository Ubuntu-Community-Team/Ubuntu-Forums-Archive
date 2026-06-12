---
title: "Ubuntu Studio 8.10 updates fail"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by techemically on 2009-03-30
update icon pops up to prompt me for update but when window comes up nothing happens. I click "check" then enter my password and it cycles through like it is getting updates but gives me the following error: W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Therion on 2009-03-30
Try using a different server (use the "Settings" button on the Update Manager dialog box).

---

### Post by techemically on 2009-03-30
there are no buttons other than "check", "install updates" and "description of update"

---

### Post by Therion on 2009-03-30
> **techemically said:**
> there are no buttons other than "check", "install updates" and "description of update"
Ugh...  Go to Software Sources/Ubuntu Software and change the server location in the "Download From" dropdown menu.  I'm behind a WinXP machine at work and have been going by memory.  Sorry for the confusion.

See this?  This should help...  [http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-UbuntuSoftware.png](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/SoftwareSources-UbuntuSoftware.png)

---

### Post by techemically on 2009-03-30
Responds with: 
W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

tried many different servers and ran the test to choose best server. all fail with the same error

---

