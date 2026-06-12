---
title: "Omg laptop overheating"
date: 2010-12-02
forum: Hardware
---

### Post by Moldjelly on 2010-12-02
THE FAN DOSENT WORK ITS AN TOSHIBA M505-s4940 PLZ HELPZZZZZZZZZZZZZ

---

### Post by cascade9 on 2010-12-03
> **UnbeatableMachines.com said:**
> Lots of online stores have after market coolers for laptops that typically go under the laptop and fan it. I don't have experience using them but some people swear by them.

Try googling "laptop cooler" to find one that would fit your laptop.

Those 'laptop coolers' arent meant to keep the laptop cool with no CPU fan. They are meant to reduce the temprature on a fully working laptop (because some of them get very hot...remember the swedish guy who burnt his genitals when using a laptop on his lap in the nude?). 

If you try using a laptop cooler with a broken/non functional CPU fan, it WILL overheat and possibly cause permanent  hardware damage.

---

### Post by Moldjelly on 2010-12-03
The fan isn't broken it works in windows 7 but not ubuntu or xubuntu

---

### Post by philinux on 2010-12-03
> **Moldjelly said:**
> THE FAN DOSENT WORK ITS AN TOSHIBA M505-s4940 PLZ HELPZZZZZZZZZZZZZ

This might help.
[http://askubuntu.com/questions/2536/my-toshibas-fan-does-not-work-automatically](http://askubuntu.com/questions/2536/my-toshibas-fan-does-not-work-automatically)

---

### Post by Kixtosh on 2010-12-03
I was worried about this on one of my laptops, so here is what I did. Firstly, some laptops run hotter than others. My Portégé R205 is almost always silent in Ubuntu, but far more noisy in Windows (it works far more frequently). This worried me initially, so:

1) I installed the sensors applet from the Ubuntu Software Center (Applications Menu, in the top left panel) that allows me to show the CPU temperature in the panel. Once the applet has been installed, it can be added to the panel with a simple right mouse click.
2) I noticed that on the Toshiba Portégé R205 the CPU frequently sits at 60°C with _no fan running_.
3) As soon as the temperature rises to 64°C, the fan starts running at a moderate speed.
4) Video use, such as YouTube, sends the CPU up to 75°C and the fan runs at full speed (much noisier).
5) The CPU never seems to get any hotter than 75°C, but this is about 10-20°C hotter than the temperature observed on another laptop.
5) I checked the Intel specifications for my CPU, from Intel's website and it turns out that it is normal for this model of Pentium 4 Mobile to hit even 90°C, so I don't worry about it any more.

_My Conclusions:_ It may not always be a cause for concern that you cannot hear the fan running, unless you check what is normal for your model of CPU. The documents available can be daunting to read, but the information is buried in there somewhere.

The fan may run differently when using Windows vs. Ubuntu, and this may not be a cause for concern either.

For comparison purposes, in my experience other laptops may have the fan running at all times, no matter what the temperature, even from the same manufacturer. That does not mean that a silent laptop fan is not working correctly.

---

### Post by Dlambert on 2010-12-03
Have you tried dialing down cpu scaling?

---

### Post by Dlambert on 2010-12-03
Right click on your panel and add the Cpu frequency monitor applet, and then dial it down to lowest settings and see if that helps cool it down.

---

### Post by Moldjelly on 2010-12-03
I don't want to underclock it to get cooler that would just be a half-a%% job i want to fix the fan to where it works in ubuntu lol

---

### Post by Kixtosh on 2010-12-03
> **Moldjelly said:**
> I don't want to underclock it to get cooler that would just be a half-a%% job i want to fix the fan to where it works in ubuntu lolI agree: there's little to no point in using Ubuntu (or Xubuntu) if you have to limit the CPU in order to do so. What makes you think it's getting hot? You cannot rely on the case feeling hotter than you might like for this. I checked your CPU, and it seems to be a Pentium Dual-Core T4200, capable of fairly high temperatures, as described in this link (it should not ever get close to TJunction, which is listed as 105°C, and which would theoretically trigger a failsafe shutdown):

[http://ark.intel.com/Product.aspx?id=37251](http://ark.intel.com/Product.aspx?id=37251)

I'd install the sensor applet I mentioned, or at least check the temperature with something such as the "System Profiler and Benchmark" (which is also available from the Ubuntu Software Center - it's available in your menus if you're using Xubuntu, since that doesn't have the "top panel" I mentioned earler). I wouldn't be concerned unless you're reaching 80°C without the fan ever turning on.

---

### Post by Jimtheplanner on 2010-12-04
Hi Folks I've done a few experiments. Indeed I did a back to back installation check against Mandriva 2010.1. Where Mandriva ran on average a good 10 Deg C cooler....

The best option I can find is to start my Dell 1545 on the battery then after a minuet or two plug in the mains. This way things run cool.....

Best regards
Jim

---

