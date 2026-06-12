---
title: "GPG Error installing Open Office 3.1"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by gargaralarga on 2009-08-13
Hi, I followed the instructions in order to install open office 3.1. The thing is, that at the end of the process the following message appears..

**"W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF"**

It says something like "the signatures couldn't be verified because of the public key is not available."

Thanks!

---

### Post by Partyboi2 on 2009-08-13
Hi, you need to add the key, this can be done by opening a terminal (Applications>Accessories>Terminal) and typing
```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF  | sudo apt-key add -
``` Then
```
sudo apt-get update
```

---

### Post by gargaralarga on 2009-08-14
Hi, I've trying what you say but it appears the following statement after the first line command..

"requesting key 247D1CFF from hkp server keyserver.ubuntu.com

error from the key server

reception from the key server fails"

---

### Post by Partyboi2 on 2009-08-14
Try going [[COLOR=Blue]here[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF") and copying and pasting the key into gedit (Applications>Accessories>Text Editor) then save it to your Desktop. Then open up Software Sources (System>Admin>Software Sources) and go to the "Authentication" tab and select "Import" then navigate to the saved file (/home/username/Desktop) that you save on your Desktop and import it.

---

### Post by gargaralarga on 2009-08-20
Hi, sadly It did not work. I don't know why but I tried to import the saved file but it did not do it. Should the saved file have any specific format? Thanks anyway.

---

### Post by nilarimogard on 2009-08-20
Running [this script]("http://webupd8.blogspot.com/2009/05/ubuntu-script-to-automatically-install.html") should install all GPG keys for your launchpad PPA's

---

### Post by gargaralarga on 2009-08-20
Hi everyone, Finally I could install the last version looks like the former distribution did not work so I used the following one
[I]
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main[/I] 

thanks for your support.

---

