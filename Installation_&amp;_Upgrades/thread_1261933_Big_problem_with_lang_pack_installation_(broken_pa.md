---
title: "Big problem with lang pack installation (broken packages)"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by francoise_peace on 2009-09-09
Hello ! I have tried everything to solve this message:

E: /var/cache/apt/archives/language-pack-kde-fr_1%3a9.04+20090803.2_all.deb: trying to overwrite `/usr/share/locale-langpack/fr/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-fr
E: /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb: trying to overwrite `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-pt

The problem is with french and portuguese languages. Packages are broken and still broken even when re-installed.
[FONT=Times New Roman]
[SIZE=2]sudo apt-get -f install[FONT=monospace]
[/FONT]sudo dpkg --configure -a[/SIZE][/FONT]
sudo apt-get build-dep language-pack-kde-fr
delete and re-install from Synaptics the fr and pt_BR broken packages
delete and re-install portuguese and french language from ubuntu 9.04
re-install libgstreamer-plugins-base (which has no problem)

francoise@Charmmy-Kitty:/$ locate phonon_gstreamer.mo/usr/share/locale-langpack/el/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/fr/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/it/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/ja/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/zh_CN/LC_MESSAGES/phonon_gstreamer.mo
/usr/share/locale-langpack/zh_TW/LC_MESSAGES/phonon_gstreamer.mo
francoise@Charmmy-Kitty:/$ sudo apt-get purge /usr/share/locale-langpack/fr/LC_MESSAGES/phonon_gstreamer.mo 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 

francoise@Charmmy-Kitty:/usr/share/locale-langpack/fr/LC_MESSAGES$ cat phonon_gstreamer.mo 
&#65533;&#65533;
&#65533;&#65533;`&#65533;wR&#65533;&#65533;C`~u&#65533;&#65533;&#65533;yu#&#65533;&#65533;+&,Ra(&#65533;
&#65533;&&#65533;&#65533;
      A required codec is missing. You need to install the following codec(s) to play this content: %0Cannot start playback. 

Check your Gstreamer installation and make sure you 
have libgstreamer-plugins-base installed.Could not decode media source.Could not locate media source.Could not open audio device. The device is already in use.Could not open media source.Invalid source type.Warning: You do not seem to have the base GStreamer plugins installed.
          All audio and video support has been disabledWarning: You do not seem to have the package gstreamer0.10-plugins-good installed.
          Some video features have been disabled.Project-Id-Version: phonon
Report-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>
POT-Creation-Date: 2009-04-08 21:20+0000
PO-Revision-Date: 2009-04-13 23:25+0000
Last-Translator: Pierre Slamich <pierre.slamich@gmail.com>
Language-Team: French <fr@li.org>
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
X-Launchpad-Export-Date: 2009-04-18 00:39+0000
X-Generator: Launchpad (build Unknown)
Impossible de trouver un codec nécessaire. Vous devez installer le(s) codec(s) suivant(s) pour lire ce contenu : %0Impossible de démarrer la lecture.

Vérifiez votre installation de GStreamer et assurez-vous 
que libgstreamer-plugins-base est installé.Impossible de décoder la source du média.Impossible de localiser la source du média.Impossible d'ouvrir le périphérique audio. Le périphérique est déjà en cours d'utilisation.Impossible d'ouvrir la source du média.Type de source non valable.Avertissement : les modules externes de base de GStreamer ne semblent pas installés.
          Toute la gestion vidéo et audio a été désactivéeAvertissement : il semble que vous n'ayez pas installé le paquet gstreamer0.10-plugins-good.
          Certaines fonctionnalités vidéo ont été désactivées.francoise@Charmmy-B/LC_MESSAGES/re/locale-langpack/fr/LC_MESSAGES$ cd ../../en_G 
francoise@Charmmy-Kitty:/usr/share/locale-langpack/en_GB/LC_MESSAGES$ cat phonon_gstreamer.mo 
&#65533;&#65533;$,8&#65533;9Project-Id-Version: phonon_gstreamer
Report-Msgid-Bugs-To: [http://bugs.kde.org](http://bugs.kde.org)
POT-Creation-Date: 2009-04-08 21:20+0000
PO-Revision-Date: 2009-04-08 11:32+0000
Last-Translator: Andrew Coles <Unknown>
Language-Team: British English <kde-en-gb@kde.me.uk>
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
X-Launchpad-Export-Date: 2009-08-03 23:37+0000
X-Generator: Launchpad (build Unknown)
francoise@Charmmy-Kitty:/usr/share/locale-langpack/en_GB/LC_MESSAGES$ 

Thank you for solving please !

---

### Post by aljoriz on 2009-09-09
if you are using Ubuntu do this: 

System>Admin>synaptic (enter admin password when asked)

Once in synaptic
Settings>filters
    Under the left side box look for broken, click on it and press OK
    Edit>fix broken packages

Hope this helps.

---

### Post by francoise_peace on 2009-09-11
I already did that several times in Synaptic.

Now I've login as root@ and did rm phonon*
So all files beginning with phonon were for the first time really deleted, phonon_gstreamer included.

So Language support tried to re-install the packs that did trouble.

And I found out that it is the packs that will be installed that are in conflict: kde and not kde.

So how to tell language pack I am not (or I am kde) ... I don't understand much about it.

---

### Post by francoise_peace on 2009-09-12
I format my PC and installed Ubuntu for the heimm 5th time.
But I'll keep it like that.
So thank you for those who read.
If you want to tell me how I should have done, you can for future problems.
Right now I abandon the question.
Thank you.

---

### Post by francoise_peace on 2009-09-13
The problem came back after format and and after I put english instead of french and the worst is that I have installed Ubuntu image from my Ubuntu in the CD from Ubuntu site and it says:
The problem cannot be reported: This is not a genuine Ubuntu package !!!???

E: /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb: trying to overwrite `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-pt

---

### Post by Partyboi2 on 2009-09-13
> **francoise_peace said:**
> The problem came back after format and and after I put english instead of french and the worst is that I have installed Ubuntu image from my Ubuntu in the CD from Ubuntu site and it says:
The problem cannot be reported: This is not a genuine Ubuntu package !!!???

E: /var/cache/apt/archives/language-pack-kde-pt_1%3a9.04+20090803.2_all.deb: trying to overwrite `/usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-pt
You could try overwriting the file
```
 cd /var/cache/apt/archives
```
```
sudo dpkg --force-overwrite --install language-pack-kde-pt_1%3a9.04+20090803.2_all.deb 
```

---

### Post by newsoft on 2009-09-13
thnx Partyboi2

---

### Post by francoise_peace on 2009-09-16
Yes !!!!
Thank you !!!!!!!!!!!!!

The solution is for language pack problem with [B]phonon_gstreamer.mo :

[ problem ]
[/B][I]E: /var/cache/apt/archives/**language-pack-kde-pt_1%3a9.04+20090803.2_all.deb**: tentative de remplacement de « /usr/share/locale-langpack/pt_BR/LC_MESSAGES/phonon_gstreamer.mo », qui appartient aussi au [B]paquet language-pack-pt

*[ solution ]*

[/B][/I]**sudo dpkg --force-overwrite --install** language-pack-kde-pt_1%3a9.04+20090803.2_all.deb

then

[B]sudo aptitude install -f

[/B](because the 2 packages are partly configured)

---

### Post by thogor on 2009-10-05
Thanks, Partyboi2 and francoise_peace that did it for me. I tried to change the default language of my Ubuntu and got this problem. 
My openoffice went wacko but thats life - says it can't identify  my user interface language. any sugestions?

I reseted my profile in OO, that solved it. 
"rm -fR ~/.openoffice.org"

I kind of used the soltion sugested in [http://katana.oooninja.com/w/openoffice.org/troubleshooting](http://katana.oooninja.com/w/openoffice.org/troubleshooting) .

---

