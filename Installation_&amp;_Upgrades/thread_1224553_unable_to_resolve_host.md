---
title: "unable to resolve host"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2009-07-27
My update package (and other stuff) doesn't work when I click on the appropriate icon. With some help from this forum I was able to get an update through a terminal window.

Here is an example of what I believe is symptomatic of the problem:

jean@jean-desktop:~$ sudo apt-get upgrade
sudo: unable to resolve host jean-desktop
[sudo] password for jean: 
Reading package lists... Done
Building dependency tree       

How do I fix the unable to resolve host jean-desktop problem?

---

### Post by coffeecat on 2009-07-27
It could be that your /etc/hosts file needs fixing. Did you do a version upgrade recently?

Anyway, the first page of this thread might help you:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

If you're not sure how to edit your hosts file, post the terminal output of:

```
cat /etc/hosts
```

---

### Post by vchapman on 2009-07-27
> **coffeecat said:**
> It could be that your /etc/hosts file needs fixing. Did you do a version upgrade recently?

Anyway, the first page of this thread might help you:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

If you're not sure how to edit your hosts file, post the terminal output of:

```
cat /etc/hosts
```

jean@jean-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 jean-desktop.home

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I assume I need to take out the ".home"

---

### Post by coffeecat on 2009-07-27
> **vchapman said:**
> I assume I need to take out the ".home"

I agree. Are you comfortable with editing system files, or do you need any help?

I've never had this problem myself, but there must be a bug somewhere affecting a lot of people because when I started typing 'ubuntu unable to resolve host' in Google, I only got as far as 'ubuntu una' when the google search bar prompted me with the whole phrase and said there were 49900 results. Seems that it usually happens after a dist-upgrade.

---

### Post by vchapman on 2009-07-27
> **coffeecat said:**
> I agree. Are you comfortable with editing system files, or do you need any help?

I've never had this problem myself, but there must be a bug somewhere affecting a lot of people because when I started typing 'ubuntu unable to resolve host' in Google, I only got as far as 'ubuntu una' when the google search bar prompted me with the whole phrase and said there were 49900 results. Seems that it usually happens after a dist-upgrade.


I have edited the file and carried out the *fix  *that I suggested above. This seems to have resolved a number of the issues I was having. 

Thank you for your assistance.

---

