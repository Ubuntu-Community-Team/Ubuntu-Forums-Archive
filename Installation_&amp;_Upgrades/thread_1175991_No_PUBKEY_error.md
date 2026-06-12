---
title: "No PUBKEY error"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by sms411 on 2009-06-01
I can't figure out how to fix this error. I've tired a few of the steps from other forums, but nothing has worked. I'm a total newb so any advice would be appreciated.   sheena@Sheena-Warrior:~$ sudo apt-get clean all [sudo] password for sheena:  sudosheena@Sheena-Warrior:~$ sudo apt-get update Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B] Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                             Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                  Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                               Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                    Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]               Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US            Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US              Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US            Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]            Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US          Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US    Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US      Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US    Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg [307B]                         Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                       Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Translation-en_US                   Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                   Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release.gpg                         Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Translation-en_US  Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]              Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty Release                             Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [46.7kB]                           Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                      Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) jaunty/cairo-dock Packages                 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                              Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                                Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages                            Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [20.3kB] Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                       Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                    Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                      Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [14B] Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [6695B] Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [14B]      Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [7664B]     Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [1187B]      Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B]     Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [52.6kB]       Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/universe Packages                            Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]     Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [14B] Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [18.4kB] Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [14B] Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [17.5kB] Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [4733B] Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [675B] Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [639B] Fetched 230kB in 1s (115kB/s)  Reading package lists... Done W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513 W: You may want to run apt-get update to correct these problems

---

### Post by lindsay7 on 2009-06-01
Try this first


gpg --keyserver subkeys.pgp.net --recv 665F9AEFE1098513


gpg --export --armor 665F9AEFE1098513 | sudo apt-key add -

sudo apt-get update


type these commands in the terminal

---

### Post by sms411 on 2009-06-01
Thanks! I had to just use the last 8 digits of the number but the updates installed.

---

### Post by lindsay7 on 2009-06-01
Keep this post handy cus I am sure you will need another key sometime.

---

### Post by sms411 on 2009-06-01
Do you know how do I clean up my repository? There's jaunty, intrepid and gutsy listed.

---

### Post by lindsay7 on 2009-06-01
No, but I would not worry about it. I am sure they are there for a reason.

---

