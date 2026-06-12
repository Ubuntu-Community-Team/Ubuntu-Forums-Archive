---
title: "Latests versions?"
date: 2008-08-15
forum: General Help
---

### Post by jotacebusta on 2008-08-15
Hi all,

I often use TeXmacs, Maxima, and Lyx. The versions I've got by sudo apt-get install ... are not the more recent: I've got versions 1.0.6.11, 5.13, and 1.5.3, respectively, while these programs already have versions 1.6.0.14, 5.16, 4.5.6, respectively. 

For TeXmacs, the only solution I see is to compile it again from the sources (but I'm not sure I would like to do that... I do not feel safe).

For LyX, I only found a lyx-1.5.6-1_mandriva2008.i386.rpm package, and managed to install it (alien, gdebi...), and it seems to work. 

However, for maxima, I cannot install it. I went to sourceforge dowload page  [http://sourceforge.net/project/showfiles.php?group_id=4933&package_id=4960&release_id=619031](http://sourceforge.net/project/showfiles.php?group_id=4933&package_id=4960&release_id=619031) I downloaded 

maxima-5.16.1-1.centos4.i386.rpm 
maxima-exec-clisp-5.16.1-1.centos4.i386.rpm 
maxima-lang-es-utf8-5.16.1-1.centos4.i386.rpm 
maxima-xmaxima-5.16.1-1.centos4.i386.rpm 

and executed the sequence alien + gdebi. However when typing maxima at the terminal I obtain an error:

/usr/lib/maxima/5.16.1/binary-clisp/lisp.run: error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory

I've tried to look for something called libreadline.so.4 via synaptic, wothout any success...

If someone could help, that would be nice..

thanks

JC

p.s. Run Ubuntu 8.04 on an Inspiron 1420, centrino Cuo.

---

### Post by Vivaldi Gloria on 2008-08-16
Ubuntu takes snapshots of debian every six months and does not upgrade programs in the next six months. On the other hand there are rolling release distros like Debian Sid, PCLinuxOS etc:

[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

These update their programs all the time.

It's much better in general to use the packages in the repos because they are compiled for ubuntu and they're supported. Wait till 8.10 to get the new versions of the apps.

And to be honest, why bother with 1.6.0.14 when 1.6.0.11 is in the repos. I would understand that if it was 1.9 out there. But there is hardly any difference between 1.6.0.14 and 1.6.0.11. Same goes for Maxima and Lyx.

---

### Post by ad_267 on 2008-08-16
I think the package you need is called libreadline5.

Unless there's a feature you really need in a new version then I wouldn't worry about it. The versions in the repositories aren't usually that much older.

---

### Post by jotacebusta on 2008-08-19
Thanks,

Indeed, in maxima there are features in versions > 5.14 that I need. And I already have libreadline5.

Thanks again

JC

---

### Post by ad_267 on 2008-08-20
Oh yup it's looking for libreadline4, not 5. You can probably get away with just linking libreadline.so.4 to libreadline.so.5.

In a terminal you can do:
```
sudo ln -s /lib/libreadline.so.5 /lib/libreadline.so.4
```

If that doesn't work you could get libreadline4 from [http://packages.ubuntu.com/dapper/libreadline4](http://packages.ubuntu.com/dapper/libreadline4)

---

### Post by jotacebusta on 2008-08-20
Thanks, I hope it will work... but before going into that I need some additional help. At the Maxima's page, [here]("http://maxima.sourceforge.net/download.html"), there are some instructions. When I ran 

sudo alien maxima-exec-clisp-5.16.2-1.centos4.i386.rpm maxima-5.16.2-1.centos4.i386.rpm 

I obtained

maxima-exec-clisp_5.16.2-2_i386.deb generated
Warning: Skipping conversion of scripts in package maxima: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
maxima_5.16.2-2_i386.deb generated

Then, I should replace rpm by dkpg, right? When I do that, i obtain an error message saying that -v is an unknown option...

At tha maxima's site, they say that both rpm's depend on each other. How do I tell that to Gdebi?

Thanks a lot!

JC

---

### Post by freemath on 2008-09-16
I'm in similar situation. I need new features in the 'draw' package of maxima, which is not available in version 5.13. I uninstalled this version, then downloaded and installed the debian unstable packages for version 5.16 here:
[http://packages.debian.org/sid/i386/maxima/download](http://packages.debian.org/sid/i386/maxima/download)
[http://packages.debian.org/sid/all/maxima-share/download](http://packages.debian.org/sid/all/maxima-share/download)

There is an error message when I do 'load(draw)' but I can use all the features.

Hope this helps.

---

### Post by bdp on 2008-10-06
I suppose it's too late to get this changed, but does anyone know why Ubuntu Intrepid installs the 13 month old version 5.13 of Maxima when there have been three releases since then.

---

### Post by jotacebusta on 2008-11-14
Well... This problem is still there: I was hoping that with the new release the versions of programs like maxima or texmacs, or the tex-live distribution would be more up-to date.

I have compiled Maxima, that wasn't that hard, I've found someone very kind that helped me a lot.
In the TeXmacs user's list, people almost laugh at ubuntu users because of that problem... This program is really great but the list user's list is almost useless for anyone (like me) who is not an expert... 
In the LaTeX lists, I haven't been able to get any useful help to update pstricks... and so on.

Is there any reasonable way to tell the right person that we are having these problems?

Thakns,

JC

---

### Post by Stefan_K on 2008-11-15
Hi JC,

if you don't want to install TeX Life 2008 manually and if you don't want to wait until it's been supported you could use the MiKTeX package manager to keep your tex packages up-to-date, perhaps have a look at this installation instruction if you're interested: [_The MiKTeX Package Manager 2.7 on Ubuntu Linux_]("The MiKTeX Package Manager 2.7 on Ubuntu Linux"). Version 2.8 has already been released, coming with a GUI. I'm still using 2.7 and I'm very satisfied with it.

Stefan

---

