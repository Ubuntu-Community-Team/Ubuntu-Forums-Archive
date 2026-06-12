---
title: "SSH stopped working on Hardy"
date: 2008-08-23
forum: General Help
---

### Post by stim on 2008-08-23
I had a LAMP server going and was tinkering with installing an e-mail server.
I have reinstalled the server with the server edition of hardy (I was previously using the regular edition)
When I ssh into my machine, it hangs, then disconnects me.
ssh to localhost works fine, but ssh to my ipaddress does not work(I can connect, but it times out and I get dropped)

Is there a firewall installed by default with the server?
Since 6.06, all Ive had to do was install openssh and it worked. 
Yes, my router is configured to forward port 22. 

```
[20:01:06]      Sent password.
[20:01:10]      Sent password.
[20:01:10]      Access granted.
 
```

After this is hangs and then terminates. 
Any help? This kind of stuff makes me want to put down ubuntu and go back to windows.  I have some fundamental piece of software that works just fine, I reinstall/upgrade and it no longer works for an unexplainable reason.

Any help is appreciated. 
Where/what are the appropriate log files I should use to debug.

---

### Post by braddcadd on 2008-08-24
Some of these guys say it works wired but not wireless.  Is that the case for you?  Are you running ndiswrapper?

[http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+hardy](http://ubuntuforums.org/showthread.php?t=838873&highlight=ssh+hardy)

---

### Post by stim on 2008-08-24
brad,  I actually resolved the problem yesterday by  using ndiswrapper instead of the proprietary "fw" driver for my bcm43xx series card.
Thanks !

---

