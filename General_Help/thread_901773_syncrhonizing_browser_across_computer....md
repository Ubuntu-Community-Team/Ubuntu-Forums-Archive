---
title: "syncrhonizing browser across computer..."
date: 2008-08-26
forum: General Help
---

### Post by Mia_tech on 2008-08-26
how could I synchronize my firefox browser between my ubuntu desktop and my windows laptop?

---

### Post by mssever on 2008-08-26
I'm sure there are several extensions that can help with that; search the Firefox extensions website. Also, you might be able to simply copy your firefox profile across (or even keep it on your windows partition and make a symlink to it from the Linux side). But I don't know whether this will work.

---

### Post by Mia_tech on 2008-08-26
the problem with that is that the file system structure of the firefox installation is not the same in ubuntu and windows, and I've tried before to get the firefox file that holds all your bookmarks and settings and import it into windows, and it doesn't recognize it.....that's why I'm asking may be someone tried something different



thanks

---

### Post by dje on 2008-08-26
try the [foxmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410") addon

dje

---

### Post by Mia_tech on 2008-08-26
ohh, I don't know... I don't feel very comfortable sending my data outside my network, I think with emails that's more than enough... I think I just save it to a network location and then restore them from my laptop



thanks

---

### Post by mssever on 2008-08-26
Have you done a search similar to this one? [https://addons.mozilla.org/en-US/firefox/search?q=synchronize+profile&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=synchronize+profile&cat=all)

---

### Post by -Zeus- on 2008-08-26
do you mean bookmarks?  you could use foxmarks add-on

---

### Post by kaligus on 2008-08-27
**edit:
If all you want to do is move the bookmarks I have just copied the places.sqlite back and forth.

If you want to sync plugins etc. as well then...
** end edit

I have moved data from both firefox and thunderbird to and from windows/ubuntu.

Gotchas so far found:
both versions must be the same
no platform specific plugins may be used on either end.

Since I dont know what versions etc. you are running here is what I do.

(on the windows machine)
winmerge or syncback between
"c:\Documents and Settings\user\application addons\mozilla\firefox\profiles\[[blaahhh]]\*"
and
"z:\" samba mounted to 
"/home/user/.mozilla/profiles/[[blaahhhhhh]]/*"

(on linux machine)
same process in reverse using similar tools

I have also synched between my local machine to a virtualbox machine on the same physical computer using similar methods.

There may be an interaction between previous plugins as well.  My wife cant get firefox to sync on a dual booter.  This has not been investigated and won't be until she has finished some work.

---

