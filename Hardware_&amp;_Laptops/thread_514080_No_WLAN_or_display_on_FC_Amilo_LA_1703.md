---
title: "No WLAN or display on FC Amilo LA 1703"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by Ueland on 2007-07-31
Hi, 

Problem 1:
Display adapter is not detected at all, so i only get the default generic driver.
The adapter on the laptop is "VIA UniChrome Pro K8N890"

Problem 2:
The WLAN does not work, it is not detected at all, even when it is enabled with the "hardware switch".

Any good tips/ideas to theese problems?

/Regards

---

### Post by krychek on 2007-09-07
I have the same problems on my La 1703 plus i don't have sound either. Do you?

Btw the vesa driver is giving me 1280*800 resolution and it's pretty smooth too.

Tell me if you were able to fix the wifi problem too!

---

### Post by dominiqueforum on 2007-09-08
Hello,

I have the same laptop and the same issues ( display, wifi and sound).
To solve the bad display, i used the  xorg.conf file of Mepis 7 beta ( livecd ).
I used ndiswrapper for the wifi ; the driver is sis167u.
I am testing the sound. :)

---

### Post by krychek on 2007-09-10
dominiqueforum: I guess that Mepis xorg.conf file only gives proper resolution, not 3D support. Do your brightness adjusting buttons work? They worked for me at 800*600 resolution but not at 1280*800.

Even if you can solve the sound problem this laptop has only 1 speaker :( I just realized it yesterday when i installed windows just to check if my sound hardware is working at all. Well it does but it's kind of a dissapointment that sound comes only from the left..
Here is the bug i filed about the sound problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137474]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137474")

Feel free to edit my wiki page about this laptop: [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLa1703]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLa1703")

---

### Post by tim1976 on 2007-09-10
> **dominiqueforum said:**
> 
 the driver is sis167u.


Hi,

I'm having problems finding this driver - tried Google but it brings up this thread lol. Would you mind posting a download link?

Tim

---

### Post by j0lliyo on 2007-09-10
alrighty, let me just say, the info on the wlan issue of this computer was hard to come by, so i figured i'd try working it out myself ;)
and guess what... i actually managed to get myself online :)

