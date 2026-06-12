---
title: "Downloading RAR Files From File-Sharing Website [NOT RS] using WGET - I Tried"
date: 2008-11-29
forum: General Help
---

### Post by navneeth on 2008-11-29
I want to download RAR files from MediaFire. (It does not require the use of a username or a password.) I have the links to the different download pages and they are of the form

```
http://www.mediafire.com/?<aseriesofcharacters>
```


Example: [http://www.mediafire.com/?tjmjrmtuyco](http://www.mediafire.com/?tjmjrmtuyco)


Yesterday, I successfully downloaded two out of six files by directly using link to the rar files, but, apart from the two, the others got timed-out, or something. Today, I was a bit more ambitious and tried to download the files by providing just the page URL. 

This was what I tried...

```
wget -A rar [-r [-l 1]] <mediafireurl>
```

That is to say, I tried with and without the recursive option. It ends up downloading an HTML page of a few KB in size, while what I want is in the range 90-100 MB and RAR. 

What happens with MediaFire for those who may not be aware, is that it first says 

> Processing Download Request...

This text after a second or so turns into the download link and reads

> Click here to start download..

I would appreciate it if someone would tell me how to write a proper script for this situation.

---

### Post by jgoguen on 2008-11-29
I don't think you can get the page and get the final link from there, unless your script also interprets JavaScript.  I tried going to that link with JS disabled, and I couldn't get the download link without enabling JS.  Maybe there's a way you could translate the URL to the final download link.  It would depend on how much they do on the back end.  Do you have a bunch of other MediaFire links to look at and see what the final link is?  If there's some sort of pattern, then you could probably write a script to take the URL and use wget to fetch the final URL.  I say "probably" because I noticed that the final link was off download52.mediafire.com, so if the file is only available off that specific server then you'd have to also figure out how to get that server name.

---

### Post by navneeth on 2008-11-30
Hi. 

> **jgoguen said:**
> I don't think you can get the page and get the final link from there, unless your script also interprets JavaScript.  I tried going to that link with JS disabled, and I couldn't get the download link without enabling JS.  Maybe there's a way you could translate the URL to the final download link.  It would depend on how much they do on the back end.  Do you have a bunch of other MediaFire links to look at and see what the final link is?  If there's some sort of pattern, then you could probably write a script to take the URL and use wget to fetch the final URL.  I say "probably" because I noticed that the final link was off download52.mediafire.com, so if the file is only available off that specific server then you'd have to also figure out how to get that server name.

These are the download links for two different files, obtained many hours apart. 

```
URL: http://www.mediafire.com/?tjmjrmtuyco
DL1: http://download52.mediafire.com/4xzz2dnmobyg/tjmjrmtuyco/Mahlerfeest09.part1.rar
DL2: http://download403.mediafire.com/menyll2mmryg/tjmjrmtuyco/Mahlerfeest09.part1.rar

URL: http://www.mediafire.com/?nljmymknkn5
DL1: http://download403.mediafire.com/ejsqdwjvjmng/nljmymknkn5/Mahlerfeest09.part2.rar
DL2: http://download403.mediafire.com/mzzvubemcc1g/nljmymknkn5/Mahlerfeest09.part2.rar

```

Final download links changes (duh!) as does the server. :(

---

### Post by jgoguen on 2008-11-30
Unfortunately it looks like you're stuck manually downloading.  I would be interested to see if the download server actually matters, but that extra string of characters throws a huge wrench into the whole thing.

---

### Post by navneeth on 2008-11-30
> **jgoguen said:**
> Unfortunately it looks like you're stuck manually downloading.

I've been doing just that for the past half hour or so. Do let me know if you crack the code. :) Thanks for the replies.

---

