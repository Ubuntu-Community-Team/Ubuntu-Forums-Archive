---
title: "Apt-Get Upgrade Hangs"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by x_jose_x on 2009-07-19
Hello,
 
I am attempting to install jeos-8.04.2 in vmware (also tried this in virtual box with the same errors listed below).
 
I ran into the problem of the install hanging at the apt-get section. I researched this and found that disabling networking after dhcp is configured solved the problem.
 
However, once the install is complete, and I run the sudo apt-get update command, it hangs at connecting to us.archive.ubuntu.com. I did some more research and read that the mirror us.archive.ubuntu.com is down. Therefore I modified the sources.list file to drop the us from the address. 
 
Now the command hangs at security.ubuntu.com. I read up on this, but there is not much help for this problem. Some posts pointed to a web site that could generate sources.list files with different mirrors, but this site does not appear to be up still.
 
How can I fix this issue now that the install is complete? Most of what I read points to editing sources.list with a new mirror. Unfortunately I can't find a good source on the web for choosing a new mirror.
 
Thanks,
Jose

---

### Post by x_jose_x on 2009-07-19
I finally got an error message:
 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not connect to security.ubunt.com:80 (91.189.88.37, connection timed out
 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Unable to connect to security.ubuntu.com http:
 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com http:
 
There were two more similiar error lines with universe and multiverse

---

### Post by cosine352 on 2009-07-19
aparently the ip address is of UK not USA. try to change the 'download from' to 'main server' in the 'System--> addministration--> software sources (Tab: Ubuntu software).

---

### Post by x_jose_x on 2009-07-19
Hi, thanks for the reply.
 
I could be mis-reading your reply, but it looks like you are describing how to change a setting using the gui.
 
To the best of my knowledge jeos does not come with a gui.
 
-Jose

---

### Post by x_jose_x on 2009-07-20
I finally found the mirror list ([https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)). Pretty sweet.
 
So I changed mirrors. I get a slightly different error now.
 
W: Failed to fetch [http://ftp.iinet.net.au/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://ftp.iinet.net.au/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2) Unable to connect to [ftp.iinet.net.au]("ftp://ftp.iinet.net.au") http:
 
There is several similiar errors to this one as a result.

---

### Post by x_jose_x on 2009-07-20
Found the solution to the issue here: [http://ubuntuforums.org/archive/index.php/t-1011694.html](http://ubuntuforums.org/archive/index.php/t-1011694.html)
 
One of the replies on that thread mentions something about dns not being correct. I then read up on how vmware handles networking. It appears that networking must be set to bridged and not NAT (I am guessing that vmware defaults to NAT as that is how my install was, and I did not change any network settings, until now).
 
For anyone else having the apt-get issue while running ubuntu jeos under vmware, set your networking to bridged so that your vm gets a real ip from the dhcp server.
 
I have not tested this theory, but I bet this fixes the apt-get issue that occurs duing install on vmware that I read so much about.

---

### Post by x_jose_x on 2009-07-21
I was able to test an Ubuntu install with vmware set to bridging. This did solve the apt-get hanging during instal issue.

---

