---
title: "Sound card not working."
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by AndrewCaul on 2007-11-24
My friend recently installed Ubuntu, but he has run into a problem with his sound. And by that I mean there is no sound.
I believe his sound card is a Sound Blaster AWE64, although he actually called it "Soundblaster 16 AWE 64 ISA version".
I don't know whether it was detected or not. He doesn't know how to find out. Any help?

11/25/07: This issue is still unresolved.

---

### Post by Trevor Dola on 2007-11-24
hey I'm the friend, the windows name of it, and the name stampe don it is
Sound Blaster 16 AWE 64, its an ISA card, it does support plug and play.
I have no sound, I havent found any sort of drivers or anything in the snaptic packager thingy, and when I try to enter audio options they all fail saying no device.  The sound options thingy(where yous ent playback and events and stuff) says it failed to open a resource

I saw one thread about adding sb to a module or something, no idea what it all means, this is my third day using linux.  Id really like some help, preferably in the simplest easiest terms possible.
This is the topic that popped up
[http://ubuntuforums.org/showthread.php?t=24586](http://ubuntuforums.org/showthread.php?t=24586)

---

### Post by AndrewCaul on 2007-11-24
According to that topic, you need to add snd-sb16 to /etc/modules.
So here's what you do:
Open a terminal window and type "gksu gedit /etc/modules". Enter your password and the file will open. Type snd-sb16 at the end of the file and save.
Now restart and hopefully you'll have sound.

---

### Post by Trevor Dola on 2007-11-24
done, no effect, i restarted and everything

when I dbl click the speaker it will say an error saying "No Volume control GStreamer plugins and/or devices found"

---

### Post by Trevor Dola on 2007-11-25
I still haven't got it working, anyone help me please?  I was told the Ubuntu community was good for helping nubs like me.

---

### Post by Trevor Dola on 2007-11-28
trevor@Oldie:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
        Flags: bus master, medium devsel, latency 32

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 6300 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
        Flags: medium devsel, IRQ 9

00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo
        Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 32
        Memory at e0000000 (32-bit, prefetchable) [size=16M]
        I/O ports at 6400 [size=256]
        Memory at e1000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]

00:0b.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
        Subsystem: D-Link System Inc DFE-530TX rev A
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 6500 [size=256]
        Memory at e1001000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20020000 [disabled] [size=64K]
        Capabilities: <access denied>

---

### Post by AndrewCaul on 2007-11-29
Hmm... No sound card listed. I'm out of ideas.
Hopefully someone knowlegeable in this area will come in and help.

---

### Post by hortimech on 2007-11-29
try running 'alsaconf' it may just be that your card is not being detected because it is an ISA card.

---

### Post by Trevor Dola on 2007-11-29
Command not found
You meant type that in terminal right?

---

### Post by AndrewCaul on 2007-12-06
That's a damn good question. What package is alsaconf part of?

---

### Post by lvleph on 2007-12-06
I found [this](http://ubuntuforums.org/showthread.php?t=1805).

[quote=daveiler]I have an ISA AWE64 Value I'm used to this by now
[alsa page for us](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe)
short version
sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss
use volume control to turn up
try it out [/quote]

Hope that helps.

---

### Post by Trevor Dola on 2007-12-06
>  have an ISA AWE64 Value I'm used to this by now

[COLOR="Red"]alsa [/COLOR]page for us ([http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+64+Value.&chip=sb16%2C+emu8000&module=sbawe)) 

short version

[COLOR="red"]sudo -s
modprobe snd-sbawe;modprobe snd-pcm-oss;
modprobe snd-mixer-oss;modprobe snd-seq-oss[/COLOR]


use volume control to turn up :)
try it out :)
Loses me about where I highlighted it

Can you explain what to do please?

---

### Post by zeller on 2007-12-06
Open up a Terminal, press Alt+F2, and enter those commands one line at a time. Copy and paste might be easier. Just do one line at a time.

What they do? Hopefully get it working for you.

---

### Post by lvleph on 2007-12-06
Well I found another thing that says it is a BIOS problem.

