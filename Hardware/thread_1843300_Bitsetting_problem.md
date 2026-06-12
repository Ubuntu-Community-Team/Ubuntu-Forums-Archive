---
title: "Bitsetting problem"
date: 2011-09-13
forum: Hardware
---

### Post by Blasphemous on 2011-09-13
Following this guide ([http://nessunohastonick.altervista.org/2010/09/16/impostare-il-bitsetting-del-proprio-masterizzatore-dvd-windows-e-linux/](http://nessunohastonick.altervista.org/2010/09/16/impostare-il-bitsetting-del-proprio-masterizzatore-dvd-windows-e-linux/)) I was able to find a command to run in order to** set my burner booktype to DVD-ROM. **(need it to burn xbox backup...)
It says:
> dvd+rw-booktype -dvd-rom -unit+r /dev/hdcSo, according to disk-utility, the burner device is **/dev/sr0**, but when I try to run
> sudo dvd+rw-booktype -dvd-rom -unit+r /dev/sr0this is what I get
> :-[ LG_FCh failed with SK=5h/INVALID FIELD IN PARAMETER LIST]: Input/output errorNow, the burder **does support that book-type** 'couse on Windows I was able to burn this kind of backup.

I know there's plenty of discussions about this, but searching the internet I could not find anu guide or anything else related to my issue.

Any idea?

---

