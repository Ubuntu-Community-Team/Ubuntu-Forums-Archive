---
title: "VAIO FZ series Brightness control"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by k84 on 2008-02-20
Hi, I have a VAIO FZ290 with an NVIDIA 8400M GT. I've tried and searched for possible solutions for the brightness control issue with no luck. Just for curiosity I looked at the MacBook pro forums (MacBooks have a Santa Rosa chipset and NVIDIA 8600M GT) and they use "pommed" to handle the hotkeys of the macbooks and set  the LCD backlight, sound volume, keyboard backlight and other things. In the source code of pommed you can find a nv8600mgt_backlight.c file which handles the brightness of the LCD. I was wondering if that could work for the 8400M GT card making the right changes to the code. I would play around with it but im not much of a programmer and I don't know the risks that would envolve by testing it with a VAIO so can anyone take a look at it and see if that could solve the problem with the brightness with VAIO FZ series? THANKS!!

---

### Post by k84 on 2008-02-23
bump

---

### Post by k84 on 2008-02-28
Anyone? I found out  Vista uses a registry key for the driver to change the brightness of the panel and this registry was the same for the old linux nvidia driver 96.43.05 but not in the latest version. The registry is "EnableBrightnessControl=2". Checking at the registry keys in /proc/driver/nvidia/registry, only a few are enabled:

EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1


I don't know if enabling that registry would help to have access to the panel brightness using the sonypi driver or nvclock... I don't know what to do, can someone please help? my eyes are can't take it anymore!!

---

### Post by PurposeOfReason on 2008-02-28
Type in a terminal:
acpi_listen

and then press your fn with one of the f keys to see if you get an output. I had a FZ and I know it works in 8.04.

---

### Post by wozzinator on 2008-02-28
I've got an FZ290 with 7.10 and the gm965 integrated graphics, and for the life of me, the only operating system that can successfully use the brightness key is vista. I couldn't get it to work in xp since sony stopped releasing xp drivers and such for new models.

---

### Post by kb8pgc on 2008-02-28
My Fn key and the F5 and F6 keys adjust mine on my Vaio grt260g without any drivers or programs. I have the nvidia go5600 and the drivers that came with 7.10.

---

### Post by k84 on 2008-02-29
I tried to run acpi_listen but it shows nothing in the terminal...i'm not sure if the nvidia card handles the brightness or is directly from the vaio drivers. any other ideas?

---

### Post by David A Knight on 2008-03-01
acpi_listen shows the keypresses here for me, the brightness doesn't change though.

/proc/acpi/video/GFX0/DD04 shows brightness is supported, but even echoing values into that file doesn't change the brightness of the screen.  (FZ11M  8400M GT)

---

### Post by k84 on 2008-03-16
I tried acpi_listen in Gutsy without results but in Hardy i finally got some output. Brightness still doesnt change in Hardy. I was checking the DSDT table of my model and I found out it's totally different from the other vaio models, it actually follows with the specifications of the latest [[COLOR="Red"]ACPI[/COLOR]]("http://www.acpi.info/spec.htm"). It uses _BCM and _BCL methods to manage the brightness levels of the panel. in the BCL method you can see the list of the levels of brightness and the first two items mean the default level when the laptop is running in AC and Battery. Checking proc I get:

zero@core:/proc/acpi/video/GFX0/DD04$ cat brightness 
levels:  100 100 4 16 28 40 52 64 76 88 100
current: 0

so by default the brightness of my panel will be 100 the maximum in both modes. I'm trying to see how I can change this values and override the DSDT table with the fixed one though this won't allow to change the brightness with the keys or with any command on the fly but at least I'll be able to change the default level to something that my eyes can handle. If anyone have any tips that would be helpful. thanks!

---

### Post by starlily on 2008-03-31
Can you tell me how to change the default? I dont need to do it on the fly, but if I could make it stop blinding me Id really apppreciate that. 

Thanks, 
Lily

---

### Post by kiloxxx on 2008-04-27
Hi,
I've the same problem with a FZ11Z and GeForce 8400M GT. 
With Gutsy acpi_listen didn't give any result. Now, after an upgrade to Hardy, when I press Fn+F5 and Fn+F6 I've got respectively:

sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

and 

sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

but brightness control still doesn't work.

I've got the same levels in /proc/acpi/video/GFX0/DD04.

Unfortunately, I don't know how to help!

---

### Post by splash86 on 2008-04-30
hi, i got the same problem like kiloxxx.
fn key are reconized, and the backlight level too, but im not able to control it.
need help pls.

