---
title: "Netbook-Remix: no fsck - even after unclean shutdown"
date: 2009-02-15
forum: Hardware
---

### Post by tuxophil on 2009-02-15
Hi,

I'm wondering if it's normal that my Ubuntu system doesn't run fsck at boottime even when the previous session wasn't shut down properly. (In fact I'm suffering from hard lockups due to the Broadcom wl driver. [Bug #292450]("https://bugs.launchpad.net/ubuntu/+bug/292450"))

I then tried "touch /forcefsck" but to no avail. Somehow I can't get Ubuntu to fsck my drive even though it's probably necessary.

Any help would be appreciated!

I'm using Ubuntu Netbook Remix 1.0.1 (installed from the .img proposed [here]("https://wiki.ubuntu.com/UNR#UNR%20Image%20Installation")) which is based on hardy (8.04). The computer in question is a Lenovo Ideapad S10e.

---

### Post by tuxophil on 2009-02-15
> **tuxophil said:**
> I'm wondering if it's normal that my Ubuntu system doesn't run fsck at boottime even when the previous session wasn't shut down properly.

Well, I could track this one down by myself :-)

Of course, skipping fsck is not the normal behaviour. In fact it's due to a serious bug in the UNR .img file. After the installation the root partition is listed in /etc/fstab with a pass parameter of "0" meaning that this drive shouldn't ever be checked. This is just plain wrong!

---

