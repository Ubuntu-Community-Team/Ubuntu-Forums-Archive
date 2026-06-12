---
title: "Lightweight Chinese text viewer?"
date: 2008-08-24
forum: General Help
---

### Post by khughitt on 2008-08-24
Hi all,

Anyone happen to know a good lightweight text-editor/word-processor that can either auto-detect encodings, or makes it easy to view documents in UTC, Big5, and GB encodings?

I can view the documents in OpenOffice, but its a pain to have to specify the language, encoding, etc. I've also tried gedit and leafpad, but couldn't get either to support Chinese encodings.

If anyone has any suggestions I would be greatly appreciative.

Thanks!
Keith

---

### Post by linux_tech on 2008-08-24
Some suggestions 

System>Admin>Language Support should have a variety of languages to select, chinese

you may need to install some fonts-
[http://developer.novell.com/wiki/index.php/HOWTO:_Optimise_Ubuntu_for_Chinese_desktop](http://developer.novell.com/wiki/index.php/HOWTO:_Optimise_Ubuntu_for_Chinese_desktop)

Input methods are needed to enter complex characters in many non-latin languages-  [https://launchpad.net/ubuntu/+source/scim/1.4.7-3ubuntu1](https://launchpad.net/ubuntu/+source/scim/1.4.7-3ubuntu1)
IME guide-  [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by tacutu on 2008-08-24
gedit-> open-> Character Coding -> Add or remove

and add your encodings. Don't rely on the "autodetect" feature of gedit, as it's not always (ever?) working. After adding the encodings to the list, select the correct manually before opening the file.

if you want to convert <fileA> from, say, BIG5 to UTF, you can use the command line utility iconv.

```
iconv -f BIG5 -t UTF8 <fileA> -o <fileAunicode>
```

---

### Post by khughitt on 2008-08-24
Awesome. Thanks, you read my mind :)

I have a bunch of old documents saved in Big5 that I was planning to convert to UTC for ease of use. The encoding selection also works great with gedit. It only failed when I tried to open the document directly by double-clicking.

Thanks also linux_tech for the suggestions. My system is setup already to view and input Chinese. The problem I was having was more related to word-processing with specific encodings.

Take care!

---

