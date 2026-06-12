---
title: "How to install Seamonkey Alpha 2.0 using tarballs?"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2009-02-27
Hi Guys!!

I have downloaded the setup for Seamonkey Alpha 2.0 on my Desktop.
This'll be my "First Time" to install any such software like this( Iam used to installation through repositories).

Downloaded file carries the name as "seamonkey-2.0a2.en-US.linux-i686.tar.bz2"

Please tell me on how to install the same?

---

### Post by zvacet on 2009-02-27
```
tar jxvf seamonkey-2.0a2.en-US.linux-i686.tar.bz2
```

This way you will untar file and get folder.Look inside of that folder searching for **install file**.

---

### Post by Saurabhdua on 2009-02-28
Hey Man!!

It returned an error message:

tar: seamonkey-2.0a2.en-US.linux-i686.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Please assist me further.

---

### Post by taurus on 2009-02-28
```
**cd ~/Desktop**
tar jxvf seamonkey-2.0a2.en-US.linux-i686.tar.bz2
```

---

### Post by Saurabhdua on 2009-02-28
Hey Taurus!!

Thanks Man..That worked!!

You are Great Man...!! Now I'll relish the latest & "Super Successful" release of Seamonkey!! The Best part is that it contains "Add On" Manager like other popular Mozilla Browsers. Thnks a TON from India!!

---

### Post by Saurabhdua on 2009-02-28
Hey Taurus!!

Just hold on...!! Now How do I differentiate b/w this newly installed alpha version & the one that was already installed within Ubuntu i.e. Version 1.1.12 ? Because everytime on access, it coming up with Old release only with no whereabout for this New alpha version!!??

Assist again..Please!!

---

### Post by taurus on 2009-02-28
After you unpacked seamonkey-2.0a2.en-US.linux-i686.tar.bz2 in ~/Desktop, is there a new directory that looks something like seamonkey-2.0a2.en-US.linux-i686 (or something close to that)?  Change to that new directory and post the output of this command.

```
ls -la
```

---

### Post by Saurabhdua on 2009-02-28
Yes, I do have a New Directory at the desktop only that says just "Seamonkey". Now, I couldn't very much able to understand when you say:

Change to that new directory and post the output of this command ls -la??!!

Please make that clear!

---

### Post by taurus on 2009-02-28
Now change to that new directory and post the output of the second command here.

```
cd Seamonkey
ls -la
```

---

### Post by Saurabhdua on 2009-02-28
I will do so in a short while, just updating the Security Softwares of Windows!!...Please do not feel offended by that!!

I know, in the world of Linux...who requires Gates & Windows!!..Smile!

---

### Post by Saurabhdua on 2009-02-28
Hey Taurus,,

Iam BACK...!!

Here it comes up for what you have stated, I guessed I have done that right:

saurabhdua@saurabhdua-desktop:~/Desktop$ cd seamonkey
saurabhdua@saurabhdua-desktop:~/Desktop/seamonkey$ ls -la
total 6160
drwxr-xr-x 14 saurabhdua saurabhdua   4096 2009-02-28 07:06 .
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2009-02-28 06:42 ..
-rw-r--r--  1 saurabhdua saurabhdua   2045 2008-12-02 18:08 application.ini
-rw-r--r--  1 saurabhdua saurabhdua      0 2008-12-02 18:08 .autoreg
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2008-12-02 18:09 chrome
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2009-02-28 06:46 components
-rwxr-xr-x  1 saurabhdua saurabhdua  45504 2008-12-02 18:09 crashreporter
-rw-r--r--  1 saurabhdua saurabhdua   3801 2008-12-02 18:09 crashreporter.ini
drwxr-xr-x  7 saurabhdua saurabhdua   4096 2008-12-02 18:09 defaults
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 dictionaries
drwxr-xr-x  7 saurabhdua saurabhdua   4096 2009-02-28 07:04 extensions
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 greprefs
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 isp
-rw-r--r--  1 saurabhdua saurabhdua    478 2008-12-02 18:09 libfreebl3.chk
-rwxr-xr-x  1 saurabhdua saurabhdua 292320 2008-12-02 18:09 libfreebl3.so
-rwxr-xr-x  1 saurabhdua saurabhdua   7788 2008-12-02 18:09 libgfxpsshar.so
-rwxr-xr-x  1 saurabhdua saurabhdua  48984 2008-12-02 18:09 libgkgfx.so
-rwxr-xr-x  1 saurabhdua saurabhdua  12944 2008-12-02 18:09 libgtkxtbin.so
-rwxr-xr-x  1 saurabhdua saurabhdua  78864 2008-12-02 18:09 libjsj.so
-rwxr-xr-x  1 saurabhdua saurabhdua 188624 2008-12-02 18:09 libldap60.so
-rwxr-xr-x  1 saurabhdua saurabhdua   8076 2008-12-02 18:09 libldif60.so
-rwxr-xr-x  1 saurabhdua saurabhdua 801800 2008-12-02 18:09 libmozjs.so
-rwxr-xr-x  1 saurabhdua saurabhdua 188816 2008-12-02 18:09 libmozlcms.so
-rwxr-xr-x  1 saurabhdua saurabhdua  61424 2008-12-02 18:09 libmozz.so
-rwxr-xr-x  1 saurabhdua saurabhdua 200736 2008-12-02 18:09 libnspr4.so
-rwxr-xr-x  1 saurabhdua saurabhdua 960176 2008-12-02 18:09 libnss3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 309236 2008-12-02 18:09 libnssckbi.so
-rwxr-xr-x  1 saurabhdua saurabhdua 119812 2008-12-02 18:09 libnssdbm3.so
-rwxr-xr-x  1 saurabhdua saurabhdua  77564 2008-12-02 18:09 libnssutil3.so
-rwxr-xr-x  1 saurabhdua saurabhdua  13180 2008-12-02 18:09 libplc4.so
-rwxr-xr-x  1 saurabhdua saurabhdua   8748 2008-12-02 18:09 libplds4.so
-rwxr-xr-x  1 saurabhdua saurabhdua  16688 2008-12-02 18:09 libprldap60.so
-rwxr-xr-x  1 saurabhdua saurabhdua 125644 2008-12-02 18:09 libsmime3.so
-rw-r--r--  1 saurabhdua saurabhdua    478 2008-12-02 18:09 libsoftokn3.chk
-rwxr-xr-x  1 saurabhdua saurabhdua 181776 2008-12-02 18:09 libsoftokn3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 432592 2008-12-02 18:09 libsqlite3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 160036 2008-12-02 18:09 libssl3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 786724 2008-12-02 18:09 libthebes.so
-rwxr-xr-x  1 saurabhdua saurabhdua 544864 2008-12-02 18:09 libxpcom_core.so
-rwxr-xr-x  1 saurabhdua saurabhdua  11824 2008-12-02 18:09 libxpcom.so
-rwxr-xr-x  1 saurabhdua saurabhdua 186880 2008-12-02 18:09 libxul.so
-rwxr-xr-x  1 saurabhdua saurabhdua  30826 2008-12-02 18:08 license.txt
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2008-12-02 18:09 modules
-rwxr-xr-x  1 saurabhdua saurabhdua  10804 2008-12-02 18:09 mozilla-xremote-client
-rw-r--r--  1 saurabhdua saurabhdua     52 2008-12-02 18:08 platform.ini
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 plugins
-rw-r--r--  1 saurabhdua saurabhdua   4823 2008-12-02 18:08 README
-rwxr-xr-x  1 saurabhdua saurabhdua   3152 2008-12-02 18:08 removed-files
drwxr-xr-x  6 saurabhdua saurabhdua   4096 2008-12-02 18:09 res
-rwxr-xr-x  1 saurabhdua saurabhdua  11455 2008-12-02 18:08 run-mozilla.sh
-rwxr-xr-x  1 saurabhdua saurabhdua   3926 2008-12-02 18:08 seamonkey
-rwxr-xr-x  1 saurabhdua saurabhdua  53776 2008-12-02 18:09 seamonkey-bin
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:08 searchplugins
-rw-r--r--  1 saurabhdua saurabhdua    825 2008-12-02 18:09 Throbber-small.gif
-rwxr-xr-x  1 saurabhdua saurabhdua  69704 2008-12-02 18:09 updater
-rw-r--r--  1 saurabhdua saurabhdua    302 2008-12-02 18:08 updater.ini
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2009-02-28 06:46 updates

What Next?

---

### Post by taurus on 2009-02-28
How about if you just run it from that directory since there is nothing to compile or build?

