---
title: "Dell Inspiron 6400/e1505"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by nischg on 2006-06-05
Hi,

I ve got a Dell i6400 for some time now and I am really sick of WinXP. I used to have Ubuntu on my desktop but a laptop is another thing.

I installed Dapper final a couple of days ago and I've managed to get almost everything to work. Just two things remaining:

1.- Suspend/Hibernate. I've tried almost any guide, tip and how-to I found with no luck. I can suspend but it's impossible to resume afterwards. Just a blank scree, some HDD led activity but no resuming. I've read that it could be the SATA drive or the Radeon X1300. Any clues?

2.- Ricoh SD card reader. Some say it just works out of the box in Dapper but not for me.:(  

I am using the latest 686 kernel on an almost fresh Dapper install with ATi's 8.25.18 drivers installed following the second method on this guide [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually")

Please consider that I used Ubuntu for a year now but my knowledge is still basic.

I hope someone can point me in the right direction to finally ditch Windows.

---

### Post by quini on 2006-06-08
> **nischg]I installed Dapper final a couple of days ago and I've managed to get almost everything to work. Just two things remaining:

1.- Suspend/Hibernate. I've tried almost any guide, tip and how-to I found with no luck. I can suspend but it's impossible to resume afterwards. Just a blank scree, some HDD led activity but no resuming. I've read that it could be the SATA drive or the Radeon X1300. Any clues?[/QUOTE]
My laptop (Benq JB7000 [http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html]("http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html")) also has an Ati card (Radeon 9700), but, despite it seems to suspend and resume fine with latest Ati drivers, it does not.  It suddenly hangs shortly after resume.

As I don't need 3D in linux I'm using the GPL driver "ati".  If you don't need 3D you can try with this one.

I also need a parameter at boot time for my laptop to suspend&resume fine said:**
> 2.- Ricoh SD card reader. Some say it just works out of the box in Dapper but not for me.:(  
Mine shows as **0000:02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller** (by lspci), and is not supported.  What does lspci show there?  :-\" 

Good luck  :cool:

---

### Post by nischg on 2006-06-10
Thanks for the reply. I tested an SD card yesterday and it worked. The problem is that I own a Sony camera that uses Memory Stick :-? 

Still haven't tried your tip on the suspend issue, I am still hoping someone with the same lappy gives me some advise.

Thanks

---

### Post by nischg on 2006-06-10
SUSPEND WORKS!!! Let me try it out a bit to make sure it works absolutely OK and I'll post the solution.

---

### Post by lorinel on 2006-06-11
[QUOTE=nischg]SUSPEND WORKS!!! Let me try it out a bit to make sure it works absolutely OK and I'll post the solution.[/QUOTE]

I would absolutely love if you posted your solution. I have heard dropping ATI's driver might work... but the xorg driver just does not have the performance I want :(.

Suspend and the mmc card reader are the only two things keeping my Dell Inspiron E1505 from working 100%.

Thanks :)

---

### Post by nischg on 2006-06-13
What I did is edit the configuration file at /etc/default/acpi-support, and uncomment the second line, # ACPI_SLEEP=true. After that it has worked OK when plugged in but when on battery sometimes it does and sometimes it does not work.

Please try it to see if it helps.

---

### Post by Ward Bergmans on 2006-06-29
Hello,

I'm documenting how I get all the hardware on the Dell Inspiron 6400 / e1505 laptop working. So, for everybody who wants to know, check this out:

[http://home.concepts.nl/~bergmans/linux/install_linux.html]("http://home.concepts.nl/~bergmans/linux/install_linux.html")

I havn't got everyting working yet. But at least you can see how I got the things that are workiing working :-)

nischg, if you got helpfull information on how you got things working. Please let it know.

---

### Post by nischg on 2006-06-29
I'll be more than happy to contribute to the documentation. I do have little time this week though. Please let me put what I did in written this weekend and I will post it.

I hope we I6400 owners can gather as much information we can to make everything run smoothly.

Best regards

---

### Post by ficotalancon on 2006-06-30
Check your swap partition, it must be at least 1.25 of your ram memory, im using 1GB of RAM memory and 1.5 GB of swap on a e1505 and the hibernation mode works perfect..;)

