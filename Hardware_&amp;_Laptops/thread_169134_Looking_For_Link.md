---
title: "Looking For Link"
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by rushin1nd on 2006-05-02
how do i get to universe' repository...............i would like load drivers for epson cx4600 .........i understand it can be done by using Synaptic help please](*,) ](*,) ](*,) ](*,)

---

### Post by gabruo on 2006-05-02
Open synaptic go to repositories in settings and check universe and any others you like.

---

### Post by rushin1nd on 2006-05-02
im new to this site and forum im lost ...............how do i find>>>>>Synaptic<<<<<

---

### Post by Sef on 2006-05-02
This wiki explains how to add the multiverse and universe repositories.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by rushin1nd on 2006-05-02
im totally lost  oh well thanks anyway...................guess it does have direct link or direct download.....................maybe another forum can help with not so much complications.

---

### Post by jazzmuzik on 2006-05-02
Synaptic is in the menus: System, Administration, Synaptic Package Manager.

---

### Post by rushin1nd on 2006-05-02
guess it does not have a direct link or a direct download..............Synaptic

---

### Post by aysiu on 2006-05-02
[QUOTE=rushin1nd]im totally lost  oh well thanks anyway[/QUOTE] What are the complications?

Well, if you're more of a visual learner, hopefully [this](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories) will help.

---

### Post by deadgobby on 2006-05-02
[QUOTE=rushin1nd]guess it does not have a direct link or a direct download..............Synaptic[/QUOTE]
 You should be able to access Synaptic menu feature. Go to the upper left hand corner of your computer and right click on System> then go to Administation>. You should find a file called Synaptic Package Manager and right click on to it. This will open your Synaptic Manager to install software on your Ubie system. If you are looking for games. Click on the search button and type in games or scroll down on the left hand side and click on Games. There should be like three files called Games. To be able to install extra repositoties for Synaptic and Ubuntu.
 Please go to the upper left hand of your and right click on Applications. Scroll down till you see Terminal. This will open the Terminal  window. ( You will need to close up your Synaptic window ) [COLOR="Red"]The Following is if you have installed Ubuntu 5.10 or called Breezy.[/COLOR]
Type in or copy and paste this into your Terminal.
[COLOR="Sienna"]sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/COLOR]

The system will now make a up a back up file of your repositories.

Type in or copy and paste this to the Terminal window. The Terminal may ask you for a password, it may be the same pass word when you logged onto Ubuntu log in screen.

[COLOR="Sienna"]sudo gedit /etc/apt/sources.list[/COLOR]

This will now open up the Text Editor and now you can copy the brown text below and paste it over the text in the Text Editor. 

[COLOR="Sienna"]#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse [/COLOR]

   [COLOR="Black"]noow save and closed the Text Editor and go back to your Terminal and type in.[/COLOR]

[COLOR="Sienna"]sudo apt-get update[/COLOR]

[COLOR="Black"]After it has run its corse and now type in[/COLOR]

[COLOR="Sienna"]sudo apt-get upgrade[/COLOR]

[COLOR="Sienna"][COLOR="Black"]Now close your Terminal and you are now done. Now go open up you Synaptic and install some games or what you may be looking for. It it a great feature of Ubie and have lots of fun.

Gobby[/COLOR][/COLOR]

---

