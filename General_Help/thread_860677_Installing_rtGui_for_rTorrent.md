---
title: "Installing rtGui for rTorrent"
date: 2008-07-15
forum: General Help
---

### Post by GrimRe on 2008-07-15
Hi all,

I came accross [this guide for creating a web interface for rtorrent using rtGui.]("http://www.zimbio.com/Ubuntu+Linux/articles/195/Install+rtGui+on+Ubuntu?Success=Your+account+was+created+and+your+comment+was+saved.+To+customize+your+account+%3Ca+href%3D%27%2Fregister%27%3Eclick+here%3C%2Fa%3E.&NewUser=1")

At the moment I'm using uTorrent in Wine so I thought I would give this a go.

First question: Where exactly do I insert this line: 

```
LoadModule scgi_module /usr/lib/apache2/modules/mod_scgi.so
SCGIMount /RPC2 127.0.0.1:5000
```

in the apache server config file?

Second question: How can I make rtorrent automatically start on system boot?

Any help would be greatly appreciated!

Thanks

---

### Post by victor.zamanian on 2008-08-17
I don't know about the apache question, but you can add startup programs by going to System->Preferences->Sessions, selecting Startup Programs and then clicking the Add button. Enter maybe... "screen rtorrent" or whatever you want to run. I like using screen with rtorrent.

All the best!

---

### Post by Ryadt on 2008-08-17
Why do you use utorrent through wine? Ubuntu has lots of better alternatives. Transmission comes built-in. Deluge is my favourite and it's in the repos. 
To start something at start-up, just go in System > Preferences > Sessions and add the program there.

---

