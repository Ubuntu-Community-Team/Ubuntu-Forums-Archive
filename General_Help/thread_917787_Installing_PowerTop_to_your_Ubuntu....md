---
title: "Installing PowerTop to your Ubuntu..."
date: 2008-09-12
forum: General Help
---

### Post by ajack on 2008-09-12
Hi all,

I wanted to install PowerTop v1.10 but the Ubuntu repos only had v1.9.  So I downloaded the latest version from linuxpowertop.org site tried compiling it.  Had a bit of problems with it, so after figuring it out, decided to share the script with anyone who is interested.

Just copy the text and paste it into a file called PowerTopInstall.sh, and chmod +x PowerTopInstall.sh the file.  Then a simple ./PowerTopInstall.sh will install PowerTop v1.10 for you.  Hope this helps.

```

#!/bin/bash
cd ~
if [ ! -f powertop-1.10.tar.gz ]
  then
    wget http://www.lesswatts.org/projects/powertop/download/powertop-1.10.tar.gz
fi
sudo apt-get -y install build-essential libncurses5-dev libncursesw5-dev
tar -xvvzf powertop-1.10.tar.gz
cd powertop-1.10
make
sudo make install
cd ~ 

```

Please feel free to comment...

---

### Post by max69 on 2008-12-11
Thanks a lot. Perfect!!!!!

---

### Post by Hilko on 2009-04-19
I think you can also install powerTOP using Synaptic Package manager.

---

### Post by ajack on 2009-04-30
> **Hilko said:**
> I think you can also install powerTOP using Synaptic Package manager.

If you read my post carefully, you'd notice that at the time of posting, the repos had an older version.

---

### Post by yoasif on 2009-04-30
if you replace make install with checkinstall, you can remove the package later if you like.

obviously, you will need to install checkinstall using aptitude.

---

