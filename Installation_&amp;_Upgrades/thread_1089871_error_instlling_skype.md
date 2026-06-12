---
title: "error instlling skype"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by simon dew on 2009-03-07
when i download Skype debian I get 'Error: Dependency is not satisfiable libqt4-core'on the package installer.
This has not happened to me before what has changed and how can I fix it?

Simon

---

### Post by taurus on 2009-03-07
Use the version from Medibuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

---

### Post by simon dew on 2009-03-07
THanks for the prompt response but the error is the same as before. I am also having trouble installing VLC player.

---

### Post by taurus on 2009-03-07
Can you post the command that you ran to install vlc and the whole error message?

---

### Post by simon dew on 2009-03-07
I used applications/system/add/Remove and it popped up a window that said that this software conflicts with installed software use synaptic package manager to remove. I'm getting the feeling that I need to go back to rewriting my live cd and start from scratch as this is running like a dog, 
Simon

---

### Post by taurus on 2009-03-07
Close add/remove first.  Then, open a terminal and post the outputs of these two commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by simon dew on 2009-03-07
I think I might have an answer. For some reason the updates are all coming from the New Zealand Ubuntu/linux site which is understandable as thats where I live. But for some reason it is failing to connect

Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Translation-en_NZ       
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10). - connect (111 Connection refused)

with this a typical response. Can I change the location of my updates source or can I fix this issue locally?

Simon

---

### Post by simon dew on 2009-03-07
Nailed it! Changed the source from NZ to Main and things have started to work. Many thanks for the assistance

Simon.

---

