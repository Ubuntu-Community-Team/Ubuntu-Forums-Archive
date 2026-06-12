---
title: "KDE 3.5-rc1"
date: 2005-11-12
forum: General Help
---

### Post by Juippisi on 2005-11-12
Yay! The final release of KDE 3.5 is coming!

[http://dot.kde.org/1131747786/](http://dot.kde.org/1131747786/) and [http://www.kubuntu.org/announcements/kde-35rc1.php](http://www.kubuntu.org/announcements/kde-35rc1.php) (coming soon).

Whee, I'm really waiting for the KDE 3.5 and most of them all, KDE 4.0. How about you?

---

### Post by ace2005 on 2005-11-12
Wohooo !!

[QUOTE=Juippisi]Whee, I'm really waiting for the KDE 3.5 and most of them all, KDE 4.0. How about you?[/QUOTE]

So am i :)

---

### Post by JuanC on 2005-11-12
Kubuntu packages for KDE 3.5 RC 1 are available :
[http://download.kde.org/unstable/3.5-rc1](http://download.kde.org/unstable/3.5-rc1)

---

### Post by DoeRayMe on 2005-11-12
Great they fixed the system sound problem

---

### Post by Juippisi on 2005-11-12
So, they're here!

Add "deb [http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1) breezy main" to your /etc/apt/sources.list to get the newest KDE. You can add the gpg-key by downloading [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg) to your home directory, opening terminal and writing "sudo apt-key add ~/kubuntu-packages-jriddell-key.gpg" into it.

[http://www.kubuntu.org/packages/kde35rc1/](http://www.kubuntu.org/packages/kde35rc1/)


And what it comes to the sound system... I don't even have arts installed ;-). I thought that the development of arts would have been stopped since long time ago.


EDIT: The GPG-Key.

---

### Post by JuanC on 2005-11-12
There is no Amd64 packages  :(

---

### Post by Juippisi on 2005-11-12
Heh, it seems that sometimes it pays back to have a "good old x86 system" ;-).

---

### Post by anono on 2005-11-12
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

root@lupus:/home/peter# wget [http://www.kubuntu.org/announcements...iddell-key.gpg](http://www.kubuntu.org/announcements...iddell-key.gpg) && sudo apt-key add kubuntu-packages-jriddell-key.gpg
--15:59:48--  [http://www.kubuntu.org/announcements...iddell-key.gpg](http://www.kubuntu.org/announcements...iddell-key.gpg)
           => `announcements...iddell-key.gpg'
Resolving [www.kubuntu.org](www.kubuntu.org)... 82.211.81.147
Connecting to www.kubuntu.org|82.211.81.147|:80... connected.
HTTP verzoek verzonden, wacht op antwoord... 404 Not Found
15:59:48 FOUT 404: Not Found.

---

### Post by Juippisi on 2005-11-12
[QUOTE=anono]W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

root@lupus:/home/peter# wget [http://www.kubuntu.org/announcements...iddell-key.gpg](http://www.kubuntu.org/announcements...iddell-key.gpg) && sudo apt-key add kubuntu-packages-jriddell-key.gpg
--15:59:48--  [http://www.kubuntu.org/announcements...iddell-key.gpg](http://www.kubuntu.org/announcements...iddell-key.gpg)
           => `announcements...iddell-key.gpg'
Resolving [www.kubuntu.org](www.kubuntu.org)... 82.211.81.147
Connecting to www.kubuntu.org|82.211.81.147|:80... connected.
HTTP verzoek verzonden, wacht op antwoord... 404 Not Found
15:59:48 FOUT 404: Not Found.[/QUOTE]

Blame the forum, not me! 
You see, it cuts long sentences, just like URL's. So, copy the URL with clicking it on mouses right button and selecting "Copy link location". Paste that location to terminal.

---

### Post by anono on 2005-11-12
ok, thanks.

wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg)
--16:16:32--  [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg)
           => `kubuntu-packages-jriddell-key.gpg'
Resolving [www.kubuntu.org](www.kubuntu.org)... 82.211.81.147
Connecting to www.kubuntu.org|82.211.81.147|:80... connected.
HTTP verzoek verzonden, wacht op antwoord... 200 OK
Lengte: 26,430 (26K) [text/plain]

100%[====================================>] 26,430        --.--K/s

16:16:33 (581.49 KB/s) - `kubuntu-packages-jriddell-key.gpg' saved [26430/26430]

that part worked.
but when I do 


root@lupus:/home/peter# sudo apt-get update
Ophalen:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ophalen:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ophalen:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper Release.gpg [189B]
Geraakt [http://kubuntu.org](http://kubuntu.org) breezy Release
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper Release
Ophalen:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [19,6kB]
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release
Geraakt [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ophalen:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/restricted Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/multiverse Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/universe Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/restricted Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/multiverse Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/universe Sources
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
20,0kB opgehaald in 1s (12,3kB/s)
Pakketlijsten worden ingelezen... Klaar
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen


still a GPG error  :-(

---

### Post by stoeptegel on 2005-11-12
Is it safe to reboot when the upgrade broke the kdelibs and kdelib4c2 packages? :confused:

---

### Post by dolny on 2005-11-12
Downloading. <dances> :)

---

### Post by Juippisi on 2005-11-12
[QUOTE=stoeptegel]Is it safe to reboot when the upgrade broke the kdelibs and kdelib4c2 packages? :confused:[/QUOTE]

I don't really think so...

Try removing the old stuff (as I had to do) and try to fix your installation. 

Hmm, if kdelibs doesn't install, it doesn't break your system, only KDE.

---

### Post by Juippisi on 2005-11-12
[QUOTE=anono]ok, thanks.

wget [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg)
--16:16:32--  [http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg)
           => `kubuntu-packages-jriddell-key.gpg'
Resolving [www.kubuntu.org](www.kubuntu.org)... 82.211.81.147
Connecting to www.kubuntu.org|82.211.81.147|:80... connected.
HTTP verzoek verzonden, wacht op antwoord... 200 OK
Lengte: 26,430 (26K) [text/plain]

100%[====================================>] 26,430        --.--K/s

16:16:33 (581.49 KB/s) - `kubuntu-packages-jriddell-key.gpg' saved [26430/26430]

that part worked.
but when I do 


root@lupus:/home/peter# sudo apt-get update
Ophalen:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ophalen:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Ophalen:3 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper Release.gpg [189B]
Geraakt [http://kubuntu.org](http://kubuntu.org) breezy Release
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper Release
Ophalen:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [19,6kB]
Genegeerd [http://kubuntu.org](http://kubuntu.org) breezy Release
Geraakt [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ophalen:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/restricted Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/multiverse Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/universe Packages
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/main Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/restricted Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/multiverse Sources
Geraakt [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) dapper/universe Sources
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Geraakt [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
20,0kB opgehaald in 1s (12,3kB/s)
Pakketlijsten worden ingelezen... Klaar
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen


still a GPG error  :-([/QUOTE]

Download [http://www.kubuntu.org/announcements...iddell-key.gpg](http://www.kubuntu.org/announcements...iddell-key.gpg) to your home directory, open terminal and write "sudo apt-key add ~/kubuntu-packages-jriddell-key.gpg" into it.

Then do "apt-get update" and "apt-get upgrade". Now it should work.

---

### Post by stoeptegel on 2005-11-12
Lame... i had to do the upgrade twice to unbrake it, but it's working now.

---

### Post by anono on 2005-11-12
sudo apt-key add /home/peter/kubuntu-packages-jriddell-key.gpg

thank you! :-)
this one did the trick

---

### Post by dolny on 2005-11-12
I also had some errors, should I use --force? :(

Here's the link with output: [http://www.forum.ubuntu.pl/viewtopic.php?p=16154#16154](http://www.forum.ubuntu.pl/viewtopic.php?p=16154#16154)

---

### Post by Juippisi on 2005-11-12
[QUOTE=dolny]I also had some errors, should I use --force? :(

Here's the link with output: [http://www.forum.ubuntu.pl/viewtopic.php?p=16154#16154](http://www.forum.ubuntu.pl/viewtopic.php?p=16154#16154)[/QUOTE]

I'm not sure if I understanded correctly... but do

apt-get remove kicker
dpkg -r libdjvulibre15
apt-get -f install

That did the trick for me.

---

### Post by dolny on 2005-11-12
Didn't work for me, so I'll force... I guess.

Heh... Can somebody give me a  command to force overwrite? I'm confused.

```
mrplant@milkshake:~$ sudo apt-get install -f -force=all
Czytanie list pakiet&#243;w... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Naprawianie zale&#380;no&#347;ci... Gotowe
Zostan&#261; zainstalowane nast&#281;puj&#261;ce dodatkowe pakiety:
  kdelibs-data
Nast&#281;puj&#261;ce pakiety zostan&#261; zaktualizowane:
  kdelibs-data
1 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 9 nieaktualizowanych.
33 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0B/7036kB archiw&#243;w.
Po rozpakowaniu zostanie zwolnione 1499kB miejsca na dysku.
Czy chcesz kontynuowa&#263; [T/n]? t
UWAGA: Nast&#281;puj&#261;ce pakiety nie mog&#261; zosta&#263; zweryfikowane!
  kdelibs-data
Zainstalowa&#263; te pakiety bez weryfikacji [t/N]? t

Prekonfiguracja pakiet&#243;w ...
(Odczytywanie bazy danych ... 199161 plik&#243;w i katalog&#243;w obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia kdelibs-data 4:3.4.91-0ubuntu1 (wykorzystuj&#261;c .../kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego kdelibs-data ...
Zast&#261;pienie plik&#243;w z poprzedniego pakietu kttsd ...
Zast&#261;pienie plik&#243;w z poprzedniego pakietu kdevelop3-data ...
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb (--unpack):
 pr&#243;ba nadpisania `/usr/share/mimelnk/image/x-djvu.desktop', kt&#243;ry istnieje tak&#380;e w pakiecie libdjvulibre15
dpkg-deb: podproces paste zosta&#322; zabity sygna&#322;em (Przerwany potok)
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dolny on 2005-11-12
OK I forced it. And did upgrade again.

---

### Post by tikal26 on 2005-11-12
sorry to go alittle of topic but I hear that konqueror is much faster in 3.5. I think that if its true I'll upgrade to the beta

---

### Post by Rob2687 on 2005-11-12
It kinda broke artsd or something on my laptop. 
It gives this crash error whenever I log in... Is there any way I can try to reconfigure it some thing?

---

### Post by haaglin on 2005-11-12
I just installed KDE 3.5, And now, if my mouse hoovers an desktop icon, the text of that icon dissapears, and 1 second after that the desktop goes black, just for 2-3 seconds or so, and then back to "normal", but this happens everytime my mouse hoovers an desktop icon. Anyone know what is wrong?

Edit: 

Sorry, Just looked at the KubuntuKDE35BetaKnownProblems list, and this problem is listed there already, but no fix, anyone got a solution?

---

### Post by piquadrat on 2005-11-12
Damn, akregator is still going down the drain on startup... but everything else seems to work. Cool!

---

### Post by dolny on 2005-11-12
OK. Installed it... WOW: it works so much faster than my previous KDE 3.5 Beta 1! Konqueror is like 5x faster! Impressions for now - great.

---

### Post by stoeptegel on 2005-11-13
The looks are much more ubuntu integrated then in the previous version, now i like it even more. :D  No problems seen yet besides that kate doesn't open tabs anymore when opening a text file from konqueror. I upgraded from breezy kde3.4.

---

### Post by Tschaeck on 2005-11-14
- amarok doesn't work with arts. i switched to xine ;)
- kate always opens new windows instead of opening file in existing kate window.
- selection (the nice transparent effect) is still extremly slow.


+ new popuplabels on kicker are great. but it could be more detailed when windows are grouped.
+ switching between different views (icon-, treeview) is finally possible when viewing e.g. smb://computer or media://sda1 with konqueror.

---

### Post by sinbad782 on 2005-11-14
On the whole it has been fine for me. The two major problems I have had are:

* Superkaramba sometimes crashes at startup
* Right-clicking on a jpg when in Konqueror and choosing  'Actions -> Set as Background - > Centred/Tiled' seems to crash everything. 

PJS

---

### Post by shakin on 2005-11-14
apt-get failed and I had to run dpkg --force-overwrite on, I think, the kdelibs package. Works fine now and RC 1 is many times better than beta 2. It's faster and lots of bugs have been fixed.

Thanks goes to the packagers!

---

### Post by Aikurn on 2005-11-14
[QUOTE=Juippisi]And what it comes to the sound system... I don't even have arts installed ;-). I thought that the development of arts would have been stopped since long time ago.[/QUOTE]

I've had problems with arts too. I had to downgrade to beta1. How can I change my sound system? I don't see any option in kcontrol.

Also, I had to manually overwrite a package for some dependency problem, but it went fine at the end.

---

### Post by getaceres on 2005-11-14
Beta 2 had all the bugs of Beta 1 plus some more. RC1 has the same bugs as Beta 2 and baybe some more. Shouldn't it be more stable on every release?
I hope the final version will be better than this.

---

### Post by Kebabji on 2005-11-14
beta 2 was very buggy for me but rc1 is great, no bugs encountered so far, everything seems to be running more efficiently and i've yet to experience the kdm crashes i've experienced with beta 2. all in all i like rc1.

---

### Post by JShadow on 2005-11-14
Anyone else getting a bunch of 404's when they try to upgrade?

---

### Post by monotux on 2005-11-14
[QUOTE=JShadow]Anyone else getting a bunch of 404's when they try to upgrade?[/QUOTE]
Same problems here :(

---

### Post by hatefulthreatening on 2005-11-14
>Anyone else getting a bunch of 404's when they try to upgrade?

Yes. We don't seem to be the [ only ones]("http://www.ubuntuforums.org/showthread.php?t=90311&highlight=rc1+404")

---

### Post by hatefulthreatening on 2005-11-14
Looks like it is fixed.

---

### Post by DoeRayMe on 2005-11-14
I was trying every 5 minutes, one package at a time was being uploaded

---

### Post by chadwick359 on 2005-11-14
Is anybody else getting? > Failed to fetch [http://kubuntu.org/packages/kde35rc1/pool-breezy/kdelibs/kdelibs4c2_3.5-rc1-0ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35rc1/pool-breezy/kdelibs/kdelibs4c2_3.5-rc1-0ubuntu0breezy1_i386.deb) Size mismatch
Failed to fetch [http://kubuntu.org/packages/kde35rc1/pool-breezy/kdepim/libksieve0_3.5-rc1-1ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35rc1/pool-breezy/kdepim/libksieve0_3.5-rc1-1ubuntu0breezy1_i386.deb) Size mismatch 
Failed to fetch [http://kubuntu.org/packages/kde35rc1/pool-breezy/kdepim/libktnef1_3.5-rc1-1ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35rc1/pool-breezy/kdepim/libktnef1_3.5-rc1-1ubuntu0breezy1_i386.deb) MD5Sum mismatch 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 

---

### Post by dtfinch on 2005-11-14
I wonder what this'll do to my kubuntu dapper system upgraded from kubuntu breezy upgraded from ubuntu breezy upgraded from ubuntu breezy preview release. I had to make it skip kdepim, otherwise it wants to remove kde. That's the 2nd package in 3 days that apt-get has wanted to remove kde to upgrade.

EDIT: so far, so good. It took a couple tries to get everything downloaded, and a couple more to get everything to install, and kdepim and all kdepim related packages had to be held back, but so far it all seems to be working.

---

### Post by j0217995 on 2005-11-15
[QUOTE=dtfinch]I wonder what this'll do to my kubuntu dapper system upgraded from kubuntu breezy upgraded from ubuntu breezy upgraded from ubuntu breezy preview release. I had to make it skip kdepim, otherwise it wants to remove kde. That's the 2nd package in 3 days that apt-get has wanted to remove kde to upgrade.
[/QUOTE]
I upgraded a system from Breezy to Dapper and then upgraded KDE to KDE 3.5 RC1 yesterday with no issues.  In speaking w/ Riddell via IRC he is working on getting actual dapper builds, but you can use the current breezy builds on a dapper build with no issues.  Haven't had any problems since the upgrade yesterday.

---

### Post by joakim2 on 2005-11-15
[QUOTE=chadwick359]Is anybody else getting?[/QUOTE]

Yup. I'm still getting size mismatch and MD5 errors.

---

### Post by Tschaeck on 2005-11-15
[QUOTE=joakim2]Yup. I'm still getting size mismatch and MD5 errors.[/QUOTE]

me too. hope it is getting fixed soon.

---

### Post by hogweed on 2005-11-15
I was getting these errors as well, but just kept updating until things finally went well.

I so far have had not a single problem with KDE 3.5-rc1. Not a one. So far, all that I have really noticed is that it is a bit more polished than 3.4, and is really [I]significantly[I]faster than 3.4.

Also, I at the same time upgrade my OpenOffice.org to the full release, using the repositories in this thread: [http://www.ubuntuforums.org/showthread.php?t=80392](http://www.ubuntuforums.org/showthread.php?t=80392)

Again, *huge* improvement in speed, and I have seen no noticeable bug.

Now, to poke around a bit more...

-- hogweed

---

### Post by ltmon on 2005-11-15
I've got RC1 now, and it's a big improvement over beta2 bug-wise.  All the annoying bugs I had are gone!  I'm especially glad that Akregator is back to fully functioning - I didn't realise how much I had gotten to rely on it.

The only "problem" I still have is Kaffeine crashing every time I quit... which isn't that much of a problem really.

L.

---

### Post by z-vet on 2005-11-15
[QUOTE=haaglin]I just installed KDE 3.5, And now, if my mouse hoovers an desktop icon, the text of that icon dissapears, and 1 second after that the desktop goes black, just for 2-3 seconds or so, and then back to "normal", but this happens everytime my mouse hoovers an desktop icon. Anyone know what is wrong?

Edit: 

Sorry, Just looked at the KubuntuKDE35BetaKnownProblems list, and this problem is listed there already, but no fix, anyone got a solution?[/QUOTE]
Configure desktop > Behavior > Show Icon Previews for, uncheck Sound files, this fixes a problem with desktop refresh and flickering. I don't know why and how, but it works. Seems to be arts related problem... Why KDE uses unmaintained buggy sound system, that's something i can't understand...

---

### Post by chadwick359 on 2005-11-16
Hmm, well, everything seems to have worked this time, but other than improved launch time in Konq, nothing seems to really have changed. Apps still have rediculous font sizes unless I launch them from terminal, CD's still have trouble mounting, and my batter app still refuses to show up if i use kompmgr. Can anybody link to a changelog for me?

---

### Post by dtfinch on 2005-11-16
The fonts look alright on mine, exactly as before. I have DisplaySize specified in the Monitor section of my xorg.conf, if that matters. CD's automount, but open twice in Konqueror.

---

### Post by ltmon on 2005-11-16
[QUOTE=dtfinch]The fonts look alright on mine, exactly as before. I have DisplaySize specified in the Monitor section of my xorg.conf, if that matters. CD's automount, but open twice in Konqueror.[/QUOTE]

That's because of ivman.  Search for it in the forums and you will find how to turn it off.

It really should be disabled by default in future Kubuntu versions, because KDE contains it's own volume manager that is less powerful, but much easier to use and configure.  The default configuration of ivman is not using any of it's power features anyway.

L.

---

### Post by tokyovigilante on 2005-11-16
Good to see AMD64 packages for RC1 have been uploaded. Thanks Jonathan (and anyone and everyone who's been working on this)!

---

