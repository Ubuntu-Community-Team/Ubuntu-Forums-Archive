---
title: "problem installing kde 4.2"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Tiftof on 2009-02-12
Hi,

I'm using ubuntu and I want to try out kde 4.2. I've added the kubuntu experimental repository and tried installing kubuntu-desktop but it gives me errors:

```
The following packages have unmet dependencies:
  kdeplasma-addons: Depends: libplasma2 but it is not installable
  kdebase-workspace-bin: Depends: libplasma2 but it is not installable
                         Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but it is not installable
  ksysguard: Depends: libplasma2 but it is not installable
  kdeplasma-addons-libs4: Depends: libplasma2 but it is not installable
  plasmoid-quickaccess: Depends: kdebase-runtime (>= 4:4.1.96) but 4:4.1.3-0ubuntu1~intrepid1 is installed.
                        Depends: kdelibs5 (>= 4:4.1.96) but 4:4.1.3-0ubuntu1~intrepid4 is installed.
  kdebase-workspace-libs4+5: Depends: libplasma2 but it is not installable
  libplasma3: Depends: kdelibs5 (>= 4:4.1.96) but 4:4.1.3-0ubuntu1~intrepid4 is installed.
              Depends: kdelibs5-data (= 4:4.2.0-0ubuntu2~intrepid1~ppa1) but 4:4.1.3-0ubuntu1~intrepid4 is installed.
  kdebluetooth: Depends: kdebase-runtime (>= 4:4.1.96) but 4:4.1.3-0ubuntu1~intrepid1 is installed.
                Depends: kdelibs5 (>= 4:4.1.96) but 4:4.1.3-0ubuntu1~intrepid4 is installed.
  kate: Depends: libplasma2 but it is not installable
  kdebase-plasma: Depends: libplasma2 but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
kdebase-workspace-data [4:4.1.3-0ubuntu1~intrepid1 (intrepid-updates,
intrepid-backports, now)]
kdebluetooth [1:0.2-0ubuntu2 (intrepid)]
libplasma2 [4:4.1.3-0ubuntu1~intrepid1 (intrepid-updates, intrepid-backports,
now)]
plasmoid-quickaccess [0.7.1-0ubuntu1 (intrepid)]

Keep the following packages at their current version:
libplasma3 [Not Installed]

Score is 101

Accept this solution? [Y/n/q/?] 
```

Some kde packages are already on my system because I have Kile installed. But when removing Kile, I'm getting the same problem while trying to install kubuntu-desktop...

Any ideas?

---

