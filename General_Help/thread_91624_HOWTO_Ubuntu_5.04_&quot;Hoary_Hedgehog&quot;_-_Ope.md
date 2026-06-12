---
title: "HOWTO: Ubuntu 5.04 &quot;Hoary Hedgehog&quot; - OpenOffice.org 2.0"
date: 2005-11-17
forum: General Help
---

### Post by blueturtl on 2005-11-17
Ok, now a lot of people aren't going to be upgrading to Breezy just over a word processor and some Excel sheets, so OpenOffice 2 comes in handy. The only problem is OpenOffice 2 in the Hoary repos is outdated, and the OO site only offers RPM packages. Here's how I got it to work:

[LIST]
[*]Download the OOo_2.0.0_LinuxIntel_install.tar.gz from the OpenOffice.org site.
[*]Unzip the files using **tar -xzf OOo_2.0.0_LinuxIntel_install.tar.gz** to your home directory
[*]Change to the created directory *OOO680_m3_native_packed-2_en-US.8968*
[*]Change to subdirectory *RPMS* and enter command **sudo alien -i *.rpm**
[*]Change to subdirectory *desktop-integration* and install the debian menu items using
**sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb**
[*]Now change directory to */etc/openoffice.org-2.0/program* and enter the following command:
**sudo chmod u+rx,g+rx,o+rx soffice**
[/LIST]

**Why this HOWTO:**
After initial installation if I clicked on any of the menu items under Gnome, nothing happened. There was no error, the system simply sat there. Like me, many people will propably be scratching their heads there.
For reasons unknown to me the simple installation of the packages doesn't work, as not enough rights are given to the user to actually run OpenOffice. This is what the last step in my HOWTO corrects. I searched the web, and I searched the forums and up till now I hadn't found a solution to it yet, so here it is. Hope someone has use for it.

---

