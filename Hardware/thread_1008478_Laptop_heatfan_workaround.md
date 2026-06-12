---
title: "Laptop heat/fan workaround"
date: 2008-12-11
forum: Hardware
---

### Post by brandon88tube on 2008-12-11
**[color=red]This will cause your CPU to run faster causing it to get hotter, but in turn make the fan(s) come on. Make sure that this is cooling down your laptop otherwise this method is probably not for you. Use at your own risk.[/color]**

[size=5]Description:[/size]
This is a workaround for those using laptops that are experiencing heat problems caused by the fan(s) not turning on/slow speeds or only turning on/speeding up at high CPU frequencies. This seems to be in all variations(Gnome,KDE...) of Ubuntu and is not just limited to Ubuntu, but to other distros such as Fedora. **[color=red]This workaround will cause you to consume a little more battery life, but I would rather sacrifice some battery life compared to frying my laptop from it overheating.[/color]**

[size=5]Possible Cause:[/size]
The culprit seems to be the battery saving feature that scales the CPU frequency up or down. I am not sure if it is how it sets the fan speeds for certain frequencies or what, but I do know that it is causing the problem.

[size=5]Workaround:[/size]**> for [color=orange]GNOME[/color]** as KDE might be slightly different

**A little workaround that I use is to turn off the CPU frequency manager.**
**1.** Go to System > Administration > Services then scroll down in the list and uncheck CPU frequency manager(powernowd).
This will set your CPU frequency to its highest.
Note In other distros such as Fedora it is called by another name, but should have a description that talks about scaling the CPU. Also the location of Services may be located in another place depending on the distro.

**If you wish to have control over what frequency it is set at just add the CPU Frequency Scaling Monitor to one of your panels.**
**2.** Right-click the panel and select Add to Panel. Scroll down in the list and you should see CPU Frequency Scaling Monitor, select it. This will show you a little CPU image with the frequency number besides it.

**To select your desired frequency.**
**3.** Click the new CPU icon and it should have a list of frequencies to choose from and other modes(Conservative, Ondemand, Perfomance, Powersave) [b][color=red]Be warned that selecting a low frequency, Ondemand or Powersave will cause the heat issues again. I am not sure if Conservative will cause any issues or not so it is best not to choose it. It is best to select either the top two highest(preferably the highest) frequencies or select Performance.



Note: When running off battery power and the battery's power starts to run low, the computer will most likely set your CPU frequency to the lowest levels. I am not sure if you can change this or not. [/color][/b]


*[b][size=1]Let me know if this has helped,
Brandon[/size][/b]

**EDIT: Some other users have brought to my attention a good tip that I forgot to mention. That is to try and clean your fan out as well. You never know it might just be blocked up with a ton of junk.**

---

