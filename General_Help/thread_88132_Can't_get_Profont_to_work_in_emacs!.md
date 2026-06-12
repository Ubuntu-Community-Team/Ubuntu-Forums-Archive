---
title: "Can't get Profont to work in emacs?!"
date: 2005-11-09
forum: General Help
---

### Post by absolut on 2005-11-09
Hi,
Been wanting to try out ProFont for emacs.  So I followed the instructions in this thread [http://www.ubuntuforums.org/showthread.php?t=76038&highlight=profont]("http://www.ubuntuforums.org/showthread.php?t=76038&highlight=profont")

Right now if I go to system->preferences->font, and I go to the font folder, I CAN see Profont (fonts:///ProFont type:gzip archive).  However when I try to do xfontsel or xlsfont, I can't see it at all.   I guess that is why when I go into emacs and try to search for profont, I cannot see it either.

Does any one have any idea why I can't find it in xfontsel / see it in emacs?

---

### Post by Manny C on 2005-11-09
Have you tried running the following command as per [instructions]("http://forum.tobiasjung.net/showthread.php?fid=25&tid=93&old_block=0")?:
```
 sudo fc-cache -v 
``` 
Also, you may need to [tinker]("http://forum.tobiasjung.net/showthread.php?fid=25&tid=93&old_block=0"):
[quote=Hakan]
...edit your ~/.fonts.conf file (again, create it if you don't have it). Below is my full ~/.fonts.conf that disables anti-aliasing of this particular font:
 <?xml version="1.0"?>
 <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
 <fontconfig>
 <match target="font">
     <test qual="any" name="family">
         <string>ProFontWindows</string>
     </test>
     <edit name="antialias" mode="assign">
         <bool>false</bool>
     </edit>
 </match>
 </fontconfig>
[/quote]

---

### Post by duncan_bayne on 2008-04-03
I have posted some detailed instructions on how to get ProFont going in Emacs on Xubuntu here:

[HOWTO: Xubuntu, ProFont, Emacs]("http://www.fluidscape.co.nz/?q=node/92")

---

