---
title: "Frustrating, screwy problems with Firefox/Thunderbird"
date: 2008-10-18
forum: General Help
---

### Post by Alex J. on 2008-10-18
HELP! Yesterday a bunch of really screwy things started happening with my Firefox and Thunderbird. I have no idea how to fix them or what the problem is.

> I noticed that when I tried to get into my email through Thunderbird it gave me a message that said, "Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory...."

>It also gave me two messages for my both my email accounts that said, "Thunderbird can't connect securely to pop.gmail.com because the SSL protocol has been disabled." Same message for my hotmail account.

>When I try to go into these email accounts through Firefox directly, the hotmail site and the gmail site crash.

>It's been crashing like crazy very recently, or just going really, really, really slow.

>I also tried to download a theme from gnomelook.org and got the error message, "/tmp could not be saved, because an unknown error occurred.Try saving to a different location."

>Firefox error console is telling me that, "Error: this._storage is null
Source File: file:///usr/lib/xulrunner-1.9.0.3/components/nsLoginManager.js" over and over again.

Why is Firefox being so SCREWY?!? ](*,)](*,)

---

### Post by Alex J. on 2008-10-18
bump

---

### Post by Greyed on 2008-10-18
Have you checked the permissions on your home directory?  What does the following show?

```

ls -la ~

```

---

### Post by jerome1232 on 2008-10-18
Try renaming your profile for firefox and see if the problems clear up.

Could be as simple as a crash caused some file corruption.

---

### Post by Sef on 2008-10-18
> Alex J. 	 		 		bump 	

Please do not bump unless 24 hours have gone by without an answer.  Thank you.

---

### Post by sonicb00m on 2008-10-19
It sounds like your firefox and thunderbird profiles are read only.

---

### Post by koenn on 2008-10-19
> **Greyed said:**
> Have you checked the permissions on your home directory?  What does the following show?

```

ls -la ~

```

possible, but it could also just be lack of disk space
What does the following show?
```
df -h
```

---

