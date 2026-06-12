---
title: "[SOLVED] Install new search engine in Firefox"
date: 2008-11-10
forum: General Help
---

### Post by vlc on 2008-11-10
Hi *,

I would like to install a new search engine in Firefox (upper right corner) which is not provided as an add-on (i.e. not "Manage search engines -> Get more search engines).

I assume that I have to put it somehow in "/usr/lib/firefox/searchplugins", but as I'm lacking a doc, I'm not successful.

Does anyone have a description on how to manually add search engines to Firefox?

Thanks a lot in advance!

---

### Post by alchemist0 on 2008-11-17
double post - ignore :(

---

### Post by alchemist0 on 2008-11-17
ok it's actually pretty simple! :) 

First you must download the search engine (a .src file and a .gif file).

Then go to the konsole and type: 

```
sudo nautilus
```

go to ```
/usr/lib/firefox-3.x/searchplugins
``` (where 3.x is the version of your firefox - mine was 3.0.3) and paste the src and gif file. :)

Restart firefox

DONE! ;)

(I hope I've helped :))

---

### Post by vlc on 2008-11-19
Hi alchemist,

I was actually looking for a description of the format of the files. Finally, I managed adding the new search engine by creating a new file "scroogle.src" in "/usr/lib/firefox-3.0/searchplugins/":

```

<search 
	name="Scroogle"
	description="Search Google anonymously"
	action="https://ssl.scroogle.org/cgi-bin/nbbw.cgi"
	searchForm="https://ssl.scroogle.org/"
	queryEncoding="utf-8"
	queryCharset="utf-8"
	method="GET"
>

<input name="Gw" user="">

</search>
```

Nevertheless, thanks for your help!

---

### Post by jmszr on 2008-11-19
TWIMC,
       Even though this post has been marked as solved there is a simpler solution.
1.) Click on "manage search engines" in the drop down box in the upper right corner of Firefox. 2,) Click on "Add more search engines". 3.)Add "Mycroft Project" to the search engines. 4.) Click on "Mycroft Project" in the drop down menu. 5.) Type Scroogle 6.) Click on the magnifying glass. 7.) Install Scroogle (or whatever-the Mycroft Project has a lot of good links).

---

