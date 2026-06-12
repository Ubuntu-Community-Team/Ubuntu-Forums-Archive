---
title: "Lenovo N200 users rejoyce!"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by Keithamus on 2007-12-26
Hello all of you that have a lenovo n200 with the aes2501 finger print reader!

I have found a way to get it to work! A project named "fprint", which offers out of the box functionality has been made into a deb, and I tested it, and it seems to install and work fine!

If you visit here:

[http://madman2k.net/comments/105](http://madman2k.net/comments/105)

And download the tar provided, extract it, and install all of the debs included, starting with libfprint.

Then, as the article suggests, type

```
sudo gedit /etc/pam.d/common-auth
```

And then add:

```
auth    sufficient      pam_fprint.so
```

After doing this run:

```
pam_fprint_enroll
```

And scan your finger print. If done correctly you should now be able to authenticate using your finger print!

---

### Post by monkeyking on 2007-12-26
yes!
Does this also add support for the fingerprint stuff as your password on webpages?

---

### Post by Keithamus on 2007-12-27
It only works for sudo it seems, and it occasionally will not work, which seems to temporarily break gksudo, but other than that its great!

---

### Post by CazperII on 2007-12-28
I'm trying to manually compile the packages for amd64. 

Fprint_demo and libfprint are fine but the ./configure of libpam-fprint gets stuck on this:

checking security/pam_modules.h usability... no
checking security/pam_modules.h presence... no
checking for security/pam_modules.h... no
configure: error: PAM headers missing

Anyone got an idea?

---

### Post by CazperII on 2007-12-29
I found it (thx to NT3W4LK3R) it's libpam0g-dev

---

### Post by CazperII on 2007-12-29
Everything is compiled, I scanned my finger but I haven't been able to authenticate. This is the behaviour:

When i'm trying to autenticate in a console (e.g. sudo nano test): the prompt asks for password and then there's a line printed something like "Authentec AES... fingerprint scanner". But when I slide my finger across the scanner nothing happens.

Then when I logout, the login doesn't work with fingerprint, but also my usual text based log on doesn't work any more (screen freezes). I had to boot into recovery mode and comment out the line "auth    sufficient      pam_fprint.so" in /etc/pam.d/common-auth

---

### Post by codesplice on 2008-01-07
Thanks for a clear, concise howto.  I was able to get my scanner working on my HP dv6700 following your instructions :)

---

### Post by pietermeurs on 2008-01-07
it worked for me, but i can't seem to use it. 
When i give a sudo command, it says:
aes2501:error [dev_init] could not claim interface 0
fp:error [fp_dev_open] device initialisation failed, driver=aes2501

Also, loging in takes more time now.

Somebody had a clue?

---

### Post by codesplice on 2008-01-07
> **pietermeurs said:**
> it worked for me, but i can't seem to use it. 
When i give a sudo command, it says:
aes2501:error [dev_init] could not claim interface 0
fp:error [fp_dev_open] device initialisation failed, driver=aes2501

Also, loging in takes more time now.

Somebody had a clue?

Hmmm... Did you make sure to add ```
auth sufficient pam_fprint.so
``` to your /etc/pam.d/common-auth file?

Also, try repeating *pam_fprint_enroll* to see what happens.

---

### Post by pietermeurs on 2008-01-08
How do you de-install this?

---

### Post by codesplice on 2008-01-08
> **pietermeurs said:**
> How do you de-install this?

If you installed via the deb packages,

```
$ sudo apt-get remove fprint-demo libfprint libpam-fprint 
```

Should do it.  

Then make sure to
```
$ sudo nano /etc/pam.d/common-auth
```

to comment out (with a #) the line
```
auth    sufficient      pam_fprint.so
```

(Use CTRL+X to save and exit after making the change).

---

### Post by gryzzly on 2008-03-19
made everything as you guys suggest, but now i have "no devices detected" when pam_frpint_enroll
Anybody have an idea, what could happen to my fprint? *have to notice it was there, like first time i tried it actually worked.
Thanks in advance

---

### Post by Zsola on 2008-06-06
Try this thread: 
[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)
Works perfectly for my Lenovo N200. (didnt use it now, cause i still need to type in my username and an Enter after i enrolled my fingerprint, for login... but its just me)

---

