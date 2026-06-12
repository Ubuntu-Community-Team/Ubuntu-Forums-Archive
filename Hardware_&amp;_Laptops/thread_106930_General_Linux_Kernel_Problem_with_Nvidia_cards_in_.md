---
title: "General Linux Kernel Problem with Nvidia cards in intel 865GV hotplug==blah blah :("
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by satissh srinivasan on 2005-12-21
Hello! This is my first post here!
I have a p4 3 Ghz machine plugged in a Asrock 865GV board with Agp slot. I have a Nvidia geforce 6800 gt in my agp slot. The problem is Ubuntu installation goes along well but while booting into ubuntu (all three versions, warty,breezy and hoary) it gets hanged after the line,
** detecting hotplug subsystem ** or sumthing like that associated with hotplug.

In general, only SuSe Linux works well and in that too I have to append to the kernel , NOHOTPLUG=1 and NOCOLDPLUG=1 at boot time to enforce boot.hotplug and boot.coldplug to skip. Even Fedora hangs while starting the installation after, kernel_thread_helper.. and then the kernel breaks up. But the interesting fact is both Rh9 and Rhel 3 works very well and with kernel 2.4 and XFREE86 works like a charm. What could be the problem..? I have installed the drivers and configured the /etc/X11/xorg.conf so as the drivers are detected. Is there someway i can install Ubuntu or Fedora.. I have been using older linux versions for two to two and a half years now.

The above mentioned problem is giving me a very tough time out there.. Please help.. Thank You! :)

---

### Post by rykel on 2006-01-09
[QUOTE=satissh srinivasan]Hello! This is my first post here!
I have a p4 3 Ghz machine plugged in a Asrock 865GV board with Agp slot. I have a Nvidia geforce 6800 gt in my agp slot. The problem is Ubuntu installation goes along well but while booting into ubuntu (all three versions, warty,breezy and hoary) it gets hanged after the line,
** detecting hotplug subsystem ** or sumthing like that associated with hotplug.

In general, only SuSe Linux works well and in that too I have to append to the kernel , NOHOTPLUG=1 and NOCOLDPLUG=1 at boot time to enforce boot.hotplug and boot.coldplug to skip. Even Fedora hangs while starting the installation after, kernel_thread_helper.. and then the kernel breaks up. But the interesting fact is both Rh9 and Rhel 3 works very well and with kernel 2.4 and XFREE86 works like a charm. What could be the problem..? I have installed the drivers and configured the /etc/X11/xorg.conf so as the drivers are detected. Is there someway i can install Ubuntu or Fedora.. I have been using older linux versions for two to two and a half years now.

The above mentioned problem is giving me a very tough time out there.. Please help.. Thank You! :)[/QUOTE]

not sure if this will help u, but in both suse and ubuntu, can u please start the bootup process with "acpi=off"?

i am using a laptop with nvidia go 6600 and i face problems with acpi turned on...

---

### Post by rykel on 2006-01-09
[QUOTE=satissh srinivasan]Hello! This is my first post here!
I have a p4 3 Ghz machine plugged in a Asrock 865GV board with Agp slot. I have a Nvidia geforce 6800 gt in my agp slot. The problem is Ubuntu installation goes along well but while booting into ubuntu (all three versions, warty,breezy and hoary) it gets hanged after the line,
** detecting hotplug subsystem ** or sumthing like that associated with hotplug.

In general, only SuSe Linux works well and in that too I have to append to the kernel , NOHOTPLUG=1 and NOCOLDPLUG=1 at boot time to enforce boot.hotplug and boot.coldplug to skip. Even Fedora hangs while starting the installation after, kernel_thread_helper.. and then the kernel breaks up. But the interesting fact is both Rh9 and Rhel 3 works very well and with kernel 2.4 and XFREE86 works like a charm. What could be the problem..? I have installed the drivers and configured the /etc/X11/xorg.conf so as the drivers are detected. Is there someway i can install Ubuntu or Fedora.. I have been using older linux versions for two to two and a half years now.

The above mentioned problem is giving me a very tough time out there.. Please help.. Thank You! :)[/QUOTE]

not sure if this will help u, but in both suse and ubuntu, can u please start the bootup process with "acpi=off"?

i am using a laptop with nvidia go 6600 and i face problems with acpi turned on...

---