### Post by Lyconyx on 2008-12-15
Hmm interesting problem, I find ubuntu is nicer for the fan on my laptop; windows xp use to run it all the time even in cold rooms (to the point someone asked if it was asthmatic!) With ubuntu it runs occasionally and has kept it at an alright temperature so far (finger's crossed).


Lyconyx

---

### Post by fghi906 on 2008-12-15
**[size=10pt]Pearlove Jewelry Inc[/size]**[size=10pt]., Chinese **online wholesale jewelry** store, is a professional wholesaler and supplier of **Chinese cultured pearls**. All pearls are directly from **pearl farms** in China. Pearlove&#8217;s pearl farm lies in Liusha harbor, Zhangjiang, where are known as "County of Akoya pearls"; It is professionally engaged in the pearl breeding, pearl deep process, pearl grading, pearl string and pearl production. Pearlove sells pearls in mainland China and Hong Kong, and begun to export and wholesale pearl strands and jewelries directly from family pearl farms via the Internet from 2007. Pearlove culture pearls in its own pearl farm and make jewelries in its own factory, so pearlove can offer the world's **finest pearls** with most reasonable prices. Now Pearlove&#8217;s **online jewelry store** mainly wholesale **freshwater & Akoya pearl jewelry** --- [/size][size=10pt][[color=windowtext]pearl necklaces[/color]](http://www.pearlove.com/products.php?cPath=1)[/size][size=10pt], [/size][size=10pt][[color=windowtext]pearl bracelets[/color]](http://www.pearlove.com/products.php?cPath=4)[/size][size=10pt], earrings, pendants, and rings, coral jewelry, **turquoise jewelry**, crystal, jade, **shell jewelry** and [/size][size=10pt][[color=windowtext]gemstone jewelry[/color]](http://www.pearlove.com/products.php?cPath=6)[/size][size=10pt]. Most of the jewelries are handmade. The online jewelry store also offers jewelry raw materials - freshwater pearls, **Akoya pearl beads** & strands, **coral beads**, turquoise, shell beads, **jewelry fittings**, jewelry making kits. **Pearlove Jewelry** has own jewelry designers and keep continuing to design new jewelry styles --- **Crystal**** jewelry**; **pearl jewelry**, **bridal jewelry**, **Christmas pearl jewelry**, and beautiful **party pearl jewelry**. Customized jewelry designs are welcome as well. In Chinese pearl jewelry industry, Pearlove is not enough a big guy, but the Professional Foreign Trade, Good English Communication, Product Quality, Competitive Price and On-time Delivery earn Pearlove the reputation from our clients all over the world. Pearlove&#8217;s faith is to provide as best service as possible for all clients [/size]

---

### Post by kefurd06 on 2008-12-15
is there some way to test to see if my system is affected? (without overheating my dual cores?)

---

### Post by brandon88tube on 2008-12-15
> **kefurd06 said:**
> is there some way to test to see if my system is affected? (without overheating my dual cores?)

This may sound stupid, but physically feeling the laptop for heat is always a good step. In my case it was on the left side where all of my ports were. The actual ports would feel really hot when just touched. Then right above the ports close to the keyboard, I could feel the heat coming through the case.

---

### Post by Nycticorax on 2008-12-16
You can monitor the relevant temperatures, as well as other things such as fan activity if your hardware supports it, using the lm-sensors package. Once installed the command 'sensors' produces output like this on my laptop: (the two coretemp entries are meaningful; the 26.8 deg readings are the result of imperfectly functioning ACPI on my system I think)

~> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.8°C  (crit = +100.0°C)                  
temp2:       +26.8°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +44.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (crit = +100.0°C)                  


With lm-sensors installed there is also a command 'sensors-detect' that attempts to characterise the hardware-motoring capabilities of your machine, and ensure that the relevant kernel modules are loaded. It needs to be run with root permissions.

Dan

---

### Post by kefurd06 on 2008-12-16
ha. 55C and no extra fan action. lame.

---

### Post by Henque19 on 2008-12-18
I think I suffer from this problem too. I'm trying to get an old HP Omnibook 500 to work with Ubuntu 8.10
When I let it work hard for a while (SuperPi for a few minutes) suddenly I hear a click (from a relay or something) and it dies.
I tried disabling the CPU frequency manager, but since the hardware doesn't support frequency scaling(I think...), I can't see how that would help me.

Does anyone have an idea why this happens? Are there any system logs that can give me any clues?

/Henrik

---

### Post by brandon88tube on 2008-12-20
> **Henque19 said:**
> I think I suffer from this problem too. I'm trying to get an old HP Omnibook 500 to work with Ubuntu 8.10
When I let it work hard for a while (SuperPi for a few minutes) suddenly I hear a click (from a relay or something) and it dies.
I tried disabling the CPU frequency manager, but since the hardware doesn't support frequency scaling(I think...), I can't see how that would help me.

Does anyone have an idea why this happens? Are there any system logs that can give me any clues?

/Henrik

That is interesting that a laptop doesn't support CPU scaling to save on battery life. Also to me it sounds like some other hardware issue that is causing the problem, like a bad hard drive. They tend to start clicking when they are dying. Not sure though, so I would recommend trying to make a thread about it if you can't find anything by searching.

---

### Post by xelxel on 2008-12-20
Just in case you experience overheating issues with your laptop, and before / after trying the above suggestions...

CLEAN OUT THE CPU FAN!

I pulled a dustrat that was so welldeveloped i wouldn't be surprised if it had communicationskills.

---

### Post by AlexBellisBrown on 2008-12-20
Agree with above, my fan used to run all the time, i opened it, gave it a good clean (the dust gets caked to the blades) and perfecto... fan was much quieter AND turned itself off from time to time. :)

---

### Post by giantoz on 2008-12-20
I've found that turning off tracking and indexing helps for me as well.

turn off tracking: system-preferences-sessions-uncheck tracker applet

turn off indexing:  system-preferences-search and indexing- uncheck both enable indexing and enable watching

---

