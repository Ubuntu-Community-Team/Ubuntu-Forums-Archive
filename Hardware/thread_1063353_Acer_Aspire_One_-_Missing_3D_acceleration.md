---
title: "Acer Aspire One - Missing 3D acceleration"
date: 2009-02-07
forum: Hardware
---

### Post by teatimebing on 2009-02-07
Hi All,

I have an Acer Aspire One, A150BB (the sata one).

Everything has been smooth and easy to setup, but after following some forum posts, much googling, and the AcerAsper wiki entry for ubuntu, I still can't get the right 3D stuff going.

I am running an application called Nuke from a company called The Foundry. It's a vido compositing application. I don't have a license I am trying to use the app in PLE mode, but that is not part of the problem.

Before ubuntu I tried Fedora 10 32bit, and I could install Nuke and run it no problem. With Ubuntu it seems I am missing some settings/drivers. I get the following error:

```

teatime@teatime:/usr/local/Nuke5.1v3-32$ /usr/local/Nuke5.1v3-32/./Nuke5.1 
Nuke 5.1v3, 32 bit, built Jan 16 2009.
Copyright (C) 2008 The Foundry Visionmongers Ltd.  All Rights Reserved.
INFO: Graphics card floating point support not found; Viewer hardware accelerated effects disabled.
Nuke5.1: ../common/dri_bufmgr_fake.c:576: dri_bufmgr_fake_contended_lock_take: Assertion `((&bufmgr_fake->on_hardware)->next == (&bufmgr_fake->on_hardware))' failed.
Aborted
teatime@teatime:/usr/local/Nuke5.1v3-32$

```

---

### Post by teatimebing on 2009-02-08
SOLVED: Using Fedora. Sorry Ubuntu.

---

