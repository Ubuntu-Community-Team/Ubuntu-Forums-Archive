---
title: "Hardware shuts down during boot"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by dguildford on 2009-07-03
I installed Xubuntu 9.04 (Alternate) for PPC on iMac G3 400 DV Tangerine, upgraded to 192MB RAM, 80GB HD and iMac v4.1.9 firmware update. I get a Stage 1 boot, choice l (Linux/Gnu) or c (CD). Input l or no action, boot proceeds. Yaboot 1.1.13 proceeds. There is activity with last line on a white screen "returning from prom-init". Screen goes black with "[30876121 0000:00:10.00 invalid ROM contents aty 128fb". Then hardware shuts down. Any clues?

---

### Post by milton1 on 2009-07-03
Are you getting the same result trying to boot hard disk and CD?

---

### Post by philcamlin on 2009-07-03
try booting into live cd and does it do it then

---

### Post by dguildford on 2009-07-03
Yes, identical

---

### Post by philcamlin on 2009-07-03
so its not ubuntu then its your pc same in mac?

if so 

id check the power supply

---

### Post by dguildford on 2009-07-03
Thank you philcamlin , but not so. Just got the tangerine machine back from the repair shop yesterday with a clean bill of health and a bill for new HD and RAM. The tangerine machine will run up on the original installer disk.

Additional info: I have done Alternate install and Live CD with LAN cable attached. Install asked questions about IP which I completed.

Should I try again unwired?

Tried unwired with no change in result.

Increased RAM to 768MB and booted into live cd. Entered <Tab> to choose "live-nosplash-powerpc"

From black screen:
072
[56.848451] SQUASFHS error: sb-bread failed reading block 0x99ea9
[56.848660] SQUASFHS error: Unable to read fragment cache block [267a8e36]

Makes sense?

EDIT:
Thank you xophelorak. I'll have a read and give it a go tonight. Keep in touch.

---

### Post by xophelorak on 2009-07-04
I find it an interesting coincidence that you should have posted this 10 hours ago, I've been working on installing ubuntu on my 20gig imac dv and I am having the exact same issues. I got it to install but it gives me the exact same error and then the hardware shuts down during boot. So, can anyone fix our imac dv's for ubuntu? TIA : D

EDIT: further info

I have installed the ubuntu 9.04 jaunty jackelope for PPC alternate install disc, because the jaunty ppc livecd wouldnt' load, so I found on other forum posts that the ppc alternate isntall would work, and it did work in that it installed, just now it doesn't boot, as detailed above : \

