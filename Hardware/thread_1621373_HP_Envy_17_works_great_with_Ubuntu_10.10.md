---
title: "HP Envy 17 works great with Ubuntu 10.10"
date: 2010-11-14
forum: Hardware
---

### Post by vendicate on 2010-11-14
Just installed Ubuntu 10.10 on the HP Envy 17. Works great out-of-the-box install! So far i've noticed only minor issues..

**ISSUE**: when laptop lid is closed then opened, it hangs. 
**FIX**: Haven't had the time to fix it yet.

**ISSUE**: Firefox the backspace button wasn't working to go back.
**FIX**: go to about:config on firefox type browser.backspace_action hit enter, change value from 2 to 0. Should work.

---

### Post by BigJayDogg3 on 2010-11-15
> **vendicate said:**
> Just installed Ubuntu 10.10 on the HP Envy 17. Works great out-of-the-box install! So far i've noticed only minor issues..

**ISSUE**: Firefox the backspace button wasn't working to go back.
**FIX**: go to about:config on firefox type browser.backspace_action hit enter, change value from 2 to 0. Should work.

This actually isn't an issue per se.  This is the default behavior for many Linux distros.

And I'm glad you've installed without issue.  This eases my mind a bit since I'm planning on getting a 14 in the next couple months.

What's your config?

---

### Post by 0_irishboy_0 on 2010-11-28
I'd like to know how your Envy 17 is configured too.  I'm looking into getting one and dual booting Windows 7 and Ubuntu 10.10.

---

### Post by sn3rd on 2010-11-30
I'm running an Envy 17, but on Ubuntu 10.04.

Core i7 Q720
4 GB RAM
ATI Radeon 5850
500 GB HDD
Blu-ray ROM
1920 x 1080 LED-backlit LCD
Broadcom Wireless
Backlit keyboard
Beats 2.1 audio

Things work pretty well, aside from a few issues.
1) The i7 + 5850 combination runs quite hot. However, this is an issue on Windows as well as Ubuntu. Upon installing lm-sensors from source, I'm at least able to monitor CPU temperatures.
2) The LCD backlight dims during boot (even connected to AC power). Some reports say that after login, backlight returns to the normal level, but this does not happen with me.
3) The built-in subwoofer (Beats audio) does not work in Ubuntu.
4) Blu-ray reads the disc. However, playing a Blu-ray movie is not possible without ripping the disc to the hard drive.
5) Touchpad multi-touch does not work. However, vertical edge scrolling works.
6) Touchpad disable does not work.
7) Audio mute LED does not work.

---

### Post by cil_8 on 2010-12-29
With the same Notebook i have wireless problem!!

I try "iwconfig" and the result was:

lo          no wireless extensions.

eth0      no wireless extensions.

Ubuntu don't detect the wireless adapter wlan0!!

Solutions?

I installed Ubuntu 10.10 64bit

Core i7 720-QM 1,6 GHz, 6 MB di cache L3
6 GB RAM
ATI Mobility Radeon&#8482; HD 5850
500 GB HDD
DVD ROM
1920 x 1080 LED-backlit LCD
Broadcom Wireless
Backlit keyboard
Beats 2.1 audio

---

### Post by vplayer8 on 2011-02-02
I just got an Envy 17 3D...
what I did with the wireless problem was, just hook it up with a LAN connection. 
Then go to System -> Administration -> additional drivers. 

You should see that it has 2 suggestion. 
1. Broadcom
2. ATI graphics card.

Click activate broadcom.
You should be able to get your wireless connection in no time.

---

### Post by alexthunder on 2011-02-12
> **sn3rd said:**
> Things work pretty well, aside from a few issues.
1) The i7 + 5850 combination runs quite hot. However, this is an issue on Windows as well as Ubuntu. Upon installing lm-sensors from source, I'm at least able to monitor CPU temperatures.
2) The LCD backlight dims during boot (even connected to AC power). Some reports say that after login, backlight returns to the normal level, but this does not happen with me.
3) The built-in subwoofer (Beats audio) does not work in Ubuntu.
4) Blu-ray reads the disc. However, playing a Blu-ray movie is not possible without ripping the disc to the hard drive.
5) Touchpad multi-touch does not work. However, vertical edge scrolling works.
6) Touchpad disable does not work.
7) Audio mute LED does not work.
The same problems here...

