---
title: "Location of Applicaton Files"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by meistercobbman on 2008-12-26
I just installed SwiftFox on my xUbuntu laptop (via terminal apt-get install swiftfox-pentium-m). 

I created a launcher shortcut on the top panel, and I'd like to put the swiftfox icon with it. However, I cannot find the location of the swiftfox application files, where I think the icon file would be. Where are they? 

How can I find out where programs are located on my Hard Drive? :confused:

---

### Post by alenis on 2008-12-26
Programs should be located in the /usr/bin directory. You can search for files with the find command, e.g. sudo find / -name swiftfox

---

