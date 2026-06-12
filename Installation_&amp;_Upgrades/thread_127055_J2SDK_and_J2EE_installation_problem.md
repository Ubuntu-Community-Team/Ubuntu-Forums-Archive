---
title: "J2SDK and J2EE installation problem"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-02-08
HI,

I am trying to install j2sdk and j2ee, but i encounter problem. on sun website, stated that j2sdk should be installed prior to j2ee... j2re 1.5 has been installed already. I encounter such error before and fix by adding PLF on repositoeries. Now, I encounter this error again even if the repo is there. 

Below are the error i counter:
wizz@wizzl:~$ fakeroot make-jpkg j2sdk-1_4_2_10-nb-4_1-linux-ml.bin
Creating temporary directory: /tmp/make-jpkg.XXXXjRlHRN
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

and...

wizz@wizzl:~$ fakeroot make-jpkg j2eesdk-1_4_03-linux.bin
Creating temporary directory: /tmp/make-jpkg.XXXXuyUUm6
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

Here's my repo for reference:
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team
## Official backports
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse  

## Security Updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 

#KDE 3.5 Upgrade (Breezy)
deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main 

## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free 

## Ubuntu China
deb [http://archive.ubuntu.org.cn/ubuntu-cn/](http://archive.ubuntu.org.cn/ubuntu-cn/) breezy main 

My System:
Dell Inspiron 700m
Kubuntu 5.10 Breezy

Hope you could help.

Thanks.

---

### Post by wizzkid on 2006-02-08
any help?

---

### Post by hod139 on 2006-02-08
Since you have added the PLF repositories, you should be able to simple do:
```

sudo apt-get install sun-j2sdk1.5

```

The sdk I believe comes with a runtime environment, if not you can also install 
```

 sudo apt-get install sun-j2re1.5
 
```

---

### Post by wizzkid on 2006-02-09
Thanks it worked... how about the j2ee? :) can I use PLF also?  By the way, how would i know what software i can install using the PLF repository? or the list of software, I visit [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf) but i ant understand since in french languange.

For curousity sake, whats the difference between deb and deb-scr. I assume scr is source? what make it difference with deb?

Hope you could give me suggestions heres.

Thanks

---

### Post by hod139 on 2006-02-09
I don't know of any j2ee ubuntu package, you may have to install that one manually. Sun has its own installer, you will just lose some of the nice package integration benefits.

The link for PLF you posted isn't in french for me!  From their website the list of packages is:

