---
title: "Upgrade to OpenOffice.org 3.0"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by sanemanmad on 2009-04-05
This should almost be copy and paste, literally. (Assuming OpenOffice is downloaded to /tmp)

Before the installation, download the newest package from [OpenOffice.org:]("http://download.openoffice.org/other.html#en-US")
```
	 
sudo aptitude remove openoffice.org-base-core openoffice.org-common &#8211;-purge openOffice.org-base-core openoffice.org-common
tar -xvzf /tmp/OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
cd OOO300_m15_native_packed-1_en-US.9379/DEBS/
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb

```

Now logout and login. 
There should be icons under Menu > Office > * 
Open one of the newly installed office programs and follow these next steps to make this fully compatible with MS.

Tools > Options > Load/Save > change the settings to look similar to the screenshots below:

After these changes have been applies, go ahead click &#8220;OK&#8221; and close and open OpenOffice.org windows. 
You should now be able to load an .xls or .doc at anytime and all future documents will saved in MS format.


If this worked correctly... You can safely remove the folder you extracted in your ~ directory and the tar file.

---

### Post by fuwkej on 2009-05-09
Thanks, had to change the numbers/directories around with new version, but worked great after that.

---

