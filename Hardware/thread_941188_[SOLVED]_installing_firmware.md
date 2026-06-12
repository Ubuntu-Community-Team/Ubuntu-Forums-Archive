---
title: "[SOLVED] installing firmware"
date: 2008-10-07
forum: Hardware
---

### Post by fishbulb1022 on 2008-10-07
I'm trying to install firmware for a usb tv tuner (ati tv wonder 600). I checked the video4linux wiki page on the tuner and have been going through the steps to install it. The link is [http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB]("http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_HD_600_USB") if you'd like to check it out. I got to extracting the file and now I'm stuck. It wasn't located where they say, but i found it, but when I run ./extract_xc3028.pl it says command not found. Any help would be appreciated.

Alright, after a few more hours of searching I found a solution. .pl files are perl scripts, so the correct command is```
perl ./extract_xc3028.pl
``` However, you have to be in the correct directory to run this. For me this was /usr/src/linux-headers-2.6.27-6-generic/Documentation/video4linux. If yours is different, and you can't find the path, search for the file (go to places>computer and then search the entire filesystem, the regular search thing didn't work for me) and copy it to the desktop, then just ```
cd Desktop
``` and run the command. Also, you must have the hcw85bda.sys in the same directory as the extract file. Again, an easy way to do this is to search for it, and then just copy it to the desktop. Then you know where it is. If you run into ANY snags, type sudo before the command. It may not give an error message, it didn't for me, but some of the folders are restricted and its necessary. For the next steps go to the wiki page.

---

