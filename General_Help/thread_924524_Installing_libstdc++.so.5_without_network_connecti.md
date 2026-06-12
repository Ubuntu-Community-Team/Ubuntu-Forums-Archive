---
title: "Installing libstdc++.so.5 without network connection?"
date: 2008-09-19
forum: General Help
---

### Post by Morrowj on 2008-09-19
For the past couple of days I've been trying to run a particular script(Bradford Dissolvable Agent) thats required to access my campus network.  When running the script I receive the following error:

"error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory"

So I am assuming from this statement, as well as a few posts here that I've seen, I'm missing this older library.  However, because I'm unable to connect to the internet, I can't use the apt-get methods to install libstdc++5. I tried downloading and then dpkg -i the libstdc++5-3.3-deb file but it was missing quite a few dependencies to complete the install.

 Any suggestions on what I can do?

---

### Post by acidsolution on 2008-09-19
try 
```

sudo apt-get install -f

```

---

### Post by Morrowj on 2008-09-19
Alright, well this removed libstdc++5-3.30-dev.  Now what should I do?

---

### Post by jonian_g on 2008-09-19
Open synaptic and mark the package you want for installation. Then click File>Create download script. Save it and run it on a computer with internet access and it will download the package you want and all its dependencies. Basicaly the script saves all the packages that are marked for installation in synaptic.

If the computer that you are going to run the script doesn't have ubuntu, open the script with a text editor and use the links do download the packages.

Sample of download script created by synaptic:
```
#!/bin/sh
wget -c http://gr.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer-translations_0.6.1-1~hardy1_all.deb
wget -c http://gr.archive.ubuntu.com/ubuntu/pool/multiverse/s/smplayer/smplayer_0.6.1-1~hardy1_amd64.deb
wget -c http://gr.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer-themes/smplayer-themes_0.1.15.dfsg-0ubuntu1_all.deb
```

---

