---
title: "Twitux Twitter Client Display Pic Bug!!! Help!!!"
date: 2008-11-13
forum: General Help
---

### Post by arranmc182 on 2008-11-13
Small bug in Twitter when I update or somebody updates there Twitter Display picture Twitux will not update to the new picture :confused: even when uninstalling and reinstalling Twitux, I used gTwitter an that works 100% and even has the Option to Clear Cached Images unlike Twitux.
If there is a folder that Twitux saves the pictures to can somebody tell me where that is so I can delete them so that Twitux will get the new Display pictures.

---

### Post by villalcalde84 on 2009-01-03
I have the same problem. Many of the people I follow have changed their picture, but Twitux shows the old one. I have looked for the folder of the program in my home folder, and found it inside .gconf, but the pictures does not appear, just some .xml files, so I can not delet the ones that changed.

Is there a way to do this? How can I delete or update the images shown?

Thanks.

---

### Post by sizzam on 2009-01-15
It looks like twitux caches avatars in:

~/.gnome2/twitux/avatars

When I rm all the files in the avatars directory, twitux downloads a fresh copy.

---

### Post by villalcalde84 on 2009-01-26
Thanks, it worked! Now I have the avatars updated.

It would be good if Twitux updates them automatically, I hope this is included in a future version.

---

### Post by abhiroopb on 2009-10-23
Twitux still displays oversized version of some avatars. 

Is there a fix for this?

---

### Post by abhiroopb on 2009-10-24
I have attached a screenshot of what the problem is. It should be obvious from the picture but if there are any problems of interpretation please let me know.

---

