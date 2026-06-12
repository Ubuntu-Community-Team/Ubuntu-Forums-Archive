---
title: "JAVA upgrade to 6 15 fails, why?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by stpike on 2009-08-18
I am attempting to upgrade JAVA from 6.14 to 6.15 on Ubuntu 8.04LTS.  I have downloaded and installed it into /usr/local/jre1.6.0_15 with the expectations that this will be accessible to all users of this system.

I have modified the /usr/lib/firefox-3.0.12/plugins/ directory to include the libjavaplugin_oji.so link and expanded the ffjcext.zip in the extensions directory.  When I restart the Firefox browser and try to verify the installation it still indicates version 6 14.  I have also modified my .bashrc by adding the following last lines:

#JAVA Runtime Environment Variables
export PATH=$PATH:/usr/local/jre1.6.0_15/bin
export JDK_HOME=/usr/local/jre1.6.0_15

Do I need the JDK_HOME variable?

Where have I gone wrong?

Thanks for any help.

---

### Post by bostonaholic on 2009-08-18
> **stpike said:**
> I am attempting to upgrade JAVA from 6.14 to 6.15 on Ubuntu 8.04LTS.  I have downloaded and installed it into /usr/local/jre1.6.0_15 with the expectations that this will be accessible to all users of this system.

I have modified the /usr/lib/firefox-3.0.12/plugins/ directory to include the libjavaplugin_oji.so link and expanded the ffjcext.zip in the extensions directory.  When I restart the Firefox browser and try to verify the installation it still indicates version 6 14.  I have also modified my .bashrc by adding the following last lines:

#JAVA Runtime Environment Variables
export PATH=$PATH:/usr/local/jre1.6.0_15/bin
export JDK_HOME=/usr/local/jre1.6.0_15

Do I need the JDK_HOME variable?

Where have I gone wrong?

Thanks for any help.

try
```
#JAVA Runtime Environment Variables
export JAVA_HOME=/usr/local/jre1.6.0_15
export PATH=$JAVA_HOME/bin:$PATH
```

Most apps that I know of will check for JAVA_HOME.  Also, you'll want to put the JAVA_HOME/bin in the beginning of PATH when exporting.  Whenever you use java/javac or anything similar, it searches for the first instance of a jdk with PATH, so adding it to the front of PATH will ensure it's the first in the list.

Hope that helps.

---

