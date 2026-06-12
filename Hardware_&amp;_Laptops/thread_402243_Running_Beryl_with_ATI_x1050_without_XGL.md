---
title: "Running Beryl with ATI x1050 without XGL"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by bmartin on 2007-04-05
I have a computer with an ATI x1050 (similar to/same as chipset x300) that I'd like to set up with both DRI and Beryl. Currently, I'm using fglrx, and I have to switch between a Gnome session for DRI and an XGL session for Beryl.

Here's what I seem to have learned so far:
1. Using fglrx/XGL results in no DRI support, but Beryl works.
2. Using fglrx/Gnome results in DRI support; AIGLX unsupported; Beryl causes Gnome to dump core.
3. Using radeon/Gnome results in no DRI support; AIGLX supported; Beryl causes Gnome to dump core.

I don't like switching between Gnome and XGL. Is there a way to get Gnome to run Beryl with the fglrx/radeon driver without XGL? Does anyone have any idea as to when the DRI spec for XGL will be published and implemented?

---

### Post by overdrank on 2007-04-05
> **bmartin said:**
> I have a computer with an ATI x1050 (similar to/same as chipset x300) that I'd like to set up with both DRI and Beryl. Currently, I'm using fglrx, and I have to switch between a Gnome session for DRI and an XGL session for Beryl.

Here's what I seem to have learned so far:
1. Using fglrx/XGL results in no DRI support, but Beryl works.
2. Using fglrx/Gnome results in DRI support; AIGLX unsupported; Beryl causes Gnome to dump core.
3. Using radeon/Gnome results in no DRI support; AIGLX supported; Beryl causes Gnome to dump core.

I don't like switching between Gnome and XGL. Is there a way to get Gnome to run Beryl with the fglrx/radeon driver without XGL? Does anyone have any idea as to when the DRI spec for XGL will be published and implemented?

Hi, if this helps any I am running the ati x300 on my desktop and I did not want to install the XGL this time. I just install berylsvn and it ran fine. Did not change anything in my xorg and did not have to install any additional drivers, just install Edgy and then berylsvn and off and running. Hope the will help you in the right direction. Good luck!:guitar:

---

### Post by strabes on 2007-04-06
Your chipset supports the radeon driver? Why not just use aiglx since it's more stable and included with ubuntu nowadays? My card (X1400 mobile) isn't compatible with the radeon driver so I would be stuck with xgl which is terribly unstable and slow.

---

### Post by bmartin on 2007-04-06
You know, I'm not really sure. I've read that it's the  same architecture as the 300, but I haven't had much luck with the driver. XGL seems to be the only way to go. I hope the rest of XGL is implemented so that they can stop running it on top of GLX. That's why it's so slow. The DRI support may be a long time coming. It's disappointing. It's my girlfriend's computer and she bought an ATI card.

---