> 
**Multimedia**
[LIST]
[*] w32codecs: A package of codecs needed to play multiple formats, notably DivX. (disponible. Maintainer: MirSPCM)
[*] RealPlayer: Stream player (disponible. Maintainer: keyes)
[*] libdvdcss2: The library needed to play back encrypted DVDs.(Disponible. Maintainer: MirSPCM)
[*] Xdtv: [http://xawdecode.fr.st]("http://xawdecode.fr.st/") - Tv viewer and recorder, the dependancies, and plugins like plug-m (Maintainer: Stéph)
[*] Free-Go and [FreePlayer]("http://doc.ubuntu-fr.org/doc/freeplayer"): logiciels pour freenautes exclusivement (and Linux compatible FreePlayer mods: Homeplayer, FreeMode)
[*] autopano-sift: [http://freshmeat.net/redir/autopano-sift/47274/url_homepage/autopano-sift]("http://freshmeat.net/redir/autopano-sift/47274/url_homepage/autopano-sift") - Panorama Image compositor (Disponible dans [Marillat]("http://doc.ubuntu-fr.org/doc/plf/marillat"), Maintainer: Stéph))
[*] hugin: [http://hugin.sourceforge.net/]("http://hugin.sourceforge.net/") - you can assemble a mosiac of photographs into a complete immersive panorama, stitch any series of overlapping pictures and much more.
[*] Divx4Linux: [http://www.divx.com/divx/linux/]("http://www.divx.com/divx/linux/") - Read and create DivX (Période de test. Maintainer: Stéph)
[*] Varsha: [http://varsha.sourceforge.net/]("http://varsha.sourceforge.net/") - make DVD slideshows, videos, and interactive menus.
[*] dir2ogg: [http://badcomputer.org/unix/dir2ogg/]("http://badcomputer.org/unix/dir2ogg/") - Converts mp3, m4a, and wav files into ogg-vorbis format  (Maintainer: Stéph)
[*] dvdstyler: [http://dvdstyler.sourceforge.net/]("http://dvdstyler.sourceforge.net/") - DVD Authoring System  (Maintainer: Stéph)
[*] kmplayer: [http://kmplayer.kde.org/]("http://kmplayer.kde.org/") - a working player for KDE  (Maintainer: Stéph)
[*] kplayer: [http://kplayer.sourceforge.net/]("http://kplayer.sourceforge.net/") - a working player for KDE  (Maintainer: Stéph)
[*] K9Copy: [http://k9copy.free.fr/]("http://k9copy.free.fr/") - a small utility which allows the copying of DVDs on Linux.(  )
[*] XDVDShrink: [http://dvdshrink.sourceforge.net/]("http://dvdshrink.sourceforge.net/") - allows you to create fair-use archival copies of DVD content on single-layer writable DVDs.(  )
[*] Sharpmusique: [http://www.nanocrew.net/software/sharpmusique/]("http://www.nanocrew.net/software/sharpmusique/") - iTunes music store frontend, already packaged by the author, for Ubuntu Breezy here: [http://www.nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb]("http://www.nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb")[/LIST]  
   **System Utilities**
[LIST]
[*] Sun JRE: The Java Run Time Environment by Sun, and the SDK  (Disponible. Maintainer: keyes)
[*] Hot Babe: - [http://dindinx.net/hotbabe/]("http://dindinx.net/hotbabe/") - Hot-babe is a small graphical utility which displays the system activity in a very special way. (Herbie: [http://dindinx.net/hotbabe/debs/hot-babe_0.2.1-1_i386.deb]("http://dindinx.net/hotbabe/debs/hot-babe_0.2.1-1_i386.deb") works perfectly under Breezy)[/LIST]  
   **Networking**
[LIST]
[*] Freenet: Secure Network over internet
[*] Enthropy: Secure Network over internet
[*] Waste: [http://waste.sf.net/]("http://waste.sf.net/") Secure Network over internet
[*] Skype: [http://skype.com/]("http://skype.com/") - A free Voice Over IP software - Package imported from Skype.com and corrected to work fine on Breezy (Maintainer: keyes)
[*] Opera: [http://opera.com/]("http://opera.com/") - A powerful browser - Package directly imported from opera.com (Maintainer: keyes)
[*] Azureus: [http://azureus.sourceforge.net/]("http://azureus.sourceforge.net/") - A BitTorrent client (Available in the [Extras]("http://backports.ubuntuforums.org/"))
[*] Gizmo Project: [http://www.gizmoproject.com/]("http://www.gizmoproject.com/") - A free voice over IP software - Package provided by the Gizmo Project ([http://www.gizmoproject.com/download-linux.html]("http://www.gizmoproject.com/download-linux.html"))[/LIST] 

The difference between deb and deb-src is exactly what you assumed, the src package contains the source code for the project.  The .deb associtated with the project will not install the source code, only the binaries.

---

### Post by bites on 2006-02-09
What do you mean with installing J2EE?  AFAIK, the Sun J2EE SDK is merely a bundle of some applications, of which each can be installed separately.  Basically, all you need is J2SE 5.0 SDK (the SDK already contains the JRE!) and an application server, such as Sun Java System Application Server Platform Edition 8.2.  Both of these are in the J2EE bundle, together with the API documentation (which is available online) and a bunch of samples.  I didn't install any of these using the standard Debian / Ubuntu packaging system as they're easy enough to install by themselves.  Just have a look at [Sun's download page]("http://java.sun.com/j2ee/1.4/download.html").

---

