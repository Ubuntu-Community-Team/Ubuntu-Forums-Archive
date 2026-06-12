---
title: "how can i import firefox\thunderbird from windows to ubuntu?"
date: 2008-08-30
forum: General Help
---

### Post by Loolykinns on 2008-08-30
I have Windows XP and i have alot of bookmarks in firefox and email in thunderbird...

is there a way to import firefox\thunderbird settings and files from windows to ubuntu?



thanks

---

### Post by aysiu on 2008-08-30
Copy 

C:\Documents and Settings\*username*\Application Data\Mozilla Firefox 

to 

/home/*username*/.mozilla 

and 

C:\Documents and Settings\*username*\Application Data\Thunderbird 

to 

/home/*username*/.thunderbird

(if that doesn't work, copy it to /home/*username*/.mozilla-thunderbird

---

### Post by Ms_Angel_D on 2008-08-30
For bookmarks install the [foxmarks extension]("http://www.foxmarks.com/") on both version's of firefox and it will sync your bookmarks between the installations. 

As far as thunderbird goes export your contacts to a file and save it. And then in 
```
C:\Documents and Settings\[User Name]\Application Data\Thunderbird\Profiles\(random_Characters).default 
```

Locate your Mail and/or ImapMail folders and copy them to 

```
/home/[User Name]/.mozilla-thunderbird/(random_Characters).default
```

also If you have any extensions you wish to carry over to firefox I suggest the [FEBE extension]("http://customsoftwareconsult.com/extensions/febe/febe.html").

Hope this helps

---

