---
title: "Usplash problem"
date: 2008-11-30
forum: General Help
---

### Post by trendyabinash on 2008-11-30
I had been using some usplash themes in my UBUNTU 8.04
but after upgrading to 8.10 I am not ble to use them any more.
I have already re-installed them, thinking that upgradation might have corrupted them.

Please Help me out.

I am using the start-up manager to set usplash themes.

---

### Post by red_team316 on 2008-11-30
Intrepid / 8.10 usplash is THEME_VERSION 3
Hardy / 8.04 usplash is THEME_VERSION 2

What you must do is find a usplash that specifically states it will work with Intrepid. If you have access to the source code for an existing THEME_VERSION 2 usplash, then all you should have to do to get it working is rebuild the usplash on an Intrepid box.

My [parallax usplash](http://www.kde-look.org/content/show.php/Parallax+Usplash?content=89780) has both hardy and intrepid usplashes included.

---

### Post by trendyabinash on 2008-12-02
How can I distinguish?

---

### Post by red_team316 on 2008-12-02
Well for THEME_VERSION 3 your usplash package must be 0.5.22 or newer. Anything older to edgy is THEME_VERSION 2. 
[https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu](https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu)

As far as telling if a usplash will work or not, I think it's pretty much up to the usplash creator to tell you if it will work or not. Otherwise you'll just have to test it out to see if it works. No biggie, I've ran into usplashes that just plain dont work at all, regardless of the versioning. I can say that most of the usplashes you will find at this point are probably THEME_VERSION 2.


If the source code is included with the usplash download, then all you should have to do is recompile the .so file on an Intrepid box so that it will work with Intrepid or later. There should be images, a .c file, Makefile and possibly fonts included if the source is there.

apt-get libusplash-dev package for an example usplash source.

---

### Post by trendyabinash on 2008-12-03
> **red_team316 said:**
> Well for THEME_VERSION 3 your usplash package must be 0.5.22 or newer. Anything older to edgy is THEME_VERSION 2. 
[https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu](https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu)

As far as telling if a usplash will work or not, I think it's pretty much up to the usplash creator to tell you if it will work or not. Otherwise you'll just have to test it out to see if it works. No biggie, I've ran into usplashes that just plain dont work at all, regardless of the versioning. I can say that most of the usplashes you will find at this point are probably THEME_VERSION 2.


If the source code is included with the usplash download, then all you should have to do is recompile the .so file on an Intrepid box so that it will work with Intrepid or later. There should be images, a .c file, Makefile and possibly fonts included if the source is there.

apt-get libusplash-dev package for an example usplash source.
Thanks can you please tell me how to compile or create an usplash theme???

---

### Post by trendyabinash on 2008-12-03
> **red_team316 said:**
> Well for THEME_VERSION 3 your usplash package must be 0.5.22 or newer. Anything older to edgy is THEME_VERSION 2. 
[https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu](https://code.launchpad.net/~ubuntu-core-dev/usplash/ubuntu)

As far as telling if a usplash will work or not, I think it's pretty much up to the usplash creator to tell you if it will work or not. Otherwise you'll just have to test it out to see if it works. No biggie, I've ran into usplashes that just plain dont work at all, regardless of the versioning. I can say that most of the usplashes you will find at this point are probably THEME_VERSION 2.


If the source code is included with the usplash download, then all you should have to do is recompile the .so file on an Intrepid box so that it will work with Intrepid or later. There should be images, a .c file, Makefile and possibly fonts included if the source is there.

apt-get libusplash-dev package for an example usplash source.
Thanks can you please tell me how to compile or create an usplash theme???

---

