---
title: "HP Laptops"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by J-Red on 2007-06-30
Hey, I just bought a HP Compaq 6710b without checking if it was fully compatable with Ubuntu... When trying to install feisty, I realized it wasn't. I kept getting xorg errors because the graphics card is incompatible and couldn't get it to work at all. I'm looking into returning the laptop and getting a new one, but I want to make sure it will work with Ubuntu first. i was looking into the HP Compaq 6715b ([http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-79819571-80292545.html](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-79819571-80292545.html)) which is pretty much an identical laptop, except it uses an AMD Chipset and a different graphics card. Can anyone tell me if that laptop is compatible with Ubuntu? Or can anyone help me to install feisty on my HP Compaq 6710b? I haven't had very much luck with google, so I decided to post here. (haven't had much luck in IRC either...)

---

### Post by Perfex on 2007-06-30
Hmm can you post all of your problems .. how far its getting on the install, etc.
Have you tryed using the alternate cd? 

I have a compaq v5000 quite a bit diffrent but linux ussualy is fine with most of HP's/Compaq

Edit: Found this post might interest you [http://ubuntuforums.org/showthread.php?t=452697&highlight=Intel+965GM](http://ubuntuforums.org/showthread.php?t=452697&highlight=Intel+965GM)

---

### Post by J-Red on 2007-06-30
Thanks for that link, I'm thinking of just returnign the laptop because of all the issues that I'm having it, plus in that llink the guy says the monitor is blurry, and that would get really annoying really fast. Dose anyone know if that link I posted (the HP Compaq 6715b) does will with Ubuntu? I'm mainly worried about the video card.

---

### Post by J-Red on 2007-06-30
I'm confused as to what I should be looking at video-wise on the HP Compaq 6715b It says that the chipset used inside it is AMD M690T, but it says that the video card is an ATI Radeon X1250. Are either/both of those compatible with feisty?

---

### Post by abrarey on 2007-07-04
Hi I have the same problem, let me tell you J-Red that I have the 6715b notebook and the video card is not working.
I install Ubuntu with the Alternate CD, but the video is not working I've spend all the weekend triyng to fixit but nothing yet.
If someone knows how to get ATI X1250 works on feisty will be great, please some help.
I´ve tried with ubuntu live CD, SimplyMepis 6.5 that comes with restricted drivers available and with mint 3.0
Right now I´m downloading uberyl to tried.
Thanks in advance.
Sorry my english is no so good.

---

### Post by HarshReality on 2007-07-04
As of late ATIs graphics seem to be lacking in linux in general the net is littered with posts on the subject. I myself have never tried or subscribed to an ATI chipset and alwyas went for NVidia. But as far as HP laptops go the most common issue is with an older model and some newer ones making use of an ENE card reader which has less than no linux support at all.

Work of caution, if you try linux on ANY HP laptop they will be of no assistance at all (I used to work in a corporate office with the engineers) and when you reference linux and an HP/Compaq laptop in the same sentence they get red faced and angry.

---

### Post by smylie on 2007-07-04
> **J-Red said:**
> Hey, I just bought a HP Compaq 6710b without checking if it was fully compatable with Ubuntu... When trying to install feisty, I realized it wasn't. I kept getting xorg errors because the graphics card is incompatible and couldn't get it to work at all.Or can anyone help me to install feisty on my HP Compaq 6710b? I haven't had very much luck with google, so I decided to post here. (haven't had much luck in IRC either...)

Hi

I've got the HP6710b and can confirm it all works fine under ubuntu. There are a couple of issues though:
- you can't use the default install live cd. (can't load X). I had to use the alternate install cd to install. However, I've been told that the normal live cd will work if you set the graphics to run in 640x480 vesa mode (before it boots up).
- one installed you can't run X with the default kernel as the standard fiesty kernel isn't recent enough. You need at least 2.6.20. This at least is easily fixed by doing an apt-get update and apt-get upgrade + rebooting.
- the current intel video driver in the feisty repos doesn't *quite* work - it's half a pixel off, leaving the screen blurry. This is also relatively easily fixed. See link [http://blog.smylie.co.nz/?p=4]("http://blog.smylie.co.nz/?p=4")

However, once you've fixed those issues, the laptop actually runs really well. Suspend works out of the box, and compiz fusion runs happily.

Let me know how you get on.

Regards
Dave Smylie

---

### Post by zzak on 2007-07-04
I've got a Compaq Presario V6000. (Just another HP machine)
But it has the nvidia chip set.
Feisty Fawn installed OK, but, X didn't work.
Had to go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
and downloaded his "Envy" program. Also got his FAQ.
Ran it and it worked like a charm.

Envy also does ATI chips

---

### Post by Old *ix Geek on 2007-07-05
I recently bought an HP dv6000 laptop, and Feisty runs like a charm on it. :)

