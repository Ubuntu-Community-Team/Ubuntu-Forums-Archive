---
title: "[SOLVED] subtitles, incorrect encoding"
date: 2008-10-20
forum: General Help
---

### Post by woodenbrick on 2008-10-20
Hi all,
Sometimes I watch movies with friends who require Bulgarian subtitles. The problem is that whoever makes them doesn't use unicode, but Windows-1251. the subtitles are recognised by my system as Western ISO-8859-1 and I get this kind of nonsense: È ìîëÿ òå, êàæè ìè, ÷å äí

The only way I found to change them is to open in firefox, change the encoding, copy and paste back into the original document and save.  Is there an easier way to do this, or a full solution?

edit: Some subtitles that i'm talking about are available from here:
[http://subs.unacs.bg/]("http://subs.unacs.bg/")

---

### Post by geirha on 2008-10-20
If you know the encoding, then converting to utf8 is easy:
```
iconv -f WINDOWS-1251 -t UTF-8 subtitles.srt >subtitles.utf8.srt
```

---

### Post by woodenbrick on 2008-10-20
Ok thanks geirha, this is the right idea, though it's not working correctly. Converting to unicode seems to scramble it in a different way.
I think what I need to do is this:
```
wode@wode-laptop:~$ iconv -f ISO-8859-1 -t WINDOW-1251 ./Desktop/s-thir13enghosts.srt >subs.srt
iconv: conversion to `WINDOW-1251' is not supported

```
but apparently it's not possible.

---

### Post by geirha on 2008-10-20
You mistyped WINDOW**S**. I guess it's not encoded with windows-1251 then, but rather iso-8859-1? Try converting to utf-8 from that then.

```
iconv -f ISO-8859-1 -t UTF-8 subtitles.srt >subtitles.utf8.srt
```

---

### Post by woodenbrick on 2008-10-20
My mistake geirha, Your first post was correct, The file on disk is correctly encoded, but firefox was set to open it in another encoding. The text in the file is fine.  Thanks very much for your help!

---