---

### Post by rvanderblom on 2006-07-17
I've posted my install procedure as well for those running the 6400 with an ATI card. They can be found at:

[http://opesix.com/blogen/?page_id=40]("http://opesix.com/blogen/?page_id=40")

Haven't encoutered any real notable problems except the dual core not immediately recognized and the screen resolution not set correctly.

---

### Post by irober02 on 2006-07-25
I'm pretty happy with the way (K)ubuntu Dapper is running on my Dell 6400. However, one problem is at boot up. Sometimes when I power-up (just after the kernel starts) a fan spins up and keeps spinning FAST. In this state, the rest of the boot procedures slows way down. 

I hit the power button and usually within a few attempts the machine boots smoothly. Usually the fan spins for a fraction of a section as the kernel starts and then stops.

Has anybody else seen this?

Any suggestions?

I've tried digging around the system logs without finding too much helpful information -it seems that logging starts later in the boot process.

bye

ian

---

### Post by themusicwave on 2006-08-01
I have an e1505 coming in the mail today(hopefully) and have a few questions about how you set everything up.

I have heard that Dell includes some of it's own custom paritions for the backup data and for the "no boot" DVD playing features.

I plan on running a dual boot on this machine.  I will be wiping out the backup stuff since I won't need it.  However, I would like to keep the "no boot" DVD play feature.

Is there anything special I have to do when partioning or installing GRUB to make sure this functionailty stays?  Or am I just listening to crazy rumors?

Also I'd be happy to contribute details on my setup process once I get it going.  I'm pretty new to Linux, and I think a guide like that would really be helpful for people.

---

### Post by chuckao on 2006-08-01
Hi,

I have this same laptop and sometimes I have problem with speakers/headphone jack.

Sometimes, when I turn on the laptop, only speakers work even when a put the headphone plug. I can not heard anything and headphone, only in the speakers.

My solution: Restart the system #-o  and when I have luck I got the system full functional (speakers and headphone work).

My sound card is  Sigmatel 9200.

Anyone has the same problem or the system works perfectly?

cheers,

---

### Post by jimonade on 2006-08-03
yes, i have the same problem: speakers/headphone audio output not switching properly.  (with my dell inspiron e1505)

currently, fresh boot without headphones plugged in and no sound from speakers.  when i plug in the headphones i hear audio through the headphones.  when i unplug them i still get no audio output from the speakers.

i'd rather not roll the reboot dice.

i'm searching for more info.

soundcard: sigmatel STAC9200

using default ubuntu sound setup of alsa/esd

-j

ps: i also got ripped off by dell.  initially purchased the "soundblaster audigy" sound card upgrade later to learn that it was a "SOFTWARE ONLY" upgrade.  unbelievable.  nice laptop though... although i agree with many others that dell support/sales is going straight to hell.

EDIT: i think the problem happens when the sound is muted or headphones are plugged in when the laptop shuts down.  booting with headphones plugged in seems to fix this.

---

### Post by nicbink on 2006-08-04
i got the e1705 and my default sound card is listed as HDA Intel and have had no problems with the speakers/jack not switching.  what does lspci list your audio controller as?


> **jimonade said:**
> ps: i also got ripped off by dell.  initially purchased the "soundblaster audigy" sound card upgrade later to learn that it was a "SOFTWARE ONLY" upgrade.  unbelievable.  nice laptop though... although i agree with many others that dell support/sales is going straight to hell.

yeah join the club.  i did the same thing.  i also bought the ATI 256mb "HyperMemory" video card thinking hypermemory was just some fancy term for some new faster memory.  well turns out when they said Hyper they meant Shared with the system.  So now I have a 128mb card and 768mb RAM instead of 256 and 1gb.

but other than that these inspiron series seem to be good laptops.

---

### Post by Frostmourne on 2006-08-04
Has anyone been able to upgrade the BIOS on these laptops without using Windows? It seems the BIOS upgrades are distributed as .exe's which not even Wine or a file extractor can open.

---

### Post by chuckao on 2006-08-04
Hi [COLOR="Red"]jimonade[/COLOR]

> **jimonade said:**
> yes, i have the same problem: speakers/headphone audio output not switching properly.  (with my dell inspiron e1505)

currently, fresh boot without headphones plugged in and no sound from speakers.  when i plug in the headphones i hear audio through the headphones.  when i unplug them i still get no audio output from the speakers.

i'd rather not roll the reboot dice.

i'm searching for more info.

soundcard: sigmatel STAC9200

using default ubuntu sound setup of alsa/esd



Yes, I need to do the same procedure :( and I'm using alsa.

If you get a solution, write here!! I'll do the same!

cheers

---

### Post by chuckao on 2006-08-04
> **Frostmourne said:**
> Has anyone been able to upgrade the BIOS on these laptops without using Windows? It seems the BIOS upgrades are distributed as .exe's which not even Wine or a file extractor can open.

No, I need to use Windows :evil: 

Well, I just have Windows in machine because of this :mad: 

cheers,

---

### Post by newlinuxusr on 2006-08-04
i have a dell inspiron e1405 which i think is the same except for i have intel intergrated 945gm graphics. Everything works including SD except I have not been able to get suspend to work for me no matter what I try. It goes into suspend mode and everything works except when I go to take it out of suspend it gives me an error that says "[some numbers]hci_usb 2-1:1.0:resume error -5" and it doesn't respond to anything. I tried the solution of uncommenting the line but that didnt work.

---

### Post by quini on 2006-08-05
> **newlinuxusr said:**
> i have a dell inspiron e1405 which i think is the same except for i have intel intergrated 945gm graphics. Everything works including SD except I have not been able to get suspend to work for me no matter what I try. It goes into suspend mode and everything works except when I go to take it out of suspend it gives me an error that says "[some numbers]hci_usb 2-1:1.0:resume error -5" and it doesn't respond to anything. I tried the solution of uncommenting the line but that didnt work.

What have you got in the "MODULES=" line in /etc/default/acpi-support ??

-----
sudo cat /etc/default/acpi-support |grep MODULES=
# on resume. An example would be MODULES="em8300 yenta_socket"
MODULES=""
-----

If no modules are listed there, you could try adding usb related modules to it.  For instance:

MODULES="usbhid uhci_hcd ehci_hcd"

I'd first check what modules are loaded in your box.

Hope that helps  ;)

---

### Post by newlinuxusr on 2006-08-05
> **quini said:**
> What have you got in the "MODULES=" line in /etc/default/acpi-support ??

-----
sudo cat /etc/default/acpi-support |grep MODULES=
# on resume. An example would be MODULES="em8300 yenta_socket"
MODULES=""
-----

If no modules are listed there, you could try adding usb related modules to it.  For instance:

MODULES="usbhid uhci_hcd ehci_hcd"

I'd first check what modules are loaded in your box.

Hope that helps  ;)

