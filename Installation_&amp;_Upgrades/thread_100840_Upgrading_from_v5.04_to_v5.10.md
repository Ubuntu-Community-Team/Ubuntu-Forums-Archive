---
title: "Upgrading from v5.04 to v5.10"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by itxweather on 2005-12-08
Hi,

Am a Linux newbie and haven't used Ubuntu Linux for that long (a few months at the most), however i'm impressed with the distro over-all, it seems to be very stable and quite fast which is good imho. Anyway, i'd like to know how to go about upgrading from v5.04 to v5.10. Is an upgrade possible from v5.04 to v5.10 or do I need to literally re-format my hard disk drive and install v5.10 once the .iso has been downloaded and burn't onto cd?.

I've tried to enable the repositories on my Ubuntu v5.04 installation however it's not working, is this because v5.04 is no longer supported and v5.04 users are encouraged to install v5.10?.

Thank you :-).
Best Regards.

---

### Post by MartinG on 2005-12-08
All you need to do is (should be) to edit your /etc/apt/sources.lst, replacing "hoary" by "breezy". Then
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by cstudent on 2005-12-08
You can also download the.iso and burn to CD or order the free CD. Stick it in the CD drive and it will prompt you to upgrade.

---

### Post by itxweather on 2005-12-08
[QUOTE=MartinG]All you need to do is (should be) to edit your /etc/apt/sources.lst, replacing "hoary" by "breezy". Then
sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

Hi Marting,

Thank you. Much appreciated. Shall make the changes and try the update and distro upgrade.

Best Regards.

---

### Post by itxweather on 2005-12-08
[QUOTE=cstudent]You can also download the.iso and burn to CD or order the free CD. Stick it in the CD drive and it will prompt you to upgrade.[/QUOTE]

Hi cstudent,

Thank you for your reply. Much appreciated.

Best Regards.

---

### Post by itxweather on 2005-12-08
[QUOTE=MartinG]All you need to do is (should be) to edit your /etc/apt/sources.lst, replacing "hoary" by "breezy". Then
sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

Hi Marting,

Just done a find and replace changing all references to "hoary" to "breezy", then sudo apt-get update however this doesn't appear to work :-(. Any other idea's please?.

Thank you.
Best Regards.

---

### Post by funkydan2 on 2005-12-08
In what way does it "not appear to work"?

Are there any error messages when you run "sudo apt-get upate"?

What happens when you run "sudo apt-get dist-upgrade"?

---

