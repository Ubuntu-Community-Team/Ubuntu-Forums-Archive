---
title: "Dapper updating fails"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Puzzled_Pete on 2009-11-10
Trying to update my Dapper system has recently and persistently failed with a string of error messages of the type:

"Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to 192.168.2.1:8080 (192.168.2.1). - connect (111 Connection refused)"

I've tried system/administraion/update-manager; Sudo apt-get update in a terminal; and clicking on the 'nn updates available' icon on the task bar.  All result in the same failure.  

Updating has always worked succesfully until now.  As I can get onto the internet, send and receive emails and download otherwise, I can't see what might be wrong. I've tried stopping my firewall.  It makes no difference. I haven't altered the settings on my (Belkin) wireless router, but I guess thats where the trouble lies.  Can anyone help please?

---

### Post by dvlchd3 on 2009-11-10
It looks like it is trying to connect to your router?? (Whatever is at 192.168.2.1) instead of the repo server.

I found a similar issue and resolution, however, it was attempting to redirect to localhost.  It looks like the same issue in theory.  Hope it helps!

[http://ubuntuforums.org/archive/index.php/t-281428.html](http://ubuntuforums.org/archive/index.php/t-281428.html)

---

### Post by Kevbert on 2009-11-10
I believe that Dapper is no longer supported as it's been superceded. However, you can still get updates from [http://packages.ubuntu.com/dapper-updates/](http://packages.ubuntu.com/dapper-updates/) as well as [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

