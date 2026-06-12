---
title: "Just a quick mount question.."
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by dhega on 2005-05-15
Hello all.

I have this little problem,
I mount my "download" partition @  /home  with 'defaults'

But that doesnt give me write access as user 'dhega'
Only root can do that,

So what options should i mount it with?
i want full access as dhega

thanks

---

### Post by freelovemat on 2005-05-15
add the > users option to the mountpoint in /etc/fstab.

---

### Post by dhega on 2005-05-15
[QUOTE=freelovemat]add the  option to the mountpoint in /etc/fstab.[/QUOTE]


ok, so it looks like   
/dev/hda5       /home           reiserfs defaults,users        0       2



?
thanks

---

