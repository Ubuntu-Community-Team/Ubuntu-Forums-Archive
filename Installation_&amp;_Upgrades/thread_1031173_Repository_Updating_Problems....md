---
title: "Repository Updating Problems..."
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by dayosh on 2009-01-05
Hola!  After attempting to use the Update Manager, I'm now met with a new pop-up window and error message I haven't ever seen before:

```
GPG error: http://apt.wxwidgets.org etch-wx Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E0BCE7F53B087BCMethod gave invalid 400 URI Failure message
```

I'm assuming it means that this particular 3rd-party source I have is temporarily down, but the weird thing is, it won't continue updating (ignoring the broken source) and after de-selecting the source in Software Sources, I'm met with this error:

```
Method gave invalid 400 URI Failure message
```

Has anyone experienced anything like this, before?  I didn't think I was doing anything wrong (did everything the same way I've always done it), and I don't think I missed anything, so I'm not exactly sure what's up.  Any help would be greatly appreciated, and thanks much in advance!  :)

---

### Post by theozzlives on 2009-01-05
do:
```
sudo  gedit /etc/apt/sources.list
```
put a # before  the troublesome line

---

### Post by dayosh on 2009-01-05
Opened up the .list, and it already had a # in front of the naughty source (since I unchecked it in the Sources List front-end).

However, everything seems to be working fine, now.  I'm not sure if a source was temporarily down, or what, but everything seems to be running fine now.  *shrug*  Really weird.

Thanks very much for the help, Ozz!  :)



**As an addendum, I typically have error messages when updating, but that's because it's just telling me that certain sources (like widgets) have no public key, which I don't really consider major, considering it still downloads update information from those sources.  Any rough or vague ideas as to why this might have happened?  Thanks!

---

