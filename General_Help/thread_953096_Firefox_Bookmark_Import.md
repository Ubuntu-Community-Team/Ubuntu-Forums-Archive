---
title: "Firefox Bookmark Import"
date: 2008-10-19
forum: General Help
---

### Post by sirdouglas on 2008-10-19
Before I reformatted my computer, I backed up my Firefox Bookmarks by using the "Export" function in firefox with "Organize Bookmarks."  Well, now to import the bookmarks the file doesn't even appear while browsing for it.  If I drag it into Firefox it simply has random text in the browser with my random urls mixed in there (I don't know this programming language stuff).  How can I get this imported?

Thanks,

Doug

---

### Post by Tux+ on 2008-10-19
Your baackup may be corrupted. Are you apple to open the bookmark file using a text editor? The file should still look like garbage in the text editor but has some sort of structure. You should also recognize some details of your bookmarks for example:
```
{"index":4,"title":"Google Docs","id":1509,"parent":1439,"dateAdded":1187304206000000,"lastModified":1215558218000000,"annos":[{"name":"placesInternal/GUID","flags":0,"expires":4,"mimeType":null,"type":3,"value":"fif3y8ha-26"}],"type":"text/x-moz-place","uri":"http://docs.google.com/"}
```

Is my "Google Docs" bookmark and the link is preceded with the "uri" tag. Failing that you can add them manually if you can open it in a text editor.

Next time try using [Foxmarks]("http://www.foxmarks.com/") plugin. It syncs your bookmarks to a server which can be sync'd on multiple computers / browsers and viewable online.

---

### Post by fragos on 2008-10-20
I've found the easiest way to backup bookmarks while making them available on multiple machines is to use the Firefox add-on "foxmarks".

---

