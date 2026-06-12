---
title: "Problem installing on Acer Travelmate 3002WTMI Laptop"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by Lovi on 2005-06-21
Hi I've just purchased a new laptop from Acer, the modell is an Travelmate 3002. Today I tried installing Ubuntu 5.04 on it without succes, in fact you could probably call it a total failure.

The CD loads fine and I'm allowed to select various boot settings and such, but when I initiate the boot process it freeazes at "Loading Kernel".  I've also tried with Knoppix 3.6 with the exact same result (and some extra problems resulting from the laptop screen/gpu).

My personal theory is that the laptops external CD drive is the problem since it's a firewire device. But I thought I should seek the advice of people with a lot more experience with linux than myself before proceding. Further hardware specs for the computer are:

Intel M740 1,73Ghz CPU
512mb DDR2 SDRAM
Intel GMA 900 Greaphics card

At this point I'm only interested in getting the OS to load correctly in livecd mode and will leave WLAN support and such until a later stage.

---

### Post by PhilippWollermann on 2005-06-21
This seems like an issue with APIC interrupt routing. Please append the options "noapic nolapic" (without quotation marks) when the boot-screen from the CD appears. So you would probably enter:

linux noapic nolapic

and press ENTER. This should get you further. :)

Philipp

---

### Post by mcleodz on 2005-06-22
i had the same problem to my acer extensa 4100
and i do:

