---
title: "Forum rules"
date: 2008-09-05
forum: General Help
---

### Post by shahin on 2008-09-05
Greetings-
   I am running into some issue with install JAVA docs, and went to the developer forum, and tried to post the error, but I do not get the option for "post a new thread" like I do for other forums.  Do I have to have some other type of privilege to post there?   btw here is the error I get...

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1

:confused:

---

### Post by wolfen69 on 2008-09-05
just do: ```
sudo apt-get install sun-java6-doc
``` make sure all your repos are enabled in software sources first.

---

### Post by jamesstansell on 2008-09-06
> **shahin said:**
> Greetings-
   I am running into some issue with install JAVA docs, ...   btw here is the error I get...

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1

:confused:

The sun-java6-doc package isn't a normal package.  It's a 'wrapper' package that doesn't include the actual files.  Instead it depends on you to provide them, then it moves them into place and marks them as installed.  If you later uninstall it then the files will be automatically removed.

What you saw isn't really an error message as much as an informational reminder.  It's telling you exactly what you need to do to provide the files it needs.

To re-phrase: you need to download one of the specified zip files and put it in /tmp.  Make it owned by the root user and the root group.  Then run the install command.

Frankly, I never mess with this package anymore.  In fact there are so many people reporting 'errors' that I believe it would be better if the package was removed from the repository.

If you want the docs installed from a package, look at the openjdk-6-doc package.  It _does_ include the files (because Sun relicensed them) and although I'm not positive that they are identical to the ones in the zip file that you can download, I consider them sufficient.  In fact, there's a good chance that they're improved over the ones from the zip download file.

---

### Post by shahin on 2008-09-06
This was a great explanation.  I do have a couple of other questions please:

I know this is a trivial question, but how do I make a file owned the root please?  I know it is the username.  I do "sudo apt-get -install openjdk-6-doc" and authenticate just fine.  But I still get the same error.

Also once I install the package you suggested, how do I remove the previous file from the list of files that synaptic would install?  Seems that file is in Synaptic, and every time I have a new request, it tries to install the previous unsuccessful attempts also.

---

### Post by jamesstansell on 2008-09-08
try```
sudo apt-get remove sun-java6-doc
```

---

### Post by Scunge on 2008-09-08
> **shahin said:**
> I know this is a trivial question, but how do I make a file owned the root please?  I know it is the username.
```
sudo chown root:root *filename*
```
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