my model, vaio fz11z

---

### Post by hihihi on 2008-05-05
hello there,

_*the same here:*_ ***_sony vaio fz31m,_***
got webcam, vol keys to work **but** fn-keys / brightness / sleep **will not work** _(mute works!)_
..
what next?

---

### Post by hihihi on 2008-05-07
i discovered that there is /etc/acpi/events/sony-brightness-down (-up)
and that he values there did not correspond to acpi_listen output.
so i corrected that to SNC, and restarted but laptop still wont change brightness.
i installed smartdimmer, but that wants nvclock.
installed nvclock but that one just supports nvidia-cards up to 7xxx series.
so.
i got a lot of inspiration here:
[http://www.linux.it/~malattia/wiki/index.php/Sony-laptop](http://www.linux.it/~malattia/wiki/index.php/Sony-laptop)
i inserted vaio-configuration in xorg.conf but oooo wont get fn keys to work either... :(

---

### Post by bemused0 on 2008-05-07
I know this doesn't help much, but I've got all of the same results as the last 5 posters.

Running Hardy/Latest   on an FZ340E
Definitely going to check back to see if there's any progress later.

I wonder if there's a newer version of nvClock out there somewhere that supports 8xxx cards?

---

### Post by vins32 on 2008-05-08
Same problem here with a SONY VAIO FZ11S.
I have been struggling with the brightness issue for quite a long time. I am now using Window Vista as it seems the only OS to be able to manage the LCD brightness correctly.
I have tried all the different methods reported on the internet and a lot of different linux distros.
I also contacted the developer of nvclock and he said he is not able to find the correct registers to change the brightness....

V.

---

### Post by sojusnik on 2008-05-08
Same problem here using FZ21E. Hoping for a solution.

---

### Post by BasicWolf on 2008-05-09
Same problem on FZ21Z. I've installed the latest 173.08 (Beta) drivers. No changes at all.

---

### Post by m10 on 2008-05-09
same problem here.. 
```
mio@miosworld:~/Downloads/packs of 9-05-08$ sudo dmidecode -s system-manufacturer
Sony Corporation
mio@miosworld:~/Downloads/packs of 9-05-08$ sudo dmidecode -s system-product-name
VGN-FZ31S
mio@miosworld:~/Downloads/packs of 9-05-08$ sudo dmidecode -s system-version
C6008770
mio@miosworld:~/Downloads/packs of 9-05-08$ 
```

i can't even identify the magic numbers...

i'm working on hardy heron

ps my webcam, headphone+microphone jacks, hibernate+suspend don't work either

---

### Post by nielsslot on 2008-05-10
FZ38M with Hardy here. I'm unfortunately sticking with Vista until this is fixed in some way.

From what I can find on various forums, bug reports and websites, the problem here seems to be NVidia. People with a VAIO and an Intel graphics card are able to change their backlight level with the xbacklight utility. NVClock seems to do it for the older (below 8xxx) NVidia cards.

Maybe there is a way to REALLY get NVidia's attention on this since it's making laptops practically unusable under Linux.

---

### Post by v0vus on 2008-05-11
.. have found such walkaround with mine FZ31E/Hardy - having installed 'nvidia-settings' package (throught synaptic packege manager) have got 'NVIDIA X server settings' under System->Administration .. openning it gives me 'X server color correction' option where I can change both brightness, contrast and gamma .. but didn't check yet if new settings will preserve after reboot (0: ..

---

### Post by hihihi on 2008-05-11
> **v0vus said:**
> .. have found such walkaround with mine FZ31E/Hardy - having installed 'nvidia-settings' package (throught synaptic packege manager) have got 'NVIDIA X server settings' under System->Administration .. openning it gives me 'X server color correction' option where I can change both brightness, contrast and gamma .. but didn't check yet if new settings will preserve after reboot (0: ..

BUT:
this only changes color-brightness andd not the real, tl-lamp-brightness, and that is what u want....
so, this is NOT the solution unfortunatelly...

---

### Post by v0vus on 2008-05-11
> **hihihi said:**
> BUT:
this only changes color-brightness andd not the real, tl-lamp-brightness, and that is what u want....
so, this is NOT the solution unfortunatelly...
.. yeh, u right - it has no effect if switched to runlevel-3 (terminal mode)

---

### Post by hihihi on 2008-05-11
> **m10 said:**
> same problem here.. 


ps my webcam, headphone+microphone jacks, hibernate+suspend don't work either


**@ m10**
hey, that is easy, follow this:
get camera to work:
get driver here:
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)
	$ make
	$ checkinstall
add to /etc/modules:

r5u870
videodev
video-buf
v4l1-compat
v4l2-common


get headphones output:

Add this line to the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=vaio

get internal mic:

Add the following lines to /etc/modules
snd-hwdep
snd-hda-intel


get suspend function:add to /etc/X11/xorg.conf:

Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection



good luck,
BUT FOR BRIGHTNESS WE HAVE TO WAIT FOR NVIDIA!!
btw: i recommend to install the priority-drivers from nvidia,
version 173.08 beta. (u can get it from nvidia)
it did not fix the brightness-issue but it works way much better with compiz and emerald cause it is more compatible with new hardy-kernel and 8xxx card-series...

---

### Post by hihihi on 2008-05-13
aha!!
NVIDIA is to blame:
quote from tech.brief:
[http://www.nvidia.co.uk/object/IO_26269.html](http://www.nvidia.co.uk/object/IO_26269.html)

"SmartDimmer Technology
        SmartDimmer&#8212;a feature uniquely manageable through the GPU&#8212;is an intelligent
        way to manage notebook panel power consumption. For example, it dims the panel
        when appropriate. The GeForce 8M Series or NVIDIA Quadro NVS/FX notebook
        GPU driving the notebook panel is the only component fully aware of, and
        responsible for, driving the display on the LCD panel. This unique capability forms
        the basis for SmartDimmer technology, which lets users preset certain brightness-
        related preferences through a control panel in Windows Vista (Figure 1). It also lets
        the GPU manage the panel display within these limits. As a result, the GPU can
        reduce power consumption from one of the biggest power users in a notebook&#8212;
        the display panel. This reduction seamlessly delivers enhanced battery life for the
        user."
--> i guess they mean with user vista..
what i find strange is that i buy a laptop because of certain components like the graphic card, but that it wont work cross-platform... and there is no warning on the laptop itself. it means in other words: screwed (slightly)

---

### Post by Contsa on 2008-05-13
Hi all,

FZ11M owner here. I made the function keys work with brightness. I am lazy enough to rewrite it here so if you are interested check this thread [http://ubuntuforums.org/showthread.php?t=784671&highlight=fz11m](http://ubuntuforums.org/showthread.php?t=784671&highlight=fz11m)

Cheers
KT

---

### Post by vins32 on 2008-05-14
> **Contsa said:**
> Hi all,

FZ11M owner here. I made the function keys work with brightness. I am lazy enough to rewrite it here so if you are interested check this thread [http://ubuntuforums.org/showthread.php?t=784671&highlight=fz11m](http://ubuntuforums.org/showthread.php?t=784671&highlight=fz11m)

Cheers
KT

In this way you are changing the color brightness of the image, not the backlight of the LCD screen....

Vins

---

### Post by pihhan on 2008-05-21
Hey guys. I have vaio FZ and today i spent all day figuring out how to make it work. At least, i have success. At first before i forget, you should know my way would work only for intel X3100 equipped versions! If you have nvidia, you might try to look on acpi/events in archive and change SPIC to (SPIC|SNC) and see if it had worked. If it is, try smartdimmer. Check what does /var/log/acpid says, if it does execute right scripts.

I had working evdev device Sony Vaio Keys in X in gutsy, but after upgrade to hardy, it stopped to work. At first it seemed only device is missing in X11 config, as newer hardy version does not eat Option "Name" and complains for device in Xorg.0.log. But after correcting (by the way i have problem with different kernels. One is reporting it as /dev/input/event4, second /dev/input/event11. by-id or by-path does not report sony-laptop module, which is only one working (my model does not support sonypi it seems, it gives no action at all. suppose all newer FZ series do the same). So, it worked in gutsy. i can read events from input device using input-tools, but xev does not show anything (it used to show!).

So anyway, i found another way to make it work. I found acpi events are happening and found how to handle it. Only problem is to make it work then. So i made some scripts, and they does work! I think anyone who have intel card in his notebook should be able to control backlight using that. Does work for me.

So, where is archive. If you extract it and copy to their right places (extraction to / should do the work, but i suppose you should backup files i changed!). After acpid reload it should start to work. Oh, you need to install xbacklight utility if you havent done that already ```
sudo apt-get install xbacklight
```.

If that work, consider confirming it at bug report: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/232464](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/232464)

---

### Post by suomaf on 2008-05-21
going to throw in my 2cents, got smart dimmer to work... is there any way to link the brightness applet to smart dimmer? New to ubuntu.. but ubuntu is much more friendly and the forums are much faster than the maroon headware distribution.:)

---

### Post by hihihi on 2008-05-24
hi suomaf,

how did you get smartdimmer to work?
what graphic-card do u have?

---

### Post by suomaf on 2008-05-25
Hello Hihihi,

I got a sony vaio VGN-C25G I think i got a fresh install of Ubuntu 8.0.4, cannot remember if smart dimmer was together with the install or i apt get it.. but it works. If you need more info, just tell me what you need, like lspci or xorg.conf .. etc

---

### Post by pihhan on 2008-05-25
Just install smartdimmer package, then try smartdimmer command from terminal or man smartdimmer. If it does work, you need "only" make it something on fn keys action, which will propably work with acpi events. Try acpi_listen and write which actions you receive on fn keys press.

---

### Post by bemused0 on 2008-05-25
Tried smart dimmer for a while, no luck on mine.
(Nvidia 8400m chip)


I did make a cross post at the nvidia user2user forums.

I wish some of those users were mysterious nvidia employees that actually gave out answers, though.

[http://forums.nvidia.com/index.php?showtopic=66860&st=0&p=382924&#entry382924](http://forums.nvidia.com/index.php?showtopic=66860&st=0&p=382924&#entry382924)


[Edit]  Just got off the phone with Sony's support line (hahah...) :(.....
They say 'Nvidia produces the drivers', of course Nvidia says 'call sony'.
So I calmly explain the situation to mr sony. Say, 'how do I escalate a support request to nVidia?'
... Hold for 5 minutes....(during which I get some awesome old Dinah Washington music... mixed with static)
After the hold the friendly dude in india(with accent reduction training, wewt) gives me the following web address:
[http://news.sel.sony.com/en/corporate_information/contact_us](http://news.sel.sony.com/en/corporate_information/contact_us)
GG. sony. cop-out and send me to nVidia again, k thx(which of course media only contacts are fun, I'm totally sure they'll email me back :D   ... ).
[Edit]


[Edit2]
I've contacted Sony / Nvidia corp individually via their Customer Service VP's, using both my personal, consumer info -- and my corporate account-- So far,dissapointment on both ends.
[/Edit2]
Sorry if this is disgruntled spam, I'm just seriously trying to follow up all available avenues to find at least a statement of purpose for getting this issue fixed -- It's all over, on many models. (for almost 1.5 years now)

OEM ftl...

[Man I must've been drunk'n'bitchy that day... or something]

---

### Post by hihihi on 2008-05-26
smartdimmer does not work on sony vaio fz31m cause of nvidia 8400gt m.
this is due to the dependency of nvclock which for now does not support brightness on 8xxx series.

@suomaf:
hey, could you publish your "lspci |grep nV"?

@bemused0:

cool, i think is good that you post that experience here.

i found this in my laptop under /var/log/X.log:

(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video. NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "TV:1024x768+1280+0,DFP:1280x800+0+0"
(II) Loading extension NV-GLX


this explains something too.

on top of all, i can not get TV-out to work.
somebody with nvidia 8400gt m got that to work, or not?

---

### Post by benste on 2008-05-26
This thread is a duplicate of
[http://ubuntuforums.org/showthread.php?t=465491&page=48]("http://ubuntuforums.org/showthread.php?t=465491&page=48")

This problem is well known, - in work
there are problems with Fn keys - sony snc or so
and there is a problem with nvidia brightness

---

### Post by hihihi on 2008-06-01
one thing though:
i do not have the time to figure out why i am not able to get a member of club vaio. i never get the confirmation from sony nor a activation-link for the newly created account. this commercial kgb / gestapo sh*t really drives me nuts. after two precious hours of my life trying to get a member, i dicided to let it fall. did somebody use a fake name and still managed to become a member? :confused:

---

### Post by benste on 2008-06-02
If you are an european user the registration should be ok,
I'll check it with the engeniers and their databases if you contact me today at ~ 18:00 GMT+1 (now +9hours)
Pleaswe register- this is our only chance to get sony publish it

---

### Post by hihihi on 2008-06-02
you live in aachen and i live in amsterdam.
so the time u mentioned is 19h? for both. and how should i contact you?
i really want to cooperate in this initiative and add my request to sony.
BTW i found something very interesting about how nvidia and sony split their responsibility arround the graphic / hotkey driver in windows vista:
i went with vista onto the nvidia website to check for newest nvidia driver.
than the following text appears:

Sony requires that you download the driver for your GPU from their support site.

You can find more information at: [http://www.sony.com](http://www.sony.com).

The GeForce M series and GeForce Go series notebook GPUs use drivers that have been customized by the notebook manufacturers to support hot key functions, power management functions, lid close and suspend/resume behavior. NVIDIA has worked with some notebook manufacturers to provide notebook-specific driver updates, however, most notebook driver updates must come from the notebook manufacturer. Additionally, the desktop GeForce graphics drivers will not install on Geforce M series and Quadro M series notebook GPU's. 


AHA

---

### Post by benste on 2008-06-02
you can contact me now via IM - skype, ICQ MSN or Jabber = Google Talk
- the Mobility driver for nvidia topic is normal!! all nvidia mobility drivers are distributed by the OEM not by Nvidida
-> see profile for IM's

---

### Post by hihihi on 2008-06-03
i am really sorry, but my work is quite unpredictable right now, so i could not get in touch with u yesterday.
we could try it later again? if nothing comes in between.
meanwhile i will try myself to solve this issue, and btw, the thread menssioned above was removed from sony's site...
:(

---

### Post by benste on 2008-06-03
I wrote you a PM yesterday for furthr infos,
today you can contact me between 15:00 and 18:00 (sametime zone)
The Club Vaio thread has not been deleted"!!

[http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628]("http://club.vaio.sony.de/clubvaio/de/de/forum/viewthread?thread=54628")

---

### Post by benste on 2008-06-03
@ hihihi you wanted to contact me !!! you've got 1 hour left !!
you canuse ICQ 477995243
Jabber MSN and Mail: Benedict.Stein@gmail.com
if you're not able to post ttoday please write me an e-mail and you amy send me your serial number which is under you laptop, your full name and E- MAil + maybe mobile NR.

I'll keep all informations confidentel and submit them to my contact for the CV database

---

### Post by hihihi on 2008-06-03
he benste!

sorry!! again working overhours, damn :)
now, i spent some minutes today on the phone with the vaio-callcenter and its going to be fine, I will submit my request tomorrow and spread the link.
thanks for the idea,
lets keep in touch on this,
what more can we do?
questionsQuestiONsQuestionS

---

### Post by pihhan on 2008-06-18
Hello.

I wrote some guide to setup hotkeys. I would be grateful if you read it and report your success. Also report places that are strange and hard to understand, or any grammar mistakes i did. But no violence please, i am not native English speaker and I am sure I made a lot of typos there. Be kind on me.

And forgot to add link, so here it is: [http://www.pihhan.info/sony/sony-hotkeys.html](http://www.pihhan.info/sony/sony-hotkeys.html)

---

### Post by hihihi on 2008-06-21
hey, nice initiative, it is good to gather this kind of valuable information together. 
i have a fz31m. i do enable hotkeys by reading acpi_listen and correcting / creating event-scripts under /etc/acpi/events

does xbacklight work for you?
you have intel graphics, right?

keep up good work... :)

---

### Post by pihhan on 2008-06-23
Sure, i have intel graphics and xbacklight does work on it.

I thought about making some page with summary of supported ways to control backlight and what models do support what way and how we can autodetect it. However i am not sure if that is possible or if it should be done. Maybe it would need only work on HAL & gnome-power-manager to support all known methods, as it has some support for it already.

---

### Post by Vai on 2008-07-01
ehem...hey...im using Sony Vaio VGN-C25..I just thingking want to use ubuntu 8.0..before this im using os Windows XP and Vista..Im just worry about the drivers...so if im using Ubuntu 8.0 is my sony vaio drivers support fo Ubuntu 8.0?:guitar:

---

### Post by hihihi on 2008-07-08
> **Vai said:**
> ehem...hey...im using Sony Vaio VGN-C25..I just thingking want to use ubuntu 8.0..before this im using os Windows XP and Vista..Im just worry about the drivers...so if im using Ubuntu 8.0 is my sony vaio drivers support fo Ubuntu 8.0?:guitar:

hello there:

as far as i know, you should be fine installing ubuntu hardy on c25.
i am fine anyway, even without my backlight not working, but that is a vaio fz-series thing. if u happen to have an intel graphic card, than it will be a breeze to get all to work.
i would try to install it if i was u, i am a much more happy person behind the laptop since working with linux for some years now.
i still dualboot with vista, for video-editing mainly, but the rest, internet, mail, live-video-performance, MIDI, etc, i do it with ubuntu. its stable like a rock, secure and all seems possible, it consums less power than vista and thus keeps laptop quiet when doing normal stuff like writting a letter or working with sketchup.
so please, do it. install it, and with the time you will get there anyway, good luck

---

