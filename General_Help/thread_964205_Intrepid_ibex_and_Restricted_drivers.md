---
title: "Intrepid ibex and Restricted drivers"
date: 2008-10-30
forum: General Help
---

### Post by russo.mic on 2008-10-30
So, my restricted driver manager just freezes on downloading and installing driver when I try to install ATI.  No Progress.  Any ideas?  I can't believe the servers are that slammed...

Thanks in advance!
Russo

---

### Post by tuxxy on 2008-10-30
Is this an upgrade?

---

### Post by Glugglug on 2008-10-30
> **russo.mic said:**
> So, my restricted driver manager just freezes on downloading and installing driver when I try to install ATI.  No Progress.  Any ideas?  I can't believe the servers are that slammed...

Thanks in advance!
Russo

Have you ticked any boxes in  Software sources      Third party

---

### Post by mikerhodes on 2008-10-31
I am having the same issue after upgrading from 8.04 to 8.10 this morning, trying to install the nvidia binary driver, which was installed in 8.04.

I've no third-party repositories selected under Third-Party.

---

### Post by aikiwolfie on 2008-11-01
I just rolled back to 8.04.1. There's something skrewy with the installer script or something for the NVIDIA drivers. Apparently not everything gets installed. Which means your system ends up skrewed and you need to do all sorts to make it work again.

I'll wait another month and see if these issues get sorted out.

If you really want 8.10 though try installing from synaptic. Do a search for nvidia and install everything except the stuff with -dev. That's the advice over on the bugs thread for 8.10.

---

### Post by mikerhodes on 2008-11-03
> **aikiwolfie said:**
> If you really want 8.10 though try installing from synaptic. Do a search for nvidia and install everything except the stuff with -dev. That's the advice over on the bugs thread for 8.10.

I followed this advice and installed through Synaptic. 

First, I needed to use Synaptic's reload function before the right drivers would show up. Next, rather than installing everything, I only installed "nvidia-glx-177" and the requirements for this package which Synaptic found.

Then I needed to run "nvidia-xconfig" in a terminal, rebooted the computer and the nvidia-driver was installed used and ran fine.

I would imagine the same procedure should work for the ATI driver too, but you'll need to work out each package.

---

