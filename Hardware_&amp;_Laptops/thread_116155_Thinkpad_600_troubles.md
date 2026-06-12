---
title: "Thinkpad 600 troubles"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by thefamousnomo on 2006-01-12
hello people, power windoze user, n00b liunx user enjoying a steepish learning curve here! have installed breezy on a few machines without too many problems, any faced i have managed to get through picking up the little bit of knowledge i have. but, i digress -

problems:

 - am only afforded 800x600 res at max, suspect need driver but unsure how to go about this linux-wise

 - no sound at all

but, before all that, i have a d-link dsl604-t router which another ubuntu-box is hardwired into, no probs at all. want to establish wireless from this thinkpad, which uses a belkin pcmcia card. now, before i can start to go through all the great advice surrounding this issue (kinda looking forward to cracking it!) the following happens:

 - have 2 tvs communicating in top right hand corner that i havent seen on any of my other installs (a la winnt, i hate myself!) but when trying to configure the wireless connection the machine freezes. ubuntu has detected the wireless connection is present (i think) but wont allow me to configure.

slightly off topic, although i feel im getting somewhere i feel i would benefit from getting into the guts of linux. i have seen on a few forums that a basic debian / gentoo install could teach me more about the basic workings of the os. anybody have any comments / ideas / suggestions? all welcomed!

thanx!

---

### Post by bags on 2006-01-12
i'm not very expert and i don't speak english very well (:D) but you can try to find something about the right config of you laptop here: [http://www.linux-on-laptops.com/ibm.html](http://www.linux-on-laptops.com/ibm.html)
i have an ibm r31 and i solve all my problem in this way :D
matteo

---

### Post by thefamousnomo on 2006-01-12
[QUOTE=bags]i'm not very expert and i don't speak english very well (:D) but you can try to find something about the right config of you laptop here: [http://www.linux-on-laptops.com/ibm.html](http://www.linux-on-laptops.com/ibm.html)
i have an ibm r31 and i solve all my problem in this way :D
matteo[/QUOTE]
thanx man, but none of the advice on the site under thinkpad 600 helped at all. i backed up the files i had to modify and made the changes described but still no joy.

0 out of 3 issues so far, im throwing this back out there, anyone else any ideas?

---

### Post by grumpymole on 2006-01-12
Sound: Search this forum as I know that there have been previous threads about TP 600 sound issues.  It takes a little fiddling to get it working.  I have a TP 600E and got mine working, but the 600 is slightly different.

Also, I know that my PCMCIA ethernet card won't work unless I add the boot parameters acpi=off and pnpbios=off.  This also helps with sound card detection.  To change these, press 'e' during the GRUB boot (during the countdown).  Select the kernel you are booting with, probably the most recent, and then 'e' again (I think) will allow you to add 'acpi=off pnpbios=off' to the end of the line.  Then 'b' to boot.  If this helps, then edit /boot/grub/menu.lst and add them permanently.

One other thing to check (not sure if this applies to the 600E only) is that there is a BIOS option called FastBoot.  This must be disabled, otherwise it also messes with sound card detection.  When you boot, (Alt-F2, I think) enter BIOS settings and disable it.

Regards

Warren

---

### Post by alex2035 on 2006-01-12
I received yesterday my Breezy 5.10 ubuntu CDs, I installed on my new (for me) IBM ThinkPad 600E , sure I had some problems, no sound, no Xircom PCMCIA Modem. 
A topic in Hardware/laptops solved these 2 problems, some editing and BIOS setting and it went away. I still have 2 left: my Palm refuses to sync through serial and the onboard Thinkpad modem would not exist at all (winmodem?), anyway I can live with the xircom.

hope this helps
alex

---

### Post by davinci on 2006-01-13
Try the tips in this thread, maybe they work: 

[http://ubuntuforums.org/showthread.php?t=96240]("http://ubuntuforums.org/showthread.php?t=96240")

BTW referring to your last question: Yes probably you would learn a lot more about your system with installing and configuring Debian (have been using it on my primary machine for some years; Actually I think it's not that hard nowadays). On the other hand, if you get stuck in basic configuration of Debian already and are not prepared to learn a lot, you probably will go back to Windows too soon. No good either :). Depends on you.

---

### Post by thefamousnomo on 2006-01-13
[QUOTE=davinci]BTW referring to your last question: Yes probably you would learn a lot more about your system with installing and configuring Debian (have been using it on my primary machine for some years; Actually I think it's not that hard nowadays). On the other hand, if you get stuck in basic configuration of Debian already and are not prepared to learn a lot, you probably will go back to Windows too soon. No good either :). Depends on you.[/QUOTE]
get you, but i do want to learn, the best way to do so is what i want to know. i seem to be having some trouble getting this point accross! its great to come to the forum and ask advice and get the best, even stuff that works right off. what i am looking for is to find out *why* xorg.conf, *why* /etc/modules, and so on. is there a config file for video, one for sound? do video and sound have configuration settings in different sections of one file? <- examples only, dont answer this!

aspiring to gain this knowledge is seperate from the specific issues i am having with the thinkpad, probably should have used another thread! so i did! [http://www.ubuntuforums.org/showthread.php?t=116249](http://www.ubuntuforums.org/showthread.php?t=116249), referred to a couple of books which i will give a go, but i prefer hands on, learn from mistakes type stuff. i do accept that the transistion from windoze to linux will require a bit of background research first. what do you think is the best way to go?

thanx

ps. any ideas to [http://www.ubuntuforums.org/showthread.php?t=116249](http://www.ubuntuforums.org/showthread.php?t=116249) please, can i re-rail this thread. thinkpad troubles still standing (still to try boot configuration, ill let you know grumpy!)

thanx again!

pps. havent heard any ideas on the network - hang issue, would love to hear some thoughts.

thanx again again!

---

### Post by thefamousnomo on 2006-01-13
@grumpymole

'acpi=off pnpbios=off'

am now able to adjust volume but still no sound! dont have any default sound card options in the drop down box in 

*preferences > sound*

will scrape around the forums & help stuff, see if i can get it going.

thanx

---

### Post by thefamousnomo on 2006-01-14
[QUOTE=davinci]Try the tips in this thread, maybe they work: 

[http://ubuntuforums.org/showthread.php?t=96240]("http://ubuntuforums.org/showthread.php?t=96240")[/QUOTE]
got the resolution sorted man, many thanx! still to try the rest, but have to go watch *the great escape* with the better half. we havent spent that much time together this week you see.......... :confused: 

anyway, shes working tomorrow ( :D ) so ill get through it then!

thanx

---

### Post by thefamousnomo on 2006-01-30
well, still having issues!

[http://www.ubuntuforums.org/showthread.php?t=119865](http://www.ubuntuforums.org/showthread.php?t=119865)

thanx for all help people!

---

