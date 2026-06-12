---
title: "Install Cannon LBP 2900"
date: 2011-02-06
forum: Hardware
---

### Post by ranjix on 2011-02-06
Need help installing Cannon LBP 2900. I downloaded [source]("http://software.canon-europe.com/software/0028622.asp?model=")  as instructions in [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
While running code, I get error:

```
sudo dpkg -i cndrvcups-common_1.60-1_i386.deb cndrvcups-capt_1.60-1_i386.deb
(Reading database ... 157584 files and directories currently installed.)
Preparing to replace cndrvcups-common 1.60-1 (using cndrvcups-common_1.60-1_i386.deb) ...
Unpacking replacement cndrvcups-common ...
Preparing to replace cndrvcups-capt 1.60-1 (using cndrvcups-capt_1.60-1_i386.deb) ...
Unpacking replacement cndrvcups-capt ...
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on cupsys; however:
  Package cupsys is not installed.
 cndrvcups-common depends on libcupsys2 (>= 1.1.23); however:
  Package libcupsys2 is not installed.
dpkg: error processing cndrvcups-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cndrvcups-capt:
 cndrvcups-capt depends on cndrvcups-common (>= 1.60); however:
  Package cndrvcups-common is not configured yet.
dpkg: error processing cndrvcups-capt (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 cndrvcups-common
 cndrvcups-capt

```

---

