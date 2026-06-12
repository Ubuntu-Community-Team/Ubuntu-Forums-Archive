---
title: "Fan doesn't work under ubuntu - cause of slow CPU?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by chochem on 2007-05-12
I just installed Feisty as a dualboot option alongside Windows XP. The installation went well but I have one major problem: Whenever I choose Ubuntu in GRUB and the startup process gets underway the fan stops and isn't heard from again until I reboot (it fires up before GRUB and continues to work if I choose XP but as explained, cuts out if I choose Ubuntu). I strongly suspect that this is the reason that everything feels just slightly unrepsonsive in Ubuntu as opposed to an equally fresh install of XP. 

My computer is a FujitsuSiemens laptop, an [AMILO L1310G]("http://www.fujitsu-siemens.nl/home/products/notebooks/amilo_l_1310.html") to be exact. One of my personal suspects is the throttling option, i.e. the ability to lower CPU usage in order to reduce noise, however when I check in Windows, this is noted as disabled. 

Any help appreciated.

---

### Post by silkstone on 2007-05-12
Try installing the sensors-applet from Synaptic. This will display the processor temperatures in the top panel, so you can see if there's an overheating problem.

On my laptop (Acer 5612) running Feisty, the fan doesn't become audible unless the temp rises to over 50C. The Centrino processors are supposed to be OK up to 80C and the fan should not come on full until over 60C.

---

### Post by chochem on 2007-05-12
Than ks for the tip, silkstone. I installed it and the meter just rose from 82 C to 84 C.... Better switch to Windows now....

BTW CPU is listed as Celeron M 370/390 in the data sheet. SpeedFan under Windows reports ACPI temperature (?) as a rocksteady 72.8 C. Dunno it that is reliable/relevant/menas anything.

---

### Post by silkstone on 2007-05-12
Oops that's not good. The two cores in my T2300 general settle at around 45C and go up to about 55C if I'm doing anything intensive. They've never shown as being over 60C.

I do sometimes hit a bug on boot-up when the fan stays on full, and one core shows as 74C and the other 25C. Something is obviously amiss with the sensor readings and it's adding the two together or something. It only happens occasionally though, and sorts itself out if I reboot.

---

### Post by chochem on 2007-05-12
Hmmm no, you're right there. Obviously Ubuntu doesn't attempt to control the temperature - either because it doesn't measure it to be abnormal or because it doesn't control the fan or some point in between. Does anybody have any ideas as to what if anything can be done about it? I'd hate to abandon Ubuntu just because of something like this....

---

### Post by Kakihara on 2007-05-16
Well, I have the exact model(same piece of crap) and have this problem since edgy(one release before feisty).
It seems, that newer kernels (>2.6.15) dont't work together with crappy amilo acpi implementation. My solution is to use kernel from dapper drake (2.6.15) in edgy(planning to upgrade to feisty soon).

Other solution might be to add acpi=off as the kernel boot parameter, however this might disable some acpi advantages(gnome-power-manager?, shorter life on battery).
Anyway, if you manage to make this computer work with some newer kernel(either some ubuntu tricks, firmware hacks or even other distro), please, let me know...

---

### Post by chochem on 2007-05-18
Well, we agree on that, Kakihara. If it wasnt because I have difficulty doing without my pc, it would be going continually back and forth between me and the repair shop, goddamnpieceofjunk. The paint's coming off, keys are coming unstuck and the **********ing cd-rom-drive can't read the cds it's burned itself.... :mad:

Thanks for your suggestions - unfortunately I don't know how I would go about either one. Can you help me with some instructions?

---

### Post by Kakihara on 2007-05-24
Ok, the acpi=off solution: Start your computer, in GRUB(the OS selection tool)  press 'e' button, when your default kernel is highlighted. This should allow you to edit kernel boot parameters. Just add acpi=off to the end of the line. Press enter and then 'b' key. Your kernel should boot without acpi support, thus with fans running always full throttle and no battery monitoring support...

2.6.15 solution: install Ubuntu Dappar Drake(comes with 2.6.15 by default). Update to edgy using ubuntu update manager. Update to feisty, using update manager. You should have feisty installed now, but still have 2.6.15 kernel available at boot.
You can also install 2.6.15 kernel right form feisty, just check the forum...shouldn't be too difficult.

