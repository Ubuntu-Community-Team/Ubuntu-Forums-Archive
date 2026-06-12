---
title: "problem with boot splash"
date: 2008-09-20
forum: General Help
---

### Post by electronique on 2008-09-20
I have installed ubuntu 8.04 recently.
I wanted to customize it.
I added a boot splash theme from

[http://ubuntu-art.org/content/show.php/Fingerprint+-+Usplash+Theme?content=61730](http://ubuntu-art.org/content/show.php/Fingerprint+-+Usplash+Theme?content=61730)

the splash did not work pefectly but atleast some picture comes up while booting.

and after that installed the bootsplash theme from

[http://ubuntu-art.org/content/show.php/Usplash+BlackChrome?content=66583](http://ubuntu-art.org/content/show.php/Usplash+BlackChrome?content=66583)
there were no instructions given here ,so I followed the instructions given for the first boot splash theme i installed here:

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

But now only the normal text appears while booting.

I even can't use the ubuntu default theme
(after
sudo update-alternatives --config usplash-artwork.so
entering 1.
removing vga=791)

please give me your suggestions.

---

### Post by sayakb on 2008-09-20
At a terminal:
```
sudo apt-get install startupmanager
```
Goto System->Administration->Startup-Manager
Adjust all settings from there.

---

