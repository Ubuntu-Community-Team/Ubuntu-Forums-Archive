---
title: "Canon Pixma Mg-6320 scanner not working"
date: 2017-01-06
forum: Hardware
---

### Post by Atulo on 2017-01-06
Hello,

I've got a Canon Pixma Mg-6320 printer.  The scanner is unfortunately not working and I was hoping see if anyone had any advice.

I've installed scangearmp from Canon Australia's website ([http://support-au.canon.com.au/contents/AU/EN/0100470802.html](http://support-au.canon.com.au/contents/AU/EN/0100470802.html)).

The error message I get when trying to run simple scan is 'unable to connect to scanner'.  The error message I get when trying to run Xsane is 'no devices available'.  

I'm running Ubuntu Mate 16.04 LTS.

If anyone has any thoughts, I'd be very grateful.

AB

---

### Post by pdc on 2017-01-07
Hi Atulo; welcome to the Ubuntu forums;

as ubuntu uses Debian packages, a debian package would have perhaps been the easiest; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100470702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100470702.html) 

ScanGearMP is a programme from Canon so it does not use the Simple Scan: you run it first from a terminal: do you know where to find the terminal? If not [https://linuxconfig.org/how-to-open-a-terminal-on-ubuntu-xenial-xerus-16-04-linux](https://linuxconfig.org/how-to-open-a-terminal-on-ubuntu-xenial-xerus-16-04-linux) press the control alt and t keys together;

in the terminal, type > [COLOR="#FF0000"]scangearmp[/COLOR] and hit the ENTER key; if it loads, great; I can suggest how to make a shortcut on the desktop for the future

---

### Post by Atulo on 2017-01-09
Hi pdc,

Thank you very much for that advice.  It worked very well.  If you might have any thoughts on how to make a desktop shortcut, that would be greatly appreciated. 

Mainly to learn a bit more about ubuntu, would you happen to have any thoughts on why the scanner won't connect to simple scan?  Might there be a simple solution to this.  

Thanks again for you time and advice, pdc.

Best wishes,

~AB

---

### Post by pdc on 2017-01-09
you just need to add a small file

this link tells you how [http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)

the commands they suggest are

```
[COLOR="#FF0000"]sudo apt-get install --no-install-recommends gnome-panel[/COLOR]
```

then 

```
[COLOR="#FF0000"]sudo gnome-desktop-item-edit /usr/share/applications/ --create-new[/COLOR]
```

then the key thing is the COMMAND field in the little box that opens up: the COMMAND must be ```
[COLOR="#FF0000"]scangearmp[/COLOR]
```

any joy?

---