Hope this helps & sorry for my english..

---

### Post by chochem on 2007-05-24
Cool. Thanks for the tips, Kakihara - I'll try 'em out and see how I fare. And your English is fine, no worries :)

---

### Post by chochem on 2007-05-24
Hmmm... I restarted, added 'acpi=off' to the end of the kernel line, and proceeded to boot. Everything seemingly went well, Ubuntu started, the fan still running. I noticed some failure or other during startup about sensors which seemed reasonably compatible with 'acpi=off'. Difficulty set in once I got to logging in. The short drum roll announcement that accompanies the log in screen kept going in and endless loop. I logged in and the screen changed to just being all brown and the sound continuing (though curiously in a slightly different pitch). Having waited for something to happen for a minute or two, I shut down. Though I annoys me, I have really no idea as to why this should the result. Something depends of these monitors (obviously the gnome applet that I installed to monitor temperature but should that be able to crash the whole thing?) ?

 I'll have a go at the other option as well, just thought I'd post my experience right away.

---

### Post by Kakihara on 2007-05-26
Hmm, weird. Unfortunately I don't have time for experiments right now.
I just checked my /boot/grub/menu.lst (configuration of boot parameters) and realised, that i have some more parameters. This is alchemy and I don't know what does what, but may help a bit:
```
noapic irqpoll pci=routeirq
```
This works with 2.6.15, but i don't know why. You may try it.

Also check [this thread]("http://ubuntuforums.org/showthread.php?t=285868")

Have to go now, good luck...

---

### Post by chochem on 2007-07-09
I have to admit that I never really got anywhere further than that. I tried the easy way, stumbled, made an attempt at the build-your-own-core approach but never made much headway (leaving the processor to do some pretty intensive workout for two hours made me a wee bit nervous about the temperatures it would reach...) So the solution (my solution/a solution) was a hardware one: a) return it to the store to have them switch the fan and b) intel celeron m 1.6 GHz processor out - intel m 1.8 GHz processor (some £30-40 on ebay)  in. Since the non-celeron processor is able to adjust on the fly, it will drop from working at 1,8 GHz whenever it isn't needed. Thus much less heat. Thanks to everyone who chipped in - hope this might be useful.

---

### Post by Kakihara on 2007-07-13
Never really thought about upgrading my laptop. So your Amilo L1310G is running with pentium m processor now? cool.
I just don't understand the fan thing. How would fan replacement help a software problem? Or you made them install it so that it is instantly running, or you are running fan-less now?

Anyway, good news. Yesterday i compiled a 2.6.22.1 vanilla kernel and it runs nicely,except for wireless. Fans on, everything ok. First working kernel since 2.6.15 :-)
Right now I'm downloading ubuntu 2.6.22 kernel from gutsy and hope for the best.
Will let you know.

---

### Post by mips on 2007-09-09
Got this very same problem on an Amilo L1310G. Anyone notice how the fan intake is blocked on this laptop. Does not seem normal/right as they air intake should be open in my opinion.

---

### Post by mips on 2007-09-09
Okay, the 2.6.22.11kernel fixed the fan problem.

Edit your /etc/apt/sources.list file and add the Gutsy repositories. Update synaptic and install the latest kernel from Gutsy.

---

### Post by chochem on 2007-09-12
Sorry Kaikhara, I must have missed the thread email. To be honest, I kinda doubt that there was anything wrong with the fan - I just wrote 'heat' under the list of problems and when it came back they had replaced the fan. The difference is obviously in the CPU.

To mips: Yes, the techie friend who switched my cpu noticed this too. In fact I think the rows of perforated holes were blocked by some sort of metal foil and the part below the fan is covered by plastic rather than an intake. I let him remove the metal foil but suggested we wait and see rather than proceed witht his idea of drilling tiny holes in the plastic to create an intake :) We were unable to come up with any explanation for either of these 'cover-ups'.

---

### Post by mips on 2007-09-12
> **chochem said:**
> 
To mips: Yes, the techie friend who switched my cpu noticed this too. In fact I think the rows of perforated holes were blocked by some sort of metal foil and the part below the fan is covered by plastic rather than an intake. I let him remove the metal foil but suggested we wait and see rather than proceed witht his idea of drilling tiny holes in the plastic to create an intake :) We were unable to come up with any explanation for either of these 'cover-ups'.

