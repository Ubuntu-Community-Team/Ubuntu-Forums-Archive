---
title: "Internet is so Slooow!"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by km4hr on 2005-01-28
I downloaded and installed Ubuntu this week. Overall I'm favorably impressed. However the internet connection is creeping. I've run Fedora 2 on the same machine. Internet communications were much faster. I found something in the documentation about changing an ipv6 parameter in Firefox to speed things up. That didn't help. It's not a Firefox problem. I've tried downloading files. In Fedora I get download speeds of 5 Kb/sec. In Ubuntu it's 1 Kb/sec. I'm using a dialup connection with an external modem. Any suggestions? Thanks.
xyz

---

### Post by Adrenal on 2005-01-29
I know you said it wasn't a firefox problem, but try upgrading it to 1.0
Just a thought, cos it fixed mine

---

### Post by Jad on 2005-01-29
Salam, 
I would recommend upgrading your Internet connection -:)

---

### Post by ctt1wbw on 2005-01-29
Here is a tip that someone else told me to do:

as root type this:



echo "alias net-pf-10 off" >> /etc/modprobe.conf



and then hit enter

then do this:


echo "alias ipv6 off" >> /etc/modprobe.conf



then hit enter

now for mozilla, or firefox etc u can type in the locatation bar:

about :config

then hit enter

now in the filter bar type:



ipv6



then hit enter

now double click on the value changing it from false to true

---

### Post by lukem on 2005-01-29
[QUOTE=ctt1wbw]
now for mozilla, or firefox etc u can type in the locatation bar:

about :config

then hit enter

now in the filter bar type:



ipv6



then hit enter

now double click on the value changing it from false to true[/QUOTE]

If you have difficulty with this, try     

about:config

(with no spaces)
that worked for me.

---

### Post by km4hr on 2005-01-30
Thanks to everyone for all the help. I like the Ubuntu web site and this forum. However I tried all suggestions to improve my dialup performance but nothing helped. Dialup connections were painfully slow. I'm back on Fedora now on the same computer.  Performance is drastically  improved.  Makes me wonder if anyone uses dialup with Ubuntu. How's your performance?
xyz

---

### Post by ebonflame on 2005-01-31
I use dialup with Ubuntu.... sort of.

My wife's machine is a WinXP boxen with a winmodem.  I share that dialup connection for my internet.

It's been my experience that Ubuntu is a net hog as it slows down my wife's internet connection whenever I try to do anthing on the net.  Also I noticed while using Synaptic that the downloads come in spurts.  Basically it goes for the normal download speed, then eventually slows to a standstill, then as if it was cached, the download resumes at rediculously fast speeds for dial-up, then it evens back to normal, just to start the process over again.

---

### Post by m4ng0 on 2005-01-31
[QUOTE=km4hr]...
Makes me wonder if anyone uses dialup with Ubuntu. How's your performance?
xyz[/QUOTE]

Well, I use a 56K external modem with Ubuntu, and my performance is good (as good as a dialup connection can be  :D): approx 4KB/s

---

### Post by nocturn on 2005-01-31
Maybe this has something to do with the drivers for the dialup modems.

I'm using Ubuntu on a Cable connection, and it gets exactly the same performance as my Gentoo used to get.

---

### Post by km4hr on 2005-01-31
[QUOTE=ebonflame]I use dialup with Ubuntu.... sort of.

My wife's machine is a WinXP boxen with a winmodem.  I share that dialup connection for my internet.

It's been my experience that Ubuntu is a net hog as it slows down my wife's internet connection whenever I try to do anthing on the net.  Also I noticed while using Synaptic that the downloads come in spurts.  Basically it goes for the normal download speed, then eventually slows to a standstill, then as if it was cached, the download resumes at rediculously fast speeds for dial-up, then it evens back to normal, just to start the process over again.[/QUOTE]
 ebonflame,

My experience was similar to yours. Web pages seemed to load incrementally when using dialup. First there was a long delay.   Then suddenly part of the page would appear. Then another long wait followed by quick display of another section of the page and so on.  Sometimes the web site would time out before the page was completely loaded.  It did appear that information was being held in a cache for a long time and then suddenly released.

---

### Post by geofff on 2005-02-06
I suffered for weeks and weeks. Pure agony. I tried fixes suggested re IPv6 (see [www.ubuntuguide.org#disableipv6-mozilla](www.ubuntuguide.org#disableipv6-mozilla)) but this had little effect.

Just today I have discovered [www.ubuntulinux.org/wiki/DialupModemHowto](www.ubuntulinux.org/wiki/DialupModemHowto)

My problems are over! this is ecstasy! suggest you try it. Good luck.

---

### Post by Adler on 2005-02-06
ctt1wbw,

Thanks for your post. I still use dial-up, but also Wireless and Ethernet, and notice that things have indeed gotten faster after following your instructions.

Thanks again!

---

### Post by ctt1wbw on 2005-02-06
Glad I could help.  Not often I can be somewhat of a Linux guru and help OTHERS...  :)

---

### Post by Titanium on 2005-02-28
[QUOTE=ebonflame]It's been my experience that Ubuntu is a net hog as it slows down my wife's internet connection whenever I try to do anthing on the net.  Also I noticed while using Synaptic that the downloads come in spurts.  Basically it goes for the normal download speed, then eventually slows to a standstill, then as if it was cached, the download resumes at rediculously fast speeds for dial-up, then it evens back to normal, just to start the process over again.[/QUOTE]
I just want to confirm that this is definitely seems to be some kind of a bug, because I am experiencing this exact same behavior.

I did follow the instructions in the modem howto, actually that's the way the connection was set up at the beginning, because I needed to update the graphic drivers to make X work.

Those of you who got improvement, what exactly did you do?

---

### Post by Mustard on 2006-02-09
I found that if you configured dialup using the System>>Administration>>Networking and used the 'activate', and 'deactivate' to start the dialup session then the connection was very slow.  I disabled the setup in the Networking options, and setup the dialup connection using the wiki HOW TO mentioned earlier.  Using the pon command I connected and then installed gnome-ppp which is a pretty easy to use graphical interface for dialup connections.  I think its the System>>Administration>>Networking method of doing things that doesn't seem to work too well with dialup connections.

---

