---
title: "How can I install Ubuntu over Fedora?"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by dmurat on 2009-03-18
Hi there
I am currently using Fedora 10 but want to try Ubuntu 8.10 or 9.04 Alpha for a change. I want to remove Fedora and install Ubuntu over it, but I want my settings to remain the same. For example, the firefox setting etc. and especially my Home folder. 

Here is my partitions:
NTFS partition (with Windows Vista)
/
/home and
/boot

How is this possible? Any help would be appreciated :) Thanks.

---

### Post by taurus on 2009-03-18
The UID for the first user in Fedora is 500 while Ubuntu assigns 1000 so that is not going to work if you plan to keep the same $HOME.  However, you can change the UID from 500 to 1000 for your account in Fedora before you install Ubuntu.  Then, mount whichever partition that is to /home when you get to the partition screen and create an exact username during the installing process.

---

### Post by dandnsmith on 2009-03-18
> I am currently using Fedora 10 but want to try Ubuntu 8.10 or 9.04 Alpha for a change. I want to remove Fedora and install Ubuntu over it, but I want my settings to remain the same. For example, the firefox setting etc. and especially my Home folder. 

Here is my partitions:
NTFS partition (with Windows Vista)
/
/home and
/boot


I don't know if this would be the 'approved' method, but what I'd do would be to do the install and, at the 'what to use' stage, select Manual, and then tell the installer what to install where (perhaps set the flag to format / and /boot. I'd leave /home out of things, and then sort it out manually after the install (so it wouldn't get overwritten.

Good luck

---

### Post by stergios_d on 2009-03-18
Allo , friends !
I am a new users in Ubuntu club and i `d like to now how to instal the Ubuntu in a emty desktop(new)?I also want to now if there ia a full pakage with all programs that o computer needs
Thanks!

---

### Post by taurus on 2009-03-18
> **stergios_d said:**
> Allo , friends !
I am a new users in Ubuntu club and i `d like to now how to instal the Ubuntu in a emty desktop(new)?I also want to now if there ia a full pakage with all programs that o computer needs
Thanks!

[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by enjoi19 on 2009-03-18
wouldn't you need to simply copy files you want to keep to a memory stick or external hard drive, then format the hard drive which is an option in ubuntu setup? I also question why you want to keep "Firefox settings" as that takes about 2 seconds to fixup.

---

