---
title: "Internet problems.."
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by LincIVXX on 2009-05-01
I need help setting up my internet. I am very inexperienced with Linux and feel completely useless trying to fix anything on it. My computer is hooked into a network at my store. It has a linksys router and the other computers on the network run windows xp home. My problem is: I am connected to the internet, I can ping sites, and most of the time have a 100% pingback. I can see the other computers on the network, and everything seems to be working fine except for the fact that I can't connect to websites through my browser. 

Any advice would be greatly appreciated. 
-Linc

---

### Post by Herman on 2009-05-01
There could be that firewall rules in your router not allowing your connection.

Many people think they need a CD to access their router's control panel, and the CD that came with thier router will only work in Windows. Really, all you need to know is your router's IP address and you can easily log into it through Firefox.

Try opening firefox and look for the 'address bar' near the top. it might contain something like: [http://start.ubuntu.com/9.04/](http://start.ubuntu.com/9.04/)
Replace that with: 192.168.1.1. 
That should be the IP address for your router's control panel, (I hope).
You should be able to log into it with your router's username and password.
If you don't know your router's username and password, try typing 'admin' in the username feild, and leave the password field blank. You should set a proper username and password in your router a.s.a.p. if you don't already have one for security reasons. (especially if it's a wireless router).
Then take a look around and makes sure your router's settings are correct for your connection. 

You will probably need to know your IP address to identify which computer's settings to look at in the router.
You can find out your Ubuntu computer's IP address with the command 'ifconfig'
For example, the [ifconfig command]("http://users.bigpond.net.au/hermanzone/p11.htm#ifconfig").

I'm just guessing it might be some setting inside your router that's causing the problems because I know from experience that Linux computers can normally just connect right up to the internet through almost any router. 
I also know I can ban certian websites in my own router's control panel, or set certian times of the day or days of the week or month when certain computers are allowed on the internet and so on . . .

 Again, I'm just guessing, but it's something to look at.

Regards, Herman :)

---

