---
title: "ISO file for Hardy updates?"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2009-01-12
I just recently did a clean install of Hardy 8.04 from a CD.  When the installation was complete, there were over 385 updates waiting to be downloaded.  Does anyone know if there is an ISO file that can be downloaded and burned on a CD that has these updates only?  It would make it easier if I have to reinstall again, or just for reference sake.  Thanks.

---

### Post by taurus on 2009-01-12
Once you've updated/upgraded your machine, look in /var/cache/apt/archives.

---

### Post by boof1988 on 2009-01-12
Another option is "aptoncd".  It can create a CD/DVD iso.  This iso can be burnt to a disk or placed on other media.

After a re-install etc. APTonCD can access the packages on the CD/DVD or in the file and then place them in the cache so you don't have to download them again.

You will have to install them manually though.

For the updates... when you select install from the Update Manager, they will not need to be downloaded (since you used aptoncd) and they should immediately start to install instead of downloading first.

For the other packages (that are not in the Update Manager), I maintain a text file with the command neccessary to install the other applications.

An example:
```
sudo apt-get install gparted testdisk
```

I keep the aptoncd iso image as well as the text file shown above on a seperate data partition so I can access them after a re-install.

Hope this helps some... there are better ways to do what you want and I look forward to seeing other people's ideas.

---

### Post by gilloz on 2009-01-12
Thanks guys for the responses.  Taurus, I see 419 items in this folder.  What is it I can do now for future use with these files?  In other words, OK, I have these files, what do I do with them?  No smart remarks here now.Ha!  Boof1998, the purpose of having this CD would be like my SP-2 CD for my Windows XP whereas all I do is to put it into my optical drive unit and they install themselves into the OS.  Not looking to do it manually, if possible. Too much work, don't you think?

---

### Post by boof1988 on 2009-01-12
> **gilloz said:**
> TBoof1998, the purpose of having this CD would be like my SP-2 CD for my Windows XP whereas all I do is to put it into my optical drive unit and they install themselves into the OS.  Not looking to do it manually, if possible. Too much work, don't you think?

This way is saving me time compared to how I used to do it... manually check every box needed in Synaptic Package Manager.  And that is just for the extra applications... Let alone the security updates etc.

Maybe someone else has some ideas on how to automate it a little more...  I'd be interested in learning some new stuff.

---

### Post by deanjm1963 on 2009-01-12
Hardy 8.04.2 should be out around the 22nd of January with all the lastest updates.

---

