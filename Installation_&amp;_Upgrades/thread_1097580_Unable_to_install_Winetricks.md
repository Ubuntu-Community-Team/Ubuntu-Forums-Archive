---
title: "Unable to install Winetricks"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Alexandre76 on 2009-03-16
Hello Everyone,

I have followed carefully the instructions to install Winetricks, but I get some errors, see below:

 wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
--2009-03-16 09:25:14--  [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
Resolving [www.kegel.com](www.kegel.com)... 216.92.86.126
Connecting to [www.kegel.com|216.92.86.126|:80](www.kegel.com|216.92.86.126|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 71736 (70K) [text/plain]
Saving to: `winetricks'

100%[======================================>] 71,736      34.3K/s   in 2.0s    

2009-03-16 09:25:17 (34.3 KB/s) - `winetricks' saved [71736/71736]

administrator@ICTSDUBUNTUCHINA:~$ chmod a+x winetricks
administrator@ICTSDUBUNTUCHINA:~$ sudo mv winetricks /usr/local/bin
administrator@ICTSDUBUNTUCHINA:~$ winecfg
administrator@ICTSDUBUNTUCHINA:~$ mv ~/.wine/drive_c/windows/system32/rpcrt4.dll ~/.wine/drive_c/windows/system32/rpcrt4.bak
mv: cannot stat `/home/administrator/.wine/drive_c/windows/system32/rpcrt4.dll': No such file or directory

I need to be able to Run Office 2007 (preferably) on my Ubuntu 8.10 because my company has Excel macros that won't work with OpenOffice.

Any help would be appreciated

---

### Post by OKKARE on 2009-03-25
From what I understand, winetricks just install things for you, it doesn't need to be installed itself either.

Just navigate to the folder it's in and type sh winetricks, it will show you a list of things you can install.

---