EDIT : 
[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

that link might help, I'm actually working on installing debian on the imac now it seemed a little more documented, but apparently there is some documentation are g3 imacs and ubuntu on the ubuntu wiki.

---

### Post by xophelorak on 2009-07-08
Hey dude, "Hi, you said in your post to getting Xubuntu onto a G3 iMac "I'm actually working on installing debian on the imac now".
 How is that going?
 All I want is a working machine for basic browsing and e-mail and Xubuntu 9.04 looked so promising.
 I definitely want to use my G3.
 Please keep in touch if you have success.
 The lack of replies to my query indicates a possible problem.
 dguildford"

In response to your PM:

Yes I am writing this reply laying on my stomach on a futon in a spare room, in debian w/ kde core on konqueror on the imac : D

For Debian its pretty simple, here's what I did:

1. I d/led the Debian business card stable CD [http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

2. boot the imac with the disc (hold c during bootup to boot the disc).

3. install Debian using the installer.

4. when it prompts you what you want to install, DO NOT select 'windows environment' this will make you boot to a broken x environment (black screen) : \ so, when it prompts you hit space bar to deselect the windows environment, you just want the core debian system which I think is the last option and is selected by default.

5. it'll install yaboot and debian on the imac, and boot you to a command prompt.

6. apt get all the packages you need and install x

7. get a working imac xorg.conf off the ubuntu forums site forum, copy it over into your imac debian console with a usb stick.

8. run startx and go.

There is a good debian on imac g3 guide that helped me (google, it may have been on the ubuntu forums), I put the key points above, the guide didn't mention getting the xorg.conf off the web but I found that to be the easiest solution -gotta take a break, later, hack on.

EDIT: if you get a black screen on trying to startx, hit alt plus f1 a few times to get back to the console, this may work for ubuntu, I feel like ubuntu was failing to load x, altho it did cause the hardware shutdown, sometimes it would just sit there with a black screen...

---

### Post by dguildford on 2009-07-09
Hi xophelorak and thanks for the advice.

I too have migrated to Debian and am almost there.

See post: root password changed at [http://forums.debian.net/viewtopic.php?f=10&t=39017&start=15](http://forums.debian.net/viewtopic.php?f=10&t=39017&start=15)

---

### Post by xophelorak on 2009-07-09
I saw your post on the Debian forums that you linked - if you are having problems entering your password in for the sudo command, why not just log in as root in the first place so that you don't have to sudo. 
 
imac g3 xorg.conf's to try:

claims to work w/ debian 5 and ubuntu 8:
[http://forums.macrumors.com/archive/index.php/t-662667.html](http://forums.macrumors.com/archive/index.php/t-662667.html)

that one might work, I tried alot before I found one that worked.
 
 
[http://ubuntuforums.org/showthread.php?t=770033](http://ubuntuforums.org/showthread.php?t=770033)
[http://ubuntuforums.org/showthread.php?t=1058766&page=6](http://ubuntuforums.org/showthread.php?t=1058766&page=6)

---

### Post by cariboo on 2009-07-09
Just so you know Ubuntu is doable on a ppc. I have have a G3 350Mhz with 256MB ram, and right now it is running as a mail server running 8.04 server version.

I have also run Xubuntu 8.04 on this computer and didn't encounter any of the problems you guys are having.

---

### Post by dguildford on 2009-07-09
Hi xophelorak
I don't want to do a third install, but if I have to ...
 
How do I log in as root in the first place? I am suggesting that the root password somehow has become scrambled. I'll try it tonight.
 
With Debian Business Card install were you asked for Root and User passwords? Did you comply? Are they different?
 
Thanks for the support

---

### Post by dguildford on 2009-07-09
Hi Xophelorak 
 
Re your comment:
7. get a working imac xorg.conf off the ubuntu forums site forum, copy it over into your imac debian console with a usb stick.
 
I can copy the xorg.conf from a source onto a usb stick, but navigating within the debian console and saving a text file as .conf into the directory is beyond my experience. I only know DOS, Mac and Windows.
 
Are you able to tutor me?
 
Thanks

---

### Post by xophelorak on 2009-07-15
Hi gildford, to learn how to mount a USB stick in Debian or any other linux, google 'how to mount usb stick in linux', you just need to look up the series of commands to use a usb stick in linux, it's not that hard.

but, I uploaded the working xorg.conf just now to my website from my imac.

so, at the Debian command line (make sure your imac has ethernet plugged in):

type:
[FONT=Arial Black]
cd /etc/X11/

wget [http://www.lifeinterfaces.com/jslair/xorg/xorg.conf](http://www.lifeinterfaces.com/jslair/xorg/xorg.conf)

[FONT=Arial][B]this will make your imac download my imac's xorg.conf from the command prompt.

type startx to run x.

edit: capitalized the X in X11 since linux is caps sensitive.
[/B][/FONT][/FONT]

---

### Post by xophelorak on 2009-07-16
I think Debian asks for both root username/pw and a user un/pw on install. I haven't had any issues with either of the pw's You might want to make really sure if you install again that you know exactly what you put in as the root pw during setup, it's possible that you put in a caps or something that you aren't typing later - it's also possible that your computer corrupted your PW, but it seems unlikely seeing as we both installed the same Debian distro on basically the same imac's.

---

### Post by dguildford on 2009-07-18
Hello xophelorak

Re xorg.conf
Thanks for that. I have been able to get my Tangerine Mac to run sweet. 

Re passwords
I worked out that the response was due to not having sudo configured, not one of passwords. So Tangerine mac is running sweet.

New opportunity
I want to use NextG wireless broadband (Australian 3G) via a usb modem. The pre-paid arrangement makes for very cheap connection for low usage. Of course the service provider, both of the NextG and the modem, does not support Linux. It is back to the forums. It was a nice experience to have made your acquaintence.

Frank

---

