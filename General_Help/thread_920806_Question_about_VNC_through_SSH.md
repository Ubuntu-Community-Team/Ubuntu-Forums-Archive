---
title: "Question about VNC through SSH"
date: 2008-09-15
forum: General Help
---

### Post by aetherh4cker on 2008-09-15
So I have two computers on my network.

PC1 has VNC and SSH.
PC2 just has VNC (no SSH).

While I'm at work/school/wherever I like to remotely manage my machines through VNC by tunneling through SSH.  My question is:  Is there a way I can tunnel through my SSH connection on PC1 to access the VNC on PC2?

I would really prefer to avoid enabling SSH on PC2.

I usually use PuTTY and TightVNC for my remote stuff...

... and advice?  I look forward to your replies!

---

### Post by eldragon on 2008-09-15
absolutely.....
if they are on the same LAN and from PC1 you can connect to PC2's vnc server then
```

$ ssh -L 5900:LAN_IP_OF_PC2:5900 username@WAN_IP_OF_PC1

```

fill in the blanks ;)

that will connect port 5900 on the client you are using, to the port 5900 at PC2. instead of PC1

---

### Post by bodhi.zazen on 2008-09-15
```

ssh -L 5900:LAN_IP_OF_PC2:5900 username@WAN_IP_OF_PC1 **[color=blue]-Nf[/color]**
```

the -Nf flags put ssh in the background ...

---

