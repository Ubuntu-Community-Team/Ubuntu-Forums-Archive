---
title: "Getting applets to see network at startup"
date: 2008-10-20
forum: General Help
---

### Post by poit on 2008-10-20
Here's the problem:

I've got a few desktop applets that I use:

Invest,
Specto
and GoodWeather (on gdesklets)

The problem is, I'm working on a notebook computer that gets restarted a lot. Every time I start up the computer I have to wait until the network reconnects and then restart those applets. Otherwise they never see the network. (Actually, the Invest applet will eventually connect, Goodweather never will, and Specto used to reconnect but stopped when I switched to Intreped.)

Is there something I can do about this, other than manually starting these applets?
Thanks

---

### Post by shawnrgr on 2008-10-20
You could create a script that waits 10 seconds after login before launching your apps. change the wait time until it works correctly.. add the script to your sessions and log out and back in.

```
#!/bin/bash

wait 10
invest &
specto &

```

---

### Post by poit on 2008-10-21
OK, that's certainly one way to do it. The problem is, when I'm logging on to a new network it may take a minute or so to connect to the network.  I was thinking more in the lines of trying to get these apps to reconnect automatically whenever the network restarts.

---

### Post by G|N| on 2008-10-21
Specto should wait with checking until network manager is connected, so do you use network manager? And what version of specto are you using? If it is not working correctly with network manager, could you file a bug?

Thanks

---

### Post by poit on 2008-10-21
> **G|N| said:**
> Specto should wait with checking until network manager is connected, so do you use network manager? And what version of specto are you using? If it is not working correctly with network manager, could you file a bug?

Thanks

I'm using the standard Network Manager in Ubuntu Intreped. It's specto 0.2.2
I've filed a bug report with Specto. 
Thanks

---

### Post by quasimodo69 on 2008-12-03
POIT,
I am looking to get my Invest applet to even work at all.How did you do it?It was on my system when I uprgaded-using 8.10 on a 2ghz Abit home build.I have been crawling posts and google and when I open it for preferences I get the Add screen...and when I do it..it just adds google...I don't know why.There is nothing that opens to allow me to add mt own stock symbols.I see from some of the sites I have crawled looking for answers that you should also be to set up a graph feature to show historic preformace..that would be cool..I need to know how boke I am and when I can apply for food stamps from my 401k losses! :-)
  Any help would be appreciated!Thnx
Rail against the machine...micro$oft is a loser!

---