how would I check what modules i have?

---

### Post by frogotronic on 2006-08-05
> **ficotalancon said:**
> Check your swap partition, it must be at least 1.25 of your ram memory, im using 1GB of RAM memory and 1.5 GB of swap on a e1505 and the hibernation mode works perfect..;)

how can I change the size of the swap partion?  I have a Dell Inspiron 8100 - same problemss: no suspend, no hibernation

---

### Post by UltraMathMan on 2006-08-05
> **newlinuxusr said:**
> how would I check what modules i have?
```
gedit /etc/default/acpi-support
``` then look for MODULES="*any modules you have*" 

Hope this helps :)

---

### Post by quini on 2006-08-05
> **newlinuxusr said:**
> how would I check what modules i have?

lsmod command shows all modules loaded:

quini@quinipt:~$ lsmod |grep usb
usbhid                 38464  0
usbcore                94940  4 usbhid,ehci_hcd,uhci_hcd

The above command shows 2 modules containing "usb" in its name, usbhid and usbcore.  It also shows that modules usbhid, ehci_hcd & uhci_hcd depend of usbcore, so they are also usb related.

First try editing /etc/default/acpi-support "MODULES=" line, and add usbhid, then try to suspend:

MODULES="usbhid"

If the above doesn't work, try different combinations of the modules that depend on usbcore (the list may vary from mine); all modules listed in that line have to be sepparated by a space.

