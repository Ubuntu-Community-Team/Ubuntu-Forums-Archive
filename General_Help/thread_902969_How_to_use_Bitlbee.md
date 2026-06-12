---
title: "How to use Bitlbee"
date: 2008-08-27
forum: General Help
---

### Post by orangecakez on 2008-08-27
I am following this: [https://help.ubuntu.com/community/Bitlbee](https://help.ubuntu.com/community/Bitlbee)

I did sudo aptitude install bitlbee, then edited /etc/xinetd.d/ircd with sudo and pasted in as the directions, but I changed the port to 9999 because 6667 is taken by another program I have.

I did sudo /etc/init.d/xinetd restart, and it said [OK].

In irssi, I did /connect 127.0.0.1 9999, but it said Connection Refused. I tried /connect localhost 9999, but same error message. How come I can't connect to my Bitlbee server?

---

