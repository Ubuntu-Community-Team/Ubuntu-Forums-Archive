---
title: "Upgrading nVidia driver, how?"
date: 2008-11-28
forum: General Help
---

### Post by speedsix on 2008-11-28
I want to upgrade from v173 shipped with Ibex to the newer 177 (in the repos) due to some stability issues I'm trying to troubleshoot. Amd64 system, nVidia 5200 agp.

Just installing the relevant packages and rebooting causes X not to start, is there anything else I need to run after?



Thanks

---

### Post by pedro_orange on 2008-11-28
How did you update your driver?

Did you download the package and manually install it?
Previous versions of Ubuntu had a few nvidia drivers such as: nvidia-glx and nvidia-glx-new, however Ibex only uses nvidia-glx.

You should check you have indeed installed said driver.

I would be tempted to remove it, update my apt list and install the driver from the repos using Restricted Hardware.

---

### Post by NicMagic on 2008-11-28
I agree with Pedro...

remove the old driver > run apt-get update then install the latest version in the repos
```
sudo apt-get install nvidia-glx-177
```

In fact if i'm not mistaken it might even remove the old one during installation...
I am not 100% sure about it though

Your alternative is to install the closed version downloaded from the NVidia site and to manually install it but i have just noticed that if you want to download the driver for the 5200 series Nvidia still has only the 173 version available for download...
177 off their site seems to be for newer cards? not sure if it really makes a difference though.
If someone has more insight into this they can clarify for us.

GL

---

### Post by snkiz on 2008-11-28
The nvidia drivers in the repos are closed-source binary only from nvidia. From what I've read on thier website the 5200 has been moved into legacy status. The 173 is the last all-in-one installer to support it, future updates will be through the legacy driver package, witch has yet to be updated.

---

