---
title: "Flash Player"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by pconn5 on 2009-03-09
I was just wondering if anybody else is having trouble downloading and installing adobe flash player. If I try to do sudo apt-get install flashplugin-nonfree the install just gets hung up and will never finish. Also if I go to the site and try to download the .deb file from the site. The download will not start. I think this is a problem with Adobes site not downloading properly or something. If anyone has the .deb file for adobe flash player that can post it or something that would be great.

---

### Post by Neo_The_User on 2009-03-09
Use the tar.gz for linux and build.

---

### Post by avtolle on 2009-03-09
> **pconn5 said:**
> I was just wondering if anybody else is having trouble downloading and installing adobe flash player. If I try to do sudo apt-get install flashplugin-nonfree the install just gets hung up and will never finish. Also if I go to the site and try to download the .deb file from the site. The download will not start. I think this is a problem with Adobes site not downloading properly or something. If anyone has the .deb file for adobe flash player that can post it or something that would be great.
Question(s): Are you using 64-bit or 32-bit Ubuntu? Are you on a pre-intel Mac with a ppc chip? If the answer to the second question is in the affirmative, you're not going to be able to install Flash.

---

### Post by Neo_The_User on 2009-03-09
> **avtolle said:**
> Question(s): Are you using 64-bit or 32-bit Ubuntu? Are you on a pre-intel Mac with a ppc chip? If the answer to the second question is in the affirmative, you're not going to be able to install Flash.

Flash doesn't support PowerPCs?

---

### Post by avtolle on 2009-03-09
> **Neo_The_User said:**
> Flash doesn't support PowerPCs?
For ppc on linux, no (at least not any "modern" version). If you know better, post on the Apple Users Forum; there will be a large number of very happy users who might build an altar and sacrifice a goat in your honor....

Seriously, what the ppc community (linux ppc community, and more specifically Ubuntu and its variants, as this is all I can directly comment upon) has learned is to use either gnash or swfdec for some limited Flash support (works sometimes, usually doesn't at all or just partially); or, download youtube videos via the Firefox add-on, the play the extracted video on a media player.

---

### Post by Neo_The_User on 2009-03-09
I always had a bad experience with gnash. Anything but that. But I haven't tried anything but gnash and abobe flash.

---

### Post by avtolle on 2009-03-09
Understand your bad experience with gnash. To anyone interested, see [https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash]("https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash") for the current status of Flash in ppc Ubuntu.

EDIT: The reason I posed the second question to the OP was the description of the difficulties encountered echoed many a thread on the Apple Forum I've read in the past two plus years, and a bit of personal experience "back in the day".

---

### Post by pconn5 on 2009-03-09
Thanks for the replies. No I am not on a Mac. I have tried to download the .tar.gz file for linux but it will not download from the adobe site for some reason. If I had the file I believe it should work but I cannot download it.

---

### Post by avtolle on 2009-03-09
RE: download problems. Are you stuck behind a proxy? If downloading (or trying to download) at your work site, is there some policy that proscribes downloads from sites "not authorized"?

---

### Post by chicozoo on 2009-03-09
Hello,

I'm having a hard time installing flash 10 on 8.04 32bit. When I use the package installer I get "error: dependency is not satisfiable: libpango1.0-0" Can anyone help?

Thanks

---

### Post by Neo_The_User on 2009-03-09
> **chicozoo said:**
> Hello,

I'm having a hard time installing flash 10 on 8.04 32bit. When I use the package installer I get "error: dependency is not satisfiable: libpango1.0-0" Can anyone help?

Thanks

Yes. Open up a terminal and copy and paste the following command

```

sudo apt-get install libpango1.0-0 libpangomm-1.4-1 libpango1.0-common

```

---

### Post by chicozoo on 2009-03-09
Didn't work. This is what I got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
E: Couldn't find package libpangomm-1.4-1

Sorry, Im new to all this.

---

### Post by Neo_The_User on 2009-03-09
> **chicozoo said:**
> Didn't work. This is what I got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
E: Couldn't find package libpangomm-1.4-1

Sorry, Im new to all this.

Sorry take out libpangomm-1.4-1 because that application is in 8.10. I didn't see you are using 8.04. My mistake.

---

### Post by pconn5 on 2009-03-09
I'm not stuck behind a proxy. This problem occurs even when I tried to download on my other computer running windows so I am not sure why it won't download. The download starts and freezes at .2% then won't continue. Can someone try and download the .deb file from the adobe site for me and see if it works?

---

### Post by Neo_The_User on 2009-03-09
Try using wget.

Terminal:

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz

```

or...

```

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
sudo dpkg -i install_flash_player_10_linux.deb

```

View the README.

---

