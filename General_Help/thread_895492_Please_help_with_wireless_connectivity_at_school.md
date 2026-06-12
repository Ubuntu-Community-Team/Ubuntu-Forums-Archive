---
title: "Please help with wireless connectivity at school"
date: 2008-08-20
forum: General Help
---

### Post by ragflan on 2008-08-20
Hi. I'm under Hardy Heron. I'm at student at RMIT, Melbourne. The University provides us wireless hotspots where we can connect and use the Internet. I can detect the school's wireless network and connect using my credentials. I can surf** all the RMIT domain web sites** like Blackboard, Student Email the main website and such. **But to view websites other than those belonging to the school**, I can:

1.) Open Firefox.
2.) Edit -> Preferences -> Advanced -> Network -> Settings
3.) Select the 'Automatic proxy configuration URL:'
4.) Enter the URL given to me: [http://wpad.rmit.edu.au/wpad.dat](http://wpad.rmit.edu.au/wpad.dat)

After doing that, I can surf the Internet normally. 

So my question is, for applications like Prism or Update Manager which (I couldn't find the way to enter the proxy URL) how do I enter the URL? Is there a way to allow all applications to use this URL or at least some applications? 

The applications I wish I can use are:

1.) Update Manager or Synaptic or Add/Remove ...
2.) Prism
3.) Epiphany
4.) Thunderbird (although I think this would be the same way as Firefox)
5.) Emesene or Pidgin
6.) Buoh Comics Reader


Please help with any of the above applications. I would greatly appreciate all help. Thank you!

---

### Post by Sam Lars on 2008-09-11
If you go to your System menu, under Administration (maybe Preferences if not there), see if there's a Network & Proxy selection.  You can set system-wide preferences there.  If you go to Pidgin's preferences, under network, it takes you to the same place.  I can confirm that it also affects Firefox.
As far as Update Manager, the above may affect it, but if not, I set a proxy manually for it to use my apt-cache server, so I'm sure you could do something similar.
A file called 01proxy in /etc/apt/apt.conf.d
```
Acquire::http::Proxy "http://192.168.1.100:3142";
```
I'm not sure what settings you want, though.  I looked through that dat file but I couldn't find anything.

---

