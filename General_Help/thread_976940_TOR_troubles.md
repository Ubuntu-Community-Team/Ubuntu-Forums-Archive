---
title: "TOR troubles"
date: 2008-11-09
forum: General Help
---

### Post by pakman21 on 2008-11-09
I am using Ubuntu Hardy (Mint Linux Elyssa actually, but I digress) and I'm trying to install TOR. I've installed TOR through the terminal, and I've install privoxy. I've commented out Jarfile jarfile, logfile logfile, I put in that forward socks line in /etc/privoxy/config, and I'm using torbutton. I really have no idea what to do. It's just not working, and I dunno why. Can anyone help me out?

---

### Post by petermck on 2008-11-12
I have been trying the same set up as you and found some advice in the tor extension manual to add 'forward-socks4a / 127.0.0.1:9050 .' to the beginning of the /etc/privoxy/config file. This works but browsing is now very slow. It reminds me of dialup.

---