linux acpi=off
the problem comes from acpi
:(
and im watching to resolve it but its difficult
so my laptop is running without acpi :(:(

if someone know a tip to help me
ty
:)

---

### Post by Lovi on 2005-06-22
Thank you, that did it. Of course this just means the installation fails when it tries to mount the external firewire CD drive. SIgh guess I'll have to go for a network install afterall.

---

### Post by Ogaitnas on 2005-07-04
Hi,

I have the same Acer 3002 and it works quite well. I have everything "in order" except the sound.

The CD/DVD works. No real problems with firewire. If sometimes it seems to hang, do not mind: just open and close it and try to continue as the light is turned on. Perhaps two times, but finally it's o.k. (This is just for installing).

Be aware that for using that very nice resolution, 1280x800, you will need the "855resolution" script. Once installed, everything is fine.

Do not care about wireless. It is o.k. Just forget the first messages of the kernel about some horrible mistakes with "pnpbios", and DO NOT DEACTIVATE IT. (Don't include "pnpbios=off" as suggested). The use of wireless is a little bit tricky at the beginning as the "acompanying" light doesn't work.

Now, if someone can help me with the sound I will be really thankful.

Cheers,

---

### Post by didds on 2005-07-04
[http://www.frankandjacq.com/ubuntuguide/5.04/](http://www.frankandjacq.com/ubuntuguide/5.04/)


Troubleshooting > How to configure sound to work properly in GNOME?

I have used this on Acer travelmate and Compaq Presarios

It works

kfg

---

### Post by Ogaitnas on 2005-07-04
Thanks a lot for your hint. Unfortunately, it doesn't seem to work on the 3002 as I did exactly what is said but everything remain as before.
Anyway, something is not working well as no modules for sound are inserted, and, really, I don't know exactly what chip it uses for sound. I try with snd-intel8x0 but perhaps it is another... :-(

Once more, thank you very much

---

### Post by Lovi on 2005-07-06
Thank you Ogaitnas, but unfourtunately it does not work for me. It could be that I'm trying to run the livecd and not install per say. The cd simply refuses to mount, is there som special driver or kernel image I should use to make it work?

---

### Post by Ogaitnas on 2005-07-06
Hi Lovi,
I'm afraid that your problem should be the "Live CD" affair as all the rest is the same for you and for me: same laptop, same Ubuntu, same "firewire-DVD"...
When Ubuntu starts with the install-CD I simply write:  linux acpi=off    and press enter.
I haven't done any other "magic" or "special" thing. And the installation is straight forward.
Anyway, you will have Ubuntu running shortly and our laptop is really cool...!! :-)
Cheers

---

### Post by dangerjunkie2002 on 2005-07-07
Hi,

I'm new to Hoary Hedgehog after my friends at the local club suggested switching might solve some of the issues I was having with Fedora Core 3. It's done far better with my hardware and I really like it so far.

I have an Acer Travelmate 4100WLMi (1.5G Pentium-M, 512MB, 80GB, DVD+-RW, Intel 915GM graphics, 1280x800 TFT)  The Live CD failed at boot with the same symptoms above. "live noapic" (Live CD) or "linux noapic" (Install CD) makes it work. A number of people gave me dire warnings about using "noacpi" or "acpi=off" unless it is absolutely necessary as they said the motherboard fan might become non-functional with nasty consequences if ACPI is disabled.

> Be aware that for using that very nice resolution, 1280x800, you will need the "855resolution" script. Once installed, everything is fine.

This is the problem I have. The xorg.conf file only shows what seem to be correct modelines for 1280x800

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

There is a discrepancy between these and the output of **ddcprobe** 

> 
vbe: VESA 3.0 detected.
oem: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)915GM/910ML/915MS Graphics Controller Hardware Version 0.0
memory: 12288kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 1 3
id: 00dd
eisa: HTC00dd
serial: 1314e0f3
manufacture: 11 2005
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
ctiming: 1280x1280@60
dtiming: 1280x800@59
monitorid:      Hitachi
monitorid: TX39D85VC1FA


The only resolution offered to me by the Gnome "Screen Resolution Preferences" tool is 1024x768 at 60Hz. This leaves me with several apps (Skype being one) which have dialogues I can't complete because bits of them are hanging off the screen or hidden behind Gnome toolbars.

855resolution seems perfect for my needs except that it only lists compatability with the 800 series Intel cards and not the 915GM I have. The 915GM uses the i810 driver which is the same as the 800 cards. Is 855resolution suitable for my card or is there something else I should try?

Thanks,
Paul.

---

### Post by Ogaitnas on 2005-07-07
The last version of 855resolution includes support for 915. It works very well. Just install it. You will be happy  :-)

---

### Post by Ogaitnas on 2005-07-12
Hi guys,
I'm afraid that there are not very good news, at least for those who love Ubuntu and own a Travelmate 3002. 
I haven't been able to make it work 100% right with the wonder of Ubuntu. No one seems to have solved the problems related with ACPI and/or sound. For X's there is no problem.
Now I have everything (almost) working perfect, BUT... I have been obliged to install SUSE-9.3, that can be downloaded for free.
Anyway, I hope this will not be very long to come back to dear Ubuntu. The only difference is that a german guy has explained very detailed, what to do and how to patch the kernel and reinstall last CVS version of ALSA. And it works!! Everything with the sole exception of the light in the wi-fi button and the "suspend-resume" capability. 
I can work a lot longer than before and the 3002 is not very hot as the processor change his speed dynamically.
If you want to try, this is the page that I have found:
[http://www.stud.uni-karlsruhe.de/~usjp/cms/modules.php?op=modload&name=News&file=article&sid=1&mode=thread&order=0&thold=0](http://www.stud.uni-karlsruhe.de/~usjp/cms/modules.php?op=modload&name=News&file=article&sid=1&mode=thread&order=0&thold=0)

Cheers

---

### Post by lizhao on 2005-08-03
Yea, when i see the solution for suse, really regret ubuntu has not done it yet.
But I won't shift to suse right now, just wait more patiently. 
;-)


[QUOTE=Ogaitnas]Hi guys,
I'm afraid that there are not very good news, at least for those who love Ubuntu and own a Travelmate 3002. 
I haven't been able to make it work 100% right with the wonder of Ubuntu. No one seems to have solved the problems related with ACPI and/or sound. For X's there is no problem.
Now I have everything (almost) working perfect, BUT... I have been obliged to install SUSE-9.3, that can be downloaded for free.
Anyway, I hope this will not be very long to come back to dear Ubuntu. The only difference is that a german guy has explained very detailed, what to do and how to patch the kernel and reinstall last CVS version of ALSA. And it works!! Everything with the sole exception of the light in the wi-fi button and the "suspend-resume" capability. 
I can work a lot longer than before and the 3002 is not very hot as the processor change his speed dynamically.
If you want to try, this is the page that I have found:
[http://www.stud.uni-karlsruhe.de/~usjp/cms/modules.php?op=modload&name=News&file=article&sid=1&mode=thread&order=0&thold=0](http://www.stud.uni-karlsruhe.de/~usjp/cms/modules.php?op=modload&name=News&file=article&sid=1&mode=thread&order=0&thold=0)

Cheers[/QUOTE]

---

### Post by lizhao on 2005-08-03
there is another german post for debian:

[http://chaosfactory.org/linux/](http://chaosfactory.org/linux/)

pity that i donnot know german

---

### Post by Muffe on 2005-08-21
I have just recieved my new Acer Travelmate 3000 and am about to install Ubuntu on it. Have any of you managed to get the sound working?

I will install Ubuntu now and report how it went.

---

### Post by Muffe on 2005-08-21
The installation is finished now, but X won't start. It's just a black screen. Does anyone have any Ideas about how to fix this? I have tried to find an interactive autoconfig for X.org, but I can only find a funn-automatical.

Thanks.

---

### Post by lizhao on 2005-08-22
[QUOTE=Muffe]The installation is finished now, but X won't start. It's just a black screen. Does anyone have any Ideas about how to fix this? I have tried to find an interactive autoconfig for X.org, but I can only find a funn-automatical.

Thanks.[/QUOTE]
no problem when i install 5.04, what version did u install?
[http://spide.blogspot.com/2005/07/softwarerec-install-ubuntu-on-acer.html](http://spide.blogspot.com/2005/07/softwarerec-install-ubuntu-on-acer.html)

---

### Post by lizhao on 2005-08-24
[http://spide.blogspot.com/2005/08/softwarerec-install-ubuntu-on-acer.html](http://spide.blogspot.com/2005/08/softwarerec-install-ubuntu-on-acer.html) 
it is my experience on tm3002, and most components work now

---

### Post by namru on 2005-08-29
Hi,

I've got Acer Travelmate 3004WTMi laptop and was just wondering if Breezy Badger would have better support for laptop hardware? 
I'll propably wait for it to be released since it should be quite soon. 

I've tried to boot 4 different live distros and various parameters without success. 
SLAX live has an option that creates a ram-disk and copies everything there
 (about 200Mb) 
thought that this might be a good solution but at least I didn't manage to get It to work.
If you want to give it a shot:
[http://slax.linux-live.org/](http://slax.linux-live.org/) 

/namru

---

### Post by Muffe on 2005-08-29
If you boot from a live-CD (or any other CD), just remember to use the acpi=off kernel option...

When is Breezy Badger going to br released?

Edit: I've tried Knopix (3.6 - not the newest), and it works.

---

### Post by namru on 2005-08-29
I think the expected release date of Breezy is october 13.

Did you actually get knoppix-live to work on a TravelMate 3002 or 3004?
I've tried suse, knoppix, ubuntu, and 2 other lives distros with the similiar results.

All of them boot like they should at first but when the kernel starts to load, it can't find the cd/dvd anymore as the cd/dvd drive is external and connected via firewire.

---

### Post by Muffe on 2005-08-29
Yes, I did get Knoppix 3.6 to work. The boot paramenters I used was: "knoppix acpi=off"

It is an Acer Travelmate 3002. Tre reason why I don't use Knoppix 4.0 is that 3.6 works, and the 4.0 DVD image is HUGE. I plan t download it tonight or tomorrow night.

Remember to configure BIOS to boot from CDROM.

---

### Post by namru on 2005-08-30
I downloaded knoppix 3.8.2 and booted with acpi=off and it worked!
Nice to see linux on my laptop :)
It's kind of strange that suse and ubuntu won't boot (live-cds)
knoppix-std 0.1 with acpi=off gave me this error message:

"Can't find knoppix filesystem, sorry.
 Dropping you to a (very limited) shell
 Press reset button to quit

Additional builtit commands available


I'll download the torrent of knoppix 4.0 dvd and see how it goes.
cat               mount           unmount
insmod         rmmod          lsmod"

I'm downloading the dvd-torrent of knoppix 4.0 and see how it goes.

---

### Post by namru on 2005-08-30
The dvd worked nicely, though I haven't got wireless connection to work yet. 
I guess it has to do with encryption.
The dvd is really packed with loads of applications!

---

### Post by lozzd on 2005-10-25
[QUOTE=namru]The dvd worked nicely, though I haven't got wireless connection to work yet. 
I guess it has to do with encryption.
The dvd is really packed with loads of applications![/QUOTE]

Has anyone tried Breezy badger on one of these laptops? Really eager to get ubuntu running native with full hardware support without all this faffig around with files etc rather than in VMWare like i'm running it now ;)

---

### Post by Muffe on 2005-10-26
I have tried Breezy, and everything expect sound and ACPI works out of the box. If you want WPA, you'll have to install the wpa_supplicant package (it s in the repositories). And you will also have to install the 855resolution /that's also in the repositories) package to get the screen resolution right.

---

### Post by lozzd on 2005-10-26
[QUOTE=Muffe]I have tried Breezy, and everything expect sound and ACPI works out of the box. If you want WPA, you'll have to install the wpa_supplicant package (it s in the repositories). And you will also have to install the 855resolution /that's also in the repositories) package to get the screen resolution right.[/QUOTE]

Damn, I was hoping that ACPI had been fixed. Thanks for letting me know though.

---

### Post by Muffe on 2005-10-26
The ACPI issue is probably something with the BIOS, maybe a byggy DSTD table or something because the problem occurs on all linux distros I've tried. I have reported the problem to Asus, and I've got a reply tellig me that my report has been forwarded to the people working on BIOS updates, so maybe the problem will be fixed in a few months? Let's hope so.

---

### Post by namru on 2005-10-26
I've installed breezy and while the installation was ok, I have not yet figured out how to set up WiFi with WPA, it kind of works randomly, sometimes it does work but mostly not. this without changing the configuation. (I'm using wpa_supplicant) Otherwise WiFi works fine. 

Most annoying thing is the resolution issue. I'd like to have (1280x800) because it is a wide-screen. after trying lots of different configs, I managed to screw it up so X wouldnt start. I just copied back my old xorg.conf and Voilá! there was a crisp 1280x800 resolution. BUT after a reboot, it was gone! Again after numerous reboots and config changes, same thing. Copied back xorg.conf and it worked fine. I don't get it.
I'm using the "915resolution" driver

Sound isn't working either.
I've tried a lot of methods posted in the forums with no luck.
The resolution and sound would be really nice to fix.

Acer TravelMate 3004WTMi
Inter GMA 900 (i915) grapics / Sigmatel audio?

Does any of you have similiar hardware that works with Ubuntu?

---

### Post by Muffe on 2005-10-26
915resolution? What's that? You should use the 855 resolution, even if you have a i915 chip. And that's not a driver, it is an application that loads at boot. It does need configuration to work. The driver to use is 'i810'.

Search the forum for howtos on the screen and WLAN. It is a LOT out there.

---

### Post by namru on 2005-10-26
Thanks for the advice! will try the 855resolution.

---

### Post by namru on 2005-10-26
Just wanted to say that 855resolution worked perfectly!

---

### Post by lozzd on 2005-10-28
[QUOTE=Muffe]The ACPI issue is probably something with the BIOS, maybe a byggy DSTD table or something because the problem occurs on all linux distros I've tried. I have reported the problem to Asus, and I've got a reply tellig me that my report has been forwarded to the people working on BIOS updates, so maybe the problem will be fixed in a few months? Let's hope so.[/QUOTE]

I guess you mean Acer, not Asus? 
With a bit of luck they will produce an update then.. Thanks! 
Keep us posted.


Laurie

---

### Post by Muffe on 2005-10-28
Yes, Acer of course. I always mix up Acer and Asus, I don't know why...

---

### Post by Chih-Jen Lin on 2005-11-11
I have 5.10 installed on my acer travelmate 3002wtci, but has a problem of using F5 key to output
the display to external projector. 
In fact I had the same problem on MS windows..

Anyone had a similar problem?? Thanks.

---

### Post by josema on 2005-12-17
Just to keep the thread alive. I've got a 3004WTMi very recently. The only distro I could make work properly (sound and ACPI too, but not suspend/hibernate) was FC4 following the [instructions]("http://www.baycom.org/~tom/acertm3004wtmi/") linked from tuxmolbil.org. It works but it's slow...
Oh, and the guy updated the patched kernel to a 2.14 one (I'm using his previous 2.13) and the new one doesn't work for me :( 

As several mentioned, the display thing is easy to solve, Wireless almost work out of the box, but main problems are sound and ACPI.

I even switched to Dapper (Flight 2) and display seems to work a bit better (probably a general thing because of Gnome 2.13) and the 915resolution is better integrated (you just need to edit a file to patch a mode and you're done). Sound and ACPI don't work either.

I also tried ALSA 1.0.11rc1 but no luck either.

Last thing I tried was to ask at IRC where you find a lot of helpful people, but answer I got (and that I unfortunately expected) is that hardware is too new :( 

So, I guessed the "hardware too new" thing but expected Dapper to solve it. I'm crossing fingers and look forward to it (they still have 'til April) and I'll keep testing once in a while (probably will try FC5 previews too) and I'll post here again with updates. Please, do the same. Let's make Ubuntu work in this machine :mad:

---

### Post by sroets on 2006-01-14
[QUOTE=namru]Just wanted to say that 855resolution worked perfectly![/QUOTE]

How do you activate the 855resolution ???

---

### Post by sroets on 2006-01-14
[QUOTE=Ogaitnas]Hi,

I have the same Acer 3002 and it works quite well. I have everything "in order" except the sound.

The CD/DVD works. No real problems with firewire. If sometimes it seems to hang, do not mind: just open and close it and try to continue as the light is turned on. Perhaps two times, but finally it's o.k. (This is just for installing).

Be aware that for using that very nice resolution, 1280x800, you will need the "855resolution" script. Once installed, everything is fine.

Do not care about wireless. It is o.k. Just forget the first messages of the kernel about some horrible mistakes with "pnpbios", and DO NOT DEACTIVATE IT. (Don't include "pnpbios=off" as suggested). The use of wireless is a little bit tricky at the beginning as the "acompanying" light doesn't work.

Now, if someone can help me with the sound I will be really thankful.

Cheers,[/QUOTE]

Be aware that for using that very nice resolution, 1280x800, you will need the "855resolution" script. Once installed, everything is fine.
>> how and where do you run this script?

---

### Post by Skrot on 2006-01-19
I just got this laptop also. Running Breezy. Everything except ACPI, sound (think it has something to do with APIC) and the cardreader (though work is being done on  it) works. Any success stories on the ACPI? I looked at some of the patches and it's not really a lot of code.

On a side note, anyone got DRI working on this one?

---

### Post by Beef on 2006-02-12
Hi, I've just bought a 3002WTMI. Hoping to use it as a linux only machine to try a teach myself a bit more about the OS.

I installed breezy but cannot get the network to work, the card is detected but gnome says that the cable is disconnected.

Anyone else have the same problem? Any ideas?

---

### Post by rso on 2006-02-14
aloha

somebody managed to set up both acpi and sound.
unfortunately I cannot follow his steps because he leaves out quite a lot.
If somebody followed his instructions and succeeded. Could you write a step-by-step guide here please?

OK here it is:

[http://blog.lizhao.net/2005/08/softwarerec-install-ubuntu-on-acer.html]("http://blog.lizhao.net/2005/08/softwarerec-install-ubuntu-on-acer.html")

Hope it helps

---

### Post by mad_jack on 2006-02-14
Taken me a week since I took delivery of this machine, just finished tonight. I now have all the following working correctly: :D 

[LIST=1]
[*]Ethernet LAN
[*]Wireless LAN, using ipw2200 drivers with WPA/PSK
[*]Sound
[*]ACPI without errors and including working battery monitor
[*]Graphics at 1280x800
[*]Suspend to Ram and restore
[*]CPU thermal monitoring and fan control
[*]Acer Hotkeys supported and LED lights up correctly for bluetooth and WLAN
[*]Hibernate/restore works perfectly.
[/LIST]

I'm using Breezy with a custom kernel, and modified DSDT. This is my first Ubuntu installation, previously been Fedora or Centos, so this was a bit of a learning curve. I was unable to get WLAN working on Centos, though that distro was the least problematic on initial install. Fedora core 4 would install with a few kernel options to turn off acpi/apic but crashed on post install boot no matter what.

I'll write up the notes over the next few days and publish them. In the meantime anyone struggling please feel free to email me and I'll help if I can.

In the meantime here are some very scrappy notes and links to sites that helped me:

DSDT: [http://www.unmuted.de/?p=26#more-26](http://www.unmuted.de/?p=26#more-26) (it's in English)

Hotkeys worked by using the "acerhk" package once DSDT was fixed.

Kernel/Sound Module patches: [http://blog.lizhao.net/2005/08/softwarerec-install-ubuntu-on-acer.html](http://blog.lizhao.net/2005/08/softwarerec-install-ubuntu-on-acer.html)
But don't bother with the 916resolution, use 855resolution instead - apt-get install 855-resolution and just set up the config file in /etc/default
WLAN was a bit more tricky, and I need to retrace my steps to detail it
LAN worked out of the box.
My mods for DSDT, Lan config and kernel config file are [HERE]("http://www.osml.co.uk/acer_tm3002wtmi") - please check the Read_me
Kernel build: [http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)
Need to set a few parameters for ACPI DSDT stuff, the processor type to Pentium M and insert Li Zhao's replacement .c files.
Last thing: use the following kernel parameters once you have rebuilt and installed the kernel with Li Zhao's patches:

ec_burst=1 disable_timer_pin_1

You can then dispense with apic=off, noapic, nolapic etc.

For my next trick I have to do it all over again on another Acer, this time a Travelmate 382tmi. Anyone interested in that let me know.

---

### Post by rso on 2006-02-21
Hi 
I am really looking forward to your notes, I tried to start with what 
[http://www.unmuted.de/?p=26#more-26](http://www.unmuted.de/?p=26#more-26)
told me, but already the first step "cat /proc/acpi/dsdt > dsdt.dat"
gave me an error, because in my /proc/ there is no acpi directory ):

could you also tell which steps in the kernel compile you changed to fit the needs of the 3002wtmi?

Thanks a lot!

Hope to hear from you sonn :)

Richard

---

### Post by rso on 2006-02-21
Could you tell the ubuntu developers to include the changes you made mad_jack? 
I don't know if that's possible but if it was how can we make sure they know about our problems and solutions?

ciao, richard

---

### Post by mad_jack on 2006-02-21
[QUOTE=rso]Hi 
I am really looking forward to your notes, I tried to start with what 
[http://www.unmuted.de/?p=26#more-26](http://www.unmuted.de/?p=26#more-26)
told me, but already the first step "cat /proc/acpi/dsdt > dsdt.dat"
gave me an error, because in my /proc/ there is no acpi directory ):

could you also tell which steps in the kernel compile you changed to fit the needs of the 3002wtmi?

Thanks a lot!

Hope to hear from you sonn :)

Richard[/QUOTE]

Sorry to all waiting on this - always seems to be the way, just when I think I have a few minutes spare all hell breaks loose. Bottom line is I haven't even started writing this up yet, between demands from clients and friends with extreme family problems. 

Anyway, enough of that, you're in a bit of a catch 22 here, because without any ACPI support at all you aren't going to get /proc/acpi - so just use the kernel param acpi=off for install, not subsequent boot. It will be broken, but you can at least interrogate the DSDT that way.

BTW I did upgrade the BIOS to the latest available from ACER, to rev. 3B09

Use "sudo dmidecode" to check yours. If you use the same BIOS you should be able to download my patched DSDT from the link in my original post and use that.

Kernel? As said, I just used Li's patched .c files as total replacement for the existing ones, and built the kernel as per the howto on this forum with the .config file (also available for D/L at location in my original post).

Finally, I can also confirm Bluetooth works, and I sucessfully had it establish a connection with T-Mobile 3G on a Samsung ZM60 phone. Throughput wasn't that great, but the T-Mob coverage here sucks. But failure on the builtin memory card slot so far, can't get it to recognise either Sony Memory Stick or SecureDigital card, which are the only media I have from what it's supposed to read.

Cheers!

Mad Jack

---

### Post by mad_jack on 2006-02-21
[QUOTE=rso]Could you tell the ubuntu developers to include the changes you made mad_jack? 
I don't know if that's possible but if it was how can we make sure they know about our problems and solutions?

ciao, richard[/QUOTE]

Err, not really because they aren't my changes, just my application of mods which were freely available out there. The key ones were the replacement .c files from Li, so assuming he made them, it'd really be up to him to submit changes to kernel.org, from whence they should eventually filter down into the likes of Debian and Ubuntu. Actually I suspect these hacks are already in a future kernel release, a few versions along.

Cheers,

Mad Jack

---

### Post by rso on 2006-02-23
[QUOTE=mad_jack]
without any ACPI support at all you aren't going to get /proc/acpi - so just use the kernel param acpi=off for install, not subsequent boot. It will be broken, but you can at least interrogate the DSDT that way.
[/QUOTE]
Sorry to hear about your busy schedule, thanks for your reply!

How could I tell the kernel of an already installed version of ubuntu the param acpi=off, so it loads the /proc/acpi but doesn't try to start it?

Thanks
bye
Richard

---

### Post by mad_jack on 2006-02-23
[QUOTE=rso]Sorry to hear about your busy schedule, thanks for your reply!

How could I tell the kernel of an already installed version of ubuntu the param acpi=off, so it loads the /proc/acpi but doesn't try to start it?

Thanks
bye
Richard[/QUOTE]

Try adding the parameter "pci=noacpi" instead of using "acpi=off"
Others to try, in various combinations if it won't boot at all without "acpi=off" are:

[INDENT]irqpoll=off
pnpbios=off
pci=noapic
acpi=noirq[/INDENT]

Or try downloading the pmtools from [here]("http://packages.ubuntu.com/dapper/admin/acpidump") - be careful, there are 2 pnptools packages, one for perl modules which is irrelevant here. You can then use the acpidump program to extract the acpi stuff, and parse it with acpixtract. Then you can dissasemble it with iasl -d, and try to fix it yourself.

As it happens, I'm having to do all this again, as I installed 2Gb memory in the machine and it's changed the DSDT offsets and broken it all over. My previous tricks don't seem to be working very well either, but I'm getting there. By the time I finish I should know a lot more about it than I do now. Watch this space. It looks like I managed to build a static DSDT into the kernel I was using which doesn't work with the upgraded memory, rather than it picking up the override DSDT.aml file at boot time,  so it's kernel rebuild time again.

Cheers,

mad_jack

---

### Post by rso on 2006-03-09
Hi
great the pci=noacpi option did the trick, so now I started to work with this howto: [http://www.unmuted.de/?p=26#more-26](http://www.unmuted.de/?p=26#more-26)

I installed bison and the intel iasl tools, I managed to get my own dsdt.dsl, but while trying to patch it with the patch this page provides, I got the following errors:

patch dsdt.dsl < travelmate3002-dsdt.patch
patching file dsdt.dsl
Hunk #1 FAILED at 2.
Hunk #2 FAILED at 431.
Hunk #3 FAILED at 569.
Hunk #4 FAILED at 964.
Hunk #5 FAILED at 980.
Hunk #6 FAILED at 2210.
Hunk #7 FAILED at 5733.
7 out of 7 hunks FAILED -- saving rejects to file dsdt.dsl.rej

The page tells me to fix the dsdt.dsl myself... but I have no clue how to do that, should I take somebody else's dsdt.dsl and try it or should I try to fix mine?

Thanx !

Bye, Richard

---

### Post by Muffe on 2006-03-10
I also have an Acer Travlelmate 3000, and have just installed Dapper Drake. My experiences is the following:

Frequency scaling: Works out of the box
Battery monitor: Works out of the box
Soundcard: Works **without** the 'pci=noacpi' boot parameter, but without that parameter, GDM won't log you in, so you have to use it... I know the sound works because the login sound plays.

I have already made a [thread]("http://www.ubuntuforums.org/showthread.php?t=142070") about the soundcard issue in the Dapper development forums.

Everything else works as in Breezy.

My kernel boot parameters:
```
root=/dev/hda1 ro noapic nolapic vga=771 pci=noacpi quiet splash
```

---

### Post by rso on 2006-03-28
Hi
I just skipped this part, used the pci=noacpi option and then ACPI already worked :) Perhaps I did something befor that already fixed it.
I also recompiled the kernel with the 2 .c files from the link mad_jack gave me. It worked. But now whenever I use my custom Kernel, the wifi doesn't work. I did copy the USR_SRC_LINUX_.config files though...

Thanx again for your help mad_jack :)

Ciao
Richard

---

### Post by akadruid on 2006-04-10
Hi all,

I'm a bit of a newbie, but I was able to get ubuntu server to install from a 5.10 install disk on my ancient TravelMate 212TXV using the pci=noacpi parameter - thanks to this thread!

I'm now attempting to load Xubuntu Dapper Flight 6 using this parameter, and so far all is going well.

Cheers

akaDruid

---

### Post by mad_jack on 2006-05-17
For everyone's benefit, I think it worth mentioning that I now have this laptop working _**perfectly**_ under Dapper Flight 6 with the exception of the smart card reader (seems to be a legal restriction on encrypted firmware for the device from TI) and V92 modem (which I haven't tried as I never use one these days). The key is the 2.6.16 kernel which includes workarounds for the pitifully broken DSDT's.

I've actually done the exercise twice; once from scratch and once upgrading from Breezy. Dapper is very stable, though an annoyance is it seems to remove Openoffice on upgrade for some reason, and it has to be reinstalled after the upgrade.

One thing I would add; if you want the wireless LED to light up when the ipw2200 module loads edit the file:
/etc/modprobe.d/options and add:

options ipw2200 led=1

... to the end of the file

Cheers!

---

### Post by mad_jack on 2006-05-17
[QUOTE=mad_jack]For everyone's benefit, I think it worth mentioning that I now have this laptop working _**perfectly**_ under Dapper Flight 6 with the exception of the smart card reader (seems to be a legal restriction on encrypted firmware for the device from TI) and V92 modem (which I haven't tried as I never use one these days). The key is the 2.6.16 kernel which includes workarounds for the pitifully broken DSDT's.

I've actually done the exercise twice; once from scratch and once upgrading from Breezy. Dapper is very stable, though an annoyance is it seems to remove Openoffice on upgrade for some reason, and it has to be reinstalled after the upgrade.

One thing I would add; if you want the wireless LED to light up when the ipw2200 module loads edit the file:
/etc/modprobe.d/options and add:

options ipw2200 led=1

... to the end of the file

Cheers![/QUOTE]

I just discovered another thing - restoring from hibernation with the external firewire CD/DVD drive plugged in means the drive doesn't work until you reboot, negating the value of hibernation really.:???:  Need to do some more checking about which circumstances this happens under before filing a bug report.

---

### Post by strandlooper on 2006-05-17
Is there any news about the **smart card reader**.
It's a nice to have device but I would feel very comfortable to have it working.

---

### Post by mad_jack on 2006-05-17
[QUOTE=strandlooper]Is there any news about the **smart card reader**.
It's a nice to have device but I would feel very comfortable to have it working.[/QUOTE]

There's a group looking at reverse engineering it: [http://www.webcon.ca/~imorgan/tifm21/]("http://www.webcon.ca/~imorgan/tifm21/")

...and also [http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci]("http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci")
I suggest you subscribe to their mailing list then you'll get the news when they crack it the same time I do.

The device is actually detected, but as I mentioned earlier I believe there's some nasty encrypted firmware needed to make it visible to the system. Yuk.

Apparently TI released some binary drivers for a previous kernel (which won't load in mine :evil:) and seemingly under GPL, which should be a good enough reason for them to release the source. No-one seems to have had any joy pressing them so far though.

---

### Post by Muffe on 2006-05-20
[QUOTE=mad_jack]For everyone's benefit, I think it worth mentioning that I now have this laptop working _**perfectly**_ under Dapper Flight 6 with the exception of the smart card reader (seems to be a legal restriction on encrypted firmware for the device from TI) and V92 modem (which I haven't tried as I never use one these days). The key is the 2.6.16 kernel which includes workarounds for the pitifully broken DSDT's.

I've actually done the exercise twice; once from scratch and once upgrading from Breezy. Dapper is very stable, though an annoyance is it seems to remove Openoffice on upgrade for some reason, and it has to be reinstalled after the upgrade.

One thing I would add; if you want the wireless LED to light up when the ipw2200 module loads edit the file:
/etc/modprobe.d/options and add:

options ipw2200 led=1

... to the end of the file

Cheers![/QUOTE]

I also run Dapper, and downloaded the 2.6.16 kernel from kernel.org. I copied the config file from the last Ubuntu kernel, and ran 'make oldconfig' to update the config file. When I compile and boot the kernel, I still can't get the sound working.

Can you share your kernel-configuration file (.config) with us, and perhaps write a few scentences describing how you made (almost) everything work?

Thanks

---

### Post by mad_jack on 2006-05-21
[QUOTE=Muffe]I also run Dapper, and downloaded the 2.6.16 kernel from kernel.org. I copied the config file from the last Ubuntu kernel, and ran 'make oldconfig' to update the config file. When I compile and boot the kernel, I still can't get the sound working.

Can you share your kernel-configuration file (.config) with us, and perhaps write a few scentences describing how you made (almost) everything work?

Thanks[/QUOTE]

Sorry to disappoint you, but I didn't do anything special with Dapper flight 6, the kernel is the standard one so there's little point me providing the config file from it. I used the Easyubuntu scripts to set up all the multimedia extensions etc. and wheelspin's NetworkManager install script for the WLAN/WPA2 setup. That's all, no dark arts here ;^)=

I just thought it would be useful to let everyone know that Dapper on this machine is a lot less problematic than Breezy to set up.

---

### Post by High|ander on 2006-06-28
I'm running the dapper release and its working nice on my 3002 ACER.

Only thing is that the screen is 1024*768 now, but that shuln't be any problems :)

---

### Post by mad_jack on 2006-06-28
[QUOTE=High|ander]I'm running the dapper release and its working nice on my 3002 ACER.

Only thing is that the screen is 1024*768 now, but that shuln't be any problems :)[/QUOTE]

Just install 915resolution with:

sudo apt-get install 915resolution

Once installed run sudo 915resolution -l (in a terminal).

This gives you a list of available resolutions and their mode ID's

In the file /etc/default/915resolution edit the line for the resolution you
need 

In mine the line is.....

915resolution 49 1280 800

reboot

done.....

---

### Post by High|ander on 2006-06-28
Okay, thanks, working great here!

Even the bluetooth-lamp is working :)

---

### Post by High|ander on 2006-07-04
I have problem with the ipw2200, the network Manager doesn't seem to work.

The dmesg gives this:
[17181009.580000] ipw2200: Failed to send SCAN_ABORT: Command timed out.
[17181010.596000] ipw2200: Failed to send CARD_DISABLE: Command timed out.

---

### Post by fparri on 2006-07-19
> **mad_jack said:**
> One thing I would add; if you want the wireless LED to light up when the ipw2200 module loads edit the file:
/etc/modprobe.d/options and add:

options ipw2200 led=1

... to the end of the file

Cheers!

Thanks a lot, that was exactly what I was looking for :D

---

