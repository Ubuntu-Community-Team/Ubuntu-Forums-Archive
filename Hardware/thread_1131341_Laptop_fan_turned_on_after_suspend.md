---
title: "Laptop fan turned on after suspend"
date: 2009-04-20
forum: Hardware
---

### Post by AJoe on 2009-04-20
Hello!

I'm a complete newbie to linux and ubuntu. I got fed up with Vista, I suppose Longhorn means you will grow one on your forehead from using it.

I have a HP 6735 S laptop.

So I went and replaced Vista with Ubuntu 8.10 [COLOR="Red"](EDIT: Now upgraded to 9.04, see below)[/COLOR], and so far it's been pretty excellent. Still, there have been a few problems: The laptop speakers didn't seem to work, I can't log in to my WPA2 encrypted wireless network, and last but not least, there seems to be some trouble with the cooling fan. I'll try to outline the problem for you:

Just generally surfing the internet I suddenly realized the laptop fan had been blowing full speed non stop for a long long time. I started searching the ubuntu forums for some help. I found some things to try:

the "acpi -V" command gives a proper reading of temp1, as opposed to some toshiba users reading 0.0c. Here's what it reads now:

 Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 42.0 degrees C
     Cooling 0: LCD 0 of 10
     Cooling 1: Processor 0 of 3
     Cooling 2: Fan 1 of 1
     Cooling 3: Fan 0 of 1
     Cooling 4: Fan 0 of 1
     Cooling 5: Fan 0 of 1

And the cooling fan is blasting away. It does, apparently, feel that the processor fan cooling is at 0, wonder what this cooling 2 fan is?

Someone also said to modify my grub kernel boot options, adding "acpi_osi="Linux"" to the end of the "kopt"-line. I did this as well, rebooted and everything was fine, very quiet.

So I left it at that, thinking that I fixed it. However, this evening it was doing it again, with low temperatures as well. So I went looking for more help and found a guide to recompile and fix my DSDT files. I did this far enough so that "iasl -tc /home/aleksi/ dsdt.dsl" read 0 errors, 0 warnings, 0 remarks and about 2500 optimizations. There had been only one warning, concerning _WAK not having a return value. I did all the rest of the steps, reloading it in to initramfs and so on.

Reboot, and it's quiet again, BUT:

I had read a side note about someone saying that they had this problem only when they come back from suspend, so I decided I'd try it to be sure, and lo and behold, when I go to suspend mode everything is okay, but when I switch power back on, the fan speeds up to 100% and stays on. 

The fan was completely off when I went into suspend and has now been blowing straight since I logged back in, searched the forums for others with this problem, checked acpi -V again and wrote this message. 

So what can I do? Anyone?

This problem is especially annoying since I like my laptop to go to suspend when I close the lid, and I move around with the laptop a LOT, constantly packing it away and taking it in use. This just might be a deal breaker if it doesn't get fixed. :/

---

### Post by AJoe on 2009-04-21
Hello!

I realize it's probably not the best way to conduct myself on a forum like this and that patience is a virtue when asking for help, but I still wanted to blatantly up this and ask if anyone might know a solution to this?

Thanks again

 -Aleksi

---

### Post by AJoe on 2009-04-21
Googling around, I found this bug posted here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354732)

The guys trying to solve it had asked the original poster to upgrade to 9.04 to see if the problem persists. 

I did that, and it does (plus it brought with it some new bugs of it's own, but that's unrelated...). Fan still goes on full blast after suspend. :/

But anyway, to repeat, I'm now running 9.04. 

Thanks again, 
 -Aleksi

---

### Post by AJoe on 2009-04-26
Looks like this one is still genuinely broken, haven't had any luck via google or the Ubuntu forums.

Well, it's not as bad, at least Ubuntu boots up much faster than Vista used to, and works a lot smoother too. 

If only there'd be a viable lightroom alternative... :)

---

