---
title: "Opera Missing in Repositories"
date: 2008-08-14
forum: General Help
---

### Post by Jesdisciple on 2008-08-14
This applies to both the main server and the US server:```
$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
```I'm not sure if this warrants a bug-report of any kind, but I just thought I would bring it to the community's attention.  It's not a huge problem for me; I'll just download it directly.  But that stinks for the dependent package(s)...

Is this a licensing issue, or does anyone know?

---

### Post by sayakb on 2008-08-14
Download it from here: [http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by tragicglee on 2008-08-14
nevermind [doh, stupid inability to delete posts]

---

### Post by cariboo on 2008-08-14
If the Medibuntu repositories are working you can go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you followed the directions, you should be able to download and install opera with no problem.

Jim

---

### Post by Jesdisciple on 2008-08-14
Dave/LII, that's what I meant by "download it directly."

Jim, I followed those instructions, but should I uninstall the directly downloaded installation of Opera before getting the Medibuntu copy?  And how should I do that?  (Opera's instructions are for Windows.)

---

### Post by sayakb on 2008-08-14
Oh sorry, I din't read your post completely/carefully enough :)

---

### Post by Thingymebob on 2008-08-14
I'm guessing you're using 64bit ubuntu, Opera isn't available for 64bit but is still listed in the package lists (I suppose in preparation for a release) which is why you get this error.

I get exactly the same error if I try on my 64 install

---

### Post by jerome1232 on 2008-08-14
Opera has a 64 bit deb package on their site!
[http://www.opera.com/download/](http://www.opera.com/download/)

If you are running 64 bit it auto detects it and offers the x86_64 bit version

---

### Post by TransitMan on 2008-08-14
Here's the direct download link for the 64-bit Opera from Opera - [http://snapshot.opera.com/unix/snapshot-2090/x86_64-linux/opera_9.52.2090.gcc4.qt3_amd64.deb](http://snapshot.opera.com/unix/snapshot-2090/x86_64-linux/opera_9.52.2090.gcc4.qt3_amd64.deb)

---

### Post by Thingymebob on 2008-08-14
> **jerome1232 said:**
> Opera has a 64 bit deb package on their site!
[http://www.opera.com/download/](http://www.opera.com/download/)

If you are running 64 bit it auto detects it and offers the x86_64 bit version

Thanks for that I'd stopped checking at the opera site

---

### Post by Jesdisciple on 2008-08-16
No, I'm on 32-bit.  Sorry for my delay in replying, but my DSL was down.

I installed Opera from the official site, but now I want to uninstall it and install the repository version so it will automatically update.  Does anyone know how to uninstall Opera?

---

### Post by jerome1232 on 2008-08-16
If you installed it with the .deb package apt-get should be able to remove it for you. Using auto completion is your friend if your not sure of the package name :)

---

### Post by TransitMan on 2008-08-16
You can also open Synaptic, Search and type in Opera.
When you find it, highlight it and click remove. Let Synaptic do its' thing, then when you are at a clean slate, again go to Search and type Opera, highlight it and click install.
Synaptic will then install from the repos.

---

### Post by Jesdisciple on 2008-08-16
Oh, I didn't know about auto-completion (and I actually would've guessed it was something different).

Thanks!

EDIT: Woops, something is messing up.  I'll post back when I understand it better...  Please don't leave yet!

---

### Post by Jesdisciple on 2008-08-17
```
$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
[successful HTTP request]
$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[really long output with no errors]
$ sudo apt-get install opera
[original error message]
```Did I miss something at [the wiki]("https://help.ubuntu.com/community/Medibuntu")?

---

### Post by jerome1232 on 2008-08-17
try doing an apt-cache search opera and see if anything comes up.
```
apt-cache search opera
```

---

### Post by Jesdisciple on 2008-08-17
I think that output the entire list of packages, starting with arts and ending with tmsnc...?

---

### Post by motang on 2008-08-19
I do hope Ubuntu would add it back into the repos, as it's not the that hard to go download the file from Opera site it's the fact I can do with one click away in the Add or Remove or in Synaptic.

---

### Post by bobromeo on 2008-08-20
Synaptic had 9.27, removed it.
Since  yesterday 9.52 is out.
The opera selectable download page was not working, so downloaded file
[http://ftp.opera.com/pub/opera/linux/952/final/en/i386/opera_9.52.2091.gcc4.qt4_i386.deb](http://ftp.opera.com/pub/opera/linux/952/final/en/i386/opera_9.52.2091.gcc4.qt4_i386.deb)

After download gdebi-gtk opened and the message appeared that it was preferable to install the older version in the software channel (9.27)

Installed the pakage
Did some tests, an even flash worked and now also layerd iputboxes seem to be working.

---

### Post by Jesdisciple on 2008-08-20
I don't understand...  Are you just reporting that the direct download works?  I don't find 9.27 in Synaptic.

---

### Post by TransitMan on 2008-08-20
> **Jesdisciple said:**
> I don't understand...  Are you just reporting that the direct download works?  I don't find 9.27 in Synaptic.

Yes, direct download works.
I have updated/upgraded my Opera browser this way for some time, since the repos are slow in getting the updates out.

Go to the download link in the poster above and save it on your desktop or wherever you save your downloads.
Then go to the file you downloaded and double-click on it to start the gdebi-installer, follow the directions, ignore the notice of a version older in the repos and click on install.
Wait a minute or so, the installer will finish and then close it all out.

Go to the menu and depending on what version of Ubuntu you are using it will be either Network or Internet selections.

---

