---
title: "Speakers weird noise on shutdown"
date: 2008-09-30
forum: Hardware
---

### Post by imbuto on 2008-09-30
Hi all,

I a new Linux user (as a sudoer, at least). I just installed Ubuntu 8.04 on my HP Pavillion dv6560el, but I think my problem does not go into the "Installation" thread.
Everything works fine "out of the box" but I have a rather annoying problem with the soundcard on shutdown (or reboot).
Basically, a rather loud and weird "pop" sound comes out of my speakers at power off (even if the audio is muted or headphones are plugged in), like when you suddenly remove battery and unplug power cord. This looks all but healthy for my speakers.
Strange enough, if I hibernate this does not happen: I see my audio control led turning amber (this is not happening on shutdown), and the laptop powering off smoothly.
How can I achieve the same behavior also on shutdown? I looked around a little bit but probably I am missing the right keywords.
Could somebody enlighten me? So far the best I could do was to cd into each /etc/rc?.d/ ...

BTW, my soundcard info are:
 *-multimedia
 description: Audio device
 product: 82801H (ICH8 Family) HD Audio Controller
 vendor: Intel Corporation
 physical id: 1b
 bus info: pci@0000:00:1b.0
 version: 03
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list
 configuration: driver=HDA Intel latency=0 module=snd_hda_intel

In the meanwhile I avoid shutting down and I just hibernate, but sometimes it is necessary to reboot...

Cheers

---

### Post by imbuto on 2008-10-13
It looks like HP sold really a lot of Pavillion dv6560el :-k... Anyway, I am trying to figure out myself how to solve the problem.

I found the exact description of my problem at
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/23984](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/23984)

