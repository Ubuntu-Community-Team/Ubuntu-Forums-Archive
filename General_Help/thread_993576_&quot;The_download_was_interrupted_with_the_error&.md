---
title: "&quot;The download was interrupted with the error:&quot;"
date: 2008-11-25
forum: General Help
---

### Post by slimjim8094 on 2008-11-25
Hi - with the latest WUBI (rev 515) the installation stops and doesn't even get to the cd-image.

Let me be more clear - after the setup (user/pass, etc) the installation freezes with an error dialog. The error listed is "The download was interrupted with the error:" and lists no error. The step at the time is "Rename: C:\ubuntu\install\MD5SUMS-metalink.gpg ->C:\ubuntu\install\MD5SUMS-metalink.asc"


The relevant portion of the %temp%\wubi-xxx.log
```
Trying remote metalink: http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
get_md5 http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.metalink
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
error; ; ; ; 
Error verifying signature: error
Trying remote metalink2: http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.metalink
get_md5 http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.metalink
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
error; ; ; ; 
Error verifying signature: error
```

Any guesses? "; ; ;" isn't a descriptive error

---

### Post by Orlsend on 2008-11-26
Have you tried with a pre downloaded ISO?

---

### Post by slimjim8094 on 2008-11-26
Yes. The error happens before it even tries to download the ISO, so it's not even being used.

---

### Post by slimjim8094 on 2008-11-26
Works on a different computer on my network... so it's just the computer's fault.

Bah, forget it - I already blew away my other partition anyway.

---