ok here's what i did
first, i went to [http://support.fujitsu-siemens.com](http://support.fujitsu-siemens.com)
went to download drivers, found the amilo la 1703, then went to wlan.
downloaded the drivers, then ndiswrapper -i sis163u.inf

ok there's where i encountered the first issue.
driver installed, but no hardware preset message.

so i played around a bit looking for the wlan device with various device id's, and found it at last:

sudo ndiswrapper -d 1106:4336 sis163u
sudo modprobe ndiswrapper

then i just system-network tools, properties for wlan0, entered ssid etc...

boom i'm here writing this

happy hunting! hope this helps

---

### Post by j0lliyo on 2007-09-10
btw, i fixed my gfx issue by just doing a simple sudo dpkg-reconfigure xserver-xorg
and selecting some higher resolutions... looks much better now.

i'll get back to the sound :) bedtime now

---

### Post by krychek on 2007-09-11
j0lliyo: You mean you've managed to fix the sound?! Please tell us when you wake up! :)

Do your brightness adjusting buttons work after you've set the resolution to 1280*800?

---

### Post by j0lliyo on 2007-09-11
no didn't fix the sound yett... gonna work on that a little later tonight if i get the time, but display and wlan works wonders. yes, my brightness buttons work fine. only think now is my sound issue really.

to get wlan to connect to a wpa secured network:

```
sudo apt-get install wpasupplicant
```

then go make a file called something like wpa.conf (doesn't really matter what you call it)

in this file, paste:

```

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }

```

where you fill inn myssid with the id of the access point and psk with the wpa key.

then open a console and enter:

```

sudo wpa_supplicant -Dwext -iwlan0 -c/pathtofile/wpa.conf -dd

```

assuming your wlan0 is active it should now connect to the wpa secured AP you put in that file
let it have some time to connect, as it can take a while before the connection goes active (1-2-3 mins or so in my case)

(remember to turn on the wlan card, i actually didn't get it to work the first time cause i forgot to turn it on ;))

hope this helps anyone, i'll put this into an Amilo La 1703 howto or something if i ever get the time

---

### Post by j0lliyo on 2007-09-11
just wondering, what did you all try to get sound to work? anyone tried manually compiling the alsadriver?

---

### Post by krychek on 2007-09-11
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=79434&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=79434&enterthread=y")

I tried pretty much everything i could with my basic linux knowledge. I tried to install the official via driver and the latest stable and non-stable alsa driver but nothing works. I also unmute everything with 'alsamixer'. Maybe the drivers are just bad.. but keep trying plz! :)

---

### Post by j0lliyo on 2007-09-13
ok i made a howto on the amilo la 1703, it will be updated as i figure out more.
please comment[http://amilola1703.uprize.no]("http://amilola1703.uprize.no")

---

### Post by osmoossi on 2007-09-15
Your guide is great!
But I didn't manage to get the wlan working with the instructions.
When I do sudo iwconfig i get:
lo        no wireless extensions.
eth0      no wireless extensions.

with sudo ndiswrapper -l i get:

sis163u : driver installed
        device (0BF8:100F) present

---

### Post by j0lliyo on 2007-09-16
are you sure you turned the card on by pressing FN+f2?
i got an error a few times because i forgot to turn it on (nubish of me i know =P)

---

### Post by j0lliyo on 2007-09-16
and did you sudo modprobe ndiswrapper?

---

### Post by Ueland on 2007-09-16
> **j0lliyo said:**
> ok i made a howto on the amilo la 1703, it will be updated as i figure out more.
please comment[http://amilola1703.uprize.no]("http://amilola1703.uprize.no")


Takk for den :)


Thanks for that! Il give Ubuntu a new go now on this machine, not to happy with Vista..

---

### Post by j0lliyo on 2007-09-16
yeah imo stupidity to ship this machine with vista, it just doesn't cut it....

got mine working for everything i need it to do now... (got my desktop to do stuff with sound etc, this is just for taking notes in class really) But ofc sound would be great! so if anyone got any new hints for how we gonna fix the sound, please post them

---

### Post by Ueland on 2007-09-16
> **j0lliyo said:**
> yeah imo stupidity to ship this machine with vista, it just doesn't cut it....

got mine working for everything i need it to do now... (got my desktop to do stuff with sound etc, this is just for taking notes in class really) But ofc sound would be great! so if anyone got any new hints for how we gonna fix the sound, please post them

Same here, just using it as a simple school machine, but sound is nice anyway.

Somebody else has tried it here:
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=79434&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=79434&enterthread=y)

I can adjust the sound and dis/enable it, but it simply just dosnt play anything, alltough i have not tried to mess around with sounddrivers yet.

---

### Post by j0lliyo on 2007-09-17
that's what we all get =) it detects the hardware, and we can adjust the volume, just no sound ;p

---

### Post by Ueland on 2007-09-18
WLAN was easy to get up and running, just the sound left now :guitar:

---

### Post by krychek on 2007-09-19
The latest 7.10 update made my brightness buttons work! :)

But there is another problem. When i try to launch some game that uses lower resolution than 1280*800 then the screen goes messed up. For example try supertux! If it works for you send me your xorg.conf please! Currently i cant change resolution to neither 640*480, 800*600 or 1024*768..

---

### Post by j0lliyo on 2007-09-19
i can change the resolution, but it just puts everything out of the screen(menu's taskbars etc) if i change it higher that is
if i change it lower than 1280*800 it screws up everything...

---

### Post by osmoosi on 2007-09-19
i got the wlan working, i just had to use  1106:3337 instead of the one you told. i found that with lspci.
About the audio problem. My laptop regognizes the audio card and i can adjust the volumes. I adjusted all the volumes to the max and tried some test sounds. And if I use headphones I can actually hear the sounds but they are VERY quiet. I googled around and found people with similar problems but with Intel audiocards and they got it to work by editing some file. I could not get mine to work that way. Maybe someone here can.

---

### Post by krychek on 2007-09-19
Someone was able to compile the openchrome driver:

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=76991&STARTPAGE=4]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=76991&STARTPAGE=4")

Look at nelo_bsb's comment that starts with "hello people". Still no 3D but maybe supertux will run properly ;)

He may have the answer for the sound issue as well:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

I cant try them cuz i dont have my laptop with me right now.. Im looking forward for your results!

---

### Post by Ueland on 2007-09-20
The HdaIntelSoundHowto did not work for me, gave it two tries now.. :/

---

### Post by j0lliyo on 2007-09-20
i hope i get a chance to try it out this weekend. if anyone got anything else to add to [http://amilola1703.uprize.no]("http://amilola1703.uprize.no") please inform me so i can make it better. and i hope we  can work out the sound issue soon. would be really nice to have some sound=)

---

### Post by dominiqueforum on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/137474](https://bugs.launchpad.net/ubuntu/+bug/137474) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				hello,

i have found that bug report :

---

### Post by Ueland on 2007-09-29
Too me it looks like they wont fix the bugs at all...
"This has been marked as wont fix"

---

### Post by Ueland on 2007-10-01
Hmm, the Wlan is _impossible_ to use.
I cannot connect to any wlan at all, it just tries to connect constantly and it newer stops... Any ideas? Im starting to get tired of not having anything that works correct..

---

### Post by j0lliyo on 2007-10-08
well i guess the hardware address to your wlan card is wrong, or you forgot to turn it on (fn+f2)

i'll try to get back to how to find it later no time right now

---

### Post by krychek on 2007-10-18
No good news.. 7.10 final wont install on my laptop. The x server wont start not even in safe mode.. It was fine in tribe 5 so im kinda dissapointed now. :(

---

### Post by svenerikjensen on 2007-10-25
This guide solved my wlan issues, using ndiswrapper with the windows xp driver for my wlan card. The point that actually worked was editing the Grub menu.lst and adding "pci=assign-busses" to my normal startup choice. [Ubuntu Wireless Troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

The graphics I set up using the driver provided by VIA (viaarena.com), and editing the xorg.conf to the correct driver and correct resolutions, and playing around with screen settings until I hit the correct one. For me that was with the via driver in mind, using lcd wide monitor with 1280x800@60hz resolution.

Regarding the sound issues, doesn't look like anybody got a fix, other than Via saying the ALSA driver won't work, and we have to use the one downloaded from [www.viaarena.com](www.viaarena.com) instead. Me being a linux user for one week means I need to figure out how to download, compile with correct kernel and what not before I can try that. :) But graphics and wlan works, and that's what's most important for my gf to use the web and msn. She's complaining about some damn funwall posts though. ;)

---

### Post by Ueland on 2007-11-04
My solution was simple: Sold the machine.. ;)

---

### Post by j0lliyo on 2007-11-05
haha "simplicity is the ulitimate sophistication"?

---

### Post by flugge on 2007-11-12
Hello everybody,
i followed the instruction by j0lliyo, but I have the same problem of  osmoossi on message #13.

From sudo ndiswrapper -l I get:
"
sis163u : driver installed
device (0BF8:100F) present
"

but from sudo iwconfig I get this:
"
lo no wireless extensions.
eth0 no wireless extensions.
ppp0 no wireless extensions.
ppp1 no wireless extensions.
"

(I remembered to turn on the wlan with Fn+F2.)
Where can I get the correct number if 1106:4336 doesn't feet my computer?
Thanks a lot!!!!

---

### Post by svenerikjensen on 2007-11-14
Add the line to your GRUB's menu.lst I mentioned in my post just above here, Ubuntu doesn't recognize your WLAN-card without that line, even though you have the correct drivers installed. :) After that, I got it working by using ndiswrapper with the xp driver provided from fujitsu-siemens.

---

### Post by flugge on 2007-11-15
thank you svenerikjensen,
but I still have the problem.
I added pci=assign-busses to my menu.lst.
Now my kernel line is:
"/boot/vmlinuz-2.6.20-15-generic root=UUID=7829050f-4a61-44a1-9663-1cd488885897 ro quiet splash pci=assign-busses"
But nothing changed.
In the same computer I have Windows Vista installed, and I can connect with WLAN from there.
So my WLAN device works. I also remembered to Fn+F2.
What can I do?

Thanks.

---

### Post by svenerikjensen on 2007-11-16
That's right, I had something like that as well with another computer I think. Think it was XP or Vista that "shut's down" the network card when vista's not loaded. I played around in the advanced driver settings thingy on Vista until I found a setting that said "Disable network card" at shut-down or something similar to that. It's awhile ago so I can't say for sure the exact place or name of the setting, but you'll know when you find it. It was actually Windows that still messed up my Ubuntu experience. This was not a wireless card though, but I guess it can do the same on any pci-device you're using. :)

---

### Post by Willem Souwer on 2007-12-14
> **j0lliyo said:**
> btw, i fixed my gfx issue by just doing a simple sudo dpkg-reconfigure xserver-xorg
and selecting some higher resolutions... looks much better now.

i'll get back to the sound :) bedtime now

Additional info : I tried this command on an Amilo 1703La (AMD Turion 64MK36 with VIA Chrome 9 HC IGP graphics card) with varying degrees of success (for causes (yet) unknown):
[LIST]
[*]-- Ubuntu 7.10 : none (could not install at all)
[*]-- Ubuntu 7.04 : limited (only 800x600, "dpkg-reconfigure" script froze in 3rd screen)
[*]-- Ubuntu 6.10 : limited (only 1024x768, "dpkg-reconfigure" script froze in 3rd screen)
[*]-- Ubuntu 6.06 : (64-bit AMD version) OK (started with 800x600, ran "dpkg-reconfigure" script selecting VESA driver and just clicking defaults, selected highest possible solution for my monitor i.c. 1280x800 @ 60Hz, and it worked).
[/LIST]

Btw -  manually editing the xorg.conf as proposed [here]("https://lists.ubuntu.com/archives/laptop-testing-team/2007-July/001160.html") made the display completely illegible in 7.04 (had to reinstall from CD).

---

### Post by krychek on 2007-12-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/153944](https://bugs.launchpad.net/ubuntu/+bug/153944) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				That's right, 7.10 doesn't install at all on this laptop. I've reported this bug long time ago, but none of the developers replied. There must be something wrong with x server. Hopefully the support for different screens will better in 8.04.

---

### Post by gagatz on 2007-12-22
about this "7.10 doesn't install at all"-thing:

yesterday i spent about 5 hours to upgrade from dapper (which runs fine on this laptop) to gutsy. so doing it this way its possible to having run gutsy (possibly its easier to upgrade from a higher version e.g. feisty, don't know.

about this wlan issue. 

i've got the same situation as 'flugge' above:

From sudo ndiswrapper -l I get:
"
sis163u : driver installed
device (0BF8:100F) present

but cannot see the device in the network settings. any ideas as to how to proceed from here?

this trick with pci=assign-busses didn't work for me as well...


[edit] ::: solved this issue, see    [http://ubuntuforums.org/showthread.php?t=659416](http://ubuntuforums.org/showthread.php?t=659416)

---

### Post by gagatz on 2008-01-05
I found a solution for the sound issue after all:
just download the appropriate package from opensound.com

(worked for gutsy and kernel 2.6.22-14-generic) with the tar 'linux 2.6 (amd64)'

jippieh!!

---

### Post by krychek on 2008-01-06
The OSS driver really does work, but i have problems with it. If i plug in a headphone it doesnt mute the speaker. But the bigger problem is that my logitech usb speakers doesnt work anymore after installing OSS..

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLa1703]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLa1703")

---

### Post by alexandro on 2008-01-10
[QUOTE=krychek;4082815]The OSS driver really does work, but i have problems with it. If i plug in a headphone it doesnt mute the speaker.
You can use oss mixer gui to mute speakers.

---

### Post by krychek on 2008-01-11
I tested the new Hardy alpha 3, I wrote my results in the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloLa1703") page.

At least Hardy starts but i wasnt able to go online.. please someone else try it out and feel free to edit the wiki!

Alexandro: Does your screen turn completely off in energy saving mode even if you dont close your lid? Mine doesnt but you changed my test result in the wiki. So whats the truth? :)

---

### Post by lurah on 2008-01-13
Hi folks.

> 
@laptop:~/Desktop/WLAN$ sudo ndiswrapper -i sis163u.inf

driver sis163u is already installed

@laptop:~/Desktop/WLAN$ sudo ndiswrapper -l

sis163u : invalid driver!


Same results no matter do we try vista or xp drivers from fujitsu-siemens website. FN+f2 is pressed.
We use 7.04.

Ideas, or do we need to sell laptop we bought just yesterday? :-/

---

### Post by gagatz on 2008-01-15
are you using a 386 or a x64 kernel?
i assume, that the x64 kernel does not work properly with this driver, since it is for 32 bit.
Type
dmesg |grep ndiswrapper
to see errormessages originating from ndiswrappper.
I didn't bring up the driver with the x64 kernel (gutsy) while it works fine with the 386 version.

---

### Post by lurah on 2008-01-15
Hi gagatz and thanks for reply.
I am using 32bit feisty with that PC. Currently i am in different location than it, but ill check what command you suggested, produces tomorrow.

---

### Post by lurah on 2008-01-16
Hi again gagatz.
Terminal command you suggested did not produce any return messages.

---

### Post by j0lliyo on 2008-02-05
we now got sound with alsa

see [http://amilola1703.uprize.no]("http://amilola1703.uprize.no") for a howto

---

### Post by gagatz on 2008-02-06
hi lurah, so what commands did you type into terminal which didn't succeed? Sorry for late reply...

---

### Post by sc3sc3 on 2008-02-20
hi 

my screen resolution at the moment is: 800x600

i followed the directions at
[http://amilola1703.uprize.no/](http://amilola1703.uprize.no/)
to get 1280x800
#################################
sudo dpkg-reconfigure xserver-xorg

This starts a script that configures your xserver.

Just follow the steps, select the vesa driver, and when you come to selecting resolution,
make sure you check off the 1280x800 setting.

Just follow all the steps till the end, just selecting the default ones.

Reboot
##################
but of no avail :-(

could someone post their xorg.conf please ?

thanks
kind regards
sc3*2

---

### Post by j0lliyo on 2008-02-25
yes i've been having different results with that approach aswell... after i reinstalled, i had to get kubuntu, cause if i try to run gnome, display doesn't work at all... i really have no idea why this is, if someone could enlighten us on why this is, and even better, how to resolve it, would be great... could someone who got gnome working on this comp post their xorg.conf so we could analyze it, that would be great...

Thank you in advance

---

### Post by krychek on 2008-02-26
I tested Hardy alpha 5 yesterday, it has the new alsa driver but i still dont have any sound.. I dont understand. On my current 7.10 installation a have sound from the left channel with the latest alsa. Only noise comes from the right channel of my headphone. Alsa still isnt perfect.. Should we report a bug or something?

---

### Post by j0lliyo on 2008-02-26
I have the same problem as krychek, but when i pull the jack a bit out of the plug, i get it on both channels, so there might be a bug there

---

### Post by fokukac on 2008-03-02
VIDEO PROBLEM SOLVED! I recently found out that openchrome driver does work. There is an install script on ubuntuforums [http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646) that will do the hard work for you.

---

### Post by krychek on 2008-03-02
> **fokukac said:**
> VIDEO PROBLEM SOLVED! I recently found out that openchrome driver does work. There is an install script on ubuntuforums [http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646) that will do the hard work for you.

Does 3D acceleration work also?

---

### Post by j0lliyo on 2008-03-03
did you get it to work? cause when i tried it now, the vesa driver works better, so i reverted back to that

---

### Post by fokukac on 2008-03-04
> **krychek said:**
> Does 3D acceleration work also?

After posting i realized that when i try to change the graphics mode to text (Ctrl+Alt+F1 or simply halting the laptop), the screen becomes unreadable and the system freezes. I did't try to wait, because i'm afraid of damaging the display. There is something written on the forum where the script is from that 3d accel is buggy so disabling it should fix things. I tought that without 3d accel, the chrome driver should be equal to the vesa(by my point-of-view) so I switched back to vesa.
Sound works with oss, however It leaves you with a preistoric taste in your mouth. WLAN works with ndiswraper. Convlusion: the laptop is usable for office use. However i recommend DELL for UBUNTU.

---

### Post by krychek on 2008-03-04
At least the sound is gonna work with hardy. It's muted by default so don't forget to turn the volume up!

---

### Post by fokukac on 2008-03-07
Fujitsu Siemens Amilo La 1703 wlan and sound solved on UBUNTU 7.10
==========================================================
For WLAN: [http://amilola1703.uprize.no/](http://amilola1703.uprize.no/)    PERFECT
For ALSA: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I used th version 1.0.16rc2 'cos it was reported to work by j0lliyo and i was impatient for trying a newer one.
                  NOTE: read the Troubleshooting section too
For Video: vesa woks fine, but no 3d accel and it's too slow for hi-res video playback too.

---

### Post by matogrosso on 2008-04-29
VIDEO PROBLEM SOLVED : ALTERNATIVE SOLUTION

For sc3sc3 and everyone else who still has problems reconfiguring the x-server.

I've tried that but it didn't work for me. But manually editing the xorg.conf file solved my problem.


Just back up your original xorg.conf as below

sudo cp /etc/X11/xorg.conf.backup<date> /etc/X11/xorg.conf

And then edit it to look the same as the one attached.

sudo gedit /etc/X11/xorg.conf

Basically changing the screen section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1280x800"
	EndSubSection
EndSection

****************************
*   HARDWARE               *
****************************

Laptop Fujitsu Siemens
AMILO LA 1703
AMD Athlon 64 X2 Dual-Core TK-55 1.80 GHz

Graphics Card:
VIA Chrome9 HC IGP Family WDDM
S3 Graphics Co. Ltd
Resolution: 1280 x 800 
Refreshrate: 60Hz 

****************************
*   SOFTWARE               *
****************************

Using Hardy Heron 8.04
AMD 64

---

### Post by alexandro on 2008-05-02
DISPLAY DRIVERS ALMOST FIXED :)

go to this thread:
[http://www.tkarena.com/forums/linux-arena/37154-desktop-effects-amilo-pro-3515-vn896-guide.html](http://www.tkarena.com/forums/linux-arena/37154-desktop-effects-amilo-pro-3515-vn896-guide.html)

do the same except this line in xorg.conf
Load  "glx"
change it to
Disable "glx"
because for me 3d is not working and notebook stop to respond.

Now grahics is fast, video is fast, processor is cool :)

---

### Post by krychek on 2008-05-04
So 3D still doesn't work? :(
I hope they'll develop the driver faster now that it's open source.

alexandro: thanks for the update. I didn't even know that the cooling can be turned off. I'll try it out tonight. :)

---

### Post by alexandro on 2008-05-04
3D works on other notebooks with via video, maybe it can work on 1703, but we need some options.
be careful with cooler control, tonight i turn it off and got 80 C :)

---

### Post by kimpanen on 2008-05-05
which driver did you use?

---

### Post by alexandro on 2008-05-05
ubuntu 8.04 + cn896+vt8237s from this site: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by kimpanen on 2008-05-06
thx

and was the cooling switch by default or did you guys switch it off?

---

### Post by krychek on 2008-05-06
> **alexandro said:**
> ubuntu 8.04 + cn896+vt8237s from this site: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

But we have vn896 and vt8237a. Are these compatible? Maybe would be better to wait more till we have driver that's written for exactly for our hardware.

---

### Post by alexandro on 2008-05-06
Of course we cat wait. but now i have got full screen video playback, its better than nothing.
Also, Krychek. My screen turns off when suspend without any troubles. I am not tested hibernate, because i do not have swap file and hibernate is not working without it.

---

### Post by krychek on 2008-05-07
I mean my screen doesn't turn off when the computer is idle. It just goes black but doesn't turn off. Suspend and hibernate works fine.

---

### Post by fokukac on 2008-05-07
Yes, with vesa it works quite fine. Our problem is that vesa is not a performant driver. We would like to use one like openchrome. Openchrome provides 3d acceleration too. Openchrome compiled from source has some issues that i reported at openchrome community.
Thank you for the good intention anyway.[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

> **matogrosso said:**
> VIDEO PROBLEM SOLVED : ALTERNATIVE SOLUTION

For sc3sc3 and everyone else who still has problems reconfiguring the x-server.

I've tried that but it didn't work for me. But manually editing the xorg.conf file solved my problem.


Just back up your original xorg.conf as below

sudo cp /etc/X11/xorg.conf.backup<date> /etc/X11/xorg.conf

And then edit it to look the same as the one attached.

sudo gedit /etc/X11/xorg.conf

Basically changing the screen section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1280x800"
	EndSubSection
EndSection

****************************
*   HARDWARE               *
****************************

Laptop Fujitsu Siemens
AMILO LA 1703
AMD Athlon 64 X2 Dual-Core TK-55 1.80 GHz

Graphics Card:
VIA Chrome9 HC IGP Family WDDM
S3 Graphics Co. Ltd
Resolution: 1280 x 800 
Refreshrate: 60Hz 

****************************
*   SOFTWARE               *
****************************

Using Hardy Heron 8.04
AMD 64

---

### Post by w43l on 2008-05-19
hi 
anyone having a problem with the modem
i got everything working (thnx to j0lliyo)
i just want to connect using the modem :)
anyone could help
thnx in advance

---

### Post by alpianon on 2008-07-09
> **alexandro said:**
> Of course we cat wait. but now i have got full screen video playback, its better than nothing.
Also, Krychek. My screen turns off when suspend without any troubles. I am not tested hibernate, because i do not have swap file and hibernate is not working without it.

have you managed to make compiz work on this notebook?
thanks
Alberto

---

### Post by alexandro on 2008-07-09
> **alpianon said:**
> have you managed to make compiz work on this notebook?
thanks
Alberto

No, we need 3d support for this. Via is evil here...

---