```
./seamonkey
```
If it works, then you should think about creating a launcher on the top panel so you can just click it every time you want to run it instead of running it from a terminal.

---

### Post by Saurabhdua on 2009-03-01
Man!!

Please do not take me for granted..!! I don know how come, my Profile is showing up "5 Cups of Ubuntu"?? Im very much a begineer & couldn't quite get your last instruction.Please be "More Descriptive" to pen-down each command from the very scratch!!

Here's what I got from the fact I have understood:

saurabhdua@saurabhdua-desktop:~$ . /seamonkey
bash: /seamonkey: No such file or directory
saurabhdua@saurabhdua-desktop:~$ cd ~/desktop
bash: cd: /home/saurabhdua/desktop: No such file or directory
saurabhdua@saurabhdua-desktop:~$ cd ~/Desktop
saurabhdua@saurabhdua-desktop:~/Desktop$ . /seamonkey
bash: /seamonkey: No such file or directory
saurabhdua@saurabhdua-desktop:~/Desktop$ ./seamonkey
bash: ./seamonkey: is a directory
saurabhdua@saurabhdua-desktop:~/Desktop$

Its going really awkward!...Please assist.Iam a NOVICE!

---

### Post by taurus on 2009-03-01
How about change to the right directory first, ~/Desktop/seamonkey, before you run it?

```
cd ~/Desktop/seamonkey
./seamonkey
```

---

### Post by Saurabhdua on 2009-03-02
Hi Taurus!!

This time it seems to be doing a bit, your code made Seamonkey Browser activate & then I punched in ls -la code, that came up with:

saurabhdua@saurabhdua-desktop:~/Desktop/seamonkey$ ls -la
total 6160
drwxr-xr-x 14 saurabhdua saurabhdua   4096 2009-03-01 21:07 .
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2009-02-28 23:08 ..
-rw-r--r--  1 saurabhdua saurabhdua   2045 2008-12-02 18:08 application.ini
-rw-r--r--  1 saurabhdua saurabhdua      0 2008-12-02 18:08 .autoreg
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2008-12-02 18:09 chrome
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2009-02-28 06:46 components
-rwxr-xr-x  1 saurabhdua saurabhdua  45504 2008-12-02 18:09 crashreporter
-rw-r--r--  1 saurabhdua saurabhdua   3801 2008-12-02 18:09 crashreporter.ini
drwxr-xr-x  7 saurabhdua saurabhdua   4096 2008-12-02 18:09 defaults
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 dictionaries
drwxr-xr-x  7 saurabhdua saurabhdua   4096 2009-02-28 07:04 extensions
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 greprefs
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 isp
-rw-r--r--  1 saurabhdua saurabhdua    478 2008-12-02 18:09 libfreebl3.chk
-rwxr-xr-x  1 saurabhdua saurabhdua 292320 2008-12-02 18:09 libfreebl3.so
-rwxr-xr-x  1 saurabhdua saurabhdua   7788 2008-12-02 18:09 libgfxpsshar.so
-rwxr-xr-x  1 saurabhdua saurabhdua  48984 2008-12-02 18:09 libgkgfx.so
-rwxr-xr-x  1 saurabhdua saurabhdua  12944 2008-12-02 18:09 libgtkxtbin.so
-rwxr-xr-x  1 saurabhdua saurabhdua  78864 2008-12-02 18:09 libjsj.so
-rwxr-xr-x  1 saurabhdua saurabhdua 188624 2008-12-02 18:09 libldap60.so
-rwxr-xr-x  1 saurabhdua saurabhdua   8076 2008-12-02 18:09 libldif60.so
-rwxr-xr-x  1 saurabhdua saurabhdua 801800 2008-12-02 18:09 libmozjs.so
-rwxr-xr-x  1 saurabhdua saurabhdua 188816 2008-12-02 18:09 libmozlcms.so
-rwxr-xr-x  1 saurabhdua saurabhdua  61424 2008-12-02 18:09 libmozz.so
-rwxr-xr-x  1 saurabhdua saurabhdua 200736 2008-12-02 18:09 libnspr4.so
-rwxr-xr-x  1 saurabhdua saurabhdua 960176 2008-12-02 18:09 libnss3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 309236 2008-12-02 18:09 libnssckbi.so
-rwxr-xr-x  1 saurabhdua saurabhdua 119812 2008-12-02 18:09 libnssdbm3.so
-rwxr-xr-x  1 saurabhdua saurabhdua  77564 2008-12-02 18:09 libnssutil3.so
-rwxr-xr-x  1 saurabhdua saurabhdua  13180 2008-12-02 18:09 libplc4.so
-rwxr-xr-x  1 saurabhdua saurabhdua   8748 2008-12-02 18:09 libplds4.so
-rwxr-xr-x  1 saurabhdua saurabhdua  16688 2008-12-02 18:09 libprldap60.so
-rwxr-xr-x  1 saurabhdua saurabhdua 125644 2008-12-02 18:09 libsmime3.so
-rw-r--r--  1 saurabhdua saurabhdua    478 2008-12-02 18:09 libsoftokn3.chk
-rwxr-xr-x  1 saurabhdua saurabhdua 181776 2008-12-02 18:09 libsoftokn3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 432592 2008-12-02 18:09 libsqlite3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 160036 2008-12-02 18:09 libssl3.so
-rwxr-xr-x  1 saurabhdua saurabhdua 786724 2008-12-02 18:09 libthebes.so
-rwxr-xr-x  1 saurabhdua saurabhdua 544864 2008-12-02 18:09 libxpcom_core.so
-rwxr-xr-x  1 saurabhdua saurabhdua  11824 2008-12-02 18:09 libxpcom.so
-rwxr-xr-x  1 saurabhdua saurabhdua 186880 2008-12-02 18:09 libxul.so
-rwxr-xr-x  1 saurabhdua saurabhdua  30826 2008-12-02 18:08 license.txt
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2008-12-02 18:09 modules
-rwxr-xr-x  1 saurabhdua saurabhdua  10804 2008-12-02 18:09 mozilla-xremote-client
-rw-r--r--  1 saurabhdua saurabhdua     52 2008-12-02 18:08 platform.ini
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:09 plugins
-rw-r--r--  1 saurabhdua saurabhdua   4823 2008-12-02 18:08 README
-rwxr-xr-x  1 saurabhdua saurabhdua   3152 2008-12-02 18:08 removed-files
drwxr-xr-x  6 saurabhdua saurabhdua   4096 2008-12-02 18:09 res
-rwxr-xr-x  1 saurabhdua saurabhdua  11455 2008-12-02 18:08 run-mozilla.sh
-rwxr-xr-x  1 saurabhdua saurabhdua   3926 2008-12-02 18:08 seamonkey
-rwxr-xr-x  1 saurabhdua saurabhdua  53776 2008-12-02 18:09 seamonkey-bin
drwxr-xr-x  2 saurabhdua saurabhdua   4096 2008-12-02 18:08 searchplugins
-rw-r--r--  1 saurabhdua saurabhdua    825 2008-12-02 18:09 Throbber-small.gif
-rwxr-xr-x  1 saurabhdua saurabhdua  69704 2008-12-02 18:09 updater
-rw-r--r--  1 saurabhdua saurabhdua    302 2008-12-02 18:08 updater.ini
drwxr-xr-x  3 saurabhdua saurabhdua   4096 2009-02-28 06:46 updates

---

### Post by taurus on 2009-03-02
If you want to run the new seamonkey, you have to be in ~/Desktop/seamonkey directory or you need to include the whole path.  You can create a launcher on the top panel for it if you wish.  When it asks for the command, type in

```
~/Desktop/seamonkey/seamonkey
```

---

### Post by premamotion on 2010-01-11
Hi there! I have the same problem, but with SeaMonkey 2.0.1

This is what ls -la gave me:

[html]george@george-desktop:~/Desktop/seamonkey$ ls -la
total 18068
drwxr-xr-x 16 george george     4096 2010-01-11 15:54 .
drwxr-xr-x  3 george george     4096 2010-01-11 16:29 ..
-rw-r--r--  1 george george     2123 2009-12-06 19:20 application.ini
-rw-r--r--  1 george george        0 2009-12-06 19:20 .autoreg
-rw-r--r--  1 george george     1426 2009-12-06 19:20 blocklist.xml
drwxr-xr-x  3 george george     4096 2009-12-06 19:20 chrome
drwxr-xr-x  2 george george     4096 2010-01-11 15:46 components
-rwxr-xr-x  1 george george    45912 2009-12-06 19:20 crashreporter
-rw-r--r--  1 george george     3801 2009-12-06 19:20 crashreporter.ini
drwxr-xr-x  6 george george     4096 2009-12-06 19:20 defaults
-rw-r--r--  1 george george       40 2010-01-11 15:54 description-pak
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 dictionaries
drwxr-xr-x  2 george george     4096 2010-01-11 15:53 doc-pak
drwxr-xr-x  7 george george     4096 2009-12-06 19:20 extensions
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 greprefs
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 icons
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 isp
-rw-r--r--  1 george george      478 2009-12-06 19:20 libfreebl3.chk
-rwxr-xr-x  1 george george   321140 2009-12-06 19:20 libfreebl3.so
-rwxr-xr-x  1 george george   188752 2009-12-06 19:20 libldap60.so
-rwxr-xr-x  1 george george     8076 2009-12-06 19:20 libldif60.so
-rwxr-xr-x  1 george george   839912 2009-12-06 19:20 libmozjs.so
-rwxr-xr-x  1 george george   200736 2009-12-06 19:20 libnspr4.so
-rwxr-xr-x  1 george george   863000 2009-12-06 19:20 libnss3.so
-rwxr-xr-x  1 george george   338076 2009-12-06 19:20 libnssckbi.so
-rw-r--r--  1 george george      478 2009-12-06 19:20 libnssdbm3.chk
-rwxr-xr-x  1 george george   122908 2009-12-06 19:20 libnssdbm3.so
-rwxr-xr-x  1 george george    78800 2009-12-06 19:20 libnssutil3.so
-rwxr-xr-x  1 george george    13180 2009-12-06 19:20 libplc4.so
-rwxr-xr-x  1 george george     8748 2009-12-06 19:20 libplds4.so
-rwxr-xr-x  1 george george    16688 2009-12-06 19:20 libprldap60.so
-rwxr-xr-x  1 george george   125644 2009-12-06 19:20 libsmime3.so
-rw-r--r--  1 george george      478 2009-12-06 19:20 libsoftokn3.chk
-rwxr-xr-x  1 george george   194128 2009-12-06 19:20 libsoftokn3.so
-rwxr-xr-x  1 george george   447000 2009-12-06 19:20 libsqlite3.so
-rwxr-xr-x  1 george george   160140 2009-12-06 19:20 libssl3.so
-rwxr-xr-x  1 george george   550620 2009-12-06 19:20 libxpcom_core.so
-rwxr-xr-x  1 george george    12192 2009-12-06 19:20 libxpcom.so
-rwxr-xr-x  1 george george    30826 2009-12-06 19:20 license.txt
drwxr-xr-x  3 george george     4096 2009-12-06 19:20 modules
-rwxr-xr-x  1 george george    10560 2009-12-06 19:20 mozilla-xremote-client
-rw-r--r--  1 george george      136 2009-12-06 19:20 platform.ini
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 plugins
-rw-r--r--  1 george george     4823 2009-12-06 19:20 README
-rw-r--r--  1 george george     4763 2009-12-06 19:20 removed-files
drwxr-xr-x  6 george george     4096 2009-12-06 19:20 res
-rwxr-xr-x  1 george george    10450 2009-12-06 19:20 run-mozilla.sh
-rwxr-xr-x  1 george george     3887 2009-12-06 19:20 seamonkey
-rwxr-xr-x  1 george george 13653108 2009-12-06 19:20 seamonkey-bin
drwxr-xr-x  2 george george     4096 2009-12-06 19:20 searchplugins
-rw-r--r--  1 george george      825 2009-12-06 19:20 Throbber-small.gif
-rw-r--r--  1 george george        6 2009-12-06 19:20 update.locale
-rwxr-xr-x  1 george george    67348 2009-12-06 19:20 updater
-rw-r--r--  1 george george      147 2009-12-06 19:20 updater.ini
drwxr-xr-x  3 george george     4096 2010-01-11 15:46 updates
george@george-desktop:~/Desktop/seamonkey$ 

[/html]

---

### Post by premamotion on 2010-01-11
Ok, I used a launcher! Thank you so much!

---

### Post by nanotube on 2010-01-11
you can use the ubuntuzilla repository to install seamonkey and not have to deal with manual fiddling:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

