---
title: "Advice on quiet cooling fans for home build"
date: 2019-10-09
forum: Hardware
---

### Post by benawhile on 2019-10-09
Hi
After 12 years my old self build needs replacement. Please comment if you foresee any problems with my plan below:

The PSU fan was always too loud and not controllable and a quieter system is a priority.

My old system includes:

Case:     Midi Tower Foxconn microATX chassis 
Would be happy to keep this as well as it holds a 5.25” CDRW/DVD unit which works satisfactorily. 
However although I want a case with a CD/DVD slot, keeping this case is not such a big deal. The main issue would be required fan compatibility I suppose. The present case fan is 3 wire. It was so noisy  that I permanently disconnected it 12 years ago and found no problems. I am not a power user.
    
New system usage requirements:
General use and music software
I don’t do gaming or programming, don’t need special sound reproduction quality, just speed and stability with music programs.

This is my proposed bundle assembled on pcpartpicker:
[https://uk.pcpartpicker.com/user/benawhile/saved/67QQqs](https://uk.pcpartpicker.com/user/benawhile/saved/67QQqs)

AMD Ryzen 3 2200G 3.5 GHz Quad-Core Processor
Gigabyte B450 AORUS M Micro ATX AM4 Motherboard
Corsair Vengeance LPX 16 GB (2 x 8 GB) DDR4-3000 Memory (maybe only 2 x 4 GB)
Samsung 860 Evo 250 GB 2.5" Solid State Drive
Corsair CXM (2015) 450 W 80+ Bronze Certified Semi-modular ATX Power Supply

I chose the Gigabyte AORUS because out of four B450 variants it had better reviews than the DS3H. I didn’t choose the game version because I don’t do gaming, but if that version is better than AORUS I will get that instead.

I haven’t so far included a HDD. I have seen recommendations for using a SSD and a HDD for windows and linux dual boot, but will ask about that separately.

Regarding fan noise and fan control, I know nothing. Is is always necessary to use a case fan these days? Will the noise of combination of cpu, psu and case fans be quieter than my ancient psu? Is it possible to stop them running maximum in Linux and avoid overheating?

---

### Post by CatKiller on 2019-10-09
> **benawhile said:**
> 
However although I want a case with a CD/DVD slot, keeping this case is not such a big deal. The main issue would be required fan compatibility I suppose. The present case fan is 3 wire. It was so noisy  that I permanently disconnected it 12 years ago and found no problems. I am not a power user. 

You can still control the speed of non-PWM fans. The speed of PWM fans is controlled by the pulse width; the speed of non-PWM fans is controlled by the voltage. It's easier to consistently start and stop a fan at low speeds with PWM than with voltage, which is why PWM fans can get away with running at a lower speed. Neither type *has* to be run at full speed all the time. 
    
>  Regarding fan noise and fan control, I know nothing. Is is always necessary to use a case fan these days?  

That's entirely dependent on how much heat you need to get rid of, and how much airflow there is through the case without a fan. Passive cooling setups are doable with the right attention and workload. As a general rule, fans that only come on when they need to are safer. 

>  Will the noise of combination of cpu, psu and case fans be quieter than my ancient psu? 

Yes. 

> Is it possible to stop them running maximum in Linux and avoid overheating? 

Yes. The program for controlling the speed of fans is called **fancontrol**. It needs to be able to read the sensors on the motherboard to know what the temperatures are, and how to send signals to the fan controller, so support varies depending on which chips are actually used by the manufacturer. Otherwise, most manufacturers include the ability to set a fan curve in the BIOS these days, and will advertise that fact.

I favour having several really big fans that hardly ever come on with my setups. A large fan moving slowly moves a heck of a lot of air, compared to a small fan moving quickly, without making much noise. Case fans come in standard sizes, so you can see how many and which sizes your case supports. The (3) case fans in my rig aren't audible at all till they get to about 900 rpm and most of the time they're not moving at all. Modern PSUs don't self-heat as much as old ones, and they're generally put at the bottom of the case rather than the top now, so fanless or temperature-controlled PSUs are viable and common. Having a large heatsink on the CPU means that the CPU fan doesn't need to work as hard or as often. 

Noctua fans are generally well-regarded for moving a lot of air silently. They are the standard against which other fans are judged. You can find reviews of most decent fans.

---

### Post by Dennis N on 2019-10-09
Since you are buying a new SSD, I would get m.2 NVMe drive instead of SATA. You are planning to reusing old case? You need a case fan to keep components cool. m.2 drives get hotter than 2.5" drives. Fan speeds and profiles are now managed by motherboard firmware using temperature sensors. You can set the parameters you want. Look on web for reviews on fan noise levels.  I think PSU fans are very close to silent.

---

### Post by kurt18947 on 2019-10-09
I have a somewhat similar setup to what you're proposing, Ryzen 3 2200G. I'm using a few years old AMD video adapter and have no case fans, just the CPU, GPU & PSU fans. I bought a new power supply a few years ago that's pretty quiet. My computer desk is such that I don't need side panels so leave them off. Just doing general office type stuff and web browsing heat doesn't seem to be even close to an issue. Our indoor temps run about 78*F in summer. I will second the suggestion to get an NVMe SSD if you're able. I bought one of the HP920 branded devices and it's *quick*. Not especially fast to boot due to POST, perhaps 20 seconds but once running everything is pretty much instantaneous.

---

### Post by cruzer001 on 2019-10-09
Is such a large power supply really necessary with today's power efficient systems?  I would think smaller is better :)

---

### Post by MartyBuntu on 2019-10-09
> **cruzer001 said:**
> ...a large power supply...

Where are you seeing that?

---

### Post by cruzer001 on 2019-10-09
First post
> **benawhile said:**
> Corsair CXM (2015) 450 W 80+ Bronze Certified Semi-modular ATX Power Supply


---

### Post by benawhile on 2019-10-11
To cruzer
Well, I don't know. Corsair CXM 450W is recommended on a few home build combo sites. It is suggested on a "wired" article and elsewhere on this forum for comparable builds. In fact it is the smaller of those recommended that I could find.
On "pcpartpicker" my total wattage is estimated at 160w.just for the basic list above, not allowing for an extra hard drive, or any peripherals or anything else I may want to plug in or any upgrade.

---

### Post by CatKiller on 2019-10-11
A 2080 Ti is 300 W all by itself.

I wouldn't call 450 W a large supply. 500-600 W would be a "normal" range for a desktop with a GPU. More than 750 W would be "large," I would say.

A power supply that's too small is a serious problem, but there's no harm in getting a power supply that's too big other than the cost.

---

### Post by QIII on 2019-10-11
When it comes to power supplies, the bigger the better -- within reason.  Don't cheap out.  Doing so can be disastrous.

A larger power supply runs cooler when the wattage drawn by the machine is well under the rated wattage of the PS.  If you run a PS on the ragged edge trying to push hardware that adds up to a large percentage of the rated PS wattage, the PS will run hot, the fan will be on a lot and the longevity of the PS will be negatively affected.

As far as quiet fans, I'd look at Fractal Design, Be Quiet!, or Noctua.

---

### Post by TheFu on 2019-10-11
Corsair PSUs had a good reputation a few years ago based on statistics from a large, independent, PC maker, building tens of thousands of systems in a year.  I use Seasonic 80%+ Bronze which were known at the purchase time to be quiet and cool.  I haven't been in the PSU market in a few years, so all my info is out of date.

Heat that isn't generated doesn't need to be cooled. If being quiet is paramount, look at silver and gold rated PSUs.

For systems with just a CPU, onboard iGPU and 1-2 HDDs, I don't add any more cooling than the PSU fan.  My NFS server is like that, but with a 5 disk hot-swap bay which has a largish fan pulling air into the case across the drives. No other fans. It also has an external array, so cooling those disk is outside.

My main VM server has an SSD and 1 HDD inside, plus a fan-less nvidia GPU. It has a Seasonic PSU and 1 case fan, only because that case came with one.  The Ryzen 5 CPU uses the free CPU cooler that came with the CPU and it slightly overclocked using the motherboard automatic OC feature.

None of these systems has ever shown any heat warnings in system logs.

I had a "Shuttle" Core i7 from 2009 that had cooling issues according to the system logs. It had a CAD nVidia GPU. Throttled 1 or 2 cores from time to time when doing transcoding.

There it no such thing as being over-cooled.

These days, pretty much all components have built-in thermal reporting. Setup monitoring and alarming for each part.  I do the same for low battery conditions on my laptops.

---

### Post by Dennis N on 2019-10-11
> Corsair CXM (2015) 450 W 80+ Bronze Certified Semi-modular ATX Power Supply
I used this same one in my last computer build last year and I'm satisfied with it - semi-modular or modular is worth it - with the new m.2 drives you can forget about sata cables. The fan is very quiet - essentially inaudible. That computer uses Intel integrated graphics only. The box says: Corsair CX 450M - probably the same as what you are planning.

---

### Post by him610 on 2019-10-11
I too have Corsair CX450M installed in one of my homebuilt systems. It is in a Cooler Master Elite 110 case. The semi-modular design is just what one needs in one of the smaller mini-ITX cases. There have been no issues with fan noise or cooling.
What you might consider about your legacy case is the possible lack of USB-3 or USB-C ports that a more up-to-date case may provide.

---

### Post by TheFu on 2019-10-11
I had one of these [http://www.mini-box.com/picoPSU-80](http://www.mini-box.com/picoPSU-80) running a ~25W APU as a media center player in an ITX case, before I switched to Raspberry Pis.  I wouldn't hesitate to get another picoPSU for a similar, silent, requirement in a tiny case, with x86/amd64 CPU.

Lots of options available from which to pick.

---

### Post by benawhile on 2019-10-12
[I]What  you might consider about your legacy case is the possible lack of USB-3  or USB-C ports that a more up-to-date case may provide. 				 			  			   		 			 				 			 			 				

[/I]Thanks. Good point well made. I will get a new case. Choice between Coolermaster N300 and NR400. There is an option for optical drive. Prob will get NR400.

---

### Post by TheFu on 2019-10-12
Or get a USB3.2 or c hub that sits on top of the existing case with 4-8 ports for $15.  Just depends on your budget and how "clean" you want.  Or you can get one of those 3.5inch front-panel things with 57 card reader support and 4 USB 3, 3.1, 3.2 ports for $20. 
I use both of these methods with cases from 1999 and 2002, respectively.  Nothing wrong with the cases and they have good drive access already, so why spend $80 for a nicer replacement?  At least that's my thoughts.

Reuse whenever you can. Save the landfill.

Of course, I swap out MB+CPU+RAM and call that a "new computer" and don't try to sell older systems to other people.  A good argument could easily be made if you build and use a system for 1-2 yrs, then want to sell everything to someone ready to go, just add keyboard, mouse, and monitor.

---

