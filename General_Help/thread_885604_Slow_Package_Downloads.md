---
title: "Slow Package Downloads"
date: 2008-08-10
forum: General Help
---

### Post by discoboy on 2008-08-10
I'm having some trouble downloading packages.  Whether I do it from add/remove, synaptic or the terminal my speed is usually less than a kb/s.  I thought it might be a problem with the server so I tried switching to the general Ubuntu server with no effect.

My speed on everything else is fine.  Web browsing and moving files on my network is excellent and bittorrent seems to average about 200 kb/s without me doing any tweaking.

My first guess is that it is some kind of port blocking issue, does anyone have any advice or similar experience?

---

### Post by Sycron on 2008-08-10
You may try your speed by downloading a file with wget.

```
$ wget http://path.com/to/file.bin
```
With this you may see if it is a problem with your connection or ubuntu servers....

---

### Post by geenux on 2008-08-10
You can try to select the better server :
Go to System->administration->software sources
Then in the first tab, click on the list "download from", and select other.
Then click on "select best server".

---

### Post by discoboy on 2008-08-10
> **Sycron said:**
> You may try your speed by downloading a file with wget.

```
$ wget http://path.com/to/file.bin
```
With this you may see if it is a problem with your connection or ubuntu servers....

I get a 404 error

--09:50:18--  [http://path.com/to/file.bin](http://path.com/to/file.bin)
           => `file.bin'
Resolving path.com... 72.32.187.133
Connecting to path.com|72.32.187.133|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:50:18 ERROR 404: Not Found.

---

### Post by Sycron on 2008-08-10
It is normal that error :). Find a file on the net and download it... for example try this:

```
wget http://www.linuxfortravelers.com/files/ubuntu_gimp.png
```

and tell us what average speed do you have. You may try what geenux sayd.

---

### Post by discoboy on 2008-08-10
Alright, I tried both pieces of advice.  After trying a server switch again I ran wget. It says my average download rate is 945 kb/s.  Afterwards I tried downloading a few packages.  I found that initially I get good speed, 100-200 kb/s according to synaptic, but this only lasts for literally one or two seconds.  After that it's back down to the usual <1kb/s.

---

### Post by dexter.deepak on 2008-08-10
open the system -> admin -> software sources and choose some other location for downloading the packages.

---

### Post by discoboy on 2008-08-10
Alright, after changing servers a few more times I've gone to an ftp.  My rates are now going quit fast.  Are all the servers ftp or just the ones listed as such?  If so is the switch to an ftp what caused my speed increase?

---

### Post by dexter.deepak on 2008-08-10
> **discoboy said:**
> Alright, after changing servers a few more times I've gone to an ftp.  My rates are now going quit fast.  Are all the servers ftp or just the ones listed as such?  If so is the switch to an ftp what caused my speed increase?

i think its just a matter of chance, in future your problem maybe automatically solved. ftp servers are not in general faster than http ones, but there maybe some anonymous problems.

---

### Post by MidiJake on 2008-11-21
> **geenux said:**
> You can try to select the better server :
Go to System->administration->software sources
Then in the first tab, click on the list "download from", and select other.
Then click on "select best server".
That worked for me... thanks very much.

---

