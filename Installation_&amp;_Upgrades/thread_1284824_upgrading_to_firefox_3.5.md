---
title: "upgrading to firefox 3.5"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-10-07
My friend and I are having a few problems with this.

I put the relivent repositry in sources.  Grabed the .deb.

uninstalled the old firefox 3.0 
double clicked on it, it said there are 7 deps to get, I said yes get them.

After it finished it said there were still dependancy problems :(
but firefox is there anyway.  And it's back to firefox 3.0.

what the heck?

---

### Post by Partyboi2 on 2009-10-07
Hi, if you are running Jaunty open a terminal (Applications>Accessories>Terminal) and in the terminal type
```
sudo apt-get update && sudo apt-get install firefox-3.5
```
This should install firefox 3.5., if you get any errors running the above command post the output from the commands.

---

### Post by johnh10000 on 2009-10-07
> **Partyboi2 said:**
> Hi, if you are running Jaunty open a terminal (Applications>Accessories>Terminal) and in the terminal type
```
sudo apt-get update && sudo apt-get install firefox-3.5
```
This should install firefox 3.5., if you get any errors running the above command post the output from the commands.

sorry for late reply. This thing didn't send me an email :(

Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.5 is already the newest version.
firefox-3.5 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
johnh10000@tux:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
johnh10000@tux:~$ 

I think the lack of pub key, is todo with my tring to get xbox mediapalyer last night.

---

### Post by Partyboi2 on 2009-10-08
For Firefox try going to Applications>Internet>Shiretoko.

For the gpg key open a terminal and add the key with
```
gpg --keyserver keyserver.ubuntu.com --recv 91E7EE5E
gpg --export --armor 91E7EE5E | sudo apt-key add -

```
```
sudo apt-get update
```

---

