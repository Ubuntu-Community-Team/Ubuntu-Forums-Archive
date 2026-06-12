---
title: "CUPS Filter permission error"
date: 2008-09-19
forum: General Help
---

### Post by sricketts on 2008-09-19
I am getting a printing error that has been addressed in several forums, but the proposed solutions did not work for me.


The printer is a Brother MFC-9840CDW. I followed instructions from here to install the drivers:

[http://www.pyrosoft.co.uk/blog/2008/07/28/installing-the-brother-mfc-9840cdw-on-ubuntu/](http://www.pyrosoft.co.uk/blog/2008/07/28/installing-the-brother-mfc-9840cdw-on-ubuntu/)


The /var/log/cups/error_log gives:

```

E [19/Sep/2008:16:57:03 -0700] Unable to initialize Kerberos context
E [19/Sep/2008:16:57:11 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [19/Sep/2008:16:57:11 -0700] Filter "/usr/local/Brother/Printer/mfc9840cdw/cupswrapper/brlpdwrapper_mfc9840cdw" for printer "MFC9840CDW" not available: Permission denied
E [19/Sep/2008:17:28:10 -0700] Unable to initialize Kerberos context
```


I followed both the workaround and fix suggestions from here, with no success:

[http://islandlinux.org/howto/upgrading-ubuntu-breaks-printer-cupsys](http://islandlinux.org/howto/upgrading-ubuntu-breaks-printer-cupsys)


Any suggestions?

Thanks,
Scott

---

### Post by Cytomax on 2009-02-08
I followed the instructions from the same website and received the same problem with the same MFC-9840CDW from Brother did anyone ever find a fix for this problem?
Please help
Eddie

---

