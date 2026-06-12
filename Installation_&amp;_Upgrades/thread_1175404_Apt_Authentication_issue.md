---
title: "Apt Authentication issue"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by stupor on 2009-06-01
will not let me update apt

---

### Post by lake54 on 2009-06-01
Could you provide a little more detail?

Things to include, for example, are what version of Ubuntu you're running, and also what error message you get.

Thanks!

James

---

### Post by Partyboi2 on 2009-06-01
> **stupor said:**
> will not let me update apt
hi, can you also open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
```

---

### Post by stupor on 2009-06-02
Thanks for your help




Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
 
ubuntu 9.04 jauntu

sudo apt-get update

Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Translation-en_NZ                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Translation-en_NZ
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Translation-en_NZ
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/main Translation-en_NZ     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/restricted Translation-en_NZ
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/multiverse Translation-en_NZ
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Translation-en_NZ
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports Release.gpg [189B]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports/universe Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Get:4 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release [49.6kB]         
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports Release
Get:5 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release [49.6kB]        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports Release [49.6kB]
Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports Release
  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Packages           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/restricted Sources            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/main Sources                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Sources            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Sources              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/universe Packages             
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security/multiverse Packages           
Fetched 570B in 6s (87B/s)                                                     
Reading package lists... Done
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release](http://nz.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by Partyboi2 on 2009-06-02
Go to Software Sources (System>Admin>Software Sources) and under the first tab try changing your download server to another one. If that does not work then open a terminal and try 
```
gpg --keyserver hkp://subkeys.pgp.net --recv-key 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```then
```
sudo apt-get update
```

---

### Post by stupor on 2009-06-02
Thank you very much changed to main server all good now.

---

