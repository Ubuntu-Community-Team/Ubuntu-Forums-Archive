---
title: "printer installation attempt: Lexmark X5100 series (X5150)"
date: 2009-06-29
forum: Hardware
---

### Post by mpennell on 2009-06-29
I wanted to share this experience:

My friend James who is an IT professional came over to try to help me install my Lexmark X5150. Somewhere on the forum there are instructions on doing this using a certain driver (Z55). After several hours, we concluded it could not be done. His best guess is that Ubuntu users who found success must have been using earlier distros that, for some reason, worked with that driver. 

The solution we came to was to run WinXP through Virtualbox, leaving WinXP as lean as possible so as to reduce memory demand on my computer. He was able to set it up so that I can print seamlessly from Xubuntu right through to the WinXP side and to my Lexmark. How he did that, I have NO idea -- it seemed pretty complex and he was thinking creatively as he went along, so he couldn't really explain it to me as he went along. But I share this so people will know that it is possible to do that. Sorry I can't explain how.

But I wanted to share all this to help save some frustration with Lexmark-- it just doesn't work directly in ubuntu.

---

### Post by snottrag on 2009-11-05
I don't know if this was ever figured out or if it died.  I have installed Z55 to use with x5150 on 9.04.  Please message me if you still would like install that driver so you don't have to go through virtualbox.

---

### Post by KevinBrr on 2010-04-09
I don't know which version you were using at the time, but I had my Lexmark X5150 printer working on Ubuntu 9.04, and now also, with some effort, on 9.10. I will report my experience in getting my printer printing again, for people dealing with the same problem.

With the z55 driver you should be fine. Install it with the help of "[HOWTO: Lexmark Printers]("http://ubuntuforums.org/showthread.php?t=49714")" or "[HOWTO: Install Lexmark Z55 printer]("http://art.ubuntuforums.org/showthread.php?t=803958")". Probably, when checking whether the printer backend works, e.g.:

```
cd /usr/lib/backend
./z55
```you will get this error:

```
error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```After some Googling I found out that libstdc++.so.5 was replaced with a newer version in Karmic. I solved it with the instructions found on [bootstrapping.wordpress.com]("http://bootstrapping.wordpress.com/2009/11/25/missing-libstdc-so-5-in-ubuntu-9-10-karmic/"), with a little modification, which resulted in this:

```
cd /tmp

wget http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb

dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/

cd usr/lib

sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5
```Perhaps you could also try to symlink to the new libstdc 6 version, but I don't know if it will work or not. Note that after adding the libstdc++, I was not getting any output when testing the printer backend again, but this doesn't seem to be a problem.

But after this I was still getting the "could not execute a filter" / "Unable to execute /usr/lib/cups/filter/rastertoz55: insecure file permissions (0100755)" error after trying to print a testpage, which also shows up in /var/logs/cups/error_log. To solve it I followed [the advice of KIAaze]("http://ubuntuforums.org/showpost.php?p=8879393&postcount=628") and chmod'ed two files:

```
sudo chmod +x /usr/lib/cups/backend/z55
sudo chmod +x /usr/lib/cups/filter/rastertoz55
```Since it was still giving the insecure file permissions error I also chown'ed the raster file to root:

```
sudo chown root:root /usr/lib/cups/filter/rastertoz55
```It scared the hell out of me when my printer started to make noise after pushing the "print testpage" button, since I did not expect anything to happen. But it works! Now I'm the proud owner of an Ubuntu testpage, and more important, a working X5150 printer! Perhaps this information will be helpful to other people as well. 

(Please note I'm not an Ubuntu or IT professional, but just someone with a trial and error attitude, who has access to Google and some very helpful ubuntu form posts. So thanks to the ubuntu community!)

---

