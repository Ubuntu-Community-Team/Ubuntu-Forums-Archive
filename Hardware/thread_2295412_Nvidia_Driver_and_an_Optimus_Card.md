---
title: "Nvidia Driver and an Optimus Card"
date: 2015-09-18
forum: Hardware
---

### Post by Greatly_Discourage on 2015-09-18
Oh where do I begin.

I'm very new to Ubuntu, started yesterday in fact, but most of my time with it so far was spent wrestling with the asinine Nvidia drivers I've had to deal with. I've had these problems in the following order:

1. Steam installed properly, but I could only use the integrated intel card with my game
2. Nvidia driver gets installed, Steam refuses to start. Nvidia prime doesn't switch to my GeForce 840M card.
3. I don't remember how but I fix the Nvidia prime switch thing and reboot. After the reboot I get this weird bug that causes that black screen with the _ on the top left corner flash while showing the Ubuntu login screen every now and then. That scared me into re-installing Ubuntu, which I did.

Bonus: Countless low-graphic mode entries that I had to force Nouveau to get out of.

My current problem is that Nvidia prime refuses to switch to my 840M card.

Please, help me! My laptop is new and I was very excited to get into the Ubuntu world, but it is so discouraging that I have to pick between not using my GPU and not having a working computer at all. Here is what I get:

```
sudo prime-select nvidia
Error: alternatives are not set up properly
Error: nvidia mode can't be enabled
```

I had somehow fixed that earlier but I forgot that command but it was what caused me to get that weird bug in the first place...

Thanks in advance! Please don't take any offense, I'm sure the problem is with Nvidia here.

---

### Post by Bashing-om on 2015-09-18
Greatly_Discourage; Hi ! My welcome to the forum.

Regrets that your intro to 'buntu is  problematic. Nvidia has worked hard to resolve the problems in hybrid graphics.
let us take a look at the situation, maybe it is but a matter of the wrong driver installed ? Nvidia recommends the 352 version for the reported card. 
The terminal is where we do this work. Much easier to work in terminal for what we need to do.
To get that terminal active, one way is once on your desk top, press the key combo ctl+alt+t to activate.
Execute the following terminal commands .

Let's verify the hardware:
```

lspci -vnn | grep -i VGA
lspci -vnn | grep -i 3D

```

See what drivers are installed on the system - maybe what we have here is a conflict in drivers ?
```

dpkg -l | grep -i nvidia

```

And then take a look at the log files, see what the system reports:
```

cat /var/log/Xorg.0.log
cat ~/.Xsession-errors

```
Please place the outputs Between Code Tags - to retain formatting and readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The results of the aboves will give a strong indication of what we need to do.

[INDENT][INDENT]just a matter of setting things
[INDENT][INDENT][INDENT][INDENT]right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

