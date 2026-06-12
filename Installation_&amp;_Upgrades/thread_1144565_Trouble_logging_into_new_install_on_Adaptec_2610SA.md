---
title: "Trouble logging into new install on Adaptec 2610SA Raid"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by OlPeculiar on 2009-04-30
I had a separate thread a couple weeks ago:

[http://ubuntuforums.org/showthread.php?t=1108894](http://ubuntuforums.org/showthread.php?t=1108894)

But I finally got things working.  About a week later, Jaunty was officially released, and I ran...
```
sudo apt-get update
```
...to install the latest and the greatest.  I have been unable to login since.  The GUI login screen will accept my username and password, go all black, and then hang.  If I then <ctrl><alt><F1>, I will get the same error message as described in the OP in this thread:

[http://ubuntuforums.org/showthread.php?t=647158](http://ubuntuforums.org/showthread.php?t=647158)

And that is:  

aacraid: Host adapter abort request(x,x,x,x)
aacraid: Host adapter abort request(x,x,x,x)
aacraid: Host adapter abort request, SCSI hang?


I'm not quite a newbie, but my technical knowledge of the innards of Linux and Ubuntu is pretty thin; the point being - use small words.  :)  I chose the Adaptec 2610SA card because of its reputation for Ubuntu compatibility.  Does anyone know if support for this card or its drivers has been dropped?  More to the point, has anybody ever seen this problem and solved it?  Any and all suggestions are welcome - LiveCD is great and all, but I'm eager to actually get my platters rattling.

Thanks all!

 - OlPeculiar

---

### Post by OlPeculiar on 2009-05-02
Just giving this one a bump - No suggestions yet?  Thanks again for looking...

 - OlPeculiar

---