> I got the soundcard working!!!!!!!! It WAS an IRQ problem in the BIOS. For some reason, Kernel 2.6.9 played well with the pnp settings in the BIOS, but 2.6.10 did not. I went in and manually set the IRQ 5 and IRQ 11 to the Legacy ISA setting and it seems to have worked. The soundcard detection program still says nothing is installed, but the volume control works, the CD player makes music, and I can play MP3 files, so I am happy. Much thanks to everyone who helped me out, especially rega451 for mentioning the IRQ problems.

For future reference, here is a list of my hardware in case anyone ever runs across this thread again with the same problem:

FIC FB11 Rev 1.3 Socket 370 Mainboard with Intel 440BX chipset
Intel Pentium III CPU 933 MHz with 256 L2 cache, and 133 MHz FSB
384 MB various brands PC133 SDRAM
nVidia branded (Don't ask how I pulled that off) GeForce256 Video card with 32 MB SDRAM
D-Link DFE-530TX 10/100 NIC
Creative Sound Blaster AWE64 ISA soundcard
Promise Ultra 100TX2 ATA controller
Sony CRX160E 12x8x32 CD-RW drive
Maxtor DiamondMax D540X-4K 20 GB 5400 RPM hard disk (Really NOISY)
Epson Stylus Color 850 Printer

> **Trevor Dola said:**
> Loses me about where I highlighted it

Can you explain what to do please?

The stuff you highlighted, except the very first thing, should be typed into  a terminal.

alsa is the program that controls your sound.

You will probably have to reboot once you are done.

---

### Post by AndrewCaul on 2007-12-06
> **Trevor Dola said:**
> Loses me about where I highlighted it

Can you explain what to do please?

sudo is the tool used for running stuff with root permission. 
modprobe does something involving modules. You probably won't ever use it unless someone tells you to.

---

### Post by Trevor Dola on 2007-12-06
ok, ill try this when I get home

---

### Post by lvleph on 2007-12-06
[Wow!](http://homepage.ruhr-uni-bochum.de/Marcus.Brinkmann/Soundblaster-AWE-HOWTO.html) Someone was really interested in getting this to work and helping out others.

EDIT: Try the first one I posted. This one should be a last resort.

---

### Post by AndrewCaul on 2007-12-06
> **Trevor Dola said:**
> ok, ill try this when I get home

Really? Then why does your Windows Live Messenger personal message read "Removing the Linux server, Linux sucks, never get Linux"?
That doesn't sound like someone who is willing to give Ubuntu a fair chance.
If you have issues with Ubuntu in the future, don't be afraid to ask. Ideally, you would have asked in the first place. I think the reason more people didn't try to help was that two different people had commented in this thread- me and you - which made it look like someone might already be trying to help.

---

### Post by Trevor Dola on 2007-12-06
"Windows Live Messenger personal message "
does someone have my passwords or something?  first here im making posts i never made, and now someone is logged onto Windows Live messenger as me

FYI, I do intend to try this cause I do like Linux for the most part.  There are many things about Linux that really aggrivate me, but others that I really like, liek the package manager is a great idea and I love it.  customizable shortcuts to folders and such that i can place right in my file browser.  the permissions are very nice aswell.  the web server workings are also very nice.  I don't like how one linux distro will work, and another doesn,t how its like gambeling with your computer, it might work, or it might not, you have no way of telling which will work, not from a newbies perspective.
Somewhere in the GUI system there is excess bagage, nto sure where but it shouldnt be as slow as it is, considering i've had XP on my old win 95 computer and it ran very smoothly, I don't understand the huge lag time my controls have on linux.  The time between clicking something, and the first indication of something happening is staggering.  to fire up the file browser with root permissions can take anywhere from 5 to 30 minutes to happen.  Hoverin g my mouse over a button can cause a good 3-10 seconds lag b4 the button shows a highlighted colour.  COnsidering Linux is suposed to work on all systems, i sort of feel like its a lie, yes it works, but its not useable.  Like a car without a transmission, sure it runs, it just can't go anywhere.

---

### Post by AndrewCaul on 2007-12-06
> **Trevor Dola said:**
> 
Somewhere in the GUI system there is excess bagage, nto sure where but it shouldnt be as slow as it is, considering i've had XP on my old win 95 computer and it ran very smoothly, I don't understand the huge lag time my controls have on linux.  The time between clicking something, and the first indication of something happening is staggering.  to fire up the file browser with root permissions can take anywhere from 5 to 30 minutes to happen.  Hoverin g my mouse over a button can cause a good 3-10 seconds lag b4 the button shows a highlighted colour.  COnsidering Linux is suposed to work on all systems, i sort of feel like its a lie, yes it works, but its not useable.  Like a car without a transmission, sure it runs, it just can't go anywhere.

That may be GNOME's fault. Try using a different desktop environment, such as Xfce.

---

### Post by Trevor Dola on 2007-12-06
> **AndrewCaul said:**
> That may be GNOME's fault. Try using a different desktop environment, such as Xfce.

wouldn't i then have to do this all over again?  and i really like that file broswer, the last one i had in suse was such garbage some folders u couldnt even open because it "had to many files"

---

### Post by AndrewCaul on 2007-12-06
> **Trevor Dola said:**
> wouldn't i then have to do this all over again?  and i really like that file broswer, the last one i had in suse was such garbage some folders u couldnt even open because it "had to many files"

Just install the xubuntu-desktop package and you're good to go. You don't have to re-install anything. You can choose which desktop environment to use when you log in. And you can continue to use Nautilus if you so choose.

---

### Post by lvleph on 2007-12-06
> **AndrewCaul said:**
> Just install the xubuntu-desktop package and you're good to go. You don't have to re-install anything. You can choose which desktop environment to use when you log in. And you can continue to use Nautilus if you so choose.
The OP doesn't know much about Linux or Ubuntu, so that is not enough info.

Try this.

System>>Administration>>Synaptics Package Manager
[img]http://www.simplehelp.net/images/ies4linux/ie04.png[/img]

Then search for xubuntu-desktop

or the easiest way 
alt+F2 and in the terminal that comes up type
```
sudo apt-get install xubuntu-desktop
```

When you login you will see this [img]http://www.howtogeek.com/wp-content/uploads/2006/11/WindowsLiveWriter/InstallKDEKubuntuonUbuntu_C102/sessionoptions.png[/img] in the bottom left corner. Click it. and then select xubuntu from the menu that comes up.

---

### Post by Trevor Dola on 2007-12-06
thanks Ill try that, is this xfce faster running?

---

### Post by AndrewCaul on 2007-12-06
> **lvleph said:**
> The OP doesn't know much about Linux or Ubuntu, so that is not enough info.
Actually, I know him. He already knows how to use Synaptic, so I left that step out.
But thanks for the help anyway. I did kind of leave out the information on how to switch desktop environments.

---

### Post by lvleph on 2007-12-06
> **AndrewCaul said:**
> Actually, I know him. He already knows how to use Synaptic, so I left that step out.
But thanks for the help anyway. I did kind of leave out the information on how to switch desktop environments.

Didn't pay attention to the poster. He said he didn't know even the basics, so...

---

### Post by Trevor Dola on 2007-12-06
its easy to not have enough detail, its difficult to have too much detail.

having not enough can cause problems, having too much can prevent them

---

### Post by Trevor Dola on 2007-12-06
the posted solution didnt work, and that other one scares me, unless u guys can like remote desktop to me and do it for me ???

---

### Post by AndrewCaul on 2007-12-07
> **Trevor Dola said:**
> the posted solution didnt work, and that other one scares me, unless u guys can like remote desktop to me and do it for me ???

Oh yes, that would be much less scary. :rolleyes:
So, uh, any idea anyone?

---

### Post by Trevor Dola on 2007-12-07
rly, truely, anyone at all?

---

### Post by Trevor Dola on 2007-12-07
Thanks for your time guys, I desperatly need my sound, I can't play around with this anymore.  So I am forced to go back to buggy Windows 95 (all hail the run time errors after opening any folder)

---

