---
title: "mldonkey 3.0.0"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-04-16
I just installed mldonkey through apt-get install command, but when I did this, I just got the 2.9.5 version. How can I get the newest version; 3.0.0?

I'm very new to Ubuntu Server Edition so please don't slaughter me :p

---

### Post by viralnexxus on 2009-05-20
First of all, what version of Ubuntu Server are you using and did you install it from Ubuntus: Universe Repository?  If you did install it from that repo, then you don't need to upgrade for any reason because any version of MLdonkey 2.7 and up is good to go OOTB.  There were some problems shutting down the Mldonkey-server as well as Gnutella and Gnutella 2 protocols prior to 2.7 which is why Canonical went with the fixed 2.9.5 version.  So you really don't need to upgrade unless you are having problems and if you are then download the MLD Source here: [http://mldonkey.sourceforge.net/Main_Page](http://mldonkey.sourceforge.net/Main_Page)  .  Then, install it the desired folder and run this command in your terminal:  sudo apt-get install build-essential checkinstall   [FONT=monospace]
[/FONT]After that run this command in a terminal for your dependincies: 
sudo apt-get build-dep mldonkey-server
Next, run:  ./configure
Followed by: make
Lastly: sudo checkinstall -D
And one more thing :

---