---

### Post by abrarey on 2007-07-05
I must admit that it takes me a lot of time, but I made it.
The ATI x1250 can works on Feisty.
When you boot the CD and the xserver fails and display the message you select no.
then in the console you type in this order:
    *  sudo -s
    *  killall gdm
    * apt-get install xorg-driver-fglrx
    * depmod -a
    * aticonfig --initial
    * gdm start

After that the xserver loads and you can install ubuntu.

When you install Ubuntu doesn´t load the restricted drivers so the same problems show up, but you can do the same and it works.

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects when I get some news I will postit here.
:)

---

### Post by J-Red on 2007-07-05
Turns out i didn't have to return my 6710b, with my brother's help I was able to get it working. Optical drive doesn't work yet for some reason though... It'll work eventually, I don't need the optical drive for much now anyways. I'm hoping I can do a clean gutsy install with everything working in october.

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here (Feisty backport from Gutsy):

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this helps

---

### Post by s_raghu20 on 2007-07-08
Hi Guys,

I am still struggling with Ubuntu here... Here's what I have already tried..

[LIST=1]
[*]Installation using Alternate (Text based) CD
[*]Tried to follow instructions left [here]("http://www.blaise.ca/blog/?p=14")
[/LIST]

However, during the xserver configuration, the system went to sleep (for about 15-20 minutes) before I had to reboot that. 

However, the first vista reboot cleaned the MBR and now there is no boot menu..

I dont really want to try another installation attempt.. before I know that there really are some tried installation attempts.. that work.. and work this and this way.. 

All help is REALLY appreciated... I got this laptop to work with and its not installing the basic stuf... really frustrating...

Looking for some help..

regards
raghav..

---

### Post by ibob on 2007-07-08
Hi, 

I can confirm that the 6715b laptop works just fine and took me less time than I thought. I installed feisty using the text based installer.  Basically, I resized the Vista partition to 40 gig - leaving 100gig for feisty.   Then I used the guided installation to setup the ext3 partition with swap and dual boot.  Vista just ran a disk check and sorted itself out and still works just fine.

Anyhow, to get the graphics card working... You can follow the wild goose chase and try installing the official ati drivers from their website but they instruction leave lots to be desired... 

# Become root
sudo su

# Make sure you have the latest everything
apt-get update
apt-get upgrade

# Then get the graphics
apt-get install xorg-driver-fglrx
aticonfig --initial --input=/etc/X11/xorg.conf

# Start it up
gdm start

Wonderful.

Jim

---

### Post by Atomic Dog on 2007-07-09
It's not too late to return it and het a HP laptop with intel cpu and wireless!  It will make your life much easier!

---

### Post by s_raghu20 on 2007-07-10
Well, Finally I managed to get it done....Install Feisty on 6710b... 

Here is my experience..

[http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html](http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html)

thanks to everyone 

regards
raghav..

---

### Post by EXCiD3 on 2007-07-10
This thread: [Official HP dv9000 Laptop Thread!!]("http://ubuntuforums.org/showthread.php?t=431815"), which i started has tons of information for most of the HP laptops available. Page 8 or 9 has quite a lot of info. Check it out.

---

### Post by srd on 2007-07-12
look here
for hp 6715b

