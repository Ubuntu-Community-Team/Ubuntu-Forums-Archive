---
title: "Latest version of Banshee and TuxGuitar on Ubuntu 8.04"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by frangoitia on 2009-02-10
Hey guys, due to some problems that i had on Intrepid, I decdided to go back to Hardy Heron. The thing is that when I installed TuxGuitar and Banshee they are older versions that the one i installed on Intrepid. I did exactly the same thing. I installed them both from Synaptic.
Do you know how to get the latest version ??

Another thing, do you know how to install murrine-svn on Hardy ?

Cheers !

---

### Post by Partyboi2 on 2009-02-11
If you want a newer version of Banshee you could add a 3rd party repo to your Software Sources to install banshee 1.4.2
```
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) hardy main
```

To get tuxguitar to the same version as what intrepid has you can enable your backports in Software Sources and upgrade your current version (0.9.1) to the later one (1.0)

---

### Post by frangoitia on 2009-02-11
Ok thanks. And how do I activate the wget key ?
As you can see Im really newbie in Linux.

W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 4874D3686E80C6B7

Thats what i got after an apt-get update

---

### Post by Partyboi2 on 2009-02-11
Open a terminal (Applications>Accessories>Terminal) and type
```
gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7

``````
gpg --export --armor 4874D3686E80C6B7  | sudo apt-key add -
```

---

### Post by frangoitia on 2009-02-12
> **Partyboi2 said:**
> Open a terminal (Applications>Accessories>Terminal) and type
```
gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7

``````
gpg --export --armor 4874D3686E80C6B7  | sudo apt-key add -
```
Thank you. Problem solved.
Now, i only need to install murrine svn engine on hardy. Any help would be appreciate it.

Cheers

---

### Post by Partyboi2 on 2009-02-12
I am not sure how you would go about installing murrine svn. You could check [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=239378")

---

