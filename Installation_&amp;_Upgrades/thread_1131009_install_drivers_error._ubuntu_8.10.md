---
title: "install drivers error. ubuntu 8.10"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by im_headhunter on 2009-04-20
hello i have a problem with my drivers, any of them wont install, they just come with an ERROR

"An error occurred while loading the archive  (null) "

"then i open command line output"
/home/michael/skrivebord/svs setup/ SP39403/setup.exe
End-of-central-directory sagnature not found. Either this file is not a zipfile, or it constitutes one disk of a multi-part archive. In the latter case the central directory and zipfile comment will be found on the last disk's of this archive.

setup.exe may be a plain executable, not an archive
Note: cannot find zipfile directory in one of /home/michael/skrivebord/svs setup/ SP39403/setup.exe or
/home/michael/skrivebord/svs setup/ SP39403/setup.exe.zip, and cannot find /home/michael/skrivebord/svs setup/ SP39403/setup.exe.ZIP, period.

these drivers i downloaded from this website. 
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3816485](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3816485) 


my system is.

operating system: Ubuntu 8.10
model: CQ 70-120 eo  :)

( sorry my english )

---

### Post by Mark Phelps on 2009-04-20
These appear to be MS Windows drivers made available by HP.  You can't use MS Windows drivers (except for rare exception of NDISWrapper) in Linux.

These files are self-extracting archives used for updating an HP OEM machine running Vista.

---