[http://ubuntuforums.org/showthread.php?t=499060](http://ubuntuforums.org/showthread.php?t=499060)

---

### Post by danimall on 2007-07-21
I have an HP dv6408nr notebook and I was able to get Ubuntu 6.10 to install correctly onto my computer using the live CD, but now when I try to start it up it will get to the Ubuntu loading splash screen and then just go completely blank.  Is this an issue with the Nvidia drivers for my graphics card?  If so then how would I work around it?  I am still kind of new to linux so if you have any basic solutions then that would be great.  My specs are listed below.

Microprocessor   	1.8 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache 	512KB+512KB L2 Cache
Memory 	1024 MB DDR2 System Memory (2 Dimm)
Memory Max 	Max supported 2048 MB
Video Graphics 	NVIDIA GeForce Go 6150 (UMA)
Video Memory 	Up to 287 MB

It probably doesn't make a difference but I am dual booting Ubuntu 6.10 and Vista.

---

### Post by mirnazim on 2007-07-24
> **abrarey said:**
> I must admit that it takes me a lot of time, but I made it.
The ATI x1250 can works on Feisty.
When you boot the CD and the xserver fails and display the message you select no.
then in the console you type in this order:
    *  sudo -s
    *  killall gdm
    * apt-get install xorg-driver-fglrx
    * depmod -a
    * aticonfig --initial
    * gdm start

After that the xserver loads and you can install ubuntu.

When you install Ubuntu doesn´t load the restricted drivers so the same problems show up, but you can do the same and it works.

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects when I get some news I will postit here.
:)
Thanks buddy abararey

Looks like it will work like this. Install process started 

will keep posted

---

### Post by mirnazim on 2007-07-24
> **mirnazim said:**
> Thanks buddy abararey

Looks like it will work like this. Install process started 

will keep posted
Woweeeee

It worked.

Thanks a lot

---

### Post by abrarey on 2007-07-30
> Thanks buddy abararey

Looks like it will work like this. Install process started

will keep posted

You are welcome mirnazim, now i´m triyng to enable the 3d effects but I don´t have anything yet.
We´ll keep posted
:)

---

### Post by bengrout on 2007-08-17
Hi abrarey,

I followed your advice and managed to get Ubuntu running on my laptop (thank you very much). I even managed to get wireless working with ndiswrapper.

I would love to know how you are getting on with the desktop effects... I have had no luck (although I have very limited Linux knowledge) - what confuses me though is that 3D games such as OpenArena (based on Quake 3 engine) runs with no problems whatsoever. Any thoughts on this?

Thanks.

---

### Post by FrancoNero on 2007-08-17
compaq nx7400 (intel gfx) (gutsy)
suspend/hibernate does not work, no matter what supercool "how to" or "work around" i try... if it works somehow, i don't have any keyboard/touchpad when waking my laptop up again.
what are you guys' experiences with suspend/hibernate?

---

### Post by ronthedon on 2007-08-22
For those using hp dv2530ee use the following to get the laptop configured properly using ubuntu fiesty fawn.

[LIST=1]
[*]Use an alternate cd for installing, not a live cd. For some reason some of the hardwares dont get detected properly, using live cd while installing. Ubuntu Studio would be a nice option.

[*]After installing the OS, use envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) , it will take some time to download(actually lot of time). After the installation, nvidia will be configured correctly and u will see the NVIDIA logo when logging into gnome.
[/LIST]

my system congif :
centrino duo 2.0ghz
1024mb ram
nvidia go 7400m
160gb hdd

---

### Post by insub2 on 2007-08-27
> **abrarey said:**
> I must admit that it takes me a lot of time, but I made it.
The ATI x1250 can works on Feisty.
When you boot the CD and the xserver fails and display the message you select no.
then in the console you type in this order:
    *  sudo -s
    *  killall gdm
    * apt-get install xorg-driver-fglrx
    * depmod -a
    * aticonfig --initial
    * gdm start

After that the xserver loads and you can install ubuntu.

When you install Ubuntu doesn´t load the restricted drivers so the same problems show up, but you can do the same and it works.

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects when I get some news I will postit here.
:)

Has anybody else who has used this method experiencing extremely slow bootups?  It's taking my friends comp like 3 minutes to get to the login screen where mine (older w/ slower cpu)  takes less than a single minute.

it's also running linux-mint.  I'm trying to figure out what is to blame.

also, how do i have it display verbose on boot?

---

### Post by 1337_ubunutu_teen on 2007-09-09
> **zzak said:**
> I've got a Compaq Presario V6000. (Just another HP machine)
But it has the nvidia chip set.
Feisty Fawn installed OK, but, X didn't work.
Had to go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
and downloaded his "Envy" program. Also got his FAQ.
Ran it and it worked like a charm.

Envy also does ATI chips