But not only multi-touch doesn't work in Ubuntu 10.10, but also the right and left mouse clicks are not working on the clickpad. But there are solutions to either enable the left/right mouse click or to enable mutlitouch. And it seems that the mutlitouch should be available in the next version of Ubuntu (you can try the alfa version already).

Will install the lm-sensors. But what is the critical temperature?

Another problem is with 3D. How to play 3D videos? How to make active shutter glasses work in Ubuntu?

---

### Post by yld629 on 2011-04-09
[SIZE=2]Hi, complete Linux noob here. I have a Hp Envy 17 that has numeric keys on the numpad that function as arrow keys unless I depress the shift key. There is no numlock so no luck there. anyone have thoughts on this?[/SIZE]

---

### Post by Yellow Pasque on 2011-04-09
There must be some numlock. Play with numlockx package maybe?

---

### Post by yld629 on 2011-04-13
Hey, ya I did manage to get it to work with the above mentioned package. Just installed it and opened up the terminal to type "numlockx on" and it works like a charm now. Thanks for the reply btw.

---

### Post by mohegan on 2011-04-17
For the subwoofer, it's easy.
Just add this line in the file /etc/modprobe.d/alsa-base.conf (sudo gedit ...)
```
options snd-hda-intel model=ref
```
And restart your computer !
Work for me (with natty).

---

### Post by RebateFX on 2011-07-19
> **alexthunder said:**
> Another problem is with 3D. How to play 3D videos? How to make active shutter glasses work in Ubuntu?

That is also my question. 

Just got an Envy 17 with...

Core I7 2630QM @ 2.0Ghz
8Gb Ram
ATI Radeon 6850M

---

### Post by jayfost on 2011-09-10
I just dual booted my HP Envy 17" 3D with win7 and Ubuntu 11.04 windows works fine but when I log in to Ubuntu and shutdown or restart I get the error "A thermal shutdown has occurred"  it say that the machine was shutdown because it over heated even though that was not the case. Any ideas on this BTW in a Linux newbie

---

### Post by RebateFX on 2011-09-21
> **Temüjin said:**
> There must be some numlock. Play with numlockx package maybe?

OMG +1 to you. After spending about $2.3k on a laptop, you 1/2 expect there to be a numlock key lol.

---

### Post by RebateFX on 2011-10-05
What about Hybrid gfx?

Do we have to wait to get switchable gfx working?

I want to use the Radeon HD 6850 since this is a desktop replacement and battery life is not a consideration.

I tried the catalyst from the ATI website (11.9) as I heard it fully supports hybrid gfx, but X won't even start. Had to purge and get back to the open source (functional but not very fast) driver.

Then I wanted to try the switcheroo stuff, but after installing the proprietary driver, /sys/kernel/debug/vgaswitcheroo has disappeared.

Any way to get switcheroo back? or better yet, have the ATI card working all the time? :)

---

### Post by RebateFX on 2011-10-13
Ok, so purging fglrx and reinstalling the open source driver got switcheroo back.

That still doesn't help me force the discrete (ATI) card to be used so I can install the closed source driver for opengl.

---

### Post by NETChaser on 2011-10-19
[K]Ubuntu 11.10
The same problem ... Laptop is not compatible with linux
Distributions tried opensuse, ubuntu, kubuntu, fedora, but all that I want to get failed.
It is hoped that the driver wi-fi, clickpad hd6850 and will be maintained.
But with a backlit display and warnings about the temperature just no hope.
BIOS of this laptop works with hidden partitions on HDD (for recovery and diagnosis), probably windows written on the hidden partition information on the temperature. Since installing linux this hidden partitions does not, then the menu at boot time by pressing ESC disappears and a message appears on the temperature.

---

### Post by RebateFX on 2011-10-19
> **NETChaser said:**
> [K]Ubuntu 11.10
The same problem ... Laptop is not compatible with linux

If you are just using it for business, everything works fine. Wifi works, trackpad (no right click though but I use an external mouse).

However if you want to use any OpenGL software like games etc, do not buy an Envy17 3D unless the atrocious hybrid gfx issues are sorted out.

---

### Post by alexthunder on 2011-10-20
> **RebateFX said:**
> If you are just using it for business, everything works fine. Wifi works, trackpad (no right click though but I use an external mouse).
The latest kernels don't work for me at all. It started with 11.04 and now Ubuntu/Kubuntu/Xubuntu/Lubuntu 11.10 don't work for me at all - they just freeze after first restart. I use an older Linux Mint now.

---

