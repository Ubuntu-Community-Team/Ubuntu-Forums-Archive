---
title: "Upgrading my Processor"
date: 2017-02-07
forum: Hardware
---

### Post by mitch.gray on 2017-02-07
Hello all, 

I am just trying to figure out ways I can upgrade my computer, as my laptop isnt quite cutting it for things i want to do, and my desktop is much simpler of a task to upgrade,

i have a HP pavilion a1600n and it currently has a little over 1gb or ram, but i have 4x1 gb sticks of ram on the way, i am mainly wanting to focus on a new processor, as 
i have been told that its not really worth it to upgrade the motherboard.

my motherboard specs can be viewed at [http://support.hp.com/us-en/document/c00757531](http://support.hp.com/us-en/document/c00757531)

i am not sure how to find out what processors i can upgrade to, or if i can upgrade it to anything worth while upgrading to, also if anyone knows of a better motherboard that i could upgrade cheaply to that would accomodate a worthy processor, i am open to advice on that aswell.

Thank you in advance!

---

### Post by QIII on 2017-02-07
On the page you cited, there is a section entitled "Processor Upgrade Information" that lists

    AMD Athlon 64
    Athlon 64 X2 up to 5000+
    AMD Sempron

as your upgrade options.  An AM2 socket is getting pretty old.  But the socket may not be your only limitation.  The board's chipset has a lot to do with what CPUs are compatible.

---

### Post by mitch.gray on 2017-02-07
okay, so would upgrading my motherboard be a viable option? to open up more possibilities for better processors?

---

### Post by Bashing-om on 2017-02-07
mitch.gray; For your thoughts:

I run an old AM2 socketed dual core AMD Athlon with but 4 gigs of ram (2007 year).. It runs unity "fairly" , A minimal install with xfce4 as the DE performs wonderfully; No complaint , it is fast . With an SSD and xubuntu also performs wonderfully ; only marginally the more responsive than the minimal install on a hard drive .. The hardware does support 17.04 - zesty ! Installed to a WD hard drive.

Just because it is old does not mean it is out the door !

just do not put more on the wagon than the horse can pull .

[INDENT][INDENT]my input, for what it is worth
[/INDENT][/INDENT]

---

### Post by poorguy on 2017-02-07
> **mitch.gray said:**
> okay, so would upgrading my motherboard be a viable option? to open up more possibilities for better processors?
I would gamble the price of the Athlon 64 X2 5000+ processor which can be purchased for $8.00 to $10.00 on ebay.

[http://www.ebay.com/itm/AMD-Athlon-64X2-2-6GHz-Dual-Core-5000-Processor-ADO5000IAA5DO-AM2-US-SELLER-/332111427435?hash=item4d5362376b:g:Ai4AAOSwCGVX8wM5](http://www.ebay.com/itm/AMD-Athlon-64X2-2-6GHz-Dual-Core-5000-Processor-ADO5000IAA5DO-AM2-US-SELLER-/332111427435?hash=item4d5362376b:g:Ai4AAOSwCGVX8wM5)

[http://www.ebay.com/itm/AMD-Athlon-64-X2-5000-2-6GHz-AM2-1000MHz-Desktop-ADO5000IAA5DO-/201810458656?hash=item2efcd73820:g:b0gAAOSw5cNYmdR3](http://www.ebay.com/itm/AMD-Athlon-64-X2-5000-2-6GHz-AM2-1000MHz-Desktop-ADO5000IAA5DO-/201810458656?hash=item2efcd73820:g:b0gAAOSw5cNYmdR3)

You would also need to by new thermal paste as arctic silver 5 or similar to apply to the new processor it is not that expensive.

A worthy gamble IMO.

I wouldn't buy a new motherboard as you would be better off buying a newer computer with newer hardware.

Just my thoughts.

---

### Post by Yellow Pasque on 2017-02-07
What cpu is in it right now?
```
cat /proc/cpuinfo
```

[http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html](http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html)

---

### Post by mitch.gray on 2017-02-08
> **Temüjin said:**
> What cpu is in it right now?
```
cat /proc/cpuinfo
```

[http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html](http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html)
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 1800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall
bugs		: apic_c1e fxsave_leak sysret_ss_attrs swapgs_fence
bogomips	: 3607.54
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc


processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 1800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall
bugs		: apic_c1e fxsave_leak sysret_ss_attrs swapgs_fence
bogomips	: 3607.54
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by mitch.gray on 2017-02-08
> **poorguy said:**
> I would gamble the price of the Athlon 64 X2 5000+ processor which can be purchased for $8.00 to $10.00 on ebay.

[http://www.ebay.com/itm/AMD-Athlon-64X2-2-6GHz-Dual-Core-5000-Processor-ADO5000IAA5DO-AM2-US-SELLER-/332111427435?hash=item4d5362376b:g:Ai4AAOSwCGVX8wM5](http://www.ebay.com/itm/AMD-Athlon-64X2-2-6GHz-Dual-Core-5000-Processor-ADO5000IAA5DO-AM2-US-SELLER-/332111427435?hash=item4d5362376b:g:Ai4AAOSwCGVX8wM5)

[http://www.ebay.com/itm/AMD-Athlon-64-X2-5000-2-6GHz-AM2-1000MHz-Desktop-ADO5000IAA5DO-/201810458656?hash=item2efcd73820:g:b0gAAOSw5cNYmdR3](http://www.ebay.com/itm/AMD-Athlon-64-X2-5000-2-6GHz-AM2-1000MHz-Desktop-ADO5000IAA5DO-/201810458656?hash=item2efcd73820:g:b0gAAOSw5cNYmdR3)

You would also need to by new thermal paste as arctic silver 5 or similar to apply to the new processor it is not that expensive.

A worthy gamble IMO.

I wouldn't buy a new motherboard as you would be better off buying a newer computer with newer hardware.

Just my thoughts.
 im just not sure if my motherboard could handle that processor

here is info on my motherboard: [http://support.hp.com/us-en/document/c00757531](http://support.hp.com/us-en/document/c00757531)

---

### Post by poorguy on 2017-02-08
> **mitch.gray said:**
> im just not sure if my motherboard could handle that processor

here is info on my motherboard: [http://support.hp.com/us-en/document/c00757531](http://support.hp.com/us-en/document/c00757531)
What you need to do is see if your bios version and chipset will support that processor.
It does say in the specs you provided in your earlier post that the motherboard supports up to  Athlon 64 X2 5000+ processor. 
It is a gamble as I mentioned and no one can say for certain that it will work.
If uncertain than purchase a processor under the   Athlon 64 X2 5000+ series.

---

### Post by Yellow Pasque on 2017-02-08
> **mitch.gray said:**
> im just not sure if my motherboard could handle that processor

The link in my last post shows exactly which CPU's have been verified.

> I would gamble the price of the Athlon 64 X2 5000+ processor which can be purchased for $8.00 to $10.00 on ebay.

If you could find one for that price, it would be a nice little boost over the 3800 (2.0GHz -> 2.6GHz). Don't expect the difference to be night and day though.

> okay, so would upgrading my motherboard be a viable option?

That is a question you should have asked BEFORE you bought RAM.

---

### Post by mitch.gray on 2017-02-08
> **Temüjin said:**
> The link in my last post shows exactly which CPU's have been verified.



If you could find one for that price, it would be a nice little boost over the 3800 (2.0GHz -> 2.6GHz). Don't expect the difference to be night and day though.



That is a question you should have asked BEFORE you bought RAM.

i paid 15 bucks for 4x 1gb sticks of ram, it wouldnt be that big of a loss if i did end up upgrading my processor lol

---

### Post by poorguy on 2017-02-09
> **mitch.gray said:**
> i paid 15 bucks for 4x 1gb sticks of ram, it wouldnt be that big of a loss if i did end up upgrading my processor lol

I would take a chance with one of these.

[http://www.ebay.com/p/AMD-Athlon-64-X2-4600-2-4-GHz-Dual-Core-ADA4600IAA5CU-Processor/74068245?rmvSB=true](http://www.ebay.com/p/AMD-Athlon-64-X2-4600-2-4-GHz-Dual-Core-ADA4600IAA5CU-Processor/74068245?rmvSB=true)

---

### Post by Yellow Pasque on 2017-02-09
I'd rather have this one: [http://www.ebay.com/itm/AMD-5000-Athlon-64-X2-2-6GHz-Socket-AM2-1000MHz-ADO5000IAA5DD-/361899620301?hash=item5442e5f7cd:g:jmwAAOSwLEtYmdRm](http://www.ebay.com/itm/AMD-5000-Athlon-64-X2-2-6GHz-Socket-AM2-1000MHz-ADO5000IAA5DD-/361899620301?hash=item5442e5f7cd:g:jmwAAOSwLEtYmdRm)
It's 2.6GHz and it's a Brisbane core, so only 65W instead of 89W Windsor core.
Just make sure you upgrade BIOS before you remove the old CPU.

---

### Post by poorguy on 2017-02-09
That would be a better choice I agree but the OP is uncertain if the motherboard would support it.

---

### Post by Yellow Pasque on 2017-02-10
> **poorguy said:**
> That would be a better choice I agree but the OP is uncertain if the motherboard would support it.

It's verified working with updated BIOS:
[http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html](http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html)

---

### Post by poorguy on 2017-02-10
Hey Temüjin,

If updating hp bios isn't a hassle then yes go with the choice you presented would be the best.

---

### Post by mitch.gray on 2017-02-13
> **poorguy said:**
> I would take a chance with one of these.

[http://www.ebay.com/p/AMD-Athlon-64-X2-4600-2-4-GHz-Dual-Core-ADA4600IAA5CU-Processor/74068245?rmvSB=true](http://www.ebay.com/p/AMD-Athlon-64-X2-4600-2-4-GHz-Dual-Core-ADA4600IAA5CU-Processor/74068245?rmvSB=true)
i have one ordered, gonna test it out, cant hurt any for under $10 CAD. just going to have to make sure to do my research before i attempt adding it to my system as I have not installed a new processor as of yet, any good tutorials you guys know about or personal tips on how to install new processor?

---

### Post by mitch.gray on 2017-02-13
> **poorguy said:**
> Hey Temüjin,

If updating hp bios isn't a hassle then yes go with the choice you presented would be the best.
at what stage would i update bios, and is there a guide on how to do it in layman terms?
simple step by step would be awesome lol

---

### Post by Bashing-om on 2017-02-13
mitch.gray; Hey;

> **mitch.gray said:**
> at what stage would i update bios, and is there a guide on how to do it in layman terms?
simple step by step would be awesome lol

My AMD AM2 socket board the bios is a chip . Take the easy way out and swap our the chip .

[INDENT][INDENT]all for easy
[/INDENT][/INDENT]

---

### Post by poorguy on 2017-02-13
Hey mitch.gray,

Unless absolutely necessary I wouldn't upgrade the bios as if done improperly you can render a working motherboard useless.

As far as replacing the processor lift the clip and twist the heatsink fan assembly and carefully remove it from the processor.
Clean the heatsink base very well with alcohol.
Take note on where a gold color arrow is on the processor as that is the way the new one will need to go back in.
Push down and away on the latch to release the processor and lift to remove.
Place without force the new processor into processor socket.
Secure latch that holds processor in place.
Wipe top of processor metal heat spreader clean with alcohol and let dry.
Now apply a small BB sized amount of thermal paste in the center of the metal heat spreader of the processor and careful attach heatsink fan in place.
Make sure all is attached and put back where it was remove from and close the pc and power up.

[http://support.amd.com/en-us/kb-articles/Pages/HowToReplaceAMDCPUnHSF.aspx](http://support.amd.com/en-us/kb-articles/Pages/HowToReplaceAMDCPUnHSF.aspx)

---

### Post by mitch.gray on 2017-02-13
> **Temüjin said:**
> I'd rather have this one: [http://www.ebay.com/itm/AMD-5000-Athlon-64-X2-2-6GHz-Socket-AM2-1000MHz-ADO5000IAA5DD-/361899620301?hash=item5442e5f7cd:g:jmwAAOSwLEtYmdRm](http://www.ebay.com/itm/AMD-5000-Athlon-64-X2-2-6GHz-Socket-AM2-1000MHz-ADO5000IAA5DD-/361899620301?hash=item5442e5f7cd:g:jmwAAOSwLEtYmdRm)
It's 2.6GHz and it's a Brisbane core, so only 65W instead of 89W Windsor core.
Just make sure you upgrade BIOS before you remove the old CPU.
this one wont ship to canada unfortunately
[COLOR=#333333][FONT=Helvetica neue]**AMD Athlon 64 X2 5000+ AM2 (ADO5000IAA5D_O_**[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**) Dual-Core CPU 2.6 GHz is the one i ordered, there is one that is **[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**AMD Athlon 64 X2 5000+ AM2 (ADO5000IAA5D_U_**[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**) Dual-Core CPU 2.6 GHz, can someone tell me the difference?**[/FONT][/COLOR]

---

### Post by poorguy on 2017-02-13
> **mitch.gray said:**
> this one wont ship to canada unfortunately
[COLOR=#333333][FONT=Helvetica neue]**AMD Athlon 64 X2 5000+ AM2 (ADO5000IAA5D_O_**[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**) Dual-Core CPU 2.6 GHz is the one i ordered, there is one that is **[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**AMD Athlon 64 X2 5000+ AM2 (ADO5000IAA5D_U_**[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica neue]**) Dual-Core CPU 2.6 GHz, can someone tell me the difference?**[/FONT][/COLOR]
Here are the spec sheets on both.
I believe the only difference is on was originally sold as a boxed processor shipped with a heatsink fan and the other was sold our of a tray as an OEM otherwise I see no difference.

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%205000+%20-%20ADO5000IAA5DU.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%205000+%20-%20ADO5000IAA5DU.html)

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%205000%2B%20-%20ADO5000IAA5DO%20(ADO5000DOBOX).html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%205000%2B%20-%20ADO5000IAA5DO%20(ADO5000DOBOX).html)

Here is a video on repalacing a processor.

[https://www.youtube.com/watch?v=olBnEN9YkGc](https://www.youtube.com/watch?v=olBnEN9YkGc)

---

### Post by mitch.gray on 2017-02-13
> **poorguy said:**
> Hey mitch.gray,

Unless absolutely necessary I wouldn't upgrade the bios as if done improperly you can render a working motherboard useless.

As far as replacing the processor lift the clip and twist the heatsink fan assembly and carefully remove it from the processor.
Clean the heatsink base very well with alcohol.
Take note on where a gold color arrow is on the processor as that is the way the new one will need to go back in.
Push down and away on the latch to release the processor and lift to remove.
Place without force the new processor into processor socket.
Secure latch that holds processor in place.
Wipe top of processor metal heat spreader clean with alcohol and let dry.
Now apply a small BB sized amount of thermal paste in the center of the metal heat spreader of the processor and careful attach heatsink fan in place.
Make sure all is attached and put back where it was remove from and close the pc and power up.

[http://support.amd.com/en-us/kb-articles/Pages/HowToReplaceAMDCPUnHSF.aspx](http://support.amd.com/en-us/kb-articles/Pages/HowToReplaceAMDCPUnHSF.aspx)

How would I know if i need to update bios, as i was instructed to do so before installing new CPU

---

### Post by poorguy on 2017-02-13
Compare the processor in the list in post #6 of this thread that was already posted by                                                                                      [**[COLOR=#000000]Temüjin.[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")

[URL="http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html"]http://www.cpu-upgrade.com/mb-ASUS/A8M2N-LA.html


[/URL]

---

### Post by poorguy on 2017-02-13
It looks to be supported by your motherboard but can't say for sure whether a bios upgrade is needed. 

This is why I said in an earlier post it's a gamble.

The only sure way is to research the HP upgrade thread for that motherboard.

I think I would take the gamble how ever that is me and the only sure way to know.

You have to decide if you are willing to do that unless you can find definite resources saying it is known to work.

---

### Post by poorguy on 2017-02-13
Go to this link and present your question and someone may be able to give you a definite answer.

[http://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/bd-p/HardwareDPC](http://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/bd-p/HardwareDPC)

---

### Post by Frogs Hair on 2017-02-13
> [COLOR=#000000]okay, so would upgrading my motherboard be a viable option? to open up more possibilities for better processors?[/COLOR]

Finding a mobo that supported DDR 2 memory took some searching as I found when I spruced up an older desktop recently. I bought new/old stock including Biostar mobo & Athlon II x 4 cpu  and spent $110 US. There are mobo,cpu and DDR3 memory bundles available depending on your budget.

---

### Post by mitch.gray on 2017-02-13
> **poorguy said:**
> Go to this link and present your question and someone may be able to give you a definite answer.

[http://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/bd-p/HardwareDPC](http://h30434.www3.hp.com/t5/Desktop-Hardware-and-Upgrade-Questions/bd-p/HardwareDPC)
done! and the answer i got is "[COLOR=#000000][FONT=HPRegular]The CPU is listed, so that part is OK.  I would not suggest any BIOS change, if it were offered."[/FONT][/COLOR]

---

### Post by poorguy on 2017-02-14
> **mitch.gray said:**
> done! and the answer i got is "[COLOR=#000000][FONT=HPRegular]The CPU is listed, so that part is OK.  I would not suggest any BIOS change, if it were offered."[/FONT][/COLOR]
It sounds as though you are going to have to try it to find out for sure since there is no real documentation that states where it has been tested.

---

### Post by mitch.gray on 2017-02-28
Okay so today i recieved the [COLOR=#333333][FONT=Helvetica neue]AMD Athlon 64 X2 5000+ and installed it, but i keep having an issue where my computers fans keep revving almost like a car, and then the fan will come one really loud, any suggestions, this happened at first but seems to have stopped for now, so if it ends up doing it again, any suggestions on how to fix this issue?[/FONT][/COLOR]

---

### Post by poorguy on 2017-02-28
> **mitch.gray said:**
> Okay so today i recieved the [COLOR=#333333][FONT=Helvetica neue]AMD Athlon 64 X2 5000+ and installed it, but i keep having an issue where my computers fans keep revving almost like a car, and then the fan will come one really loud, any suggestions, this happened at first but seems to have stopped for now, so if it ends up doing it again, any suggestions on how to fix this issue?[/FONT][/COLOR]
Sometimes at first power up from a cold start the fans may ramp up until boot up is completed.

Was old thermal paste cleaned from heat sink and new thermal paste applied and then heat sink fan seated and secured properly to the heat sink fan bracket on the motherboard. 
AMD heat sink fan has that latch on one side and needs to be latched down all of the way.

Make sure to check when you reinstalled your processor fan plug that you didn't miss a pin as most processor fans are four wire. I've had it happen to me before just wasn't paying close enough attention. 

Carefully check all of your work to make certain it is all correct and nothing overlooked.

Go into bios after a restart and reset the bios to factory defaults.

Install and run lm-sensors and see what kinds of temps your processor is running.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by mitch.gray on 2017-02-28
> **poorguy said:**
> Sometimes at first power up from a cold start the fans may ramp up until boot up is completed.

Was old thermal paste cleaned from heat sink and new thermal paste applied and then heat sink fan seated and secured properly to the heat sink fan bracket on the motherboard. 
AMD heat sink fan has that latch on one side and needs to be latched down all of the way.

Make sure to check when you reinstalled your processor fan plug that you didn't miss a pin as most processor fans are four wire. I've had it happen to me before just wasn't paying close enough attention. 

Carefully check all of your work to make certain it is all correct and nothing overlooked.

Go into bios after a restart and reset the bios to factory defaults.

Install and run lm-sensors and see what kinds of temps your processor is running.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
my computer would not stay on long enough for me to even get into bios, have my old processor in and all works fine, could the issue be with the processor I bought possibly?

---

### Post by mitch.gray on 2017-02-28
Yes I have removed old thermal paste from the heatsink and triple checked my work, even reset bios to defult which allowed me to get the computer up and running again, but seems to still have a rev like sound from the cpu fan when i try to play simple browser games but still an improvement from the crazy fan sounds that came just from starting up computer before resetting bios settings

---

### Post by bearlake on 2017-02-28
On some motherboards there are jumpers to remove or install across pins. See your owners manual for setup.

Just some info that can be easily over looked.

---

### Post by poorguy on 2017-03-01
> **mitch.gray said:**
> my computer would not stay on long enough for me to even get into bios, have my old processor in and all works fine, could the issue be with the processor I bought possibly?
There is a chance that your processor could have a problem but there is also more of a chance that your bios may need to be updated to a later version for that processor to work properly.

There is also the possibility that the processor you bought runs at a higher wattage and therefore produces more heat raising operating temperatures which would cause the fans to run at higher speeds.

---

