---
title: "A nice script to run to keep you up-to-date"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by blazemore on 2009-11-09
This script will get any GPG keys you need (If you have the launchpad update script), and install the latest and greatest software. It doesn't do anything that a normal apt-get update, apt-get dist-upgrade would do, it's just easier.

This is for people who like to mess around a lot with PPAs.

```

#!/bin/bash
sudo clear
echo " __________________________"
echo "|     UBUNTU UPDATER       |\\"
echo "|--------------------------|\\"
if [ -f /usr/bin/launchpad-update ]
then
echo "|      Getting keys        |\\"
sudo launchpad-update | grep err
else
echo "|      Can't get keys      |\\"
fi
echo "|  Getting list of changes |\\"
sudo apt-get update | grep err
echo "|     Applying updates     |\\"
sudo apt-get dist-upgrade -y --force-yes | grep err
echo "|           Done!          |\\"
echo "|__________________________|\\"
echo "\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\ "
exit 0

```

---

