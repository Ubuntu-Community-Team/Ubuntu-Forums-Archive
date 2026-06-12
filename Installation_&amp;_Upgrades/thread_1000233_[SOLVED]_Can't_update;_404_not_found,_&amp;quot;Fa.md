---
title: "[SOLVED] Can't update; 404 not found, &amp;quot;Failed to Fetch&amp;quot;."
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by lotrkev on 2008-12-02
I have Ubuntu Ibex, and whenever I run the Update Manager, it gives an error message saying:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-7.16_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.27-7.16_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.6svn20081008-0ubuntu4.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.11.6svn20081008-0ubuntu4.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


So, I have searched the forums for a possible solution, but found nothing; everyone has a previous version of Ubuntu and is trying to upgrade to another, or their post is unresolved. 

Any Help would be greatly appreciated.

---

### Post by Partyboi2 on 2008-12-02
Have you tried changing your download server in Software Sources?

---

### Post by lotrkev on 2008-12-04
Wow Thank you very much!! FIxed it. Will mark as SOLVED

---

### Post by Lord Xar on 2008-12-15
> **Partyboi2 said:**
> Have you tried changing your download server in Software Sources?

Hello - sorry for such a noob question - but what is the:

Software Sources?

I have my Synaptic Package Manager open, its version: 0.57.8

whenever I try to update subversion via the synaptic package manager or command line, I get the follow errors:

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libapr0 2.0.55-4ubuntu4.2
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]

I've tried the following and nothing works:
sudo apt-get install subversion   
sudo apt-get update 

same errors.

I went into the synaptic manager and looked into: 

Settings --> repositories 

changed some things, nothing.

So, what is the solution you pose above? I have no idea where to look or find the Software Sources. I am a noob with all this. 

I am on UBUNTU 6.10


):P

---

### Post by RJARRRPCGP on 2008-12-15
> **Lord Xar said:**
> Hello - sorry for such a noob question - but what is the:

Software Sources?

I have my Synaptic Package Manager open, its version: 0.57.8

whenever I try to update subversion via the synaptic package manager or command line, I get the follow errors:

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libapr0 2.0.55-4ubuntu4.2
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]

I've tried the following and nothing works:
sudo apt-get install subversion   
sudo apt-get update 

same errors.

I went into the synaptic manager and looked into: 

Settings --> repositories 

changed some things, nothing.

So, what is the solution you pose above? I have no idea where to look or find the Software Sources. I am a noob with all this. 

):P

Welp, when I clicked on one of the links above, I did get error 404, thus, the server is definitely giving error 404. :(

Looks like a server problem.

---

### Post by Partyboi2 on 2008-12-16
> **Lord Xar said:**
> Hello - sorry for such a noob question - but what is the:

Software Sources?

I have my Synaptic Package Manager open, its version: 0.57.8

whenever I try to update subversion via the synaptic package manager or command line, I get the follow errors:

Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libapr0 2.0.55-4ubuntu4.2
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu4.2_amd64.deb)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn0_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.3.2-3ubuntu2_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]

I've tried the following and nothing works:
sudo apt-get install subversion   
sudo apt-get update 

same errors.

I went into the synaptic manager and looked into: 

Settings --> repositories 

changed some things, nothing.

So, what is the solution you pose above? I have no idea where to look or find the Software Sources. I am a noob with all this. 

I am on UBUNTU 6.10


):P
You can find Software Sources by going to System>Admin>Software Sources, this is a gui tool which displays the different repositories for installing and updating you machine.
I notice that you have a error for a edgy repository. Are you using edgy? You can check by opening a terminal (Applications>Accessories>Terminal) and typing
```
 lsb_release -d
``` Edgy has reached its end of life So your repos will need to be changed. The best thing to do would be to upgrade your machine to a later ubuntu distro if you are using edgy rather then just changing the repos.

---

