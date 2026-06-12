---
title: "Encryption - Generate Keyring Denied"
date: 2005-11-29
forum: General Help
---

### Post by brisamrus on 2005-11-29
I don't seem to be able to create a keyring with any of the GPG aplications I've tried. The error reports that it's unable to create the the file. The Gnome PGP client states an error dialogue with "Permission Denied" when trying to create the keyring files. Even trying to choose a file to open is not allowed, again directory permission is denied. Even Seahorse won't do the job. What have I done that I shouldn't have to keep all these programs from allowing me to create a keyring? Thanks.

---

### Post by ranf on 2005-11-29
[QUOTE=brisamrus]I don't seem to be able to create a keyring with any of the GPG aplications I've tried. The error reports that it's unable to create the the file. The Gnome PGP client states an error dialogue with "Permission Denied" when trying to create the keyring files. Even trying to choose a file to open is not allowed, again directory permission is denied. Even Seahorse won't do the job. What have I done that I shouldn't have to keep all these programs from allowing me to create a keyring? Thanks.[/QUOTE]
I've always found error reporting with the console client `gpg' best. And you can easily copy+paste error messages to report them here.
```
gpg --gen-key
```

---

### Post by brisamrus on 2005-11-29
Here's the error that I'm receiving...

> gpg: failed to create temporary file `/home/brian/.gnupg/.#lk0x810b888.famnet.9707': Permission denied
gpg: keyblock resource `/home/brian/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/brian/.gnupg/.#lk0x810b888.famnet.9707': Permission denied
gpg: keyblock resource `/home/brian/.gnupg/pubring.gpg': general error
Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
Your selection?


Any ideas how to get beyond this? Thanks.

---

### Post by ranf on 2005-11-30
Check permissions:
```

cd
ls -lad .gnupg/
ls -la .gnupg/

```

---

### Post by John_the_linux_newbie on 2006-03-24
Hi Guys,

I have what must be a stupid question but as my name implies "I am a Linux Newbie" 

I have Gnome PGP installed but can not figure out how to add or use a key.
I ran  gpg --gen-key in the terminal.  The program seems to have made a key.

My questions :
Where did the newly made key end up?
How do I use it?
I've used PGP with a Windows FTP client and it seems that Gnome PGP can be used to sign and encrypt data, but I'm not sure how.

---

### Post by ranf on 2006-03-25
From the description of `gpgp':
```

 More information can be found at the gpgp web site at
 http://www.geocities.com/SiliconValley/Chip/3708/gpgp/gpgp.html

 Note that the upstream is not very active.  You may like another gnupg
 frontend such as gpa or seahorse.

```

All three (gpgp, gpa and seahorse) are key managers.
You can encrypt/decrypt files in nautilus.

---

### Post by John_the_linux_newbie on 2006-03-25
Thank you for the reply.  I have seahorse and have been able to sign and encrypt files.  I attempted to send in the Ubuntu Code of Conduct, but the error I now have is that there is no public key.  I had thought that when I generated the key pair there would be a public key along with my private key.

It's always an adventure :-)

---

### Post by ranf on 2006-03-25
You need to send your public key to a key server. Seahorse does this. The key servers are a global network, so it can last a while for it to populate.

---

### Post by John_the_linux_newbie on 2006-03-26
The interesting thing is that in seahorse I see there is an option to sync and publish keys. There seem to be three default servers -MIT, Europe and another. When I select a key and click sync.  Seahorse freezes (or perhaps just takes a LONG time for any new activity to register)

Thanks again for the help.

John

---

### Post by ranf on 2006-03-26
Now that you mention this I remember that I deleted one of the servers from the preferences.
These are the two remaining ones:
- pgp.mit.edu
- keyserver.pgp.com

---

### Post by John_the_linux_newbie on 2006-03-26
Just a quick note - I managed to make a public key and uploaded the coc to launchpad.
I really like this distro.  I can type in Japanese, use Nvu to publish to my website, made a key pair, was able to connect to the secure server at work and a few other things all in the space of a weekend.
 
The CLEAR readme files, forum and friendly users makes this MUCH easier than it could be.  Thanks. :-)

---