The perforated holes are blocked by metal foil/shielding as well as tape only leaving about two slots open of about 6 or so.

The plastic covering the fan is also held in places by metal foil/shielding & tape. You could use a sharp hobby knife to cut around it if one wanted to remove that round piece of plastic covering the fan intake.

I have no idea why it's done like this. One could always install xsensors to monitor the temperature at different load levels and record them. Then open the perforated vents and do the same followed by removing the plastic over the fan intake and recording the results. This way one would be able to see the effects of allowing more air into the system. Should be a interest experiement.

Your fix probably came about because the speedstep technology used between the celeron and normal cpus differ.

---

### Post by Kakihara on 2007-09-28
> **mips said:**
> Okay, the 2.6.22.11kernel fixed the fan problem.

Edit your /etc/apt/sources.list file and add the Gutsy repositories. Update synaptic and install the latest kernel from Gutsy.

Do you really have no problems with this kernel?

I tried gutsy 2.6.22 kernel before and even now with the newest one (2.6.22.12), i still have issues with sound. First half of second sent to soud card repeats in a neverending loop.
I don't have this sound problem with custom compiled 2.6.22 vanilla kernel though the wireless and wacom tablet doesn't work.

Is the sound working for you?

---

### Post by mips on 2007-09-29
> **Kakihara said:**
> Do you really have no problems with this kernel?

I tried gutsy 2.6.22 kernel before and even now with the newest one (2.6.22.12), i still have issues with sound. First half of second sent to soud card repeats in a neverending loop.
I don't have this sound problem with custom compiled 2.6.22 vanilla kernel though the wireless and wacom tablet doesn't work.

Is the sound working for you?

This is not my laptop but a friends and YES the sound works fine.

---

### Post by chochem on 2007-11-22
Having installed Gutsy afresh (2.6.22-14) I'm also having sound issues that I believe to be the problem you describe. As a general rule sound plays fine but usually sooner or later it gets trapped in just such a "neverending loop" - typically when I quit VLC/mplayer without stopping video playback or sometimes from Rhythmbox/Banshee/Exaile and sometimes from a game. I haven't really been taking notes systematically but using the 'kill' command on the program (if "force quit" doesn't show up on its own accord) tends to get rid of the sound but I still have to restart to get any sound back....

---

### Post by Kakihara on 2007-11-22
I am still dealing with this issue.
Could you try going to panel menu System->Preferences->Sound and set Alsa instead of Autodetect everywhere, where possible?  AND / (OR) try adding pci=noapic to your kernel boot paramaters?

And post here yor results...

I'm now running with both of these things set for several hours and having no problems so far(mixing flash&totem&pidgin&mplayer)

---

### Post by chochem on 2007-11-23
I'll try that. How do edit kernel boot parameters?

EDIT: And can I just ask you: Running under Gutsy, have you had any trouble with blocky video playback? I've been trying various combinations of general overlay (xv/openGL/etc.) and video players to avert this issue related to the proprietary fireglx driver for the ATI Radeon 200M on the 1310G. Just curious if you had experienced something like this too...

---

### Post by Kakihara on 2007-11-24
edit /boot/grub/menu.lst and add pci=noapic to the end of line: ```
kernel /boot/vmlinuz-2.6.22.14-generic root=whatever ...... pci=noapic
```
and reboot
you can do it also in grub by pressing 'e', 'e', editing and then pressing 'b' :) (this way, it will not be permanent)

and no, i dont have video playback problems. running fglrx driver, but event with radeon driver, i believe it was ok.
did you try mplayer?

---

### Post by chochem on 2007-11-24
Yes, I eventually settled on xv in both xorg.conf and vlc which works for everything but .wmv files for some reason (for which I use mplayer). However I needed to actively set the overlay (in xorg.conf) using the aticonfig tool to get the rid of the problem. As it was at the time of install all playback was blocky, regardless of player.

Edited done and done... I'l reboot and see over the coming days if it goes away. Thanks for the tip :)

---

