---
title: "Acer Aspire 3680 overheating problem"
date: 2011-04-10
forum: Hardware
---

### Post by georgeguitar on 2011-04-10
Hi everybody,

I got an Acer Aspire 3680 laptop and I have a problem with the cooler fan.

This laptop came with Windows Vista from factory but the performance was very bad, so I decided to install Ubuntu (many versions) and after using the laptop for a while it gets very hot, I tried using the laptop with Win XP as well and it is the same.

What happens is that this laptop seems to have a special software bundled to Windows Vista from factory, and of course everything works fine: the thermal sensors and the cooler fan. The problems comes when the laptop has a different operative system, the cooler fan doesn't work properly and I believe it is due the lack of the factory software which is not available for other operative systems. (it seems that is a secret between Acer and Microsoft, like a trap, or either you use the original software or burn your laptop by using a different OS).

At the beginning I though that the problem was dust and dirty, so I dissemble the laptop I found that the cooler fan is fine, it is like new, almost no dust, besides that when I switch on the laptop the fan works at maximum speed (it switches off after some seconds, this is normal, it was always like that). I read that updating the BIOS can fix the problem, I tried and even updating de BIOS seems not to solve the problem.

I couldn't fine enough information about Acer's cooler fan technology but I guess Acer uses some sort of Linear voltage fan regulation technology instead of Pulse-width modulation technology like the majority of this kind of devices. Due to this lm-sensor and pwmconfig doesn't work to control the cooler fan. I even try with Fancontrol under Win XP and it doesn't work.

What really happens is when the temperature arises to 50°C, the cooler fan starts working at very slow speed (I believe the fan doesn't get the 5 volts, which I presume it is the voltage to make the fan works at maximum speed) therefore causing the overheating problem.

I read that a lot of people have the same problem concerning to GNU/Linux systems and laptop overheating problems, but very few of them were able to solve the problem, well in fact, they found a very bad solution: going back to Windows.

I was thinking to unplug the cooler fan from the mother board and plug it to a external energy source or maybe plug it to the USB port, so the fan would receive the 5 volts and will work at maximum speed. The only problem is that I don't have any technical information about laptop coolers (3 wires), and I don't want do damage the cooler by making experiments.

Any ideas, suggestion?. What can I do to switch the cooler fan at maximum speed?

Thanks before hand.

---

### Post by matty abbo on 2011-04-10
if you unplug the fan from the mother board then the laptop will start up and immediately shut down so that it does not completely overheat, you could try buying a laptop cooling board that plugs into a USB port and has 2 or more fans, it should work to help keep the laptop cooler

---

### Post by georgeguitar on 2011-04-10
Hi Matty Abbo,

Thank for the reply.

I didn't mean to unplug the fan and leave it like that. I would't use the laptop without proper cooling fan.

What I meat was to plug the fan to a 5 volts external source energy (I guess the fan will work at maximum speed) and then switch on the laptop. 

In that way the laptop won't overheat at all. But I don't have the fan wire schematics to do it properly.

Any suggestions?

---

### Post by matty abbo on 2011-04-10
heyy

if the main system fan (the one over the CPU) is unplugged from the motherboard then the system will always shut down, but if you took the fan off and cleaned it and put some more thermal paste over the area where fan or heat sink sits it should help with cooling but ultimately, a laptop cooling board would help the best aswell as the basics, keep the vents clear, don't let the laptop sink into a cushion or quilt.

blehh essay/lecture over xD

---

### Post by georgeguitar on 2011-04-10
Hey matty abbo,

Sorry for the misundestanding, yes of course unplugging the fan will be a very bad idea.

I just want to unplug the fan wires (3 cables) and pug then to an external energy source (5 volts), does it has sense?. I wont take out the fan from the main board, I don't want to burn my laptop.

By the way, I did clean the fan and added thermal paste where fan or heat sink sits, but the problem is not the fan itself, the fan is new. The problem is the software that controls the fan, it only works properly with Windows Vista (the one that came from factory), may be is a problem with ACPI compatibility.

I also tried with a cooling board, I did help that much, the laptop design doesn't have many ventilations holes, only in the cooling place mainly. The cooling board only cools the plastic not the circuits.

Do you know how to use fancontrol program?

I have this messages:

[I]Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file[/I]

Thanks!

---

### Post by matty abbo on 2011-04-10
hey

yess, i know how to use fan control programs although i never use them, although if there are very few cooling vents it will always be very warm/hot but your type of laptop's biggest con is that it over heats easily even on idle, but i wonder if you could install the fan control program under wine at all if it would interact with the hardware....
and yes the attatching the fan to a external supply while keeping it plugged into the motherboard, but you would been to make sure its correctly wired up otherwise your computer could go boom

(when getting a new laptop choose Lenovo as most of their laptops are ubuntu ready)

---

### Post by Yellow Pasque on 2011-04-10
> **georgeguitar said:**
> I just want to unplug the fan wires (3 cables) and pug then to an external energy source (5 volts), does it has sense?.
No, if the mainboard doesn't detect a fan plugged in or thinks it has failed (0 RPM), it probably won't work.

> Do you know how to use fancontrol program?
It usually doesn't work on laptops because they use ACPI to control the fan. To get the configuration file, you have to run this first:
```
sudo pwm-config
```

---

### Post by georgeguitar on 2011-04-12
Hi Temüjin,

> No, if the mainboard doesn't detect a fan plugged in or thinks it has failed (0 RPM), it probably won't work.

What you said it's very bad news, I was hooping that the wire issue could be the solution.

What about if I leave the yellow cable plugged to the mainboard. If I'm not wrong, that's the cable that transmits the fan's info to the mainboard.

About pwm-config, you are right, it didn't work with my laptop, I got this message:

[I]$ sudo pwmconfig 
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
[/I] 

That's why I wrote at the beginning that Acer didn't use PWM technology to control the fan, it has to be something like Linear voltage fan regulation technology, otherwise pwmconfig will work.

At this point any ideas about what can I do?

---

### Post by dubbob on 2011-05-25
I am also suffering from the same problem with an Acer 5315 celeron with 1Gb RAM.

Bought this little laptop used with Vista pre-installed. Reformatted and installed 11.04
After a period of use laptop goes into thermal shutdown and cooling fan makes no effort to start.
On restart, Cooling fan will cut in but dies out again after booting from GRUB.

There are a lot of posts on the Ubuntu forums with solutions to this problem. To be honest many of them are slightly over my head. Has any anyone developed a straightforward solution or can explain to me how to sort this out once and for all?

By the way........ if i let the laptop get screaming hot (yes I know, not good) restart and let the system hang at GRUB stage, fan will slowly start to come to life. I can then select a kernel and make use of the laptop but the fan eventually runs at full speed until system is restarted.

I appreciate any and all help suggestions......... Cheers, Bob. :)

---

