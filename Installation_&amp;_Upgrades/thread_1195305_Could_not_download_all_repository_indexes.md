---
title: "Could not download all repository indexes"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by rhythmiccycle on 2009-06-23
i'm using a public network at my work.

i'm trying to add some software sources.
i've done this from my home with out any problem.

when i was trying to do this at work, i got this message

> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


and then

> 
GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDDFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.


i know this is because of the security on the network i'm on.

my question is,

is there a was to get these file from the network?

OR

is there a way for me to get the files from my home and bring them to work?

---

### Post by jerrrys on 2009-06-25
you need to add pubkey 

The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDDFailed to fetch

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=MGd&num=30&newwindow=1&ei=4vtDSoeBPIjssQPvztnfDQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=no_pubkey+ubuntu&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=MGd&num=30&newwindow=1&ei=4vtDSoeBPIjssQPvztnfDQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=no_pubkey+ubuntu&spell=1)

---

### Post by raymondh on 2009-06-25
to add pubkey, in terminal, one at a time :


```
gpg --keyserver subkeys.pgp.net --recv CFF71CB3AFA44BDD 
gpg --export --armor CFF71CB3AFA44BDD | sudo apt-key add -
sudo apt-get update
```

Note : I already added the pub key you needed (i.e. CFF....)

---

### Post by rhythmiccycle on 2009-06-26
i added the public key using raymondhenson code. thanks for that.

and that fixed some of the errors, but not all of them.

my main goal is to get TOR working on this computer. I have it running on my laptop just fine. I would like it to run on the desk top computer at my work.

The network security really gets on my nerves, it stops me from doing important things, such as downloading printer drivers. Thats is why i want to get TOR running

i need to add this:

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

I have some new errors, now that i have a public key

> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and then
> 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.


I also tried to update the "Add/Remove Applications" just to see if that works, and i got the same "Could not download all repository indexes" with this under it
> 
ailed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by raymondh on 2009-06-26
Hi,

Am browsing through the community documentation for TOR and I noticed that it requires a different key.  You may want to try it.

```
gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

And if you don't have it yet installed

```
sudo apt-get install tor
```

The deb repos look good.

Link for your reference:

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

I don't use TOR hence do not know if the repo is active or not. Good luck.

---

### Post by rhythmiccycle on 2009-06-26
i was already using the page that "raymondhenson" is refering to.

and it worked when i set it up on my laptop at my house, and then brought it back in to work.

but you are talking about the second step.

i have to add the sources first:

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

but those sources seem to be blocked.

I think that if i could put those sources onto a cd or usb drive from my house and then bring it to work, i could install tor.

but i don't know how to do that.

BTW: i tried just ignoring the fact that the sources didn't add, and just moved on.

i'm not going to include everything here is some of what happens

> $ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg: requesting key 94C09C7F from hkp server subkeys.pgp.net
gpg: key 94C09C7F: "Peter Palfrader" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


and

> 40% [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US


and

> E: Some index files failed to download, they have been ignored, or old ones used instead.

and

> E: Couldn't find package tor

---

