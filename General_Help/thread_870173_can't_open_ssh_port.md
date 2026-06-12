---
title: "can't open ssh port"
date: 2008-07-25
forum: General Help
---

### Post by evencoil on 2008-07-25
I'm trying to set up a ssh server, but I'm getting stuck at the very first step--opening up port 22. I don't know anything about iptables and I don't have complicated firewall needs so I'm just using lokkit. I try
```
sudo lokkit
```
The settings are on high. I go to customize and none of the boxes are checked. I check ssh. Then hit ok and ok. I get the following output in my terminal:
```
iptables: Chain already exists
```
and the settings do not get saved (i.e. if I try to do it again the ssh box is still unchecked. What's going on and how do I fix it?

---

### Post by tamoneya on 2008-07-25
when I setup my ssh server I didnt mess with any of that.  I had to setup a port forward on my router so I could access when I was away from home but I didnt change any firewall settings.  Try going forward with the install and if you get port blocked or ssh server not found errors you can come back to this.

---

### Post by evencoil on 2008-07-25
ah yes, so I neglected to say that, but the reason I started doing this was precisely because I was having problems with that.

I was able to use the host to connect to itself. But I kept getting connections refused when I tried to connect from my laptop. Both are hooked up to my router and I tried to connect using the internal IP of the host (i.e. the 192.168.1.x one). I think this is right because if I try to ping the same address from my laptop it succeeds with like 1ms latency.

---

