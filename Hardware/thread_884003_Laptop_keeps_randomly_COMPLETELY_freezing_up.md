---
title: "Laptop keeps randomly COMPLETELY freezing up"
date: 2008-08-08
forum: Hardware
---

### Post by cat5e_ on 2008-08-08
Hi, I just got a laptop for free yesterday and I installed Ubuntu on it twice withing the past two days. Both times it has been doing the same thing... completely freezing without waring. Everything on the screen stops moving, cursor and keyboard do not respond. Only way to get out of it is to reboot (there's a little switch on the laptop that forces it to immediately power off). 

So any ideas why it may be locking up like this? I even updated it to the latest stuff.

Thanks for any help, I'd really appreciate it!

---

### Post by cat5e_ on 2008-08-08
Oh and I just noticed that when it freezes the scroll lock and caps lock lights flash on and off.

---

### Post by Ayuthia on 2008-08-08
The flashing lights that you see is a sign that something went wrong in the kernel (kernel panic).  You might want to look in /var/log/kern.log to see if there are any messages in there that might tell you what is happening.  You can also check /var/log/dmesg.0 after the kernel panic.

Do you know what applications were running?

---

### Post by mikjp on 2008-08-08
I would suspect problems with graphics driver. I had similar problems when using X windows with VIA graphics card. We would need some more information about your hardware to help you with this problem.

You can, however, try to disable 3d effects, it might also help. 

When the computer hangs, you can try to use the REISUB (raising elephants is so utterly boring) magic keys. Press Alt + SysRq and the letters R E I S U B with about one seconds delay between the letters.

Greetings,

mikko

---

### Post by cat5e_ on 2008-08-08
> **Ayuthia said:**
> The flashing lights that you see is a sign that something went wrong in the kernel (kernel panic).  You might want to look in /var/log/kern.log to see if there are any messages in there that might tell you what is happening.  You can also check /var/log/dmesg.0 after the kernel panic.

Do you know what applications were running?Ok, I don't really know anything about that, but I'll look in there. I believe I remember seeing the words kernel panic when I was booting it up once on a black screen with white text. Sounds like you could be right. Well, thank you and I'll check and do some research on this. I really appreciate it.

> **mikjp said:**
> I would suspect problems with graphics driver. I had similar problems when using X windows with VIA graphics card. We would need some more information about your hardware to help you with this problem.

You can, however, try to disable 3d effects, it might also help. 

When the computer hangs, you can try to use the REISUB (raising elephants is so utterly boring) magic keys. Press Alt + SysRq and the letters R E I S U B with about one seconds delay between the letters.

Greetings,

mikkoWell, I already have 3D effects off since it is an old computer and doesn't even work with that stuff. When it hangs, I always seem to have Fire Fox open. Also Fire Fox will sometimes randomly close itself. Thank you for telling me that key combination. I will try that out next time it freezes. I appreciate it!


Ugg, but for now it is deciding to not even boot :(

---

### Post by mikjp on 2008-08-08
My problem froze the computer even without any 3d effects, as it was caused by a problematic driver used by xorg.  At the end of the day, I resigned, and bought a new NVIDIA graphics card.

You should give as some exact information about your laptop, at least it's name and model. Then we can google for the graphics chipset used in the laptop to find out whether there are known bugs connected to the hardware.

You can also check the Ubuntu launchpad's bug reports for your computer.

-> [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

Greetings,

mikko

---

### Post by cat5e_ on 2008-08-08
> **mikjp said:**
> My problem froze the computer even without any 3d effects, as it was caused by a problematic driver used by xorg.  At the end of the day, I resigned, and bought a new NVIDIA graphics card.

You should give as some exact information about your laptop, at least it's name and model. Then we can google for the graphics chipset used in the laptop to find out whether there are known bugs connected to the hardware.

You can also check the Ubuntu launchpad's bug reports for your computer.

-> [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)



Greetings,

mikkoOk, I don't know what type of graphics card is in it, but I know the model. It is an old Compaq Armada E700. Should definitely have a stock graphics card. The only thing upgraded on it that I can find would be the RAM which is now 376.5 MB. Thank you for your continued support, I really appreciate it.

This time I tried to turn it on I got the Kernal panic message at the bottom of the screen. It says:
[QUOTE=Compaq Armada E700][19.377845] Kernel panic - not syncing: Fatal exception in interrupt[/QUOTE]

Not to mention those caps lock and scroll lock lights are flashing while it says this.

---

### Post by mikjp on 2008-08-08
Your laptop is pretty old, I found all the specs [here](http://h18002.www1.hp.com/products/quickspecs/10380_div/10380_div.HTML).I tried to google quickly in order to find something about problems with your laptop. Unfortunately I did not find anything especially interesting.

I suggest you to let your computer run Memtest to see if the RAM is OK.  And you should try giving to the kernel options:

> noapic nolapic noacpi acpi=off 

You can add these to the file /boot/grub/menu.lst or you can add them using keyboard when Grub is loaded. Often this solves problems with kernel.

Greetings,

mikko

---

### Post by cat5e_ on 2008-08-08
> **mikjp said:**
> Your laptop is pretty old, I found all the specs [here](http://h18002.www1.hp.com/products/quickspecs/10380_div/10380_div.HTML).I tried to google quickly in order to find something about problems with your laptop. Unfortunately I did not find anything especially interesting.

I suggest you to let your computer run Memtest to see if the RAM is OK.  And you should try giving to the kernel options:



You can add these to the file /boot/grub/menu.lst or you can add them using keyboard when Grub is loaded. Often this solves problems with kernel.

Greetings,

mikkoThanks for the suggestion. I'm running Memtest right now and it has found over 2,000,000 errors. Yeah, TWO MILLION. None has passed. It doesn't make any sense, if the RAM is this messed up why did it even work at all?

Anyway I can fix the RAM?

---

### Post by cat5e_ on 2008-08-08
Well, I gave up and put Windows XP on it :(

The only time it froze with XP on it was during the installation at 19 minutes, but a reboot fixed it. 

But the computer makes this annoying quick several squeaky beep sounds every couple seconds from the hard drive I believe. Maybe I need a new hard drive :(

So should I buy a new hard drive?

---

### Post by phidia on 2008-08-08
You probably want to check the drive first. There is software that will help you to do that read about [SMART]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology") at that link.
I'm not sure how you would install that on windows-you should be able to run a live cd and install SMART and check the drive.

---

### Post by mikjp on 2008-08-09
> **cat5e_ said:**
> Thanks for the suggestion. I'm running Memtest right now and it has found over 2,000,000 errors. Yeah, TWO MILLION. None has passed. It doesn't make any sense, if the RAM is this messed up why did it even work at all?

Anyway I can fix the RAM?

It looks like we've located the problem. Maybe you got the laptop because problems and errors were just creeping in?

If it is the extra RAM added later, you could try to remove it and check with memtest again.  You could try to find some RAM in ebay, but I don't know if it's worth the trouble. :( It depends on how much you want to keep that laptop alive. 

Greetings,

Mikko

---

### Post by starcannon on 2008-08-09
Is it brand-name ram or is it "house ram", I learned long ago its worth spending another 10-20 dollars in the long run and just buy brand name, kingston or pny eitheway I've never been let down.

Cool that mem-test was the ticket, in the future be sure to post the output of lshw as well, that can tell us loads about your hardware.

You can probably buy some kingston ram for around $50, if ram is all thats wrong, I'd seriously consider it, a new laptop is much more expensive, and the discarded e-waste is a potential bio-hazard, so try to use them up completely if you can (just my lil sermon ignore it if it was offensive in any way)

---

### Post by cat5e_ on 2008-08-09
Thank you for the responses guys. I don't know where to find output of lshw or what that means, sorry.

Yesterday after installing Windows XP with my disk, upgrading it to SP2, it restarted ok... but I wake up this morning and it says there is some missing or corrupted system file and the computer cannot boot up. Then I try to turn it on 5 minutes later and it turns on. 

But the hard drive still makes this annoying bbbbeeepy sound every few seconds. It's like a dieing animal trying to breath or something. 

I'm running a MemTest in Windows. Every once in a while a couple second squeaky sound will come from the computer.

I'm guessing these are signs that all point to hard drive issues. I ran that SMART check program on it. In the SMART Info tab it says everything is OK except this:
[QUOTE=DiskCheckup V2.1 built with SmartDisk SDK v1.0 Build: 1013]E1 Load Cycle Count 509375 FAIL 50 50 50 N.A.[/QUOTE]

I ran a RAM test. I got one error out of 19%... I took a screenshot and was cropping it down so  I could upload it and then... the blue screen of death popped up. The computer stopped squeaking too during that.

So its apparently got bad RAM and a bad hard drive. By the way I checked the brands of two of the RAM sticks. One is Samsung the other is Infineon.

Edit:
The BSOD just popped up again for a second round, and the computer immediately restarted. And a third time...

---

### Post by starcannon on 2008-08-09
"Squeaky Sound" lol sorry have to laugh, great description though, is most often caused by overheating CPU.

Some things I'd try before spending money.

Unplug completely every cable from your computer.

Remove the dust cover from the computer housing/case

Take a can of compressed air and blow that sucker out, best to do outdoors or with a vacuum cleaner near your area to suck up the dust and lint.
I recommend having 3 cans of compressed air on hand, as they get cold they lose their stamina(if you know what I mean). So when one gets weak, grab next in line, rinse repeat, and blow every square nano-meter of that motherboard and cpu out thoroughly, take the fan off the heatsink if you need to, get all the dirt out of those fins.

Plug it all in and see if it doesn't behave better.

If a thorough cleaning does not work, then:
FIRST: Try each stick of ram individually, if one works and the other doesn't logic will dictate what to do from there. If both work individually but not together, again I will let logic dictate.

SECOND:
To help logic along go to kingston, use the ram configurator, and buy matching brandname and type of ram to put in the computer(I prefer kingston but you can use the info you get to match up the infineon or the samsung ram as well, even better if one of the sticks works, then just grab another of same timings, numbers are located on a sticker on the ram itself.)

THIRD:
If none of that works.... then try another HDD, use a known good "extra" if you have one lying around, doesn't matter what size, as long as you know its good, install something (ubuntu preferably) onto it, does it boot and work normally? If so, replace your main HDD, if not... 

FOURTH:
Check your Power Supply, again use the switch and replace method if you can... finally if none of the above works....

Fifth:
Use switch and replace with video card

FINALLY:
DOOM DOOM DOOM:
Chances are if you've run through the above, and still have a "Squealling Computer" you may have a bad motherboard... aieeeeeeeeeeee! blown capacitors, dead whatcha-ma-call-its, whatever, sadly this is a pain in the asterik, if you have "older"(using it relative to computers) hardware, then check out sites like pricewatch.com or if all else fails ebay.com or gozbay.com and get a compatible motherboard for your ram, psu, cpu, hdd, and video card.

GL

---

### Post by cat5e_ on 2008-08-09
^ thank you for all those tips starcannon, I really appreciate it.

It has been working fine for about an hour and a half now, just these "Windows has recovered from a serious error" messages pop up every now an then, and still squeaking lol.

I've never opened up a laptop before, so I don't know how easy it will be to get inside and actually blow off the mother board or change video card (I think it's on the mother board) or power supply. 

I'll try switching out RAM sticks later one at a time and running the tests to find the bad one(s).

I need to get it to stop squeaking though! XD

---

### Post by starcannon on 2008-08-09
Oh right, it's a laptop.
The video card likely hard or impossible to replace.
The rest can be done though, most laptops can be accessed easiest by removing the keyboard. Wish I could hear the "squeak", or where its coming from.

---

### Post by cat5e_ on 2008-08-09
> **starcannon said:**
> Oh right, it's a laptop.
The video card likely hard or impossible to replace.
The rest can be done though, most laptops can be accessed easiest by removing the keyboard. Wish I could hear the "squeak", or where its coming from.I just took a stethoscope that I found at a yard sale for 10 cents one day and started moving it around the computer to listen for the source of the sound... and I found it. It is coming from the left speaker! :lolflag:

So I plugged in a pair of headphones and the sound stopped comming out of the computer and then played through the headphones. There is also a bunch of gargled static sound playing through too.

But the speakers will play the chime that they're suposed to when you turn Windows on and off. They worked fine with Ubuntu when I tried to play a CD. So maybe I just need to find the proper drivers for them.

But it is still strange how the computer kept getting the BSOD and "recovered from a serious error" things all the time. Maybe this was causing the problem...

I just disabled the hardware and the insanely annoying beepepeepbeepepbep stopped yay, now to find the next problem...

Hmm, maybe that beep was my computer's way of warning me of some problem. Is that any kind of error message. I can try to record it and upload if anyone really needs to hear it.

---

### Post by cat5e_ on 2008-08-09
Aww darn. Now it won't boot into windows. 

And I can't use a Ubuntu or Kubuntu CD to install or go into the live CD mode, I get that kernel panic error. 

I took the hard drive out of the computer and it was really hot, I don't know how hot they're supposed to get, but it was hot. It rattles a little when you shake it up and down.

I can't figure out how to remove the ram (I got the door open), but I've never taken notebook ram out so I don't know what I'm doing.

This is ridiculous. Why can't I use the live CD on it now, even with the hard drive out? :(... edit: currently it doesn't say kernel panic but it later just freezes before getting anywhere


I noticed that my speakers only make the sounds when I have my Ethernet card in. Strange...

---

### Post by starcannon on 2008-08-11
None of this is sounding good, how old is the hdd, perhaps try another hdd?
Odd that the ethernet card is bleeding over the speakers, I'd try another card and determine if its the card or the motherboard.

GL

> **cat5e_ said:**
> Aww darn. Now it won't boot into windows. 

And I can't use a Ubuntu or Kubuntu CD to install or go into the live CD mode, I get that kernel panic error. 

I took the hard drive out of the computer and it was really hot, I don't know how hot they're supposed to get, but it was hot. It rattles a little when you shake it up and down.

I can't figure out how to remove the ram (I got the door open), but I've never taken notebook ram out so I don't know what I'm doing.

This is ridiculous. Why can't I use the live CD on it now, even with the hard drive out? :(... edit: currently it doesn't say kernel panic but it later just freezes before getting anywhere


I noticed that my speakers only make the sounds when I have my Ethernet card in. Strange...

---

### Post by cat5e_ on 2008-08-12
> **starcannon said:**
> None of this is sounding good, how old is the hdd, perhaps try another hdd?
Odd that the ethernet card is bleeding over the speakers, I'd try another card and determine if its the card or the motherboard.

GLOh, well it is working great now! I took out the RAM sticks on at a time, and it turns out that the 256MB Samsung was causing all the problems (except I did have to updated the sound card driver). Right now I'm running on a sad 128MB, and I've ordered a replacement 256MB RAM stick for $33 (and my computer was on the compatibility list), so this guy will live on :D Hasn't frozen up since or crashed. Hopefully the same will go for Ubuntu...

I don't have Ubuntu on it right now, just XP but I'll install Ubuntu once I get that new RAM and I'll have it dual booting with Windows still on just in case I need it.

I also ordered a Wi-Fi card (description said it is Ubuntu friendly with no drivers :)).

Thank you to all that helped me.

---

### Post by starcannon on 2008-08-12
When you got to install ubuntu again, might I suggest Xubuntu as something to try out (if you don't like it then you can always go with regular Ubuntu)

Xubuntu is nice on older laptops like that one, system requirements are much lower.

[[SIZE="4"][COLOR="Blue"]Xubuntu[/COLOR][/SIZE]]("http://www.xubuntu.org/")

---

### Post by kingbilly on 2008-08-12
> **starcannon said:**
> When you got to install ubuntu again, might I suggest Xubuntu as something to try out (if you don't like it then you can always go with regular Ubuntu)

Xubuntu is nice on older laptops like that one, system requirements are much lower.

[[SIZE="4"][COLOR="Blue"]Xubuntu[/COLOR][/SIZE]]("http://www.xubuntu.org/")

Cat5e_ , I suggest you follow starcannon's advice.  Xubuntu can make your older hardware feel blazing fast compared to the sluggishness you would have with window managers of ubuntu, kubuntu, XP, vista (kidding).

Thanks starcannon:)

---

### Post by cat5e_ on 2008-08-13
Thank you for that advice. I will download and burn that to a disk to try out. I'm hoping it still has FireFox and OpenOpen Office.

I downloaded Kubuntu one time but I didn't like it at all compared to Ubuntu, but this Xbuntu thing looks a lot similar to the Ubuntu desktop!

---

### Post by jesuisbenjamin on 2008-09-13
Hello there,

I am using a Laptop NEC Versa M300. This computer randomly and completely freezes and am not able to find a pattern or identify any apparent cause to this issue. It may stay on and be stable for 24h without a problem while it can freeze sometimes 4 times in one hour.
As far as i can remember it does not freeze before the Ubuntu logo appears on the screen. There is no specific program running when it freezes as it can freeze even before i type in my username.
When i say freeze i mean nothing responds at all, caps lock and scroll lock LEDs flash on and off, leaving me with no option but cut of power, and boot again.
I looked into the kern.log but do not know what to look for.

If anyone can help it would be great, i cannot afford to lose this computer :( 

Cheers
B.

---

