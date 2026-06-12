---
title: "How to Install the downloaded Firefox 3.5 from Mozilla"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by delphiexile on 2009-07-09
Hi everybody;

I want to know how to install Firefox 3.5 that I've downloaded from the Mozilla' website , I've tried Shiretoko but I don't see the changes ; so I want to install the official one.

I unpacked the file on my desktop, I got inside the folder using the cd command , but and when I run the script run-mozilla.sh using the command 
sh ./run-mozilla.sh , an error occurs , the system tells me:

```

fethi@fethi-lab:~$ cd Desktop/firefox
fethi@fethi-lab:~/Desktop/firefox$ ls 
[COLOR="Red"]**(used that to show you that i'm in the correct folder)**[/COLOR]
application.ini             libfreebl3.so    modules
blocklist.xml               libmozjs.so      mozilla-xremote-client
browserconfig.properties    libnspr4.so      old-homepage-default.properties
chrome                      libnss3.so       platform.ini
components                  libnssckbi.so    plugins
crashreporter               libnssdbm3.so    README.txt
crashreporter.ini           libnssutil3.so   removed-files
crashreporter-override.ini  libplc4.so       res
defaults                    libplds4.so      run-mozilla.sh
dictionaries                libsmime3.so     searchplugins
extensions                  libsoftokn3.chk  Throbber-small.gif
firefox                     libsoftokn3.so   update.locale
firefox-bin                 libsqlite3.so    updater
greprefs                    libssl3.so       updater.ini
icons                       libxpcom.so
libfreebl3.chk              libxul.so
fethi@fethi-lab:~/Desktop/firefox$ sh ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

fethi@fethi-lab:~/Desktop/firefox$ sudo sh ./run-mozilla.sh
[COLOR="Red"]**(even using the sudo command , the same error occurs)**[/COLOR]
[sudo] password for fethi: 

run-mozilla.sh: Cannot execute .

```

I tried another command , I tried to run firefox-bin & firefox , but when I do that, it opens the old version of firefox.

Please help me.

Thanks.

---

### Post by zvacet on 2009-07-09
I found [this.]("http://tuxarena.blogspot.com/2009/07/how-to-install-firefox-35-in-ubuntu-904.html")I hope it will be helpful to you.

---

### Post by gradinaruvasile on 2009-07-09
Open terminal.Type:

```
cd ~/Desktop/firefox
./firefox
```

---

### Post by feb3 on 2009-07-09
Can't get that command to work. 
Like others, have 3.5 in the repository but it doesn't replace 3.0
From what I have read 3.5 doesn't replace 3.0 but comes branded as Shiretoko (Minefield 3.5 Web Browser/Browse the Bleeding Edge). Don't know if this is right, but the article said that it will be rebranded as FF 3.5 with next version of Ubuntu. Am using it now and it has all my bookmarks and preferences in it.
Please do correct me if I am wrong in this as I would prefer to have a replacement 3.5 and not two running side by side as it were.
Alternative I suppose would be to download from another source as per link above.

---

### Post by delphiexile on 2009-07-09
> **gradinaruvasile said:**
> Open terminal.Type:

```
cd ~/Desktop/firefox
./firefox
```

it runs firefox 3.0.11

---

### Post by delphiexile on 2009-07-09
I solved my problem , i had to uninstall the previous version before proceeding in the tutorial you gave , thanks.

---

### Post by darolu on 2009-07-09
> **delphiexile said:**
> it runs firefox 3.0.11

Make sure you include the ./ and that you are on the correct directory; the file you download from the website is already compiled and ready to run.

If you want to call it with "firefox" only, and make all the previous launchers to launch the 3.5 version, you'll need to change the symbolic link in /usr/bin/firefox to the path with your firefox 3.5.

In the following example, we'll asume it is on /opt/firefox/ :

```
cd /usr/bin

sudo rm firefox

sudo ln -s /opt/firefox/./firefox firefox

```

Also remember to give 755 permissions to the directory if it is outside your home folder:
```
sudo chmod -R 755 /opt/firefox
```

---

### Post by delphiexile on 2009-10-16
Thanks to all ; I solved the problem.

---

