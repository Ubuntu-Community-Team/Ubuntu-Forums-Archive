---
title: "Ati driver crashes system before login-screen"
date: 2008-07-08
forum: Hardware
---

### Post by Sigiken on 2008-07-08
Hi,
I just installed ubuntu 8.04
I installed the updates (everything went fine)
then a message popt up telling me that I have restricted drivers available for my ati x1950 PRO card, I clicked on enable, reboot... ubuntu freezes at the login-screen.

Next I've done a reinstall of ubuntu, and used envyNG to install the atiDriver, and again it freezes before login-screen.
Does anyone have a solution for this?

Jonas

---

### Post by phidia on 2008-07-08
You can try [this]("http://www.phoronix.com/scan.php?page=article&item=843&num=1") and/or [this]("http://ubuntuforums.org/showthread.php?t=771017&highlight=ati+x1950+PRO"). The 2nd link calls out your card specifically.
Hope that's useful.

---

### Post by Sigiken on 2008-07-09
> **phidia said:**
> You can try [this]("http://www.phoronix.com/scan.php?page=article&item=843&num=1") and/or [this]("http://ubuntuforums.org/showthread.php?t=771017&highlight=ati+x1950+PRO"). The 2nd link calls out your card specifically.
Hope that's useful.

Hi i'm stuck at this:

> nstall .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb

Additional 64-bit instructions

If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package:

sudo apt-get install -f

Catalyst 8.3 on 64-bit systems requires the --force-overwrite command in the above dpkg command:

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb


It gives me errors at three files, I've done this but i think im wrong here:

sudo dpkg -i [COLOR="Red"]sudo apt-get install -f[/COLOR] xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb

---

