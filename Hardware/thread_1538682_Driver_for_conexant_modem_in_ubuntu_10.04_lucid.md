---
title: "Driver for conexant modem in ubuntu 10.04 lucid"
date: 2010-07-25
forum: Hardware
---

### Post by amp3030 on 2010-07-25
I have found how to install driver for my conexant HDA modem in my laptop. Here is how:

1. Download the modified version of the driver made by Diaco (search for it in this forum).

2. Download the latest alsa-driver from [http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/") ([this file]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip"))

3. Double click on alsa-driver-linuxant_xxxxx_all.deb and click install. It takes a while to complete.

4. Unzip the Diaco driver, open a terminal, 'cd' to the Diaco folder, and then type "sudo make install"

5. do step (3) again.

6. reboot.

That's it! :) It was actually the same as previous ubuntu versions. The only difference was that you should use the updated alsa driver from linuxant.

---

### Post by amp3030 on 2010-07-25
Remember, if you use gnome-ppp to dial, the first time you should run it as root, unless you cannot connect. I mean, you should open a terminal and type: sudo gnome-ppp

After doing it once, it is ok to run it normally.

---

### Post by amp3030 on 2010-07-27
Sorry, my previous post doesn't work! You should do this instead:

Go to System -> Administration -> Users and Groups 

Click on your username, then click on 'Advanced Setting' then go to 'User Privileges' tab. On that list check the box that reads 'Connect to Internet using a modem'

That's it.

---

### Post by zakad on 2010-08-31
> **amp3030 said:**
> I have found how to install driver for my conexant HDA modem in my laptop. Here is how:

1. Download the modified version of the driver made by Diaco (search for it in this forum).

2. Download the latest alsa-driver from [http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/") ([this file]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip"))

3. Double click on alsa-driver-linuxant_xxxxx_all.deb and click install. It takes a while to complete.

4. Unzip the Diaco driver, open a terminal, 'cd' to the Diaco folder, and then type "sudo make install"

5. do step (3) again.

6. reboot.

That's it! :) It was actually the same as previous ubuntu versions. The only difference was that you should use the updated alsa driver from linuxant.

Searching this forum for the Diaco Driver was fruitless. Extensive googling led nowhere.  Where can the "modified version of the driver made by Diaco" be found and downloaded?
Thank you in advance.

---

### Post by smonteith on 2010-09-15
> **zakad said:**
> Searching this forum for the Diaco Driver was fruitless. Extensive googling led nowhere.  Where can the "modified version of the driver made by Diaco" be found and downloaded?
Thank you in advance.

Try this link:  [http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip]("http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip")

---

### Post by vaikz on 2010-10-14
Hi, need help here on Maverick.

I was able to install successfully on lucid, but not in maverick.
I don't have problems installing the driver but have problem's configuring the modem using the hsfconfig. I get this error:
```
WARNING: missing file /lib/modules/2.6.35-22-generic/build/include/linux/autoconf.h
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).
...
Unable to prepare temporary kernel tree

First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

```How could I fix this?

---

### Post by Ganton on 2010-10-15
> **vaikz said:**
> 
```
WARNING: missing file /lib/modules/2.6.35-22-generic/build/include/linux/autoconf.h

```

The same problem happens here!

I suppose this is solved easily.

---

### Post by vaikz on 2010-10-16
yup, i think this should not be a problem now since we don't experience it from the last build.

So anybody from this community can help us?

---

### Post by Ganton on 2010-11-11
For the case of newer versions of (K)Ubuntu, please see [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

### Post by Ralph L on 2012-06-11
Has anybody been able to install a conexant winmodem in Precise Pangolin 12.04.  If so I would like some instructions.

Thanks

Ralph

---

### Post by mbuell on 2012-06-26
> **Ganton said:**
> For the case of newer versions of (K)Ubuntu, please see [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

Unfortunately, while that link takes you to a page with many other links, there is nothing there for 12.04 - and there is apparently a need for the package fixes to be version specific. Due to warnings about not using the various driver packages with a different version - I did no more than download a few of the files. However, there are also some problems with file availability and other issues. It seem Dell no longer offers their driver package, and it is the base for most of the fixes. After investing a few hours, when I still had way too many questions, I moved on and bought a pcmcia modem that I finally got to work. 

It seems that modems are a weak spot in Ubuntu's otherwise fine hardware coverage. 

If anyone has resolved the conexant chipset driver issues in 12.04, an updated post of your experience would be MOST welcome.

---

