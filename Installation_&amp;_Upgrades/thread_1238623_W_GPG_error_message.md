---
title: "W: GPG error message"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2009-08-12
When I run Update manager and click the "check" icon, it starts to download some 30 files, and then, right after downloading the 29th file, an error message appears, reading:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

What do I have to do?

Cheers

---

### Post by Partyboi2 on 2009-08-13
Hi, you need to add the key, open a terminal (Applications>Accessories>Terminal) and add the key with
```
gpg --keyserver keyserver.ubuntu.com --recv EF4186FE247510BE
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by d2globalinc on 2009-08-13
So what happens when the keyserver.ubuntu.com is down? Like right now :( - is there a morror or something we can set as an alt source?

- D2G

---

### Post by Partyboi2 on 2009-08-13
Sometimes the keyserver can be a little slow, I just tried it now and had no problems. 
If you are still having problems, go [[COLOR=Blue]here[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xEF4186FE247510BE") and copy and paste the key into gedit (Applications>Accessoreis>Text Editor) and save it to your Desktop. Then open Software Sources (System>Admin>Software Sources) and go to the "Authentication" tab and click on "Import Key File" then navigate to your Desktop (/home/user/Deskop) and select the saved file. It should then import it.

---

### Post by RedRat on 2009-08-16
> **Partyboi2 said:**
> Hi, you need to add the key, open a terminal (Applications>Accessories>Terminal) and add the key with
```
gpg --keyserver keyserver.ubuntu.com --recv EF4186FE247510BE
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
```
then
```
sudo apt-get update
```

OK, I am new at this and your example helped me out. However, isn't there some way to do this in an automated fashion under Synaptic or Software sources? Your method worked great. 

Another related question I have is in regard to some clearly missing urls. When I hit reload now, I do get the following to what must be obsolete or outdated urls:
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


My question is where do get rid of these references? I don't have them in my Software Sources tabs. Where are these stored?? It is not that this is really hurting anything, just an annoyance.

---

### Post by Partyboi2 on 2009-08-16
> **RedRat said:**
> OK, I am new at this and your example helped me out. However, isn't there some way to do this in an automated fashion under Synaptic or Software sources? Your method worked great. 

Another related question I have is in regard to some clearly missing urls. When I hit reload now, I do get the following to what must be obsolete or outdated urls:
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


My question is where do get rid of these references? I don't have them in my Software Sources tabs. Where are these stored?? It is not that this is really hurting anything, just an annoyance.
Gutsy has reached its end of life and the repos removed, that is why you are getting  '404 Not Found' If you are using Gutsy I would recommend upgrading to a later release of Ubuntu.


Using the terminal to add the gpg key is more automated then using the 'Import' function in Software Sources.

---

### Post by RedRat on 2009-08-16
> **Partyboi2 said:**
> Gutsy has reached its end of life and the repos removed, that is why you are getting  '404 Not Found' If you are using Gutsy I would recommend upgrading to a later release of Ubuntu.


Using the terminal to add the gpg key is more automated then using the 'Import' function in Software Sources.

Sorry I wasn't very clear. I am running 8.04 and already upgraded from 7.10. My guess is that the refrences to Gutsy are residual. Where are they kept??? I would remove them if i knew where they were. It is not readily apparent.

---

### Post by Partyboi2 on 2009-08-17
You can open your sources.list and remove the Gutsy entries or # them out.
```
gksu gedit /etc/apt/sources.list
```

---

### Post by RedRat on 2009-08-17
> **Partyboi2 said:**
> You can open your sources.list and remove the Gutsy entries or # them out.
```
gksu gedit /etc/apt/sources.list
```

Thanks!!! took care of the problem. Kudos to you!

---

### Post by Defenestrator09 on 2009-09-22
I keep getting this message when I try what the first responder suggested:

gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


What do I do about that?

---

