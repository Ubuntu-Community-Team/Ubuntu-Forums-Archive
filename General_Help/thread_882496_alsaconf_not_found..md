---
title: "alsaconf: not found."
date: 2008-08-07
forum: General Help
---

### Post by Sinkingships7 on 2008-08-07
In Ubuntu, I can get sound. That works by default without any configuring. However, my motherboard comes with built-in realtek HD audio. In order to be able to use the HD feature of my on-board audio, I need to install the Linux HD realtek drivers.

When I go to do this, everything seems to work fine until the end when it spews this error message forth and exits the installation:
```
./install: 101: alsaconf: not found
```

I've done tons of searching on the matter, and it would seem that alsaconf has been omitted from the both the repos and the default Ubuntu install due to crashing another program.

Does anybody know where I can find alsaconf, or if there is another workaround to this problem?

---

### Post by fuzzyk.k on 2008-08-07
alsaconf is not included in ubuntu try and get the deb from debian lenny repos or build it from source

---

### Post by cdtech on 2008-08-07
You need to have the "alsa-utils" installed which includes the "alsaconf"

---

### Post by Sinkingships7 on 2008-08-07
[QUOTE=cdtech]You need to have the "alsa-utils" installed which includes the "alsaconf"[/QUOTE]
As I stated, alsaconf is no longer included with alsa-utils. Besides, I already have alsa-utils installed.
[QUOTE=fuzzyk.k]alsaconf is not included in ubuntu try and get the deb from debian lenny repos or build it from source[/QUOTE]
I'm going to keep searching, but I haven't been able to find it yet. If you'd be so inclined as to provide me with a link, I'd be most grateful.

---

### Post by fuzzyk.k on 2008-08-07
sorry it seems to no longer exist on debian according to 
[https://bugs.launchpad.net/alsa-utils/+bug/29597](https://bugs.launchpad.net/alsa-utils/+bug/29597)

sorry bout that
thanks

---

### Post by vnluc on 2009-11-06
I got this message  "alsaconf: command not found" too

As alsaconf is now not available under Ubuntu, what should I do? can someone give us instruction?

---

### Post by vnluc on 2009-11-07
The download is here:

[http://www.realtek.com.tw/DOWNLOADS/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/DOWNLOADS/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Now I can ./configure
make
make install

but the   alsaconf command fail & I still can not use Audio.

Now I can see the audio icon in the Panel but in Sound Preference -> hardware tab, I see no devices. Can you suggest?

---

### Post by mjjna on 2009-11-08
I have exactly the same problem...

---

### Post by mjjna on 2009-11-08
ok, I've installed alsa 1.0.21, following this procedure:

[http://monespaceperso.org/blog/2009/11/01/mise-a-jour-de-alsa-1-0-21-sous-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog/2009/11/01/mise-a-jour-de-alsa-1-0-21-sous-ubuntu-karmic-koala-9-10/)


(If you don't speak french, just type all commands except the "sudo ln -s" things, that is only if you have the " configure: error: panelw library not found" problem.


The hardware reappeared in the sound preferences.

And I can now type alsaconf, and my sound card is recognized.

(But the strange part is that i still have the 1.20.0 version installed according to the command cat /proc/asound/version ...)

---

### Post by vnluc on 2009-11-09
It's ok for me now:
Here are what I do:
cd  alsa-driver-1.0.21
sudo ./configure
sudo make
sudo make install
sudo ./snddevices

---------------
then use command      
alsamixer 
to check the volume, I see I can scroll the Master Volume.

Go to: System-> Preferences -> Sound
check that volume for Hardware, Output and Application tab are not muted. (volume must be greater than zero).

Go and test some music.

---

### Post by stalis on 2009-11-13
> **mjjna said:**
> ok, I've installed alsa 1.0.21, following this procedure:

[http://monespaceperso.org/blog/2009/11/01/mise-a-jour-de-alsa-1-0-21-sous-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog/2009/11/01/mise-a-jour-de-alsa-1-0-21-sous-ubuntu-karmic-koala-9-10/)


(If you don't speak french, just type all commands except the "sudo ln -s" things, that is only if you have the " configure: error: panelw library not found" problem.


The hardware reappeared in the sound preferences.

And I can now type alsaconf, and my sound card is recognized.

(But the strange part is that i still have the 1.20.0 version installed according to the command cat /proc/asound/version ...)


There is an english version on his page you just click the link above his picture that says "English" and it will take you here:

[http://monespaceperso.org/blog-en/](http://monespaceperso.org/blog-en/)

---

