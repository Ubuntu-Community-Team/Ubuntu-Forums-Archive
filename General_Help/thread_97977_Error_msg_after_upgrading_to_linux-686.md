---
title: "Error msg after upgrading to linux-686"
date: 2005-12-02
forum: General Help
---

### Post by leechin on 2005-12-02
I upgraded the kernel from linux-386 to linux-686 since then i have been receiving this error message. 

-------------------------------------------------------------------------------------------------------

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory) W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

-------------------------------------------------------------------------------------------------------

Anyone has any ideas why or how to go abt it?

---

### Post by Pablo_Escobar on 2005-12-02
That's no kernel related :)
It's just an entry in Your sources list.
Edit as root Your sources.list and put a hash (#) in front of a line which says something about CD-ROM.
It should be ok :)

---

