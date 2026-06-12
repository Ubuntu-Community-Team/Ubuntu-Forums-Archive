---
title: "kpdf doesn't show pdf correctly"
date: 2008-10-30
forum: General Help
---

### Post by impeesa on 2008-10-30
Hi all, I have this weird problem:

kpdf does not display pdf files correctly (while evince does it), I suppose this happened after installing acroread.

Purging and reinstalling kpdf does not work...

This is the screenshot I get when a file is opened:
[[img]http://www.divshare.com/img/thumb/5699314-834.png[/img]](http://www.divshare.com/download/5699314-834)

Launching kpdf from shell, after the file is opened, the following error is returned:

```

al@al-laptop:~$ kpdf
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

```

I was wondering if this can be solved deleting one or more config files of kpdf..
thanks in advance

---

