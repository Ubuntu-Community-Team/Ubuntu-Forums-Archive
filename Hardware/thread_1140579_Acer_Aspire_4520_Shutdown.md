---
title: "Acer Aspire 4520 Shutdown"
date: 2009-04-27
forum: Hardware
---

### Post by razor7 on 2009-04-27
Hello...qhen shutting down this laptop with Jaunty, the screen gets black and I have to press enter key to finish shutdown ¿¿??

Please advise

Thanks a lot!

---

### Post by jomacintosh on 2009-06-19
I have the same issue with my laptop.  I find even touching the touchpad will finish the shutdown.

I don't know why it happens, but I'm happy that this is the only real issue I am having with my setup. Hopefully your system is running as well as mine.

---

### Post by redwinedrummer on 2009-06-20
I have the same model and the same issue.

I've been working on this problem and managed to isolate it. It's being caused by the bluetooth service. The bluetooth killswitch has nothing to do with it.

To confirm, please input this command at a terminal:

```
sudo /etc/init.d/bluetooth stop
```

Then shutdown your system. It should power down normally. If this reproduces it, then we're sure of the problem.

Alternatively, you can shut down your system (with the bluetooth service running) and wait until you reach the blank screen. Simply press your bluetooth switch and it will power down. In this sense, the bluetooth switch is actually a better power button as it let's the system shut down properly, as opposed to holding the power button down.

Unfortunately, I haven't found a solution, but maybe someone in the forums can help us out.

Personally, I don't mind with bluetooth enabled during startup, but with this problem, it's important bluetooth is disabled at shut down. I think it's only a matter of modifying the shutdown script to properly stop the bluetooth service.

---

### Post by felipefoz on 2009-06-30
> **redwinedrummer said:**
> I have the same model and the same issue.

I've been working on this problem and managed to isolate it. It's being caused by the bluetooth service. The bluetooth killswitch has nothing to do with it.

To confirm, please input this command at a terminal:

```
sudo /etc/init.d/bluetooth stop
```

Then shutdown your system. It should power down normally. If this reproduces it, then we're sure of the problem.

Alternatively, you can shut down your system (with the bluetooth service running) and wait until you reach the blank screen. Simply press your bluetooth switch and it will power down. In this sense, the bluetooth switch is actually a better power button as it let's the system shut down properly, as opposed to holding the power button down.

Unfortunately, I haven't found a solution, but maybe someone in the forums can help us out.

Personally, I don't mind with bluetooth enabled during startup, but with this problem, it's important bluetooth is disabled at shut down. I think it's only a matter of modifying the shutdown script to properly stop the bluetooth service.

I uninstalled bluetooth services here, and still got the problem
I managed to isolate the problem, as people has been talking that there is something about the wireless and network, if you take off the splash, you'll see in the shutdown, problems with ifupdown service
I did a script, for now it's working for me,
let me know if it works for you too
directions in:

[http://parecedificil.blogspot.com/2009/06/problemas-no-desligamento.html](http://parecedificil.blogspot.com/2009/06/problemas-no-desligamento.html)

I wanted to post it here, but I don't have time now
See you

---