### Post by chochem on 2007-11-26
Uhm not so good it seems.... I changed the autodetects to ALSA but it didn't seem to change anything. 

and I just noticed that during startup a notice comes up saying that noapic is an unknown option for PCI.... :(

---

### Post by Kakihara on 2007-11-26
Erm, ok, you are right. The pci=noapic parameter doesn't exist. The correct one is just 'noapic' (without the '). But I don't know, if it really helps(it used to help me with this amilo on some older kernels with ethernet card problems). I think, you should try it like this. I will be running with noapic now also.

But anyway, i didn't have the sound issue since i added this (wrong) parameter. I also deleted the 'splash' and 'quiet' parameters at the same time, so it might be the real reason(deleting these parameters lets kernel print lots of info during boot and don't let it initialize the framebuffer(vga progress bar) IMHO).

so, i would advice you to change 'pci=noapic' to just 'noapic' and delete splash and quiet (or how these parameters are called-i don't remember exactly-i deleted it lol ).
And please report whether it helps or not. good luck

---

### Post by Kakihara on 2007-12-15
Ok, in case someone with Amilo L 1310g is still reading this, the best way for booting I see so far is deleting the default **quiet** and **splash** parameters(causing slow boot for some reason) from the kernel parameters and adding **pci=routeirq** (as suggested by the kernel itself - try running **dmesg|grep irq** ).
the previously suggested **noapic** parameter caused my usb mouse&keyboard not to work after some time.

Now if only we could get suspend to ram working...

---

### Post by chochem on 2008-01-21
Kakihara, you're a life saver. I'm sorry to say that this thread had completely slipped my mind and only rediscovered it, searching for an different issue with... yes, the amilo l1310g :) I've tried your suggestion for a day now and no more audio issues - thank you, thank you, thank you...

Uhm now that I'm here... Can I just ask you how you turn on the wifi? Seeing as how the wifi-switch seems to be windows dependent?

---

### Post by Kakihara on 2008-01-21
Glad to help...

