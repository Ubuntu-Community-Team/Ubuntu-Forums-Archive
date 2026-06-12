---
title: "Older HP laptop overheating -"
date: 2009-01-25
forum: Hardware
---

### Post by xarte on 2009-01-25
I'm having trouble with my HP Compaq nx6125 overheating on any Ubuntu based distro. Hardy, Mint and Progex are all cooking it. No, I can't tell you the exact temp as I haven't managed to get a temperature sensor working yet, but it is almost too hot to touch, far too hot to use on my lap. NO, it isn't a dirty fan as it was running just fine on windows, and NO I don't want to turn off all the processes and not play Flash. IT IS A BUG and it shouldn't be running this hot.

Spent hours googling. Installing kpowernow and tweaking something (think I had to uninstall some other power manager which had disabled the cpu scaling option) was promising but no joy. 

I think the real problem is with the fan controls. This model has some sort of power management built into the bios and it seems that must conflict somehow with the linux kernel? Maybe?

I've found one informative page on the next-model-up, and I hope that these fixes might work for my computer. However I've had pretty mixed results whenever I start tinkering with things and I really don't know what I'm doing.

[http://www.wolframschenck.de/nx6325.htm](http://www.wolframschenck.de/nx6325.htm)

Patching a kernel is probably something I'll screw up, so if I can get any advice on dealing with this it would be appreciated. I've seen quite a lot of questions about notebooks overheating so I think I won't be the only person who'll make use of any information. Most of the solutions so far are pretty useless (clean your fans and install a temperature sensor... not going to fix a bug, really....)

I hope I can get this sorted, as the Ubuntu based distros are really my favorite. I've found most of the others I've tried quite frustrating, especially with wireless support or sound issues.

thanks!

---

### Post by linux_tech on 2009-01-25
Cleaning the dust out is a good idea, on laptops, just lift off the keyboard and then with a can of air, spray the dust out away from it. You should be able to see the air vents on the back of the case, w/ some copper cooling fins. The dust usually gets stuck in the cooling fins and causes it to run hotter.

If you havn't got a good temperature gauge to monitor cpu temp, then you should install one first. Here is a temp sensor pkg you can install-
[http://www.gnomefiles.org/app.php?soft_id=1065](http://www.gnomefiles.org/app.php?soft_id=1065)
You can also install sensors-applet to show CPU, GPU, and HD temperatures.
```
sudo apt-get install sensors-applet
```

To cool the laptop, there are two common ways- regulate the fan, when it turns on or off, as well as speed Another thing you can do is change the cpu frequency scaling to make it run cooler, both methods often work.

To regulate the fan speed you want to install i8kutils/gkrellm
[http://packages.debian.org/etch/i8kutils](http://packages.debian.org/etch/i8kutils)

Enabling CPU Frequency Scaling
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

Using cooling mats also help keep the laptop cooler-
[http://www.targus.com/us/accessories_cooling.asp](http://www.targus.com/us/accessories_cooling.asp)

---

### Post by xarte on 2009-01-26
It is NOT, I repeat NOT a problem withe dirty fans they are CLEAN. (I swear I'll SCREAM next time I see a fix telling me to clean the darn fans!)

CPU scaling doesn't seem to be the problem either, however your fix for the fans might well work, hopefully that will do the trick.

I've already selected 'always on' in bios.

I shouldn't have to use a cooling pad - if I do, there's something wrong. It's a 64 bit processor and has always run at a comfortable, warm but not hot temperature. 

sensors-applet was just what I was looking for for some solid figures though, thanks. (though "scorching hot to the touch" is a sufficient alarm bell for me....)

---

