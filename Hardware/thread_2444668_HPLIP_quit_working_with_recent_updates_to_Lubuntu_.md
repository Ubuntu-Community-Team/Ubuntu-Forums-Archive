---
title: "HPLIP quit working with recent updates to Lubuntu 18.04 64-bit"
date: 2020-06-02
forum: Hardware
---

### Post by MoebusNet on 2020-06-02
After recent updates hplip didn't want to recognize my ancient HP officejet printer. I was running the most recent version (3.17.10) in the ubuntu repository (hplip isn't offered in Lubuntu's Software application). To fix this, I purged the old hplip from my system ```
sudo apt-get purge hplip hplip-data hplip-doc hplip-gui hpijs-ppds libsane-hpaio printer-driver-hpcups printer-driver-hpijs

sudo rm -rf /usr/share/hplip/

sudo apt-get autoremove
```

I installed the latest version of hplip as instructed from the developer's website: [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)

HPLIP installed and is working well for me. The new version (3.20.5) fixed my issues with printer recognition and installed the previously-missing taskbar icon.

I suspect the issue with hplip being missing from Lubuntu 18.04's Software application has to do with LXDE being replaced with LXQt and with 18.04 approaching EOL.

---

