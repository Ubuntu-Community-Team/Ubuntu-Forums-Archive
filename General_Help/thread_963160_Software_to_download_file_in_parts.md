---
title: "Software to download file in parts"
date: 2008-10-29
forum: General Help
---

### Post by harsh1kumar on 2008-10-29
We use proxy server to access internet in our college. The problem is that we cannot download files which are of the size bigger than 150 MB. So i cannot download linux distros iso's or big games. This problem can be over come by using a program which can break big files into small pieces and then download them so that the proxy server doesn't knows that a file larger than 150 MB is being downloaded. I wanted to know if there exists such a program for linux. Any comments or advices will be greatly welcome. Thanks in advance.

---

### Post by shaggy999 on 2008-10-30
Does bittorrent work on your campus? One thing you might want to check into is the manpage for 'wget'. It comes wiht ubuntu installed by default so you definitely have got it. There may be an option to tell wget to download a file in chunks.

---

### Post by harsh1kumar on 2008-10-30
Unfortunately torrents are also blocked on our campus.:(
I will try seeing the man pages of wget in the evening. Any other  advise or trick will be welcome. Thanks of the reply.:)

---

### Post by harsh1kumar on 2008-10-30
I read the man pages of wget but I didn't find anything which will solve my problem. :(

Is there any other option or software which I can use.

---

### Post by Woody1987 on 2008-10-30
If your using firefox i suggest you use the DownThemAll addon, you can download upto 10 parts so if the maximum u can download is 150MB then you sohuld be able to download a 1.5gig file.

---

### Post by harsh1kumar on 2008-10-30
I am not able to get downthemall working to download in chunks. Is there any other way??

---

### Post by harsh1kumar on 2008-10-31
Any answers ???

---

### Post by sandipb on 2008-10-31
Try d4x. It support multi parts downloads. You can play with the number of parts to suit your download size.

The alternative is to use wget/curl to get different chunks of the file. There is a accept-range http header which you can manipulate to download http sources. ftp sources can be used to download using the rest command.

---

### Post by harsh1kumar on 2008-11-01
Thanks for the reply. I will try these out

---

### Post by soro2005 on 2008-11-02
Does the proxy sniff the download size, and you cannot even request it? Because if not, you could just try starting the download until it breaks, then resume. For instance in a terminal with
```
wget ftp://download-location
```
then interrupt it with ctr+c if it gets stalled. Then resume with
```
wget -c ftp://download-location
```
I think that most of the Ubuntu mirrors should let you resume a download. You may have to install wget before you can use it.

---

