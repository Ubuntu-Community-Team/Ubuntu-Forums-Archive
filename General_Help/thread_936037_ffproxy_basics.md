---
title: "ffproxy basics"
date: 2008-10-02
forum: General Help
---

### Post by Martin_sensei on 2008-10-02
Hello,

I have been trying to get ffproxy to work for most of today, and have spent a good few hours searching for help.  I am still stuck so if anyone can help, please, put me out of my misery!

I installed ffproxy using the synaptic package manager.

Then I had a look at the config file in /etc/ffproxy. The defaults of any IP address to bind to and a port of 8080 seem fine to start with.

Next I started ffproxy ```
sudo /etc/init.d/ffproxy start
``` This returned "[OK]".

I then tested the proxy server using a different machine but it didn't work.  I can ping my ubuntu box with ffproxy however (and I know the network is generally OK as I had squid proxy working earlier today)

On examining the processes on the ubuntu machine, ffproxy doesn't appear to be a running process...  I am not actually sure anything is happening when I start ffproxy.  

Can anyone help me? This looks so easy to set up, but I have spent over 6 hours going round in circles... :(

---