Good luck ;)

---

### Post by Fry-kun on 2006-08-11
Hi all,
I'm also having some problems with the headphones jack ](*,) 
I left the windows partition intact, so I was able to check my theory - apparently the headphone plug detection is now done in software. In fact, if you insert a plug into the microphone jack, it pops up a dialog asking if it's a microphone or line-in (difference being that line-in works by varying a small voltage that it also supplies, and the microphone just changes the resistance to encode the sound)
I've never actually heard of this being done in software before - this was a shocker to me... but anyway, it looks like the kernel (or sound drivers) will need to get support for this before our problem is solved.
Does anyone know who to contact about this? ALSA developers? Kernel developers? Person(s) who wrote the sound card plugin/driver (in my case it's recognized as SigmaTel in windows and Intel 82801G (ICH7 Family))?

---

### Post by cyberkoa on 2006-08-12
I have E1505 also.

My problems are 

1. Memory Stick cannot be read but SD can.

2. My built-in Audio cannot use sound input. This is a big problem for me because I need to use voice chat. 

3. Suspend problem - after I put the laptop in hibernate mode, I try to resume , the ubuntu restart and come to the logon screen , after I logon , it  wouldn't enter GUI and keep going back to the log on screen.

I heard that the problem 1 has been solved in lastest kernel but anybody know  the status of problem 2 ?

---

### Post by bmandoline on 2006-10-03
Reference:
------------------
Re: Dell Inspiron 6400/e1505 
yes, i have the same problem: speakers/headphone audio output not switching properly. (with my dell inspiron e1505)
currently, fresh boot without headphones plugged in and no sound from speakers. when i plug in the headphones i hear audio through the headphones. when i unplug them i still get no audio output from the speakers.
i'd rather not roll the reboot dice.
i'm searching for more info.
soundcard: sigmatel STAC9200
using default ubuntu sound setup of alsa/esd
---------------------

My hint: Kick your DELL-Sigmatel audio chip to perform as you want and go to : [http://www.ekhoury.com/2006/08/25/sigmatel-stereo-mix-support-for-dells/](http://www.ekhoury.com/2006/08/25/sigmatel-stereo-mix-support-for-dells/) for your solution for your Dell Inspiron. 
I am looking for a solution for same problem for my :( :( Dell Dimension5100 :( with same Sigmatel chip, however an other processor chip then your Inspiron .
Cheers, Bert

---

### Post by atxlin2006 on 2006-10-20
I am unable to get the MMC Card Reader working on my Inspiron e1505.  I noticed some people here were able to get it working without any special procedures.  How?  Please let me know.  Thanks.

---

### Post by humbll on 2007-03-10
i am trying to get the memory card reader to recognize my fujifilm xD 128MB card from a camera. no idea where to begin.
any ideas?

---

### Post by weijie90 on 2007-03-26
> **atxlin2006 said:**
> I am unable to get the MMC Card Reader working on my Inspiron e1505.  I noticed some people here were able to get it working without any special procedures.  How?  Please let me know.  Thanks.

Are you using edgy? I believe that it's a kernel issue.

---

### Post by Jeroen Vernooij on 2007-07-06
> **atxlin2006 said:**
> I am unable to get the MMC Card Reader working on my Inspiron e1505.  I noticed some people here were able to get it working without any special procedures.  How?  Please let me know.  Thanks.

same problem here :(
Anyone got a solution?

I am on gutsy tribe 2 by the way.

---

### Post by Essence on 2007-07-24
Mine works ok for SD cards, but not MMC.

---