I tried to add the magic alsactl power off line in the /etc/init.d/alsa-utils script, and [-o<:
```
$ alsactl power off
alsactl: Unknown command 'power'...

```
Obviously the "power [card #] [state]" command does not exist any more in alsactl...
I just wonder how to replace it.

---

### Post by lucazade on 2008-10-17
I'd like to bump this thread because i have the same issue with a hp dv5-1005 and an intel soundcard.. is there any news, suggestion or workaround?

bye
Luca

---

### Post by Helios1276 on 2008-10-17
HP Dv6920 , same issue as well.

---

### Post by Helios1276 on 2008-10-29
bump

---

### Post by JMorg on 2008-10-29
Yeah it is a common issue, however I don't think there is a way to fix it. If there is I'd love to know because I also have an HP with the same issue! It seems that it is a power based issue on shutdown and I don't know if there truly is a way to halt the little surge that generates the pop. Let's hope there is though because that would be great.

---

### Post by b0yd07 on 2008-12-09
Bump :popcorn:

---

### Post by c_pantera on 2009-02-03
Has anyone solve this problem yet?

---

### Post by eelensar on 2009-02-07
I've got the same problem with an HP dv5t. Not quite sure what the sound card is...I think it's an IDT.

---

### Post by Insanus on 2009-04-23
Same here with HP Pavilion dv5-1116ez Notebook. :(

---

### Post by jonbonjovi on 2009-05-29
same problem on HP Pavilion dv5-1112el. No solutions yet?
I havo noticed a difference, though: the problem shows only at reboot and suspend (not hibernation), not on shutdown as you're saying.

---

### Post by eelensar on 2009-05-29
Actually, I've found that this only happens when I reboot now on my HP dv5t. Otherwise, it shut downs normally.

Edit: NVM, I only read the first sentence of your post in my email. But I guess it's extra confirmation.

---

### Post by brunolabs on 2009-05-29
Same problem with a Fujitsu-Siemens Scaleo P.

---

### Post by patricio_irabien on 2009-06-07
same problem on mi hp dv5 it seems that sound server does not shuttdown on log out... if there's a solution plese post it.

---

### Post by kwidge_bo on 2009-06-11
Same problem, HP HDX
Would greatly appreciate fix!!

---

### Post by Gfnn on 2009-07-29
Same problem on HP dv6627el.

---

### Post by Stingxgl on 2009-09-11
Just bought a HP dv5-1234ca running Ubuntu 9.04 64bit... same issue.. terrible cracking on reboot just before switch over to post. Gotta be a way to disable the sound in a script while exiting ubuntu.

---

### Post by roger_la_fee on 2009-10-06
I had the same problem and found the solution here :
[http://art.ubuntuforums.org/showthread.php?t=1259307](http://art.ubuntuforums.org/showthread.php?t=1259307)
> 
Add this line:
 "blacklist pcspkr"

into
/etc/modprobe.d/blacklist.conf

Tip: Open the configuration file as root, i.e.,
Code:

 gksudo gedit /etc/modprobe.d/blacklist.conf


---

### Post by Dropbear on 2009-10-11
Not sure if my problem has the same cause but on karmic the speakers have been making a pop whenever a sound has been played or when adjusting the volume.

I seem to have fixed it now by...

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then changing 

options snd-hda-intel power_save=10

to

# options snd-hda-intel power_save=10

then rebooting.

hope this helps.

---

### Post by Albert Clarke on 2009-10-11
I recently bought a Jensen JPS8 8" subwoofer for my home system. The sub is connected with Monster cables to my Sony receiver. Now the sub works fine as long as it is on and not in auto-shutdown mode, but as soon as the auto shutdown is engaged, it gives off a very loud noise uncharacteristic of a sub. For lack of a better description, it sounds like a loud farting noise.

The sub is positioned beside my entertainment unit which houses my TV and L/R/center channel speakers. The unit has a two-prong plug, plugged into a power bar, which is a three prong plug plugged directly into a 3 prong outlet. The rear speakers are probably too far away to cause any kind of real interferance.

---

### Post by starang on 2009-12-15
Same issue.  I am using a HP DV7-2173CL running Ubuntu 9.10

I really doubt this is an unfixable issue, because I dual boot with Windows 7 on this machine, and a Windows 7 shutdown does not cause this crackling/popping noise.

In fact, my Windows 7 partition was a Vista upgrade...and Vista did not make those noises at shutdown either.

---

### Post by gbashore on 2009-12-23
Thanks Dropbear!
That fix the sound problem.

---

### Post by f1ckratte on 2010-02-19
same with me.

BUT the problem only occurs when i try to shutdown via commandline. else i dont get any noise. Also HP Pavilion DV5 here...
Dropbears solution doesnt work with me.

---

### Post by opethfan89 on 2010-03-16
Just thought that I'd post my success story, Dropbear's solution works for me running 9.10 on an HP Pavillion dv7-3060US laptop. Just commented out that line, and the sound went away :)

Thanks dropbear.


*EDIT* Well, as it turns out, the problem ISN'T gone. It now shows up even with speakers muted, so I'm really not sure what more to do. Rather annoying to have my laptop fart during class.

---

### Post by andersgb1 on 2010-04-13
No one found a solution for this yet?

---

### Post by andersgb1 on 2010-04-13
I've experienced this extremely irritating and hardware-wise severe bug both in Karmic and Lucid beta 2. Being a very frequent user (certainly no expert, though) of Ubuntu, I find it very frustrating that this bug has not been fixed. I've managed to remove the terminal autocomplete noise by appending:
```
termset -blength 0
```
to ~/.bashrc. Regarding shutdown/restart, I've tried to add scripts to /etc/rc0.d/ and /etc/rc6.d/ containing the same line, but without any luck. None of the previous suggestions involving blacklist.conf and alsa-base.conf worked for me...

EDIT: For reasons still unknown to me, the suggestion in [http://ubuntuforums.org/showthread.php?t=1367499]("http://ubuntuforums.org/showthread.php?t=1367499") solved the problem for me:
> I seem to have found a workaround... I turned of the splash screen (edited /etc/default/grub and changed GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet", and ran update-grub, both with sudo), and now after that my laptop didn't beep. So far I tested it only once, but the laptop used to beep every time, and now it didn't.
I don't have a splash screen anymore, but if those beeps go away I'm more than happy with that solution.

---

### Post by RuncaProfundus on 2010-04-25
I already have the pcspkr blacklisted and the "options snd-hda-intel power_save=10" isn't even listed in my alsa-base.conf. But the above solution worked after reboot.

---

### Post by jonbonjovi on 2010-05-05
I have just upgraded to Lucid 64bit and the option "power_save" doesn't appear any more, so I can't change it in "4".

Anyone knows how to avoid the cracking noise on reboot?

P.s.: hp dv5

---

### Post by pakkatechie on 2011-05-11
could someone help me on this irritating issue? i face it in dell inspiron 1564 with lucid 32 bit. still no solution after so many days ? i am interested to stay with latest LTS

---

### Post by marky1254 on 2012-08-15
I do not think that this is a software issue. Regardless of the OS installed (I have installed Win7, Ubuntu/Linux, and OSX; not all at the same time) the speakers have made a pop noise. The problem started after the computer was several years old and was still using the factory installed OS (win7) with the original drivers.

I would doubt that there is anything to worry about as the speakers play just fine during uptime.

---

