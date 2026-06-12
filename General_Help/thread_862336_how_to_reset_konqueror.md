---
title: "how to reset konqueror?"
date: 2008-07-17
forum: General Help
---

### Post by firsttimeuser on 2008-07-17
somehow my konqueror get messed up, for every hyper link on any website, when I click it, the link does not get opened,instead, another program, freemind is called, I don't know what cause this.

Can I somehow reset konqueror to its default profile to correct this behavior?

Thanks a lot.

---

### Post by firsttimeuser on 2008-07-17
nobody knows?

---

### Post by editrix on 2008-07-18
This is very strange. No, I don't know how to solve it, but it sounds more like freemind is your problem.

Try closing freemind, then rename its folder in your home directory (it's hidden). Then try Konqueror again.

I checked the file associations in Control Centre but can't find anything for http.

If nothing else, I bumped the post.

---

### Post by haegl on 2008-07-18
I've never used Konqueror but in most cases the best way to reset anything is to remove the ~/.[app] directory.

```
rm -rf ~/.konqueror
```

---

### Post by firsttimeuser on 2008-07-18
I had thought about this but it turned out that there is no .konqueror dir under my home directory. I just double checked same result.


> **haegl said:**
> I've never used Konqueror but in most cases the best way to reset anything is to remove the ~/.[app] directory.

```
rm -rf ~/.konqueror
```

---

### Post by der_joachim on 2008-07-19
If you are using KDE3, the konqueror settings should be in .kde/share/config/konquerorrc and .kde/share/apps/konqueror . I do not know though how safe it is to remove them blindly.

BTW: if you use kde4, the user settings sit in .kde4 .

---

### Post by editrix on 2008-07-19
> **der_joachim said:**
> If you are using KDE3, the konqueror settings should be in .kde/share/config/konquerorrc and .kde/share/apps/konqueror . I do not know though how safe it is to remove them blindly.

BTW: if you use kde4, the user settings sit in .kde4 .

Agreed, I wouldn't remove them, just rename them or move them. But I'd still try freemind first, since it seems to have hijacked Konq, and not the other way round.

---

### Post by eudemus on 2010-01-15
I'm running kde4 (Kubuntu Karmic), and renaming the directory

~/.kde/share/apps/konqueror

seemed to do the trick of resetting everything.

There is another load of stuff under ~/.kde4/share/apps/ but it doesn't seem to have been recently updated. I don't know which bits of config go in one of these folders and which in the other (nor indeed which bits get stored somewhere else entirely!).

I've done a few things in konqueror since renaming that dir, but as yet it doesn't seem to have recreated that directory .... presumably it will do eventually.

Anyway, hope that helps someone.
Eudemus

---