Hey, I have an HP Compaq 6715b, and I just installed Ubunutu, and downloaded the patch listed above (& burned it to a cd).  what commands would I use in order to mount the Cd drive and run the .DPM file???

:confused:

---

### Post by ggumas on 2007-09-11
I can't load Ubuntu 7.10 from a Live Disk onto a HP 6510 notebook with a vista operating system.
My problem seen\ms to be caused by the fact that the live Disc fails to find an xserver. Further since y\the loaded Ubuntu system fails to recognize either my wired ethernet connection or my wireless card I cant load an xserver.
I tried the same thing with complete success on a Compaq 2500 with an XP operating system, so I am sure that my problems are due to either the HP 6510 or the vista operating system.
My steps in the setup were as follows:
When the Ubuntu logo appeared I entered F6, removed the text "splash" and "quiet", and entered "all_generic_ide". This was done to fix a previous error of the sort "Can't access tty".
After which Ubunti begins to load, but eventually fails with the message  "failed to start Xserver".
I then got to a bash prompt and entered.
>sudo -s
>killall gdm
>apt-get install xorg-driver-fglrx
This resulted in a message of the sort : could not resolve "archive.ubuntu.com" maybe run apt-get update or try with --fix missing.
I then enterred 
>apt-get update
and got a message of the sort: failed to fetch [http://-------------](http://-------------), could not resolve "archive.ubuntu.com"
It then became apparent to me that the loaded Ubuntu kernel could not access the Internet even though I was hard wired on an active Ethernet.
I have been struggling with this for the last few days and I am about ready  to give up, but I am still hoping someone will come to my rescue with a recommended fix

George G

---

### Post by ggumas on 2007-09-12
> **ibob said:**
> Hi, 

I can confirm that the 6715b laptop works just fine and took me less time than I thought. I installed feisty using the text based installer.  Basically, I resized the Vista partition to 40 gig - leaving 100gig for feisty.   Then I used the guided installation to setup the ext3 partition with swap and dual boot.  Vista just ran a disk check and sorted itself out and still works just fine.

Anyhow, to get the graphics card working... You can follow the wild goose chase and try installing the official ati drivers from their website but they instruction leave lots to be desired... 

# Become root
sudo su

# Make sure you have the latest everything
apt-get update
apt-get upgrade

# Then get the graphics
apt-get install xorg-driver-fglrx
aticonfig --initial --input=/etc/X11/xorg.conf

# Start it up
gdm start

Wonderful.

Jim
Your suggestions sound good, but unfortunately when the live ubuntu Cd loads ubuntu on my hp6510 with a vista operating system, it fails to find an internet connection. I would appreciate suggestiions.

George G

---

### Post by Podmornik on 2007-09-14
Hello!

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects and I'm not getting it to work.

I'm trying to get to work Compiz and I managed to install XGL and Compiz but when I start them nothing seems to work. The only thing that works is that my terminal window displays me gtk-window-decorator error and I loose my window borders.:(

Is that the because of the graphic card or what?

Any ideas, solutions?

Did anyone get to work this on his 6715b laptop?

---

### Post by samjam on 2007-09-14
> **abrarey said:**
> I must admit that it takes me a lot of time, but I made it.
The ATI x1250 can works on Feisty.
When you boot the CD and the xserver fails and display the message you select no.
then in the console you type in this order:
    *  sudo -s
    *  killall gdm
    * apt-get install xorg-driver-fglrx
    * depmod -a
    * aticonfig --initial
    * gdm start

After that the xserver loads and you can install ubuntu.

When you install Ubuntu doesn´t load the restricted drivers so the same problems show up, but you can do the same and it works.

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects when I get some news I will postit here.
:)

Nice one; just the trick!
Thanks

Sam

---

### Post by miro_braun on 2007-09-18
Help please:

[http://ubuntuforums.org/showthread.php?p=3384712#post3384712](http://ubuntuforums.org/showthread.php?p=3384712#post3384712)

muchos gracias..

---

### Post by hatmal on 2008-03-03
I have hp compaq 6710b too.

i had a problem to download redhat enterprise linux 5 at that laptop

so when i search i found that ubuntu 7.10 is compitable with my laptop.

i download it as an iso image from the site [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), which need one cd

i found some problem when install but now all thing work well

so if u explain your problem i could help you

---

