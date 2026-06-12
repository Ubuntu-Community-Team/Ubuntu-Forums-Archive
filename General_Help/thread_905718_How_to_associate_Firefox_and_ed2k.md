---
title: "How to associate Firefox and ed2k?"
date: 2008-08-30
forum: General Help
---

### Post by shallpion on 2008-08-30
Hello everybody. I am now using Ubuntu 8.0.4 and just installed mldonkey. I met a common problem that is how to associate  firefox and ed2k. I tried two ways, following instructions
from internet. The first one is to install an handler Add-on, the second is to write a subscript
by myself. None of them worked. In fact when I click on an ed2k link, there will be a "Launch application" window. However, when I choose ed2k or my subscript, nothing happens.

My subscript is ~/.mldonkey/submit
> #!/bin/bash
(echo "dllink $*"; echo q ) | nc localhost 4000
Then I give it permission by
> chmod +x ~/.mldonkey/submit
Also I constructed a boolean and a string in firefox's about:config as 
> network.protocol-handler.external.ed2k TRUE
network.protocol-handler.app.ed2k home/myname/.mldonkey/submit 
In fact when I tried to run this subscript manually, I found the following output:
> Usage: file [-bcikLhnNrsvz0] [-e test] [-f namefile] [-F separator] [-m magicfiles] file...
       file -C -m magicfiles
Try `file --help' for more information.
bash: /: is a directory
bash: %5B%E6%83%85%E9%9D%9E%E5%BE%97%E5%B7%B2%E4%B9%8B%E7%94%9F%E5%AD%98%E4%B9%8B%E9%81%93%5D.What.On.Earth.Have.I.Done.Wrong.2007.DVDRip.XviD-SSF-Sample.avi: command not found
bash: 7315456: command not found
bash: 4f0c268eae7675a048838862c162677d: command not found

when I tried to open 
>  ./submit ed2k://|file|%5B%E6%83%85%E9%9D%9E%E5%BE%97%E5%B7%B2%E4%B9%8B%E7%94%9F%E5%AD%98%E4%B9%8B%E9%81%93%5D.What.On.Earth.Have.I.Done.Wrong.2007.DVDRip.XviD-SSF-Sample.avi|7315456|4f0c268eae7675a048838862c162677d|h=LJSCTKCIXGKIHSLVRRMLCOPCLQHRZN2F|/
 

I followed other people's experience, but it did not work. So I have to seek for help in 
forum. Hope somebody can help me on it. Thank you very much.

---

### Post by markharding557 on 2008-08-30
I get around this by copying the link to the clipboard(copy link location)in firefox

---

### Post by shallpion on 2008-08-30
> **markharding557 said:**
> I get around this by copying the link to the clipboard(copy link location)in firefox

yeah, i have to do that also, but too troublesome ~~>_<~~

---

### Post by shallpion on 2008-08-31
> **shallpion said:**
> Hello everybody. I am now using Ubuntu 8.0.4 and just installed mldonkey. I met a common problem that is how to associate  firefox and ed2k. I tried two ways, following instructions
from internet. The first one is to install an handler Add-on, the second is to write a subscript
by myself. None of them worked. In fact when I click on an ed2k link, there will be a "Launch application" window. However, when I choose ed2k or my subscript, nothing happens.

My subscript is ~/.mldonkey/submit

Then I give it permission by

Also I constructed a boolean and a string in firefox's about:config as 

In fact when I tried to run this subscript manually, I found the following output:

when I tried to open 


I followed other people's experience, but it did not work. So I have to seek for help in 
forum. Hope somebody can help me on it. Thank you very much.


I have solved this problem. I just set the value of 
network.protocol-handler.external.ed2k  as FALSE, rather than TRUE
so now it works well.

---

### Post by toiger on 2008-09-02
I could not enter the existing ed2k launch application either, so I just 

choose it new again below.        /usr/bin/ed2k

Works fine for me

---