Wifi is one thing i always had trouble to get working with NetworkManager, especially with WPA.
It sometimes worked, but hard freezed my system after while(no security/ WEP), or it wouldn't connect(WPA). I tried compiling newest rt2500 driver from serialmonkey(not the rt2x00, which is for newer kernels) - caused hard freeze after load. Tried ndiswrapper, which almosed seemed to work, but wouldn't find any network(as you mention it, i never tried to press the 'wireless' button next to power button, i should have tried it. but still, i don't think it does matter in linux).

Anyway, i'm running the hardy 2.6.24 kernel now(because of faulty drivers for motorola gprs modem in 2.6.22). I didn't try the wifi with it and don't have any visible now, but it "could" work. Since I will be busy for at least another 14days(exams), i will not experimen with it, but if you had time, you could install the hardy kernel(it is as easy as changing every 'gutsy' to 'hardy' in /etc/apt/sources.list and upgrading kernel-generic and than changing /etc/apt/... back).
It should be also possible to compile rt2x00 driver with the 2.6.24 kernel. There is high possibility, that it would work.
But on the sad side - problems with fans on this amilo are back with 2.6.24. If you boot from cold state, the kernel would shut the fand down and never make them run again. My solution is to reboot once the system gets hot(5 minutes). The kernel wouldn't switch fans off after that and you can work. Sad, but still worth it for me...

Anyway, good luck. I will experiment again later...

---

### Post by mips on 2008-01-21
> **Kakihara said:**
> 

Anyway, i'm running the hardy 2.6.24 kernel now(because of faulty drivers for motorola gprs modem in 2.6.22). I didn't try the wifi with it and don't have any visible now, but it "could" work. Since I will be busy for at least another 14days(exams), i will not experimen with it, but if you had time, you could install the hardy kernel(it is as easy as changing every 'gutsy' to 'hardy' in /etc/apt/sources.list and upgrading kernel-generic and than changing /etc/apt/... back).
It should be also possible to compile rt2x00 driver with the 2.6.24 kernel. There is high possibility, that it would work.
But on the sad side - problems with fans on this amilo are back with 2.6.24. If you boot from cold state, the kernel would shut the fand down and never make them run again. My solution is to reboot once the system gets hot(5 minutes). The kernel wouldn't switch fans off after that and you can work. Sad, but still worth it for me...

Anyway, good luck. I will experiment again later...

As far as I know rt2x00 is included in 2.6.24 kernel so you should not have to compile them from scratch.

---

### Post by onefilip on 2008-01-22
hi.
I have a fujitsu siemens L1310G and I have installed ubuntu 7.10 !
I have the same problem with the fan because the fans are always on! 
If I run windows xp the fans runs normal, only where there are some process the fans are noise.
but with ubuntu fans are always on! since it start!
can you help me?
When I have ubuntu 7.04 installed the fans runs as windwos Xp but now the noise is very high!

chochem: what have you done to solve the problem?
I have wifi installed and wifi work ok! but I haven't restriced driver for ATI video enable becuase with ths driver the fan are always on!
pleeeese heeeelp meeee!
save me!

---

### Post by chochem on 2008-01-22
> **Kakihara said:**
> ... if you had time, you could install the hardy kernel(it is as easy as changing every 'gutsy' to 'hardy' in /etc/apt/sources.list and upgrading kernel-generic and than changing /etc/apt/... back).


I replaced all gutsy's with hardy's, saved, and ran sudo apt-get upgrade and waited for the upgrade notice to show up. When I open the upgrade thingy, I get a notice saying that "Not all upgrades can be installed" and I'm unable to check the linux-generic, linux-image-generic and linux-headers-generic packages. 

Odd that. I guess other than upgrading this way, I have the options of building a gutsy distro with 2.6.24 myself or getting hold of a hardy alpha (if it's even at that stage?) I'm probably going to reinstall the lot in a couple of days or weeks so I'll try again from a clean install, see how that works. 

The rt2x00 driver is for wifi? or the modem thingy?

onefilip: wifi works in 7.04? I never really tried until I went to friend's place and he tried connecting me to his wireless network. As for my solution  to the fan issue, I'm gonna quote my own post in this thread:

[QUOTE=chochem]I have to admit that I never really got anywhere further than that. I tried the easy way, stumbled, made an attempt at the build-your-own-core approach but never made much headway (leaving the processor to do some pretty intensive workout for two hours made me a wee bit nervous about the temperatures it would reach...) So the solution (my solution/a solution) was a hardware one: a) return it to the store to have them switch the fan and b) intel celeron m 1.6 GHz processor out - intel m 1.8 GHz processor (some £30-40 on ebay) in. Since the non-celeron processor is able to adjust on the fly, it will drop from working at 1,8 GHz whenever it isn't needed. Thus much less heat. Thanks to everyone who chipped in - hope this might be useful.
[/QUOTE]

I haven't had any overheating since, and the fan works normally (like you'd see in xp). Having the fan switched was due to it being bust and is probably not essential.

---

### Post by onefilip on 2008-01-22
hi
I don't remember if wireless with 7.04 work... Now with 7.10 wireless on L1310G work very well, I have installed the Fsaa driver...and the led of wireless card is always on...fantastic!!!!
now I don't remember what is the web site for install these drivers but if you want I post here tonight!
Plese, Have you solve the problem of fans on ubuntu 7.04?
is there a guide or steps to do it?

---

### Post by chochem on 2008-01-22
Uhm all I can say is that you should read the thread... Kakihara has posted a lot of ideas regarding what kernels work and which ones don't and how to go about it. And if that doesn't work for you - well, as I said in my previous post, I think the cause of the issue is the celeron processor. Chuck it and you've solved the problem.

As for fsaa... My googling seems to tell me that it's graphics related (full screen anti-aliasing) and a feature of the aticonfig utility. So I think you may have got things confused.

---

### Post by Kakihara on 2008-01-22
I don't remember what kernel was shipped witch 7.04, but i believe, that kernels newer than 2.6.15 and older than 2.6.22 had problem with not running fans sometimes and thus overheating.

