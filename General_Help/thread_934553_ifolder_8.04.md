---
title: "ifolder 8.04"
date: 2008-09-30
forum: General Help
---

### Post by chrishj82 on 2008-09-30
Hi

[So far the instructions work for Hardy Heron (8.04) as well, but I could not get the forthcoming description to work...] [checkinstall seems handy, could you provide instructions for using that instead of sudo make install? 
[https://help.ubuntu.com/community/iFolderClient](https://help.ubuntu.com/community/iFolderClient)

I happen to have hardy heron.. And i get some kind of script error..

Any ideas anyone??

Thanks!

Chris

---

### Post by Partyboi2 on 2008-10-02
Follow the instructions on that page but instead of using ```
sudo make install
``` to install it use ```
sudo checkinstall
``` eg
```
./autogen.sh --prefix=/usr/local
make 
sudo checkinstall
```
You may need to install checkinstall if you have not already done so
```
sudo apt-get install checkinstall
```

Also what was the error you where getting?

---

### Post by chrishj82 on 2008-10-02
Thanks for your help!

The error I get is when doing this command

```
cd ../ifolder/
./autogen.sh --prefix=/usr/local
```

I get this error in the script

configure.in:256: error: possibly undefined macro: AM_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

So I have to make the simias script with checkinstall instead?

Regards

---

### Post by Partyboi2 on 2008-10-02
Because the error you are getting is before you would use checkinstall, you would still run into the same error, as the error is generated while you are running the ./autogen.sh process.

---

### Post by Yellow Pasque on 2008-10-02
```
sudo apt-get install gettext
```
:P

---

### Post by chrishj82 on 2008-10-04
Hi, thanks again for your time..

I got one step further now.. The scripts runs without error but when I "make" I still get this error..

make[4]: *** [iFolderClient.exe] Error 1
make[4]: Leaving directory `/home/chrishj82/ifolder/ifolder/src/LinuxClient/application'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/chrishj82/ifolder/ifolder/src/LinuxClient'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chrishj82/ifolder/ifolder/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chrishj82/ifolder/ifolder'
make: *** [all] Error 2

Thanks:)

Thinking about leaving a guide when i get it running

Chris

---

### Post by Yellow Pasque on 2008-10-04
It appears iFolder might not be maintained.
> Of what I know, you need to compile this package yourself.
A while ago I write some documentation to compile iFolder on gusty and Feisty. It's should work with minor modification on Hardy. Here the link [https://help.ubuntu.com/community/iFolder](https://help.ubuntu.com/community/iFolder). I invite you to modify this documentation if it's not working properly.
My personal recommendation would be to forget about iFolder and search another alternative, because iFolder is a death project. Nobody work on the GPL version of iFolder anymore soon.
[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

---

### Post by chrishj82 on 2008-10-05
So it seems..

This is getting a little above my skill level:) had ubuntu for a month now.

What I want is a easy way to access documents from my home computer to my office computer and vica verca.

The catch is that I can`t port forward the ip of my office computer, so remote desktop is out of question.

I have access to another computer which I was thinking about setting up as a server for ifolder.

Is there any good alternative to ifolder? And how difficult is it to set up a home server? (On a read and learn basis). I really like learning new stuff but programming is not my strongest side.

Thanks for all help! You guys are amazing

Chris

---

### Post by Partyboi2 on 2008-10-05
You could have a look at unison
[http://en.wikipedia.org/wiki/Unison_(file_synchronizer](http://en.wikipedia.org/wiki/Unison_(file_synchronizer))
[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)
[http://www.ubuntugeek.com/unison-file-synchronization-tool.html](http://www.ubuntugeek.com/unison-file-synchronization-tool.html)

Or even try rsync
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

