---
title: "problems installing MFC-210C printer..."
date: 2005-11-21
forum: General Help
---

### Post by bitrateforty on 2005-11-21
well i accidentally deleted my windows operating system and so have no fallback, now i have a MFC-210C brother printer, but when i downloaded the .deb file from brother and tried to run it, it says that there are no lpr files in the spool directory, is there a way to ratify this, because i desperatly need my printer.

---

### Post by mihakriket on 2005-11-23
bitrateforty,

    I have the same printer, I have no problems printing. You have to download 2 files from Brother's web site.

mfc210clpr-1.0.0-1.i386.deb
cupswrappermfc210c_1.0.0-1_i386.deb

After you downlaod the 2 files, you need to install 'csh'.

After installing 'csh' then :

Install the LPR driver.

(i.e) 
For Debian Users: 
dpkg -i --force-all mfc210clpr-1.0.0-1.i386.deb


Install the cupswrapper driver.

(i.e)
For Debian Users: 
dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb


Open your browser and enter: "http://localhost:631", with out quotes.

Click on the 'printers' button, the MFC210 printer will show up.

You should be good to go.

Harry

---