The problem is not with the Celeron processor, but with the buggy Fujitsu ACPI(it tells the OS how to handle hardware power, temperatures, fans, suspend....). It is possible to disassemble the ACPI of a laptop(howto is somewhere on the net or in forums and it's not difficult) and if you do so(I did), you will see conditions like "if system="Windows XP, do ....whatever" "if system=Win 98 ...".
You can  try to correct the ACPI(I don't have the skills) and load it up. You can also tell the laptop, that your system is "Windows XP" (you can do this with some kernel parameter, which I don't remember now), but it didn't help me much with the 2.6.17(I didn't try with newer kernel). It's worth the try, anyway.
So basically what Fujitsu did is that they have written buggy ACPI code(you can compile the dissassembled ACPI with IBM ACPI compiler and you will see the errors) and tuned it so that it somehow works with windows(which, btw, doesn't follow ACPI standard very closely).
This is why our fans either run always full throttle or doesn't run at all. Many laptops have problems with ACPI, but this fujitsu laptop is exceptionally buggy.

As for the wifi, i tried the new rt2500pci module bundled with 2.6.24 and had no luck connecting to WPA encrypted network. Will try some more tricks later.

for chochem: you don't need to upgrade to hardy completely. You can just change the /etc/apt/sources.list (in vim you run ":%s/gutsy/hardy/g"). Than run "apt-get update" than in synaptic select only linux-kernel-generic, or how it is called now, and upgrade it(it will also upgrade some few other packages but not more than 10). Than change the /etc/apt/... back and you can run gutsy with hardy kernel.(don't forget to add the pci=routeirq line)

Anyway, if you had some luck witch this crappy amilo, please inform us in this thread..
gotta go now...

---

### Post by chochem on 2008-04-17
> **Kakihara said:**
> Anyway, if you had some luck witch this crappy amilo, please inform us in this thread..
gotta go now...

I'm fiercely proud to say that I believe that I have had just that :) In a demonstration of just how much the forum search sucks, I had to google "ath_pci rfkill" to stumble upon [this thread]("http://ubuntuforums.org/showthread.php?t=203242") (and looking for more of Eversmann's pearls of wisdom, [this one as well]("http://ubuntuforums.org/showthread.php?t=207428&highlight=l1310g")) The threads are almost two years old, and I figured that his remarks about having to get another driver might no longer be current, so I just went ahead and did
```
sudo rmmod ath_pci
sudo modprobe ath_pci rfkill=0
```
and checking 'dmesg', looked promising:
```
[ 5592.640000] ath_pci: driver unloaded
[ 5604.832000] ath_pci: 0.9.4.5 (0.9.3.2)
[ 5604.832000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
**[ 5605.420000] ath_pci: switching rfkill capability off**
[ 5605.428000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 5605.428000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 5605.428000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 5605.428000] wifi0: mac 7.8 phy 4.5 radio 5.6
[ 5605.428000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 5605.428000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 5605.428000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 5605.428000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 5605.428000] wifi0: Use hw queue 8 for CAB traffic
[ 5605.428000] wifi0: Use hw queue 9 for beacons
[ 5605.428000] wifi0: Atheros 5212: mem=0xc0200000, irq=11

```
('rf kill' is radio frequency kill)
I opened the network-manager applet, found my friends' wifi network and I'm writing this via that  :-) No installs or anything. Mind you, I haven't figured out how to make it permanent yet but the Eversmann threads seem to be full of suggestions.

---

### Post by Eversmann on 2008-04-25
Just some heads up. I'm testing Hardy and i have plans to update the wiki page with instructions on how to install hardy from scratch on this laptop.

And.... i really really cross fingers on this, i'm trying to fix the fan switching off bug that we're having in hardy. Right now, i've tweaked the dsdt file and, right now, using it for almost an hour with no heat problems. Hope so, because before after 15 minutes the fans goes down.

But i won't post anything until i can confirm this. I'm not an expert on acpi tables and don't think i've done anything yet..... (or just anything so obvious on the dsdt file).

It's a big problem and, once i can confirm this, i'll post, and report it on launchpad.

---

### Post by chochem on 2008-04-26
Good idea, Eversmann, and thanks again for the original posts. Since I haven't got the original CPU, I can't really comment on the heat issue and my fan's working fine. Obviously a mention might be made of the fact that the fglrx driver now works with compositing. Other than that I don't know if there are any 1310-news for hardy, but I'll bookmark the page and see what you come up with.

BTW: Do you still follow th procedure you describe in the thread I referred to to get wifi working? I just sorta took the easy way out and added the two lines (minus sudo) to /etc/rc.local...

---

