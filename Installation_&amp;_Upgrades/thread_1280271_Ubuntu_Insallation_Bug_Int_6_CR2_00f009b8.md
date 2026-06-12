---
title: "Ubuntu Insallation Bug Int 6: CR2 00f009b8"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by archish on 2009-10-01
I am using ASUS K40IN Notebook with Intel Core 2 Duo T6670 processor. This notebook is based on Nvidia MCP75 Chipset. Current BIOS version/Latest Version: 213
When I try to install Ubuntu 9.04 32bit or use try Ubuntu without installing I get the following Error
 Bug Int 6: CR2 00f009b8
 The same issues are reported in other places as well:
[http://vip.asus.com/forum/view.aspx?board_id=3&model=K40IN&id=20090718171113562&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=K40IN&id=20090718171113562&page=1&SLanguage=en-us)
[http://translate.googleusercontent.com/translate_c?hl=en&sl=ru&u=http://forum.ubuntu.ru/index.php%3FPHPSESSID%3D85151119ce9bba4818443e948a496d3d%26topic%3D59881.0&prev=/search%3Fq%3Dubuntu%2BBUG:%2BInt%2B6:%2B00f009aa%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DKyO%26newwindow%3D1&rurl=translate.google.com&usg=ALkJrhggo-aeC9HtSNxVKgmz1yG2O8jLtg](http://translate.googleusercontent.com/translate_c?hl=en&sl=ru&u=http://forum.ubuntu.ru/index.php%3FPHPSESSID%3D85151119ce9bba4818443e948a496d3d%26topic%3D59881.0&prev=/search%3Fq%3Dubuntu%2BBUG:%2BInt%2B6:%2B00f009aa%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DKyO%26newwindow%3D1&rurl=translate.google.com&usg=ALkJrhggo-aeC9HtSNxVKgmz1yG2O8jLtg)
 Whome should I report this bug??
Its quite annoying as I am unable to install Ubuntu at all. Any fix for this issue?
 Thanks.

---

### Post by BraedenNaylor on 2009-10-01
Here is how to file a bug report, otherwise can you post your log files.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by rreese6 on 2009-10-01
Is this a 64-bit system?

---

### Post by archish on 2009-10-02
> **rreese6 said:**
> Is this a 64-bit system?

Well its Core 2 Duo T6670 and supports AMD64 bit extensions also. But I am trying to install the 32 bit version only.

---

### Post by rreese6 on 2009-10-04
Try to install the 64 bit version and see what error you get.
Post it here please.

---

### Post by archish on 2009-10-08
> **rreese6 said:**
> Try to install the 64 bit version and see what error you get.
Post it here please.

No issues with 64 bit kernel and also works fine with 9.10 beta 32 bit. I suppose the bug is there only in 2.6.28 series kernel.

---

### Post by rreese6 on 2009-10-09
it appears to be a bug like you said.

---

