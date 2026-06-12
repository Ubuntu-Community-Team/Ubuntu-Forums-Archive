---
title: "superkaramba"
date: 2005-11-30
forum: General Help
---

### Post by tikal26 on 2005-11-30
has any one managed to install themes using the get new stuff from the new superkarmaba. I get all sort of errors that I don't even know where to start. I have a green scke next to the and there is no option to install but I can't apply the theme.

---

### Post by carlos1 on 2005-11-30
I just tried via that feature but it says it has no access to /tmp/kde-(user).

---

### Post by tikal26 on 2005-11-30
yeah I get that one too. what that means?

---

### Post by ltmon on 2005-11-30
That's odd.  By default everyone should have access to all files in the /tmp directory.

Go into your ~/.kde directory and you should have a folder there named "tmp-<hostname>" which is actually a link to "/tmp/kde-<username>".  Make sure you have permissions to both these objects (the link and the /tmp/kde-<username>). The following commands do this:

> sudo chmod a+rwx /tmp/kde-<username>
> sudo chmod a+rwx /home/<username>/.kde/tmp-<hostname>

L.

---

### Post by troywill1 on 2005-12-02
Yes, I am getting this too (cannot rename partial file: /tmp/kde-(user)) and my permissions to /tmp/kde-<username> and /home/<username>/.kde/tmp-<hostname> are a+rwx.

---

### Post by tikal26 on 2005-12-05
me too I also have permission but no luck

---

### Post by limit223 on 2005-12-05
I had this problem too, but after I close programs which were using files in /tmp/kde-*, changing the permission of the director, and restart superkaramba...I could install whatever theme I wanted.

---

