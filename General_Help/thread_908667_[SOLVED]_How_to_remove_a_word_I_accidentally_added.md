---
title: "[SOLVED] How to remove a word I accidentally added in Mozilla Firefox spell checker?"
date: 2008-09-02
forum: General Help
---

### Post by FastMady123 on 2008-09-02
I accidentally added the word "becuase" in Mozilla Firefox spell checker. I used the instructions from [Firefox Support]("http://support.mozilla.com/en-US/kb/Using+the+spell+checker#Removing_a_word_you_have_accidentally_added") but I can't find the file *persdict.dat*. That word is the most common misspelling of becuase when I type. I want to remove that word from spell checker. I'm using Ubuntu.

---

### Post by EmanresuusernamE on 2008-09-02
Should be somewhere in the dictionary directory of the ~/mozilla/firefox directory in your /home directory.............

/home/<username>/mozilla/firefox/dictionary

---

### Post by raptor2552 on 2008-09-02
look for the file presdict.dat in the directory: /home/yourid/.mozilla/firefox/something.default/presdict.dat

---

### Post by junglist313 on 2008-11-02
I also added a missspelled word. I have checked in 

/home/<name>/.mozilla/firefox/<profile_ID>.default/

but there is no persdict.dat file. Where could it be? Here is a listing of the above directory:

```
.                compatibility.ini     formhistory.sqlite  permissions.sqlite     urlclassifier3.sqlite
..               compreg.dat           gm_scripts          places.sqlite          urlclassifierkey3.txt
adblockplus      content-prefs.sqlite  gm_scripts_08bak    places.sqlite-journal  webappsstore.sqlite
blocklist.xml    cookies.sqlite        key3.db             pluginreg.dat          XPC.mfasl
bookmarkbackups  downloads.sqlite      localstore.rdf      prefs.js               xpti.dat
bookmarks.html   extensions            lock                search.sqlite          XUL.mfasl
Cache            extensions.cache      mimeTypes.rdf       secmod.db
cert8.db         extensions.ini        OfflineCache        session.rdf
chrome           extensions.rdf        .parentlock         signons3.txt

```

I am running Firefox 3.0 on Ubuntu 8.04. I tried doing a "locate" command on persdict.dat but no hits. 

Any ideas? :confused:

---

