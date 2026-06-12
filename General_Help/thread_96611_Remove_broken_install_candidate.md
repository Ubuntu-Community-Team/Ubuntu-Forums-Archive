---
title: "Remove broken install candidate"
date: 2005-11-29
forum: General Help
---

### Post by ember on 2005-11-29
Hi,

I tried to install a package from Dapper on my breezy system today and (as expected) the dependencies were not met. Unfortunately after remove this package and downgrading to the old one, the install candidate with the unmet dependencies is still available.
Any idea how I can get rid of it?

Best,
ember

---

### Post by Xian on 2005-11-29
Can you give an ouput of the error message?

---

### Post by ember on 2005-11-29
Sure:

apg-get install gphpedit gives:

Die folgenden Pakete haben nichterf&#252;llte Abh&#228;ngigkeiten:
  gphpedit: H&#228;ngt ab: libbonobo2-0 (>= 2.13.0) aber 2.10.1-0ubuntu1 soll installiert werden
            H&#228;ngt ab: libgcc1 (>= 1:4.0.2) aber 1:4.0.1-4ubuntu9 soll installiert werden
            H&#228;ngt ab: libgnomevfs2-0 (>= 2.13.1) aber 2.12.1-0ubuntu2 soll installiert werden
            H&#228;ngt ab: libgtkhtml2-0 (>= 2.11.0) aber 2.6.3-1 soll installiert werden
            H&#228;ngt ab: libstdc++6 (>= 4.0.2-3) aber 4.0.1-4ubuntu9 soll installiert werden
            H&#228;ngt ab: libxml2 (>= 2.6.22) aber 2.6.21-0ubuntu1 soll installiert werden
E: Kaputte Pakete


and apt-cache showpkg gphpedit:

Reverse Depends:
Dependencies:
0.9.80-1ubuntu1 - libart-2.0-2 (2 2.3.16) libatk1.0-0 (2 1.9.0) libbonobo2-0 (2 2.13.0) libbonoboui2-0 (2 2.5.4) libc6 (2 2.3.4-1) libcairo2 (2 1.0.2) libfontconfig1 (2 2.3.0) libgcc1 (2 1:4.0.2) libgconf2-4 (2 2.9) libglib2.0-0 (2 2.8.0) libgnome-keyring0 (2 0.4.3) libgnome2-0 (2 2.8.0) libgnomecanvas2-0 (2 2.11.1) libgnomeui-0 (2 2.8.0) libgnomevfs2-0 (2 2.13.1) libgtk2.0-0 (2 2.8.0) libgtkhtml2-0 (2 2.11.0) libice6 (0 (null)) liborbit2 (2 1:2.10.0) libpango1.0-0 (2 1.10.1) libpng12-0 (2 1.2.8rel) libpopt0 (2 1.7) libsm6 (0 (null)) libstdc++6 (2 4.0.2-3) libx11-6 (0 (null)) libxau6 (0 (null)) libxcursor1 (4 1.1.2) libxext6 (0 (null)) libxfixes3 (0 (null)) libxi6 (0 (null)) libxinerama1 (0 (null)) libxml2 (2 2.6.22) libxrandr2 (0 (null)) libxrender1 (0 (null)) zlib1g (2 1:1.2.1) phpdoc (0 (null))
0.9.80-1ubuntu1 - libart-2.0-2 (2 2.3.16) libatk1.0-0 (2 1.9.0) libbonobo2-0 (2 2.8.0) libbonoboui2-0 (2 2.5.4) libc6 (2 2.3.4-1) libcairo2 (2 1.0.2) libfontconfig1 (2 2.3.0) libgcc1 (2 1:4.0.1) libgconf2-4 (2 2.9) libglib2.0-0 (2 2.8.0) libgnome-keyring0 (2 0.4.3) libgnome2-0 (2 2.8.0) libgnomecanvas2-0 (2 2.11.1) libgnomeui-0 (2 2.8.0) libgnomevfs2-0 (2 2.11.3) libgtk2.0-0 (2 2.8.0) libgtkhtml2-0 (2 2.6.3) libice6 (0 (null)) liborbit2 (2 1:2.10.0) libpango1.0-0 (2 1.10.1) libpng12-0 (2 1.2.8rel) libpopt0 (2 1.7) libsm6 (0 (null)) libstdc++6 (2 4.0.1) libx11-6 (0 (null)) libxcursor1 (4 1.1.2) libxext6 (0 (null)) libxfixes3 (0 (null)) libxi6 (0 (null)) libxinerama1 (0 (null)) libxml2 (2 2.6.20) libxrandr2 (0 (null)) libxrender1 (0 (null)) zlib1g (2 1:1.2.1) phpdoc (0 (null))
0.9.50-2build1 - libart-2.0-2 (2 2.3.16) libatk1.0-0 (2 1.9.0) libaudiofile0 (2 0.2.3-4) libbonobo2-0 (2 2.8.0) libbonoboui2-0 (2 2.5.4) libc6 (2 2.3.4-1) libesd0 (18 0.2.29-1) libesd-alsa0 (2 0.2.29-1) libgail-common (2 1.6.6) libgail17 (2 1.6.6) libgcc1 (2 1:4.0.0-7) libgconf2-4 (2 2.9) libgcrypt11 (0 (null)) libglib2.0-0 (2 2.7.0) libgnome-keyring0 (2 0.4.0) libgnome2-0 (2 2.8.0) libgnomecanvas2-0 (2 2.11.1) libgnomeui-0 (2 2.8.0) libgnomevfs2-0 (2 2.10.0-0) libgnutls11 (2 1.0.16) libgpg-error0 (2 1.0) libgtk2.0-0 (2 2.6.0) libgtkhtml2-0 (2 2.6.3) libice6 (0 (null)) libjpeg62 (0 (null)) liborbit2 (2 1:2.10.0) libpango1.0-0 (2 1.8.1) libpopt0 (2 1.7) libsm6 (0 (null)) libstdc++6 (2 4.0.0-9) libtasn1-2 (2 0.2.8) libx11-6 (0 (null)) libxml2 (2 2.6.17) zlib1g (2 1:1.2.1) phpdoc (0 (null))
Provides:
0.9.80-1ubuntu1 -
0.9.80-1ubuntu1 -
0.9.50-2build1 -

On is the package is download from packages.ubuntu.com (i.e. dapper) and installed via dpkg, the other one is a successful backport which I am running now, the third one is the package from breezy.

So now my question is, how can I remove the option to install the gphpedit that does not work?

Best,
ember

---

