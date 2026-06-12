---
title: "Problem with remote desktop"
date: 2009-11-18
forum: Hardware
---

### Post by SkyFly on 2009-11-18
Hi.

I've been trying to set up my stationary computer as a remote desktop server (not by the internet, but on LAN). I have tried both Ubuntus own remote desktop viewer and now have I tried with GRDC remote desktop viewer. I have tried with VNC4server (I'm using that right now) and also Ubuntus own remote desktop server program. But it all ends up with the same problem.

I can connect, I can see the screen and I can move the cursor. But if I click on an application to start it will start, but the laptop dosen't show that. The view from the laptop never updates when the screen on rd server updates. 

This problem isn't just when I start an application. If I open a meny it doesn't update, if I write in the terminal or anywhere else it doesn't update.

What's the problem?

Laptop specs:
2.0 ghz Centrino processor 
2 gb RAM @ 667 mhz RAM
Intel mobile 4-series graphic card

I hope my spelling isn't to bad, it's quite late.

Cheers

/SkyFly

---

### Post by SkyFly on 2009-11-19
This problem was also with 9.04 as 9.1

---

### Post by franklamoureux on 2010-04-03
I had the same problem with 9.1. I tried all encoding protocols from the remote host, still no luck. Initial screen shows up, I see the cursor (dot) moving, clicks are being reflected in Ubuntu but the where vnc viewer is running, nothing gets updated.

-- Update
Using the built-in Remote Desktop Server (vino) I was having the same problem. Uninstalling it and using x11vnc resolved my problem. Follow this thread for a success : [http://ubuntuforums.org/showthread.php?t=45565]("http://ubuntuforums.org/showthread.php?t=45565")

---

### Post by IcarusR on 2010-04-03
Much faster & more usable with FreeNX or Nomachine server & nomachine client.

[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

[http://www.nomachine.com/download.php]("http://www.nomachine.com/download.php")

Can't find the thread with instructions on setting up nomachine server & client.

Alternately if you are just administering the server then could use webmin.

[http://www.webmin.com/]("http://www.webmin.com/")

---

### Post by 2hot6ft2 on 2010-04-03
> **IcarusR said:**
> Much faster & more usable with FreeNX or Nomachine server & nomachine client.

[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

[http://www.nomachine.com/download.php]("http://www.nomachine.com/download.php")

Can't find the thread with instructions on setting up nomachine server & client.

Alternately if you are just administering the server then could use webmin.

[http://www.webmin.com/]("http://www.webmin.com/")
Somehow I doubt the OP is still looking since it was back in November of last year but there's one in my sig.

---

### Post by IcarusR on 2010-04-03
Silly me should have taken not of the dates when I read it through !

That's what happens when people post to a dead, four & a half month old thread !!

Always better to start a new one.

2hot6ft2 I was trying to find the thread I followed to set up nomachine server without freenx.

---