### Post by Dutchmaster on 2008-12-21
With my laptop, it's Ubuntu and it's siblings only that this is a problem.

I had to go to another distro to avoid cooking my cpu.

Try an rpm distro. Debian, drealinux, and sidux seem to also be ok with it, as is Mepis.  

(forgive me for being a distro hopper sometimee - it's fun ;))

---

### Post by k3lt01 on 2009-01-01
I have turned off the CPU Frequency Manager and my laptop is still extremely hot to touch.

This is a new thing for my machine, up until a couple of weeks ago it has been fine with regards to running temp but all of a sudden it is really really hot to touch. The touch pad can burn you if you keep your finger on it, no I'm not exaggerating, also the laptop housing near the keyboard is getting extremely hot to touch.

I think I'll take the base off and see what the fan looks like and give it all a blow out.

---

### Post by joshh88 on 2009-01-01
This is the exact reason why I keep my Zalmann Aluminum cooling base within reach fro my laptop. After installing Ubuntu I noticed that the laptop gets darn near unbarebly hot. The Zalmann makes quick work of it and I can turn the fans down after cooling it off to maintain a suitable temperature.:

---

### Post by brandon88tube on 2009-01-02
> **k3lt01 said:**
> I have turned off the CPU Frequency Manager and my laptop is still extremely hot to touch.

This is a new thing for my machine, up until a couple of weeks ago it has been fine with regards to running temp but all of a sudden it is really really hot to touch. The touch pad can burn you if you keep your finger on it, no I'm not exaggerating, also the laptop housing near the keyboard is getting extremely hot to touch.

I think I'll take the base off and see what the fan looks like and give it all a blow out.

I'm curious, did you ever set your CPU frequency or not? You didn't mention that so I was wondering. If you didn't do that, I would give it a try. Remember the highest frequency is probably the best bet as it should have the fan kick on more or on constantly.

---

### Post by k3lt01 on 2009-01-02
> **brandon88tube said:**
> I'm curious, did you ever set your CPU frequency or not? You didn't mention that so I was wondering. If you didn't do that, I would give it a try. Remember the highest frequency is probably the best bet as it should have the fan kick on more or on constantly.Nope, I didn't. I took the base off the laptop today and blew the dust out of the fan that I could. The laptop is now running noticeably cooler, still not perfect but alot better than it was.

---

### Post by semi_fiction on 2009-01-03
> **Henque19 said:**
> I think I suffer from this problem too. I'm trying to get an old HP Omnibook 500 to work with Ubuntu 8.10
When I let it work hard for a while (SuperPi for a few minutes) suddenly I hear a click (from a relay or something) and it dies.
I tried disabling the CPU frequency manager, but since the hardware doesn't support frequency scaling(I think...), I can't see how that would help me.

Does anyone have an idea why this happens? Are there any system logs that can give me any clues?

/Henrik

There is a kernel module package for Omnibook laptops that you can install, it also works for Toshiba Satellite L305-x laptops.
You can get it here: [http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20071217-1_all.deb]("http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20071217-1_all.deb")

---

### Post by psihodelia on 2009-01-03
Some Tips:
1. Install Linux-PHC kernel patch and undervolt your CPU
2. System->Administration->Services
Turn on only "powernowd, gdm, acpi, apmd, dbus". Turn all other services off.
3. System->Preferences->Sessions
Turn off all what has Tracker in its name.
4. Install fresh video card drivers. For Nvidia, go to nvidia.com, download new beta driver and install it from terminal by "sudo sh ./NVIDIA-driver-name".
5. Install AdBlock addon for Firefox Web-Browser and block all flash-animation (by blocking all *.sfw) but youtube.com and video.google.com or any other site you need, you can make some exceptions for them. But remember, that thanks to proprietary crap software, flash animation consumes enormous CPU and GPU time.
6. System->Preferences->Appearance->Visual Effects set to None

---

### Post by kefurd06 on 2009-01-03
and the previous version of ubuntu? does it have this same bug?

---

### Post by Oram on 2009-01-04
My laptop would overheat in XP the most, Vista being the only OS I could run. I tried Ubuntu 8.04 which worked perfectly on my old laptop(Got a new one start of school this year). Ubuntu 8.04 would overheat when ever I had my computer on to long.  This almost made me go back to Vista.  Finally, I upgraded to 8.10 and everything was fixed.  Even when I run games in Wine like CoD4 it doesn't overheat. :) so 8.10 was the fix for me.

---

### Post by linux_tech on 2009-01-04
If you don't already have it, you can install sensors applet that will show the HD, CPU, and GPU temps.

```

sudo apt-get install sensors-applet

```

---

### Post by Cloudy on 2009-01-05
Hmmm.. just tried this (my laptop just recently started doing this - a few days ago the fan worked just fine) and it doesn't seem to be helping. Oh well, I suppose I'm going to go clean the fan again and hope it helps.

---

### Post by brandon88tube on 2009-01-05
Yeah, cleaning the fans is another good step to try and fix the problem, but I am curious about this kernel patch that was mentioned. What does it patch?

---

### Post by kefurd06 on 2009-01-05
just a side note.. using a hinged laptop tray that raises your laptop (and fan since it's on the bottom of the laptop) off your desk will drasticly reduce the amount of heat that builds up. i've been using one for a year and my fan rarely kicks up in vista, even when playing World of Warcraft. XD

---

### Post by angelsniper45 on 2009-01-11
thanks for this, been trying to figure out why my laptop kept overheating.

---

### Post by brandon88tube on 2009-01-11
No problem, just trying to help out the best I can.

---

### Post by xluryan on 2009-01-15
I'm hoping someone in this thread can help me. I'm desperate for a solution! My problem is, my fan ***won't turn off***.

I have an HP Pavilion TX 1000.

I suspect the video card; my sensors-applet shows all other temps as normal, but the video card is maxed out on the temp graph. I've installed *tpfand* to try to control the fan, but it requires the thinkpad_acpi module. Here's what I get when I try to modprobe that:

```

$ sudo modprobe thinkpad_acpi
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.27-9-generic/kernel/drivers/misc/thinkpad_acpi.ko): No such device

```

If anyone has any suggestions I'm more than willing to try them out. Thanks in advance!

---

### Post by odelay on 2009-01-15
Sharing Rhythmbox over a network was killing my CPU (DAACP I think?).
Whenever Tracker starts indexing there's also a massive heat up.

Just curious, how involved is cleaning your fan?

---

### Post by k3lt01 on 2009-01-15
> **odelay said:**
> Just curious, how involved is cleaning your fan?Depending on where it is on your laptop it can be as easy as blowing it very carefully with some compressed air. Apart from that you will need to take the bottom of your laptop and then give it a clean being careful not to scratch your boards or break any of the laptops internals.

---

### Post by Unreal223linux on 2009-01-16
I installed that sensor applet and it says 51c for both hard drive and processor... is this considered too hot or what? The fan cuts on for a second every now and then but I'm not sure if thats a good temp or not.

My processor is a pentium m 410 in a toshiba l35.

---

### Post by Alejandro Nova on 2009-01-16
@xluryan: Your issue is serious, but, fortunately, it seems you are spared. Overheating was a legendary cause of doom with Pavilion dv9000, and the tx1000 was built on the same architecture. Enraged HP customers from all the world [united in sites like this]("http://www.hplies.com") complained, and HP replied with the F.20 BIOS update, whose function is precisely that: keep the fan spinning always, so your system won't overheat.

You are spared, because you are using Ubuntu, and you can keep this lappy running happily at 800 MHz without problems. Vista users are not so lucky: they are burning their laptops in a ~18 months period. To increase your survival chances, add these lines to your /etc/X11/xorg.conf ($ sudo nano /etc/X11/xorg.conf)

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
[I]        Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3333"
        Option  "OnDemandVBlankInterrupts"      "True"
[/I]EndSection
```

The first option will enable PowerMizer downclocking for you. That will surely help. The second is a recognized power-saving option, that will do marvels for you.

---

### Post by xluryan on 2009-01-16
@Alejandro Nova, thanks for your reply! I've added those lines in and will reboot when I get home to see if it has an effect! Thank you infinitely!

Secondly, I Google'd PowerMizer just to get some info about it. I want to be sure: It looks like it's an on-board technology. That should mean I don't have to install anything on my system, correct?

Thanks in advance to your reply :)

---

### Post by Alejandro Nova on 2009-01-16
@xluryan: You are right, but with an stock Ubuntu setup, you are stuck in the highest speed. In our tx1000, that's 450 MHz for the graphic chipset.

The PowerMizer line enable the "Dynamic" speed profile for PowerMizer, so, when you are not using heavy 3D, the speed of your graphic chipset will be 100 MHz. You'll get slightly jerkier motion in Compiz (and I do mean slightly: Compiz doesn't use all your available graphic power), in exchange for less heat, and more battery life.

When you add that line, you can fire up nvidia-settings, go to the PowerMizer page, and check how the speed lowers from 450 MHz to 350 and 100 MHz. Good luck ;)

And don't worry: whenever you need graphic power, the speed will automagically rise to 450 MHz in a matter of miliseconds.

---

### Post by brandon88tube on 2009-01-16
Anything like that for lets say a dv8000z?

---

### Post by sandip26879 on 2009-01-17
ubuntu 8.10 (regularly updated) on my little acer aspire one seems to be fine :popcorn:

---

### Post by Entwicklung Medizinproduk on 2009-01-18
> **AlexBellisBrown said:**
> Agree with above, my fan used to run all the time, i opened it, gave it a good clean (the dust gets caked to the blades) and perfecto... fan was much quieter AND turned itself off from time to time. :)
Nice fan.. Does it have a timer? We use exhaust fan for the back of our computer..

---

### Post by xluryan on 2009-01-21
@Alejandro Nova, assuming you have a tx1000 like me, what temperature is your video card on average?

Mine seems to sit right around 60C, while the processor cores are around 40-46C.

---

### Post by Snowman46919 on 2009-01-22
I found that installing dellfand helped tremendously on my inspiron 9300 although it only outputs and controls the cpu fan. You can find dellfand at: [dellfand]("http://dellfand.dinglisch.net/")

also I have managed to lose all of my rubber feet on the bottom of my laptop not that they were a great help anyway so I found a replacement at radioshack.  Simply look for none slip project box feet, they are ugly and big but I saw a huge improvement over what the original feet and no feet at all provided as far as airflow.

this is the product I used: [Example]("http://www.radioshack.com/product/index.jsp?productId=2104070")

Also some laptop makers are notorious for being neglectful with thermal paste.  I have replaced mine on the cpu and will on the gpu when i find my t8 screwdriver.  At first I thought something was wrong until my fan finally came on.

---

### Post by xluryan on 2009-01-22
@Snowman46919, the equivalent to dellfand for the tx1000 is tpfand. Unfortunately, there doesn't appear to be any way to get it to work on my particular laptop. See this thread: [http://ubuntuforums.org/showthread.php?p=6466989]("http://ubuntuforums.org/showthread.php?p=6466989")

Disassembling my laptop is sort of my last resort, but it's coming down to it here, so we'll have to give it a little bit more time and see what I can get out of the the forums...

---

### Post by samurai_47 on 2009-01-23
seems to work for me, i have an HP Pavilion dv2845 se, when i had Vista/Windows 7 on it the fan ALWAYS ran, and the CPU was ALWAYS really really hot.

---

### Post by ROBarber on 2009-01-23
Good to know that. 
In the last weeks I decided to move on my work on the Win Desktop because my Fujitsu Siemens laptop is having problems with cooling down the heat, and I wasn't able to use it more than a few hours. 
The fan is always on speed, and from time to time even on high speed. I'll try this work around and I''l post my feedback.

Cheers

---

### Post by Snowman46919 on 2009-01-23
> **xluryan said:**
> 

Disassembling my laptop is sort of my last resort, but it's coming down to it here, so we'll have to give it a little bit more time and see what I can get out of the the forums...

@xluryan:  At this point if your laptop is over a year old I would seriously consider disassembling at the least cleaning the dust out of your fans and heat sinks if not reapplying some heat sink compound.  I think this will prolong the life of your laptop and help you get lower temperatures.  There is no real substitute for a good cleaning and fresh thermal paste IMHO.

---

### Post by ROBarber on 2009-01-23
judas@judas-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +61.8°C  (crit = +89.8°C)
this is the output for the sensors command?
What could be wrong? And this is just after a few minutes I've started my laptop. Also Frequency Scaling is Unsupported, but the frequency is set to the maximum value. After a few minutes the temperatures dropped with 6 degrees.

---

### Post by beyboo on 2009-01-24
> **sandip26879 said:**
> ubuntu 8.10 (regularly updated) on my little acer aspire one seems to be fine :popcorn:

Can you define "fine". I see my acer 5920 runnin intrepid at 60C and am not too happy. Dont run anything much on it except torrents and firefox and compiz. The CPU utils rarely goes over 25% :(

---

### Post by Arabso on 2009-01-25
Nice move
thanks

---

### Post by Bs0 on 2009-01-27
I followed these instructions did step 1 , but I cannot implement step 2 .<br>
when I had frequency scaler a error message pops up telling me the following:

> You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

should I still implement step 1?

---

### Post by brandon88tube on 2009-01-27
Hmm, is the error stopping you from doing step 2 or are you not doing it because of the error? Also, what hardware are you using?

---

### Post by BrentonEccles on 2009-01-31
> **sandip26879 said:**
> ubuntu 8.10 (regularly updated) on my little acer aspire one seems to be fine :popcorn:

Lucky for you because that´s precisely the system that I´ve got and I´ve been lucky to get 20 minutes of use inbetween resets.
I just found this thread and taken the advice... so far it appears that my computer isn´t getting so hot... I´m only assuming so far because I keep feeling around the fan and it feels pretty cool at the moment.
Australian Summers do not help, either. :\

---

### Post by k3lt01 on 2009-01-31
> **BrentonEccles said:**
> Australian Summers do not help, either. :\Especially when 1/3 of the country is in the mid 40 degrees (about 113 F for all those who dont know Celcius) and has been for a week!!!!! ;)

---

### Post by sdennie on 2009-01-31
This "fix" is at best a poor workaround.  Essentially, you are increasing the CPU temperature in order to make the fans turn on more aggressively.  Yes, this fix is literally "make your machine hotter so your fans turn on more".  Do not be surprised when this advice doesn't work or prematurely breaks your fans.

---

### Post by k3lt01 on 2009-01-31
> **sdennie said:**
> This "fix" is at best a poor workaround.  Essentially, you are increasing the CPU temperature in order to make the fans turn on more aggressively.  Yes, this fix is literally "make your machine hotter so your fans turn on more".  Do not be surprised when this advice doesn't work or prematurely breaks your fans.
I like how it has taken 49 posts before someone said something like this.

---

### Post by brandon88tube on 2009-01-31
> **sdennie said:**
> This "fix" is at best a poor workaround.  Essentially, you are increasing the CPU temperature in order to make the fans turn on more aggressively.  Yes, this fix is literally "make your machine hotter so your fans turn on more".  Do not be surprised when this advice doesn't work or prematurely breaks your fans.

I never said it was a fix. I said it was a workaround and yeah your system will get a little more hot if your frequency is up, but that will still happen whether you use this workaround or not. The fan running a lot is the same as it is with Windows, so I don't understand how this would be a problem. Why would you say setting your frequency to performance is bad? Windows even gives you the option under the power settings. Also, I would rather people be able to cool down their laptops some way rather then having them fry the thing because no one has a fix for this yet. I'm trying to help people out here and your comment is kind of like a slap in the face.

---

### Post by sdennie on 2009-01-31
> **brandon88tube said:**
> I never said it was a fix. I said it was a workaround and yeah your system will get a little more hot if your frequency is up, but that will still happen whether you use this workaround or not. The fan running a lot is the same as it is with Windows, so I don't understand how this would be a problem. Why would you say setting your frequency to performance is bad? Windows even gives you the option under the power settings. Also, I would rather people be able to cool down their laptops some way rather then having them fry the thing because no one has a fix for this yet. I'm trying to help people out here and your comment is kind of like a slap in the face.

It wasn't meant as a slap in the face.  It was meant as a very real understanding of what you are doing and why it's simply wrong.  This thread is literally about making your CPU hotter to cool the machine.  That's insane but that's what you are advocating.

---

### Post by brandon88tube on 2009-01-31
How is this insane? Its an option given to you even in other OS's. Its not like we are overclocking the system or anything. We are just setting it to performance. The fans don't run that high unless the CPU usage goes high. Even so this will not break the fans. I just don't understand your logic behind this. The default setting is set to ondemand, but even that will raise your CPU frequency when it is needed causing the exact same thing. I'm not saying you are wrong or anything, but I would like you to explain this.

---

### Post by sdennie on 2009-01-31
This "fix" is literally, "make the machine hotter so the fans turn on more".  I'm not sure how you can't consider that a bad thing.  Setting the CPU governor to performance is a poor solution in almost all cases.  Humans can't detect the difference between ondemand and performance.  So, essentially, you've found a way to make your computer hotter and that indirectly makes it cooler.

---

### Post by brandon88tube on 2009-01-31
Why must you keep referring to this as a fix? Where have I stated that it is a fix? I still can't see your reasoning. HOW IS THIS BETTER THEN LETTING IT FRY UP? My workaround at least cools it where as without this it tends to not cool at all and it gets extremely hot to the point I can cook <snip> on it.

---

### Post by k3lt01 on 2009-02-01
Brandon, you haven't mis-stated anything so you have nothing to worry about, chill mate and don't let the naysayers get to you.

[quote=sdennie]This "fix" is literally, "make the machine hotter so the fans turn on more". I'm not sure how you can't consider that a bad thing. Setting the CPU governor to performance is a poor solution in almost all cases. Humans can't detect the difference between ondemand and performance.[/quote]sdennie, the title clearly states this is a work around, it doesn't state that it is a fix. You have your opinion and have stated it clearly.

I have 2 problems with what you have done.
1-the needless twisting of words to make your point.
2-the emotiveness of your post insinuating that Brandon has done the wrong thing.

[quote=sdennie]So, essentially, you've found a way to make your computer hotter and that indirectly makes it cooler.[/quote]Actually this can be taken a completely different way, i.e. that this workaround makes the computer cycle the fan more efficiently therefor keeping the computer cooler.

---

### Post by brandon88tube on 2009-02-01
> **k3lt01 said:**
> Brandon, you haven't mis-stated anything so you have nothing to worry about, chill mate and don't let the naysayers get to you.

sdennie, the title clearly states this is a work around, it doesn't state that it is a fix. You have your opinion and have stated it clearly.

I have 2 problems with what you have done.
1-the needless twisting of words to make your point.
2-the emotiveness of your post insinuating that Brandon has done the wrong thing.

Actually this can be taken a completely different way, i.e. that this workaround makes the computer cycle the fan more efficiently therefor keeping the computer cooler.

Thank you and you are correct in that I should not let this bother me. It just rubbed me the wrong way when all I was trying to do here was help people out and then I get a post like that.

---

### Post by sdennie on 2009-02-01
I was perhaps too harsh in my initial rant.  However, any good HOWTO (regardless of whether or not it's a workaround or fix) explains the reason for the change.  In this case, it's "make your machine hotter to turn the fans on more often".  That may actually help some people but, it's not advice to be followed without understanding the consequences.

---

### Post by Ubangi on 2009-02-09
I agree with Sdennie. Surely the issue is not whether this is a fix or workround or whatever but the facts about what is a safe way to solve this problem.
My Acer Aspire One started overheating and locking up the touchpad after I unwisely followed some instructions for "making the fan quieter". 
I then turned down the scaling to "conservative" and it is noticeably cooler and has not locked up yet since I did it. On "performance" it overheated in minutes. This is what I would expect by using my common sense. Note that it is exactly the opposite of the original (arguably well meant) advice.

---

### Post by Cauda_Draconis on 2009-02-11
My fan works most of the time, but then when I wake it up from hibernation, it's started neglecting to turn the fan on at all and my computer heats up and locks. It keeps my processors between about 43C and 52C if I boot it up from a completely turned off state. 
Anyone know what's going on?

---

### Post by k3lt01 on 2009-02-12
> **Ubangi said:**
> I agree with Sdennie. Surely the issue is not whether this is a fix or workround or whatever but the facts about what is a safe way to solve this problem.
My Acer Aspire One started overheating and locking up the touchpad after I unwisely followed some instructions for "making the fan quieter". 
I then turned down the scaling to "conservative" and it is noticeably cooler and has not locked up yet since I did it. On "performance" it overheated in minutes. This is what I would expect by using my common sense. Note that it is exactly the opposite of the original (arguably well meant) advice. There is no problem agreeing with anyone except the way it is done. I disagree with sdennie's method of saying what he said not with what he meant and it is obvious he himself has later thought about how he did it.

As for "unwisely" following advice you the user need to be sure what you are doing. There is no warranty implied or given in the Ubuntu forums indeed there is no warranty in Ubuntu in general, so if you bork your system then the buck stops with you. The OP says this is a work round, in no place does it state it is a fix. Now people can mince words as much as they like, and words were minced to make a point that isn't relevant (to my way of thinking anyway), but you the user must use your own decision making processes to use the information supplied (whether rightly or wrongly) to your advantage of disadvantage.

---

