---
title: "Trouble shoot with codeblocks under Ubuntu 8.10 !"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by WILL_CHAN on 2008-12-20
I just got some automatic updates from Ubuntu 8.10 but then I was unable to use CB anymore. Then I tried to reinstall CB follow this link : [http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)
Then from the terminal I got these error messages :
> 
sudo apt-get install codeblocks
bash: codeblocks: command not found
Ken@Widget:~$ sudo apt-get install codeblocks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  codeblocks: Depends: codeblocks-common (= 8.02svn5340-0ubuntu1~feisty) but it is not going to be installed
              Recommends: codeblocks-contrib (= 8.02svn5340-0ubuntu1~feisty) but it is not going to be installed
E: Broken packages

What is the problem that I'm having ? Is that the problem of Ubuntu or CB ? Anyone could help me out ? Thanks in advance !

---

### Post by leg on 2008-12-20
It looks like the packages mentioned at the end are not being installed. They are not stable versions and are probably kept on the servers you are told to add to your sources.list on the page you listed. Maybe you missed updating your sources or something so they are not getting picked up. Personally I wouldn't bother with that and just install the version that is in the Ubuntu repositories.

---

