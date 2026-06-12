---
title: "How to install gyachi 1.1.26 on gutsy"
date: 2008-09-24
forum: General Help
---

### Post by rfrayer on 2008-09-24
unfortunately because of the pulse adio thing you cant install 1.14 on gutsy no big loss though personally i like alsa-base the best


First install the dependancees
```

sudo aptitude install build-essential automake libtool libgpgme11-dev libmcrypt-dev libnotify-dev libcurl4-openssl-dev libgtkhtml2-dev libjasper-dev imagemagick xmms-dev checkinstall
```

Now download gyachi 

```
wget http://ftp.heanet.ie/disk1/sourceforge/g/gy/gyachi/gyachi-1.1.26.tar.gz

tar -zxvf gyachi-1.1.26.tar.gz

cd gyachi-1.1.26

./autogen.sh

./configure --disable-rpath --enable-maintainer-mode --prefix /usr --enable-v4l2

make

sudo checkinstall --install=no

```

type y for the answer then click enter for everything else

```
mv gyachi_1.1.26-1_i386.deb ~/Desktop

cd $HOME

rm gyachi-1.1.26.tar.gz

sudo rm -rf gyachi-1.1.26

cd ~/Desktop

sudo dpkg -i gyachi_1.1.26-1_i386.deb 
```


Do you have win32 codecs installed for voice if no heres what i did but you can get the basics from medubuntu


```
cd $HOME

wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2

sudo mkdir -pv /usr/local/lib/codecs

tar xjvf all-20071007.tar.bz2

sudo cp -v $HOME/all-20071007/* /usr/local/lib/codecs

sudo ln -s /usr/local/lib/codecs /usr/lib/codecs

sudo ln -s /usr/local/lib/codecs /usr/local/lib/win32

sudo ln -s /usr/local/lib/codecs /usr/lib/win32

rm all-20071007.tar.bz2

sudo rm -rf all-20071007
```

---

### Post by rfrayer on 2008-09-25
i did some more research it seems yahoo patched the cookie on the captcha code on entering rooms.. long story short means that you will need a new captcha each rooom. here is a fix below download this and unzip and copy and replace the file in gyachi-1.1.26/client folder  basicly the cookie settinsg for captcha have been changed to null

---

### Post by loell on 2008-09-25
howdy, i don't mean to trample your efforts, its a good start. :)

i do have though a 1.1.31 build for gutsy, captcha included.

[http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")

---

