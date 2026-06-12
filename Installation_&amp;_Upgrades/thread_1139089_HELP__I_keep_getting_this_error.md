---
title: "HELP  I keep getting this error"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by thegodsquirrel on 2009-04-26
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA5D96E9AB82B686


How can I fix this error and get the next update.

---

### Post by antikristian on 2009-04-26
This video should explain it to you:
[http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws)

In short, you have to find the gpg key for your ppa (Personal Package Archives) I believe you are looking for this one [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCA5D96E9AB82B686](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCA5D96E9AB82B686)

Save the contents of the webpage as a text file

Import the textfile into System -> Administration -> (Software Sources(Authentication->import key))

---

### Post by thegodsquirrel on 2009-04-28
Thanks for the help and it worked flawlessly

---

