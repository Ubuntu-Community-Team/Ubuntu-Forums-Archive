---
title: "w32codecs + synaptic problem."
date: 2005-11-21
forum: General Help
---

### Post by linbetwin on 2005-11-21
I tried to install w32codecs from plf. Synaptic downloaded a small package that was supposed to download and install w32codecs. But the site (mplayer.hu or sth like that) wasn't responding so I killed Synaptic. But now whenever I try to use Synaptic or apt-get it asks me to run "dpkg --configure -a" which also tries to download w32codecs from that site. apt-get won't even let me remove w32codecs until I "dpkg --configure -a". Any suggestions?

---

### Post by linbetwin on 2005-11-21
It's mplayerhq.hu.  Is this site down?

---

### Post by teaker1s on 2005-11-21
if you have trouble finding win32 and libdvdcss2 these repositories have it
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by linbetwin on 2005-11-21
[quote=teaker1s]if yo have trouble finding win32 and libdvdcss2 these repositories have it
## FTP mirror from [http://free.fr]("http://free.fr") (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/") breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/") breezy free non-free[/quote]

That is the mirror I'm using but apt-get cannot download w32codecs. Will it try indefinitely or will it stop after a while. I want to use Synaptic for other downloads and I can't until dpkg is done.

---

### Post by linbetwin on 2005-11-21
It says:
> --21:38:44--  [http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip]("http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-all-20050412.zip")
  (try: 5) => `windows-all-20050412.zip'
Connecting to www1.mplayerhq.hu|192.190.173.45|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying

---

### Post by teaker1s on 2005-11-21
not sure of the problem but just tried w32codecs and libdvdcss2 and both installed fine. 
1)I had dns try opening source through browser not synaptic if it works you have a dns issue thats why it's not connecting. try manually setting your dns and static ip in router and ubuntu
2) backup your sources list try mine
3)find out how to dpkg purge the affected package

## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe main restricted
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by linbetwin on 2005-11-22
> I had dns try opening source through browser not synaptic The adress works in the browser. > if it works you have a dns issue thats why it's not connecting. try manually setting your dns and static ip in router and ubuntu How do I do that?
> find out how to dpkg purge the affected package I'll install the w32codecs manually. How do I purge this package, so that I can use Synaptic and apt-get again?

---

### Post by linbetwin on 2005-11-22
Solved!
sudo dpkg --purge -a
Those man-pages sure come in handy! Maybe people like me should read them more often before posting questions.

---

