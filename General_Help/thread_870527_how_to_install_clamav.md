---
title: "how to install clamav?"
date: 2008-07-25
forum: General Help
---

### Post by gkjau on 2008-07-25
I tried to install with apt-get, but when i run clamscan the text "your clamav version is out-of-date" or kind of. So i downloaded a clamav source and followed this tutorial: [http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html](http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html)

When i typed make install it was shown:
Making install in libclamunrar
make[1]: Entrando no diretório `......./clamav-0.93.3/libclamunrar'
make[2]: Entrando no diretório `......./clamav-0.93.3/libclamunrar'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libclamunrar.la' '/usr/local/lib/libclamunrar.la'
/usr/bin/install -c .libs/libclamunrar.so.4.0.4 /usr/local/lib/libclamunrar.so.4.0.4
/usr/bin/install: cannot remove `/usr/local/lib/libclamunrar.so.4.0.4': Permission denied
make[2]: ** [install-libLTLIBRARIES] Erro 1
make[2]: Saindo do diretório `......../clamav-0.93.3/libclamunrar'
make[1]: ** [install-am] Erro 2
make[1]: Saindo do diretório `......../clamav-0.93.3/libclamunrar'
make: ** [install-recursive] Erro 1

What should i do?

---

### Post by DirtDawg on 2008-07-26
I don't mean to sound snarky, but I suggest giving [Avast]("http://www.avast.com/eng/download-avast-for-linux-edition.html") or [AVG]("http://free.avg.com/ww.download?prd=afl") Linux versions a try. Both are free (as in "beer"). I can't speak for AVG, but I use Avast and it works great.

EDIT: I should say why I use Avast instead of ClamAV. In my experience, ClamAV is slooooooooow. Also, I did a little research and, from what I read (take that for what it's worth), since ClamAV has no paid staff, their virus definitions are sometimes a little out of date.

EDIT2: I should also tell you that the answer to your *original* question is to install as super user (using 'sudo'):
```
sudo make install
```
:D

---

### Post by tinny on 2008-07-26
You dont really need Anitvirus software on linux. Unless you are trying to protect windows machines on your local network. (Your linux machine can be a carrier of viruses but wont be effected by them).

These are the things you should do to keep your Linux machine safe.

[https://help.ubuntu.com/8.04/keeping-safe/C/index.html](https://help.ubuntu.com/8.04/keeping-safe/C/index.html)

If you still want to use clamAV...

You really only want to use clamAV from the Ubuntu "Universe" repository. (then tested new versions will be delivered to you within the standard ubuntu updates)

1. Enable "Universe" repository.

2. 
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install clamav

```

As for the "your clamav version is out-of-date" message, I wouldnt worry about this too much. The important thing is to remember to check that your virus database is up to date.

```

sudo freshclam

```

---

### Post by hansdown on 2008-07-26
Hi gkjau. If you feel you need clamav, the easist way is to click system>administration> synaptic package manager. Use the search window, insert clamav, hit search. Please remember to click upgrade packages, then install. I hope this helps.

---

### Post by gkjau on 2008-07-26
Ok, i'll try to install avast, i didnt know the avast for linux.
Should i install avast by synaptic or apt-get?
Thank you for the help.

---

### Post by DirtDawg on 2008-07-26
> **gkjau said:**
> Ok, i'll try to install avast, i didnt know the avast for linux.
Should i install avast by synaptic or apt-get?
Thank you for the help.

Actually, I don't think Avast is in the repositories (I can't check at the moment because I'm on a Windows box). But even if it's not, it's easy to get. 

Simply hit their [download page]("http://www.avast.com/eng/download-avast-for-linux-edition.html") and there are two options for you. The first is to download the "DEB" package. After download, double click it and this will install it on your computer system-wide. Then you should be able to access Avast through the Applications menu (or maybe 'avastgui' in a command line).

The other option is to download the "tar gz" package. After download, right-click to extract the package wherever you would like, then enter the extracted directory and click the "avastgui" file to run it.

Remember either way you'll need to [register]("http://www.avast.com/eng/home-registration.php#register-form") to get a key to unlock Avast, although it is free for personal use.

And no, I am not paid by Avast to spam Linux forums :D Even though Linux doesn't need antivirus software, I recently started scanning my Windows partition from the Linux side (it tends to catch more bugs than running AV from Windows). So I just went through the whole, "which AV is best" thing about 2 weeks ago.

Good luck

---

### Post by gkjau on 2008-07-27
That's the point. i want an AV to scan windows' partition..hah
Im downloading right now...thanks for the help.

---

