---
title: "Canon Pixma mg2220 support."
date: 2013-08-26
forum: Hardware
---

### Post by laboyinaz on 2013-08-26
Hello, I recently purchased a Canon Pixma MG2220 printer. I am not able to locate any drivers for this printer. 

Has anyone found a solution or recommendations?

---

### Post by Rockman-X on 2013-08-26
Try this:

 [http://forums.linuxmint.com/viewtopic.php?f=51&t=128400](http://forums.linuxmint.com/viewtopic.php?f=51&t=128400)

---

### Post by pdc on 2013-08-28
so you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html)

and you will download [COLOR="#008000"]cnijfilter-mg2200series-3.80-1-deb.tar.gz[/COLOR] 

the commands would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -xzvf cnijfilter-mg2200series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg2200series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

____________________________________________________

Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner

so go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469701.html)

and you will download [COLOR="#008000"]scangearmp-mg2200series-2.00-1-deb.tar.gz[/COLOR]

close and open the terminal again and then

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mg2200series-2.00-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mg2200series-2.00-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

and to run ScanGearMP 

> **[COLOR="#FF0000"]scangearmp[/COLOR]**

and you can then create a launcher to open it regularly

---