### Post by Eversmann on 2008-04-26
well, actually, to make the wifi work is really easy. Since gutsy, atheros driver are up to date, so just only putting in modprobe.d/options the rfkill=0 for the ath_pci, and compile the fsaa1665g and add it to the module options with radio=0 (to enable the radio antenna). Doing that the wifi is fully functional and NetworkManager works great.

BTW, does any of you guys who have the fan problem have the following options on your bios enabled?

USB legacy support
0 bit compability mode.

My works on the dsdt file didn't worked ok. I'm trying to get any other dsdt table from a linux distro that comes with 2.6.24 kernel and work (right now, opensuse 10.3 and fedora 8, neither of them booted easily). But, with the dsdt file tweaked, and those options from the bios disabled, the laptop is working cool all this evening (and i've done a few reboots). So if in the next days everything works like in gutsy, i'll post it.

---

### Post by akamuza on 2008-04-26
i got the same fan issue with may Amilo L1310G
in 7.10 everything worked fine, but in 8.04 the fan just stops 
after about half an hour of working and then never starts again.. 
and the system slows down critically - almost impossible to work. 
so i have to reboot to make the fan work again. 

trying to find any way to fix this problem, but i'm a novice to Ubuntu so it's kind of difficult for me )

---

### Post by Eversmann on 2008-04-28
Well, finally it's fixed. Here is the bug thread i started since feisty, and my last post  explains what is broken, and how to fix it. There is the dsdt.aml compiled for that.

Right now, working great, 

[https://bugs.launchpad.net/bugs/72775](https://bugs.launchpad.net/bugs/72775)

---

### Post by shayan_mihiran on 2008-04-28
Hey Frnd try dis out.:)

try tio istall Im Sensors

Go to Console ant type 
apt-get install im sensrs

---

### Post by Eversmann on 2008-04-28
I think he's saying to install lm-sensors package. This is a must for every laptop, but for the l1310g doesn't work.

---

### Post by chochem on 2008-04-28
Glad you translated it - I thought it was a Russian bot posting trying to get me to install spyware... :D

---

### Post by chochem on 2008-06-08
> **Kakihara said:**
> Hmm, weird. Unfortunately I don't have time for experiments right now.
I just checked my /boot/grub/menu.lst (configuration of boot parameters) and realised, that i have some more parameters. This is alchemy and I don't know what does what, but may help a bit:
```
noapic irqpoll pci=routeirq
```
This works with 2.6.15, but i don't know why. You may try it.

Also check [this thread]("http://ubuntuforums.org/showthread.php?t=285868")

Have to go now, good luck...

Ever since Hardy came out I've been seeing some irregularity in USB performance. After a long and tedious search and more data loss than I care to contemplate, I finally found out that the 'noapic' parameter that I'd been draggging along since I can't remember when was the culprit - digging this thread fortunately came up with an alternative that works 'pci=routeirq'. But just as Kakahari said, I don't really know the why or wherefore either... Anybody else?

---

### Post by Eversmann on 2008-06-08
Actually chochem, those options aren't necessary to use on hardy with this laptop anymore.

If you force the irq approach from the kernel to "noapic" or worse like pci=routeirq you'll have some performance decrease. Those options should be used just if they strictly are necessary. 

If you use hardy, the usb disconnection because of ATIIXP chipset isn't an issue anymore, and the fan problem is fixed by the dsdt file i provided. 

If you're still having problem do a clean install of hardy. I can tell you that i'm running the fujitsu l1310g with no further necessary changes on the kernel boot line, just the one for telling the kernel to load my dsdt file instead of letting it generate one by itself.

---

### Post by chochem on 2008-06-08
That's odd... When I found out that noapic wasn't any good, I just removed it from the boot options, so that the only ones left were ro and quiet (default, right?) 

Noapic was the cause of very slow usb transfers but with the new no-parameter setup came a new problem: Striking  seemingly at random, transfers would slow to a crawl and the file manager/shell would be come unresponsive and eventually the device would disconnect entirely (no sdb in /dev). That's when I tried various alternative boot options - seems like irqpoll is (also) needed.

Of course, if you're right, I must've done done something myself to **** things up, so that the boot parameters are needed but what that would be is beyond me...

---

