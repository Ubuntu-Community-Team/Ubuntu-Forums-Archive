---
title: "How to ASUS K50IJ - Ubuntu 9.04 Jaunty"
date: 2009-07-05
forum: Hardware
---

### Post by KoKuToru on 2009-07-05
Well the laptop originally comes with linux but I wanted ubuntu..
I had some problems and solved them after googeling a lot..

[FONT=Arial Black][SIZE=4]WLAN[/SIZE][/FONT]
run this command and wlan will work
```
sudo apt-get install linux-backports-modules-jaunty
```I think this is not the best solution.. but it works

[FONT=Arial Black][SIZE=4]Compile own WLAN[/SIZE][/FONT]
at [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

I can't say it's better/worser..
I did it .. but i can't see any improvement..
compared to **linux-backports-modules-jaunty**

[FONT=Arial Black][SIZE=4]Sound 1[/SIZE][/FONT]

***[COLOR="Red"]DONT USE THIS ! USE SOUND 2 ![/COLOR]***

Sound is more work
Get the ALSA updater script from:
[URL="http://ubuntuforums.org/showthread.php?p=6589810#post6589810"]http://ubuntuforums.org/showthread.php?p=6589810#post6589810
[/URL]Extract it .. and make it executable ! and run it :)
```

sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di

```**-di** will download and install newest ALSA

Then run this script: (found at [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/393523/comments/38](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/393523/comments/38))
```
sudo -s
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz
tar xf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
cp hda-verb /usr/bin
gedit /etc/rc.local
```And add this line before "exit 0"
```
hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM
```Reboot and your sound will work :)

[FONT=Arial Black][SIZE=4]Sound 2[/SIZE][/FONT]
```

wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install

```

Reboot and it will work :) 
If you used **Sound 1** ! Don't forget to change back the edited /etc/rc.local file !

[FONT=Arial Black][SIZE=4]Sound problems
[/SIZE][/FONT]**Executing wine** stops the sound play back, no idea why.. just restart VLC,Rythmox
or what ever you use..and it will work again..

**Sound crackles:**
I upgraded my ext3 to ext4 .. and sound was crackeling.. 
look at the attached image, make sure PCM is at 100%

**After every boot PCM is a 0%**
Do this:
```
sudo gedit /etc/rc.local
```and add before "exit 0" this:
```
amixer set PCM 70%
```and/or also add it into the autostart (Session-manager) !
[FONT=Arial Black][SIZE=4]
Webcam (flip)
[/SIZE][/FONT]Found at: [http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/](http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/)

And for copy and past:
```

sudo -s
cd /bin/
wget http://codebin.cotescu.com/uvcvideo/flip_webcam
chmod +x flip_webcam
flip_webcam 1

```And it will be done..

After a kernel update run again:
```

sudo flip_webcam 1

```
If left and right is also wrong.. then use the "2" :)
```

sudo flip_webcam 2

```[SIZE=4][FONT=Arial Black]LCD brightness FN-Keys[/FONT][/SIZE]
(also solves flickering)
```
sudo gedit /boot/grub/menu.lst
```add to this line
```
**# defoptions=**quiet splash
```this:
```
# defoptions=quit splash **acpi_backlight=vendor**
```save and do:
```
sudo update-grub
```Reboot.. and it will work ;)

---

### Post by 2541 on 2009-07-10
Hi KoKuToru!

Thanks for your advice.
WLAN is working now.

But I still couldn't manage the sound-problem.
I did everything you recommend, but when it gets to the hda-verb command I get the following error-message in the terminal:

hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM
open: No such file or directory

Any ideas?

2541

---

### Post by KoKuToru on 2009-07-11
did you installed newest ALSA ?

and i hope you didn't copy&past this:
```
wget [ftp://ftp.kernel.org/pub/linux/kerne...erb-0.3.tar.gz]("ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz")
```

it need to be like this..
```

wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz

```I will edit my post..

---

### Post by 2541 on 2009-07-12
Of course I tried to copy & paste the 'wrong' link, but found out easily how to download the correct file.

But I didn't use the '-di' option at this command:

sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di

I only had set the '-i' option.
After redoing it with '-di' sound started to work!!

So Ubuntu is the very first Linux-Distro to bring a single beep out of my notebook...

btw: Windows 7 RC configures every single piece of hardware in a correct way, except for the webcam (picture is upside down, or with a newer driver left and right side are mixed up) ...

Now the only remaining problem with the notebook is, that the monitor starts flickering everytime I click on the touchpad, but that's a minor issue. Brightness control via FN-keys is working on my machine.

Thanks again for your help und lieben Gruß aus Wien...

2541

---

### Post by KoKuToru on 2009-07-12
> **2541 said:**
> 
Now the only remaining problem with the notebook is, that the monitor starts flickering everytime I click on the touchpad, but that's a minor issue.


You can deactive "Dim screen at idle" in the Energie-settings (you can look at the image.. but it's in german..)
Solved my flickering a little

FN-Key are working right ? hmm.. They wont for me.. grr
I just can set  brightness value to 0 and 1
If i look into the file which saves the brightness i can see that the max-brightness is 13 !
And I can set the brightness manually via terminal to 0-13 ...

---

### Post by MadTheologian on 2009-07-12
I tried "sudo apt-get install linux-backports-modules-jaunty" but it could not find the package.  What should I do?  I'm new at compiling, so any help would be appreciated.

---

### Post by KoKuToru on 2009-07-13
> **MadTheologian said:**
> I tried "sudo apt-get install linux-backports-modules-jaunty" but it could not find the package.  What should I do?  I'm new at compiling, so any help would be appreciated.

```

sudo -s
apt-get update
apt-get install  linux-backports-modules-jaunty

```

And when it still doesn linux-backports-modules-jaunty work... no idea you can downlaod the deb file manually from

[Kernel 2.6.15]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.15/")
[Kernel 2.6.20]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.20/")
[Kernel 2.6.22]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.22/")
[Kernel 2.6.24]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.24/")
[Kernel 2.6.27]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/")
[Kernel 2.6.28]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.28/")
[Kernel 2.6.30]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.30/")
[Kernel 2.6.31]("http://at.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/")

You can get your version with:
```
uname -r
```

But apt-gt should work .. ah ! 
You need a internet connect to do this !!

Thats it xD yeah .. you need to connect your laptop over LAN..
Install the packages .. and then you can use WLAN..
Or you download the file manually (with the links) copy it to
your laptop somehow.. and install it

---

### Post by mikeypizano on 2009-07-28
Posting for a friend...

My friends Asus K50 sound is still not working, even after doing this twice and several other methods. Its the Best Buy model and has a dual boot with Vista 64 and Ubuntu 9.04 X64.

---

### Post by KoKuToru on 2009-07-29
I saw on ASUS page a extra page for a BestBuy version...
Maybe the hardware is different ?

---

### Post by mikeypizano on 2009-07-29
We ran the hardware monitor I installed for him, and its an HDA Intel sound card, and under terminal the one command that tells you the card says VIA.

---

### Post by saem on 2009-08-02
I'm using Fedora, but I stumbled upon this thread as I was attempting to get my K50IJ setup, in particular I didn't have working sound.

As far as I can tell there is a bug/misconfiguration with the codec detection for this particular model, and to fix it I followed the advice in the following post: [https://bugzilla.redhat.com/show_bug.cgi?id=509542#c3](https://bugzilla.redhat.com/show_bug.cgi?id=509542#c3)

So, first thing, what's HDA-Analyzer? Google turns up:

[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

Basically, make sure you have python-gtk2 libs installed, not sure what they're called in ubuntu. Then running as root, might not need to I did in fedora, run the tool. You'll see a tree of 'nodes' click on Node[0x1c] PIN. Then looking about the display, you should see the section about 'EAPD', there will be a number of checkboxes as part of it, and one of those will be 'EAPD', check that one.

Then try out your sound, if it works, you're all set. If not, you might have to do a few other things, I did have to do the usual pulseaudio stuff like change the tsched=no, and reducing the timing from 25ms to 10ms as well.

I hope this helps. That last bit did it. I haven't tested the Mic or headphones. Best of luck!

---

### Post by mutrax on 2009-08-02
Hey, was strugling with sound, and the alsa upgrade script didn't work with me... I solved it a bit different.
[http://ubuntuforums.org/showthread.php?t=1191356](http://ubuntuforums.org/showthread.php?t=1191356)

:KS

---

### Post by saem on 2009-08-02
> **2541 said:**
> Brightness control via FN-keys is working on my machine.

Did you have to do anything to get this working, or was this out of the box?

---

### Post by 2541 on 2009-08-02
> **saem said:**
> Did you have to do anything to get this working, or was this out of the box?

No it worked out of the box, but only sometimes.
Strange behaviour; with Sidux, the brightness control is working correctly and 'always'.

---

### Post by peterlx on 2009-08-05
Hi everybody,
back to the sound problem. Thx to Sebastian from Cream desktop project who executed the installation steps for install of the latest ALSA driver the sound works in general now. But one problem I have on this AND on another computer: I cannot switch the external mic jack on using ALSAMIXER or another mixer.
Have you any idea how to solve it?

Thanks to everybody which helped already,
Peter

---

### Post by gerard.leonardo on 2009-08-08
Hi there,

Did somebody was able to setup the webcam on this model of asus? I got mine few days ago, I am very thankful with this guide that I was able to setup the audio and the WLAN, however I have a problem with the built in webcam, it is upside down (inverted). Please help. :-(

Thanks in advance!!!

---

### Post by 2541 on 2009-08-08
> **gerard.leonardo said:**
> Hi there,
 I have a problem with the built in webcam, it is upside down (inverted). Please help. :-(

Thanks in advance!!!

My webcam is also upside down.
I've tried a few distros (Fedora, Sidux...).
It is always the same misbehaviour.

Under Windows 7RC with the driver from the asus-website installed
you can turn the stream of the webcam 180° but then left and right are mixed up...
But this is better than upside down.

---

### Post by KoKuToru on 2009-08-09
> **2541 said:**
> My webcam is also upside down.
Same here, you can apply a patch for the driver to flip it..
And yeah without installing something the webcam works.

And well ASUS is stupid.. why didn't they just rotated the camera..
Under WinXP it's also wrong.. (with the driver from ASUS, just stupid !)

---

### Post by 2541 on 2009-08-09
> **KoKuToru said:**
> Same here, you can apply a patch for the driver to flip it..


How do I apply this patch for the driver?

---

### Post by KoKuToru on 2009-08-11
> **2541 said:**
> How do I apply this patch for the driver?

Found at: [http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/](http://radu.cotescu.com/2009/07/31/resolving-vertically-flipped-images-from-webcams-in-ubuntu/)

And for copy and past:
```

sudo -s
cd /bin/
wget http://codebin.cotescu.com/uvcvideo/flip_webcam
chmod +x flip_webcam
flip_webcam 1

```And it will be done..

After a kernel update run again:
```

sudo flip_webcam 1

```

I will add this to the first post..

---

### Post by 2541 on 2009-08-11
Thanks again!
Now the webcam is working almost perfect.
Just left and right are still mixed up (the same as under windows...)

---

### Post by alexnews on 2009-08-16
it all works fine, thanks a lot!
Greetings from Alex

---

### Post by alexnews on 2009-08-16
... i detected a problem with the internal microfone, so skype cannot be used. Any 
ideas to solve?

btw: in Win7RC 64-bit the webcam is correct, horizontal and vertical.

---

### Post by KoKuToru on 2009-08-17
> **alexnews said:**
> ... i detected a problem with the internal microfone
There is a microfone ? 

Because of the driver it wont work maybe.. (we are using a stupid workaround)
There is a also much noise, if you plugin a headphone...

---

### Post by 2541 on 2009-08-17
> **KoKuToru said:**
> There is a microfone ? 


Yes, there is a microphone.

With Windows 7 RC it works (more or less out of the box ;-)).
You can easily test it using Skype.

---

### Post by KoKuToru on 2009-08-19
Solved a new problem ... Brightness control and Brightness-flickering ;)
 
[SIZE=4][FONT=Arial Black]LCD brightness FN-Keys[/FONT][/SIZE]
(also solves flickering)
```
sudo gedit /boot/grub/menu.lst
```
add to this line
```
**# defoptions=**quiet splash
```
this:
```
# defoptions=quit splash **acpi_backlight=vendor**
```
save and do:
```
sudo update-grub
```

Reboot.. and it will work ;)

(I also added this to the first page)

---

### Post by 2541 on 2009-08-19
> **alexnews said:**
> 

btw: in Win7RC 64-bit the webcam is correct, horizontal and vertical.

Not on my machine. I've tried Windows 7RC 64 bit and the webcam is still upside down. :-(

---

### Post by xphill64x on 2009-08-21
I'm having three problems so far with the same laptop, though the best buy version.

The most pressing is that the touchpad isn't recognized in Linux, which means I can't configure it or use G-Synaptic to enable palm detection etc.

The second problem is the very bad screen flicker, soon as you try to use the Fn F5 or F6 combos. I'm wondering how you can set it through terminal
to adjust the brightness.

The third problem seems widespread for Linux users of Skye. The camera can't seem to get any light in/way too dark.
When I use VLC to capture video, it decides to just "turn" the screen to a superdim/off faze. It's weird.

I haven't tested the Microphone yet. But until I have functionality  rivaling windows I can't  use this system. (The touchpad is driving me nuts!) If anyone knows how to probe for the touchpad manufacture/model so I can file a bug report, that would be useful.

---

### Post by KoKuToru on 2009-08-21
> **xphill64x said:**
> 
The most pressing is that the touchpad isn't recognized in Linux, which means I can't configure it or use G-Synaptic to enable palm detection etc.

No idea, everything works normal at the normal version.. 
But what you can try is this:
When I plug-in an extern mouse, I deactivate my touchpad with the following command
```
sudo modprobe -r psmouse
```and when i need the touchpad again .. i do
```
sudo modprobe psmouse
```.. maybe the last command activates your touchpad...
> **xphill64x said:**
> 
The second problem is the very bad screen flicker, soon as you try to use the Fn F5 or F6 combos. I'm wondering how you can set it through terminal
to adjust the brightness.

Look at first post LCD brightness FN-Keys...[SIZE=4][FONT=Arial Black]
[/FONT][/SIZE]> **xphill64x said:**
> 
The third problem seems widespread for Linux users of Skye. The camera can't seem to get any light in/way too dark.
When I use VLC to capture video, it decides to just "turn" the screen to a superdim/off faze. It's weird.

Aha.. I will install skype and checkout ;)

---

### Post by KoKuToru on 2009-08-21
> **2541 said:**
> Just left and right are still mixed up (the same as under windows...)

```
sudo flip_webcam 2
```
Will do the magic ;)

---

### Post by tobey2k on 2009-08-21
hey guys,

i don´t know if I understand you right,

but on my K50IJseries the display flickers all time when the brightness of the display is not 100%.

you see it at darker backgrounds a lot...

this solution doesn´t change it:
[SIZE=4][FONT=Arial Black]LCD brightness FN-Keys[/FONT][/SIZE]
(also solves flickering)
     Code:
     sudo gedit /boot/grub/menu.lst 
add to this line
     Code:
     **# defoptions=**quiet splash 
this:
     Code:
     # defoptions=quit splash **acpi_backlight=vendor** 
save and do:
     Code:
     sudo update-grub 
Reboot.. and it will work :wink:




Is it the same on your Asus Laptops???

when I start Win7RC the flickering is gone?!

tobey2k

---

### Post by KoKuToru on 2009-08-22
> **tobey2k said:**
> 
Is it the same on your Asus Laptops???


No, the solution works on my laptop..

Ubuntu 9.04 with Kernel 2.6.28-15-generic without backports-modules (using extern wlan-stick, backports sux's)

Desktop I use: Xfce4 with Xfwm4 .. but gnome does work too (with compiz)

At my the graphic card i am using the new UXA-mode, because it makes indirect-rendering possible ! => Comiz and xfwm4 will work with OpenGL-applications (without flickering)

To summary it:
Works:

[LIST]
[*]Sound, intern speakers
[*]Webcam
[*]Touchpad
[*]Wlan (not on my system, backports sux's)
[*]LCD backlight (FN+keys and no flickering)
[*]Graphic with 3D-acceleration
[/LIST]
Doesn't work:

[LIST]
[*]Sound, extern speakers (works but sounds horrible) + intern/extern microphone
[/LIST]
> **tobey2k said:**
> 
but on my K50IJseries the display flickers all time when the brightness of the display is not 100%.
you see it at darker backgrounds a lot...
Well i think what you mean is not the flickering of what we are talking about..
The flickering you mean is like on and old monitor (no flat-screen) with low refresh speed like 50Hz ..(you would see this at dark areas..) ? 

If yes..:
Hmm I remember at the first week I had this laptop I was able to see it too (sometimes) .. but now it's like gone.. ..
You can check is the "Display settings" there you can set the screen-refresh..
Well "can" the only option I have there is 60Hz..

---

### Post by 2541 on 2009-08-22
> **KoKuToru said:**
> ```
sudo flip_webcam 2
```
Will do the magic ;)

Not on my machine!
No difference between 'sudo flip_webcam 1' or 'sudo flip_webcam 2'.

Left and right are still mixed up.
At least I don't have to stand on my head anymore... :-)

---

### Post by 2541 on 2009-08-22
> **KoKuToru said:**
> 
Doesn't work:

[LIST]
[*]Sound, extern speakers (works but sounds horrible) + intern/extern microphone
[/LIST]



If I plug in my old Plantronics-Headset the sound in the headset is okay and even the microphone of the headset works...

This notebook keeps surprising me!

---

### Post by miaerbus on 2009-08-23
KoKuToru, this topic is priceless for me! :D
I've been dealing with these exactly problems ever since I got the computer, and then I found your post and all solutions just worked for me! Except for one thing... Sound. Here's deal: from now on it works perfectly when I turn on the computer. But if I put it to sleep (FN+F1/ suspend/ you name it), then sound stops working :(
I tried to run /etc/rc.local by hands, but no luck.
Any suggestions? Many thanks in advance!

---

### Post by KoKuToru on 2009-08-23
> **2541 said:**
> If I plug in my old Plantronics-Headset the sound in the headset is okay and even the microphone of the headset works...


I rechecked now.. 

Extern microphone works.. but also with much noise..
My headset does have a lot of noise..

Interesting is the inter-microphone does work xD Mean I can hear myself when I am using the headset (when i activate to play microphone also).

But the front speakers wont play it...
I can record from the extern-microphone !
But recording from intern-microphone doesn't work ..lol

Funny... I hope next alsa-update will fix this sound problems :P

> **2541 said:**
> No difference between 'sudo flip_webcam 1' or 'sudo flip_webcam 2'.
Did you reload the modules ? or restarted the PC..?
```
sudo flip_webcam 2
```Did work for me .. I don't think that skype flips right and left.. itselves..
Recheck with VLC (look attachment)
Funny.. intern-microphone works with vlc :)
But wont work with Skype or the audio-recorder :lolflag:

[quote=miaerbus]if I put it to sleep (FN+F1/ suspend/ you name it), then sound stops working[/quote]
Well you mean after you reactivated your PC ?
1 solution i found (but don't know if it works for suspend-mode) is changing the tty to make sound working again just do:
```
CRTL+ALT+1
```and then (to come back)
```
CRTL+ALT+7
```Also works if "wine" destroys the sound play...

---

### Post by tobey2k on 2009-08-23
hey kokotoru,

I use Kubuntu 9.04 with the kernel 2.6.31-rc6 and all functions, WLAN, Sound (I dont know if webcam functions, i dont need it.) I use 64bit version...

the flickering is also there with 2.6.28.15.

when I look in the displaysettings the only option is 59.6 Hz... maybe theres the problem?

I installed the latest intel-drivers from this source: [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)

and the flickering is as you said, only on dark background... :-(

thanks tobey

---

### Post by miaerbus on 2009-08-23
> **KoKuToru said:**
> 
Well you mean after you reactivated your PC ?
1 solution i found is changing the tty to make sound working again just do:
```
CRTL+ALT+1
```and then (to come back)
```
CRTL+ALT+7
```Also works if "wine" destroys the sound play...
Yes, after I reactivate my PC, forgot to mention that detail :D
I tried CTRL+ALT+F1 and then CTRL+ALT+F7, still no success :(
(I don't use wine)

Nobody else has these problems?

---

### Post by KoKuToru on 2009-08-23
> **tobey2k said:**
> I installed the latest intel-drivers from this source: [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)

Wow the driver worked Oo ? Didn't for me.. I am using the driver from ubuntu..(but with UXA activated)

> **tobey2k said:**
> 
when I look in the displaysettings the only option is 59.6 Hz... maybe theres the problem?


Hmm.. I don't know I will boot with WinXP and check if can set there an other refresh-rate.. if there is an other we can just update "xorg.conf" with a own refresh-rate (Mean I think this should work xD)

***Edit:***
I checked now WinXP. It also says 60 Hz .. and it's the only option..
But ej.. ***The older you get , the less you will see it .. so just wait a little..*** :D 

Checkout: [http://en.wikipedia.org/wiki/Refresh_rate](http://en.wikipedia.org/wiki/Refresh_rate) Liquid crystal displays
Maybe the Backlight doesn't refresh at the right speed..?

> **miaerbus said:**
> 
I tried CTRL+ALT+F1 and then CTRL+ALT+F7, still no success :(

Hmm.. bad ..

> **miaerbus said:**
> 
Nobody else has these problems?
Be happy that your suspend-mode works.. :lolflag:
When I do it.. my Laptop freezes..:mad: (maybe the extern usb-wlan-stick makes problems..hmm)
=> I can't test it.. sorry

---

### Post by 2541 on 2009-08-24
> **kokutoru said:**
> 


did you reload the modules ? Or restarted the pc..?
```
sudo flip_webcam 2
```did work for me .. I don't think that skype flips right and left.. Itselves..
Recheck with vlc (look attachment)
funny.. Intern-microphone works with vlc :)
but wont work with skype or the audio-recorder :lolflag:

.

No way. VLC, Cheese and Skype mix up the image from the webcam in both webcam-flips.
But I can live with that.
The microphone-thing is more annoying, because I have to use a headset while using skype.
But finally, with all your help the laptop works almost perfect under Ubuntu.
Thanks again for all the advices.

---

### Post by Szunti on 2009-08-24
Hi!

Thanks for the howto. Without you I wouldn't use Ubuntu, and I would have to use only Vista. I just have a minor brightness flickering. I also have it on the BIOS setup screen with the lowest brightness settings. Do you also see it in the BIOS screen or it"s just my notebook?

Thanks 

Szunti

---

### Post by tobey2k on 2009-08-25
hey szunti,

my laptop does the same!!!!!

completely the same!

what Hz do you have in your monitor-settings???

so...

my xorg.conf:

what do I have to change here to set 60 hz?
I&#7743; a big n00b.. :-)
thanks for you help man!
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by Szunti on 2009-08-26
Hi!

I have 60 Hz but its flickering. I don't know if here it can detect 60 Hz then why can't it for you. I followed the Jaunty Intel Graphic Performance Guide's optimal part [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582).

Something about flickering: I installed xbacklight, and setting the backlight with that is indepenent from the backlight keys. Changing the backlight setting with xbacklight make states where my display is flickering harder or stops flickering for some time.

---

### Post by Szunti on 2009-08-26
Hi!
 
 No more flickering for me. Steps:
 
 Clear acpi_backlight=vendor from menu.lst if you put it there, else go to 5,:
 1,  gksudo gedit /boot/grub/menu.lst
 2,  remove acpi_backlight=vendor
 3,  sudo update-grub
 4,  reboot
 5, xrandr --output LVDS --set BACKLIGHT_CONTROL combination
6, go to System/Settings/PowerManagement (or something like that, I use hungarian translation) and make brightness something that is NOT 100% or 50% e.g. 99% (weird, not?)
 If you are as lucky as me it works for you until you reboot. 
7, Report if it work.

If it works, make it permament:
 8, get xbacklight: 
     sudo apt-get install xbacklight
 9, edit /etc/gdm/Init/Default:
    gksudo gedit /etc/gdm/Init/Default
    insert before exit 0:
    xbacklight -set 99
10, You are ready.
11, If you know why can't we set it to 50% or 100% tell me, because I am curious. :)

---

### Post by tobey2k on 2009-08-27
hey szunti,

fist of all I have KDE4 installed, but I configured in each profile (Powersave,Performance...) anything about 30% but it didnt work!Then I starte a Ubuntu 9.04-LiveCD and configured the brightness, but it didnt work, too.


does it still flicker in your bios?
does it flicker in linux at 30 %?

---

### Post by MadTheologian on 2009-08-27
KoKuToru:

Thank you for your help.  My wifi card works and I'm currently compiling ALSA.  :KS  Have not been at these forums for various reasons and glad I stopped by today.

---

### Post by Szunti on 2009-08-28
HI tobey2k,

To be precise I have an ASUS K50IJ-SX003L.
I don't have KDE, but tried 9.04 LiveCD, and it seems I left out something. Sry for that. 
Try this, it worked for me with the live cd, but I would try it in KDE first:

in the console write: 
xrandr --output LVDS --set BACKLIGHT_CONTROL combination
then change brightness with the keys, or in the power management or with xbacklight
And flickering should stop.

if not work:

reboot (may not need, but better to do, i think BACKLIGHT_CONTROL can be changed just once without reboot)
xrandr --output LVDS --set BACKLIGHT_CONTROL native

I prefer combination because it lets me change brightness with the keys in a more convenient way.

It seems to remember the value you set after rebooting, so my last post "make it permament" is enough I think, or even that doesn't need if KDE remember your last brightness setting.  You can see BACKLIGHT _CONTROL value with 
xrandr --props
Power management just needed because it tends to set the brightness if the comp is idle, and changing to 100% ... makes it flickering again.

And don't forget to tell me if it works.
I hope it solve your problem.

And it does flicker in BIOS for me, and 30% is good.

---

### Post by O'bibi on 2009-08-28
Thank you for this topic KoKuToru!:)
I get the sound now, but the flip_webcam didn't work for me: it's still upside down.

---

### Post by shybovycha on 2009-08-28
Thanks A LOT!
Worked for me just perfect!
LET'S ROCK! :guitar:

---

### Post by Szunti on 2009-08-28
HansdeGoede wrote about the upside down webcam problem:

> **HansdeGoede said:**
> Hi,

I've noticed that you and a few others are still trying to fix this with a kernel patch. As I've explained in a comment in this thread before, that is really not the right way to fix this.

The correct way to fix this is to let libv4l the v4l format conversion library of which I'm the author, do the flipping. Ubuntu has been shipping this library for 2 releases now, and the new 0.6.0 release has a table with DMI identification strings for many Asus laptop models which are known to have an upside down webcam and will correct this automatically without any kernel patching necessary.

If you can send me the necessary information for your laptop I'll happily add that to libv4l for the 0.6.1 release, and I'll send you detailed instructions how to get and install the latest libv4l so that you can fix this quick and easy without needing to patch the kernel.

See this post for what information I need and howto get it:
[http://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004886.html)

Please send this information in a mail to:
Hans de Goede <jwrdegoede@fedoraproject.org>

Regards,

Hans

p.s.

Please do not copy and paste the dmidecode output, but use the redirection operator '>' as given as example in the mailinglist post and attach the resulting file to the mail. The dmidecode output may contain trailing whitespace which I need and this whitespace may get lost using copy and paste.

I sent him a mail, and he answered me in a day,  most programs (which are not too primitive) works with these. If someone else follow this, you should first test the latest version: [http://people.atrpms.net/~hdegoede/libv4l-0.6.1-test.tar.gz]("http://people.atrpms.net/%7Ehdegoede/libv4l-0.6.1-test.tar.gz")
Compiling and building instructions on [http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

---

### Post by tobey2k on 2009-08-29
so szunti,

I tried your steps with my installation and it didnt help... and after that I tried the Kubuntu 9.04 64-bit -LiveCD and tried your steps and it didnt function,too...

Im thinking about sending it back to asus.


Greetz Tobey

---

### Post by miaerbus on 2009-09-02
Has anyone tried Ubuntu 9.10? Are these bugs still there?

Now I have also problems with my wired connection. In my dormitory we use wpa_supplicant. So the internet is up for a while, then it goes down.
Then I type:```
ifdown eth0
ifup eth0
```
and eventually comes back. Sooner or later. But this is so annoying! :x

---

### Post by iacchos on 2009-09-03
Thanks, the brightness instructions that you gave solved the brightness problems I was having with my ASUS F6A.

---

### Post by KoKuToru on 2009-09-03
> **miaerbus said:**
> Has anyone tried Ubuntu 9.10? Are these bugs still there?

Now I have also problems with my wired connection. In my dormitory we use wpa_supplicant. So the internet is up for a while, then it goes down.
Then I type:```
ifdown eth0
ifup eth0
```and eventually comes back. Sooner or later. But this is so annoying! :x

well why do you think is the driver at backports ?

I am using an extern wlan-stick works wonderful.
But I hope in some years,months,days there will be a better driver.

---

### Post by sdlabs on 2009-09-12
Most of the fixes work wonderfully, thank you!

(ok so the webcam is still upside down, that that's a minor gripe)

My problem is, the sound fix only works until the next reboot. Am I a complete n00b, did I miss something?

---

### Post by heio on 2009-09-15
I still can't get q/gsynaptics to work, I still get the "set 'SHMConfig' 'true' in xorg.conf" error. I long since added that line, as well as several other xorg.conf entries, none of them work. It sems like it is refusing to detect the touchpad at all, and thusly refuses to run anything that refers to it. This, of course, makes typing somwhat aggravating.
The backlight fix does'nt work either, btw, pressing fn+ backlight key still just turns it way down, and not back up, and it still flickers if its idle for 60 seconds. 
Perhaps this best buy model is more different than previously suspected?

---

### Post by killer1000001 on 2009-09-20
I have the best buy model and all those fixes work for me (dont know about web cam since i dont need it).

The touch pad is a elantech, i have been searching for hours and still cant find a way turn turn off 'tap to click'. I think most of us would be very happy if you show us how to turn off tap to click. Thanks

---

### Post by spanky1023 on 2009-09-24
ok, i just bought this asus k50ij laptop from bestbuy and hate vista.  i just did a fresh install of ubuntu 8.1 and updated to 9.04

i fixed the wireless issue, but now im stuck with no sound

i am COMPLETELY CLUELESS when it comes to this.
is there someone who can hold my hand and walk me through this and give me Step by Step detailed instructions on how to get sound working?

much appreciated

---

### Post by spanky1023 on 2009-09-27
bump

a little help here please ??

---

### Post by spanky1023 on 2009-10-03
nevermind, i figured it out.

---

### Post by KoKuToru on 2009-10-10
Found a easier way to make sound working :)

[FONT=Arial Black][SIZE=4]Sound 2[/SIZE][/FONT]
```

wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install

```

It also wont make problems now if you upgrade to Ubuntu 9.10 !

**BUT !** Don't upgrade to Ubunut 9.10..
**The graphic-driver doesn't work..**

If you upgrade(d) to **Ubuntu 9.10** don't **PANIC** because of black screen ! Just plugin an extern screen (VGA-Port) and you will be able to see your screen!

I hope that the final release will have this bug fixed .. 
Because at **Ubuntu 9.10:**
[LIST]
[*]Sound works by default
[*]WLAN works by default
[/LIST]

But yeah no screen at laptop yet :P just at VGA-Port

---

### Post by IAP on 2009-10-22
This is a very upset user. I have been trying my best to explain to others why Linux is good for you but it is a story I find increasingly hard to believe myself.

I got this Asus K50IJ, I put Ubuntu x64 on it -- much didn't work out of the box, including sound. I spent a couple of days trying things out of this and similar threads, and eventually I got some sound, even if I don't believe a normal laptop user should be made to go through all this.

Today, after  a regular upgrade with Upgrade Manager, I find all sound gone again. I repeated this:

wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install
sudo reboot

and that:

Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere

2. cd <your-download-dir>

3. tar xvf AlsaUpgrade-1.0.21-4.tar

4. sudo ./AlsaUpgrade-1.0.21-4.sh -di

5. sudo shutdown -r 0

and there is no sound still... and I feel that no OS should ever treat anyone like that!

---

### Post by KoKuToru on 2009-10-22
> **IAP said:**
> and I feel that no OS should ever treat anyone like that!
1. Then wait for Ubuntu 9.10

> **IAP said:**
> 
wget [ftp://ftp.kernel.org/pub/linux/kerne...napshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kerne...napshot.tar.gz)
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install
sudo reboot

and that:

Short Alsa-Upgrade script install instructions:

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.21-4.tar
4. sudo ./AlsaUpgrade-1.0.21-4.sh -di
5. sudo shutdown -r 0

2. Read the instruction again, you made it wrong..

> **IAP said:**
> and there is no sound still... 
3.Check out your Master Front settings...

---

### Post by spanky1023 on 2009-10-22
im in the exact same boat !!  after installing some updates this morning, my sound DOESNT WORK... AGAIN !! 

back to the drawing board.

---

### Post by KoKuToru on 2009-10-23
> **spanky1023 said:**
> im in the exact same boat !!  after installing some updates this morning, my sound DOESNT WORK... AGAIN !! 

back to the drawing board.

[B]There was a Kernel-Update.. and like everytime..
New Kernel = New Source[/B]

Because of this, you need to r**ecompile the drivers**..(*But to  tell the truth, I don't know why you need to recompile at new Kernel.. maybe because of memory-adresses ? Hardcoded into the binary ?*)
Just redo "**SOUND 2**" and reboot. Set **Master-Front to 100%** and your sound will work again. 

and for webcam do again "***sudo flip_webcam 2***"

---

### Post by spanky1023 on 2009-10-23
i tried to redo SOUND 2 last night and got nothing.  for fun i just tried it again, and it worked!  dont ask me why, but it works now, and thats all that matters.

also my over volume is Louder now.  not by leaps and bounds, but it is very noticeable.  very nice!

---

### Post by d.renaudot on 2009-10-23
I did what is writen here : [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

It was taken from Sound 1 on the first page. It does the trick for me as it did before.

While I am here, any news concerning the black screen with karmic ?

++

---

### Post by killer1000001 on 2009-10-23
1. Go to this thread. Download the "alsa upgrade" at the bottom of the first post.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

2. These are the instructions from that thread.
Short Alsa-Upgrade script install instructions:
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.21-3.tar
4. sudo ./AlsaUpgrade-1.0.21-4.sh -di
5. sudo shutdown -r 0

3. Explanation of the instructions.
     1. Move the downloaded folder in a folder, such as in your home folder.
     2. Open up the terminal.(It is a application in the menu) Now type where you put the folder, if it is your home folder, type "cd" without quotes, that brings you to your home folder if you are not already in it within terminal. If you type "dir" without quotes, you should see your file listed in the terminal. (google if you still dont get it"
     3. Now type "tar xvf AlsaUpgrade-1.0.21-3.tar" without quotes into the terminal.
     4. Now type "sudo ./AlsaUpgrade-1.0.21-4.sh -di" without quotes into the terminal.
     5. Now type "sudo shutdown -r 0" into terminal to shutdown your computer, or just shut it down the normal way if you want.
4. FINISHED!
     1. Now when you start back up you will have sound.

---

### Post by beav_35 on 2009-10-24
I just download the Karmic RC and I also had the same black screen problem.  To fix it I just had to boot with the i915.modeset=0 option.  I would assume that this problem is caused by the new Intel video driver architecture in Karmic.  Hopefully this will be fixed in the final release.  Other than that it seems to work good on my laptop although I have only tried a live boot for a little while.  The sound, wireless and LCD brightness keys all work by default.  There still seems to be a flickering problem but that can be reduced by dimming the display, choosing a lighter background and some of the other tricks posted in this thread.

---

### Post by KoKuToru on 2009-10-24
> **beav_35 said:**
> i915.modeset=0

As Kernel-parameter ? Well I will try it :)

EDIT:
Works ! nice .. So well yeah good bye to ubuntu 9.04
**I am using now 9.10..** (upgraded from 9.04)

The wlan-driver isn't better than the old ubuntu 9.04 backports-driver.. it's still max. 54 mbit/s and you lose connection very easy. So I am still using my extern wlan-stick :P

---

### Post by d.renaudot on 2009-10-24
Hi guys ! 

Can you explain to a newbie how to install Karmic using "i915.modeset=0" cause it doesn't speak to me at all unfortunaltly.

Thanks in advance !

++

---

### Post by beav_35 on 2009-10-24
This page explains how to change boot options for a live cd and existing installation.  You just need to add a space then "i915.modeset=0" to the end of the boot options.  

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by d.renaudot on 2009-10-24
Thanks !

---

### Post by genfinch on 2009-10-26
> **xphill64x said:**
> 
The third problem seems widespread for Linux users of Skye. The camera can't seem to get any light in/way too dark.
When I use VLC to capture video, it decides to just "turn" the screen to a superdim/off faze. It's weird.


Has anyone found a solution for that problem yet? I just tried to google it, but this forum seems to be the only one that mentions it at all and I found nothing in here. 

Regarding everything else: huge big heap of kudos to KoKuToru for his good work collecting all these fixes. I was really used to 95% of the things I need working ootb under ubuntu, just the way it used to be under Windows way back when. It was kind of a shock when I got this Asus notebook, I must confess... :)

---

### Post by d.renaudot on 2009-10-30
Hi !

I tried to install Karmic, not upgrade, install.

I used the boot options "i915.modeset=0" to have access to the install on the live CD.

The installation seemed to have worked pretty fine, no problem encountered.

The first boot using Grub ended up with the same black screen so I edited the grub file, using "e" to add "i915.modeset=0" before "splash" in the command beginning with "linux" (sorry I am a beginner.)

This seemed to work cause I managed to boot Linux but the PC ended up completely freezed a few seconds later while having to choose the User.

And I have no clue what is going on and how to solve it. I will try to reinstall it and to modify the grub file via the live CD.

If you have any idea...

++

---

### Post by KoKuToru on 2009-10-30
> **d.renaudot said:**
> Hi !

I tried to install Karmic, not upgrade, install.

I used the boot options "i915.modeset=0" to have access to the install on the live CD.

The installation seemed to have worked pretty fine, no problem encountered.

The first boot using Grub ended up with the same black screen so I edited the grub file, using "e" to add "i915.modeset=0" before "splash" in the command beginning with "linux" (sorry I am a beginner.)

This seemed to work cause I managed to boot Linux but the PC ended up completely freezed a few seconds later while having to choose the User.

And I have no clue what is going on and how to solve it. I will try to reinstall it and to modify the grub file via the live CD.

If you have any idea...

++

In someday I will maybe open a "[HOW TO] ASUS K50IJ Ubuntu 9.10"
Because it looks like it's much better installing newer wlan-driver than using the one from ... ubuntu (still testing)
and the old camera flip doesn't work.. hmm need to search new or find why it doesn't work..

but quick instruction for ya:
[LIST=1]
[*]Edit menu.lst of grub (add i915.modeset=0) at the kernel-line or at default options.. 

[*]run sudo update-grub
[/LIST]

It freezes ? bad.. No idea I just upgraded my Ubuntu 9.04 :P

EDIT:
Ubuntu 9.10 uses GRUB2 ?
Then you need to edit /boot/grub/grub.cfg
..
and then run
sudo update-grub2 (I think)

---

### Post by Transmutable on 2009-10-31
> **KoKuToru said:**
> 

EDIT:
Ubuntu 9.10 uses GRUB2 ?
Then you need to edit /boot/grub/grub.cfg
..
and then run
sudo update-grub2 (I think)

Can you be a little more specific? /boot/grub/grub.cfg has a header that says not to edit that file. I can't figure out what section boot options are. Where specifically, in what file, do I add the i915.modeset=0?

EDIT: Is it /etc/default/grub? That file looks more right.
EDIT2: Except that file won't let me make a backup or save.

---

### Post by beav_35 on 2009-10-31
I just upgraded my install to 9.10 and I just had to add i915.modeset=0 to the /boot/grub/menu.lst file under default options.  I then ran sudo update-grub and it works.  It doesn't look like the updater updated grub to v2.  Any ideas why?

---

### Post by KoKuToru on 2009-11-01
> **beav_35 said:**
> I just upgraded my install to 9.10 and I just had to add i915.modeset=0 to the /boot/grub/menu.lst file under default options.  I then ran sudo update-grub and it works.  It doesn't look like the updater updated grub to v2.  Any ideas why?

Because you upgraded...

you can install GRUB2 if you do "sudo apt-get install grub2"

But since I don't know how to set default Kernel-parameters with grub2 .. I am using grub xD

For everyone who installed Ubuntu 9.10 (not upgraded)
You can run "sudo apt-get install grub"

and use the menu.lst edit very easy

---

### Post by KoKuToru on 2009-11-02
> **Transmutable said:**
> 
EDIT: Is it /etc/default/grub? That file looks more right.
EDIT2: Except that file won't let me make a backup or save.

Hm don't know where it's saved but..

you need to open the file with "gksudo gedit" you need root-rights

---

### Post by d.renaudot on 2009-11-02
I managed to install Karmic. I didn't do something special, I just redid the install with the i915.modeset=0 for the live cd and in the grub2 options. I don't understand why it didn't work the first time.

Now I seem to have wifi connection problems. I have to look into that. I will try wicd instead of the default connection manager.

++

EDIT : you have to change /boot/grub/grub.cfg and had "i915.modeset=0" between "quite" and "splash" for Grub2

---

### Post by KoKuToru on 2009-11-03
> **d.renaudot said:**
> 
Now I seem to have wifi connection problems. I have to look into that. 

wifi works really well,when you install the compat-wireless-2.6
It includes the newest Ath9k driver and solves many connection problems.. Don't know why Karmic doesn't include the "newest" driver..

---

### Post by Transmutable on 2009-11-04
I used ```
gksudo gedit /boot/grub/grub.cfg to open grub.cfg
```
I added "i915.modeset=0" between "quiet" and "splash"
When I hit save, it told me ```
Could not save /boot/grub/grub.cfg 
You are trying to save the file on a read-only disk. Please 
check that you typed the location correctly and try again.
```

While annoying, it's not really that bad. I can just temporarily change it and since I rarely ever shut down my laptop it's not that big of a deal.

But now I have a new problem!

While I am STOKED that sound actually works, it ain't perfect. Plugging in headphones or external speakers doesn't do anything. I can go into System -> Preferences -> Sound -> Output and change Connector to Analog Headphones and that turns off the built-in speakers, but doesn't output anything in what's plugged in.

Also, switching between applications with sound doesn't work well/at all. Going from music in Banshee to a YouTube video in Firefox? Forget about it.

---

### Post by d.renaudot on 2009-11-04
For the grub.cfg, I had the same problem. I thought it was just me. I just did :

[php]sudo chmod 777 /boot/grub/grub.cfg

sudo gedit /boot/grub/grub.cfg[/php]I assume there is a more elegant way to do it, but I am a beginner. Grub2 is faster than Grub, so you can shut down your system without it being a bother.

Another thing : be careful if you try to install the compat-wireless-2.6. I tried without doing exactly what I was doing and ended up reinstalling my system... A full tuto would be appreciated.

++

---

### Post by KoKuToru on 2009-11-04
> **d.renaudot said:**
> 
Another thing : be careful if you try to install the compat-wireless-2.6. I tried without doing exactly what I was doing and ended up reinstalling my system... A full tuto would be appreciated.

Do you really wan tme to copy the README here ?

But okay...

0. Make sure you installed the important packages like: 
1. Open a terminal
2. go to the folder where you extracted compat-wireless-2.6 (with cd command)
3. Select your driver
[INDENT]```
./scripts/driver-select
```[/INDENT]
4. Read the instruction or just run
[INDENT]```
./scripts/driver-select atheros
```[/INDENT]
5. Build it
[INDENT]```
make
```[/INDENT]
6. Install it
[INDENT]```
sudo make install
```[/INDENT]
7. Read again .. and use the command to reaload the driver.. or just reboot..

---

### Post by Squier13 on 2009-11-06
i upgrade to ubuntu 9.10...
black screen...
help me. laptop asus k50ij, sounds is 
no image.

p.s. 2.28.16 works

p.s. sorry

[PHP]I've added "i915.modeset=0" before splash in /boot/grub/menu.lst
title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid c9f6e5c3-90db-4869-a00f-11de1823796a
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=c9f6e5c3-90db-4869-a00f-11de1823796a ro i915.modeset=0 quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet[/PHP]

---

### Post by moosesoom on 2009-11-08
> **heio said:**
> I still can't get q/gsynaptics to work, I still get the "set 'SHMConfig' 'true' in xorg.conf" error. I long since added that line, as well as several other xorg.conf entries, none of them work. It sems like it is refusing to detect the touchpad at all, and thusly refuses to run anything that refers to it. 

Have the same problem on my X5DIJ (with K50 motherboard). It seems our touchpad is the Elantech one. I've read there's a gsynaptics-elantech package in some EEEpc repository, don't know if it works with Ubuntu.

Just found the driver's page: [http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)
I wrote to the driver's author, hope he (or some other gentle kernel hacker) help us to solve the touchpad problem.

---

### Post by mutrax on 2009-11-09
On a fresh karmic install, the keypad numbers don't seem to work? anyone had this problem?

---

### Post by moosesoom on 2009-11-09
> **mutrax said:**
> On a fresh karmic install, the keypad numbers don't seem to work? anyone had this problem?

It'seems ok to me. Have you tried to press "NUM LK" key to activate'em?

---

### Post by mutrax on 2009-11-10
> **moosesoom said:**
> It'seems ok to me. Have you tried to press "NUM LK" key to activate'em?

Yes I did...:lolflag:

---

### Post by cakekong on 2009-11-10
How do you do with webcam ? My webcam is retourned with Karmic ...

---

### Post by mutrax on 2009-11-11
> **cakekong said:**
> How do you do with webcam ? My webcam is retourned with Karmic ...

This is explained in the first post of this thread... However, for me this fix doesn't work anymore in karmic....:(

---

### Post by cakekong on 2009-11-11
I know. But with karmic, that doesn't work ... With Juanty was OK, not with Karmic.
(sorry for my english)

---

### Post by moosesoom on 2009-11-11
My flipped webcam returned to normality after following the instructions at this url:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/")

---

### Post by moosesoom on 2009-11-11
A new mistery about audio settings:

At boot with headphone unplugged I can hear everything from pc speakers.
When I plug in headphone, music disappear from speakers and comes from headphone (and that's good)

Now the mistery....if I try to get more volume using Sound Preferences applet, suddenly speakers turn on and music comes from both headphone and speakers.

Can somebody please give me some clues?

---

### Post by cakekong on 2009-11-11
> **moosesoom said:**
> My flipped webcam returned to normality after following the instructions at this url:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)
Yeah !! Thx !!

---

### Post by mutrax on 2009-11-12
> **moosesoom said:**
> My flipped webcam returned to normality after following the instructions at this url:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/]("http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/")

Now that was simple! thanks!

---

### Post by moosesoom on 2009-11-12
> **moosesoom said:**
> Have the same problem on my X5DIJ (with K50 motherboard). It seems our touchpad is the Elantech one. I've read there's a gsynaptics-elantech package in some EEEpc repository, don't know if it works with Ubuntu.

Just found the driver's page: [http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)
I wrote to the driver's author, hope he (or some other gentle kernel hacker) help us to solve the touchpad problem.

I better browsed arjan's site so I discovered his driver is already in Linux Kernel since 2.6.28.
It works with Elantech's type 1 and 2....it seems K50's one is from another type not known to the driver.

Still searching for the solution.... :(

GOOD NEWS!!!! Arjan wrote to me....we'll begin to debug Asus K50's Elan Touchpad.

---

### Post by Szunti on 2009-11-14
> **moosesoom said:**
> A new mistery about audio settings:

At boot with headphone unplugged I can hear everything from pc speakers.
When I plug in headphone, music disappear from speakers and comes from headphone (and that's good)

Now the mistery....if I try to get more volume using Sound Preferences applet, suddenly speakers turn on and music comes from both headphone and speakers.

Can somebody please give me some clues?

Partial solution for me in Karmic, that auto-mute speakers if headphone plugged in. 

In sound preferences, go to the output tab and change connector (? i don't know the exact name I use hungarian translation, it's the combo box on the bottom) to Analog Headphones.

Now use alsamixer from terminal and increase Headphone and PCM to 100%, and mute Front with m (if not muted already). Changing Master Front and the muted Front, while leaving muted change the volume. 

Note: If I move Master Front above appr. 70% I have a constant noise from my headphone, in that case lower Master Front, and increase Front's volume.

Problems: 
1) The sound volume applet change the Headphone Channel, this changes nothing in the real volume. You can use alsamixer to change volume.
2) After logging in the Front volume will be 0%

To make everything work as it should, we should contact ALSA developers I think, or there might be some settings of alsa which help but docs on those are too difficult for me.

---

### Post by mutrax on 2009-11-22
> **mutrax said:**
> On a fresh karmic install, the keypad numbers don't seem to work? anyone had this problem?

Fixed! 
"use nupad keys as mouse" was default enabled in accesibility options. disabling this did the trick.

---

### Post by tiger0383 on 2009-11-26
ok upgraded from 9.04 to 9.10

ZG5 aspire one AOA105

now been having the problems with the wireless dropping connection under full load. Now here is the weird part of it to throw into the mix, I am not an expert with ubuntu or linux for that matter but when it drops under load, i noticed that it sort of freezes before it fully dropped. I am using Wicd for my connection manager, well when it pauses, if i hit the refresh button in the Wcid program 3 times, it resumes :confused: Maybe this will help someone with some more knowledge on this matter and hopefully fix this problem once and for all. If i use a wired connection, not a problem will go strong no matter how much load i put it through just wireless has problems. I have did not have an issue with sound or with display like many others. :tongue:

---

### Post by moosesoom on 2009-11-28
> **tiger0383 said:**
> ok upgraded from 9.04 to 9.10

ZG5 aspire one AOA105



So, did you see this is a thread about Asus K50?

---

### Post by KoKuToru on 2009-12-02
Found a better way than editing grub or grub2
Just install newest kernel :)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/)

and magic will happen.. Graphic output will work and the boot-logo wont be streched to widescreen :popcorn:

---

### Post by Szunti on 2009-12-02
> **tiger0383 said:**
> ok upgraded from 9.04 to 9.10

ZG5 aspire one AOA105

now been having the problems with the wireless dropping connection under full load. Now here is the weird part of it to throw into the mix, I am not an expert with ubuntu or linux for that matter but when it drops under load, i noticed that it sort of freezes before it fully dropped. I am using Wicd for my connection manager, well when it pauses, if i hit the refresh button in the Wcid program 3 times, it resumes :confused: Maybe this will help someone with some more knowledge on this matter and hopefully fix this problem once and for all. If i use a wired connection, not a problem will go strong no matter how much load i put it through just wireless has problems. I have did not have an issue with sound or with display like many others. :tongue:

I had the same problem with K50IJ until I installed the linux-backports-modules-karmic package. It seems ok now.

---

### Post by cakekong on 2009-12-02
Do you have sound problems until Karmic ?

---

### Post by moosesoom on 2009-12-04
> **KoKuToru said:**
> Found a better way than editing grub or grub2
Just install newest kernel :)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/)

and magic will happen.. Graphic output will work and the boot-logo wont be streched to widescreen :popcorn:

Not a white magic anyway....it seems alrite but sometimes there's a strange flickering in lower part of LCD.

Turning back to 2.6.31.

---

### Post by KoKuToru on 2009-12-04
> **moosesoom said:**
> Not a white magic anyway....it seems alrite but sometimes there's a strange flickering in lower part of LCD.
There is Oo ? Sorry but it doesn't here..
I extra installed a full new Ubuntu 9.10 ..
Did you upgrade from Ubuntu 9.04?

---

### Post by moosesoom on 2009-12-04
> **KoKuToru said:**
> There is Oo ? Sorry but it doesn't here..

Did you mean OpenOffice or something else?

> I extra installed a full new Ubuntu 9.10 ..
Did you upgrade from Ubuntu 9.04?

Fresh 9.10 install, my pc was brand new.

---

### Post by KoKuToru on 2009-12-07
> **moosesoom said:**
> Did you mean OpenOffice or something else?
the LCD flickering...

---

### Post by WestCity on 2009-12-09
> **Szunti said:**
> I had the same problem with K50IJ until I installed the linux-backports-modules-karmic package. It seems ok now.
I installed that package. Still loosing wireless connection with "Transmission BitTorrent Client". After computer restart it works, but again for short time only. Btw., when I use "Firefox" to browse internet - no problems. 
K50IJ + upgraded from Jaunty to Karmic.
Maybe clean install would help?

Edit: I am loosing connection than downloading files with "Firefox"...

So, the problem is not with a program, that is used to download files, but somethere else.

---

### Post by ferral-cat on 2009-12-28
In reference to the WiFi:

Does the Wifi indicator light stay lit on the laptop itself?

Does pressing Fn + F2 toggle the WiFi on and off?  Does the indicator light itself also toggle on and off properly?

Thanks in advance guys.

---

### Post by moosesoom on 2009-12-28
> **ferral-cat said:**
> In reference to the WiFi:

Does the Wifi indicator light stay lit on the laptop itself?

Yes, it's turned on at boot.

> 
Does pressing Fn + F2 toggle the WiFi on and off?  Does the indicator light itself also toggle on and off properly?


Fn+F2 actually toggles wifi on and off....but sometimes (as it happens after suspend/resume) wifi link doesn't seem able to connect to any access point.

I usually re-enable the link with following commands sequence:

rmmod ath9k
rmmod ath
rmmod mac80211
rmmod cfg80211
modprobe ath9k
echo 1 > /sys/devices/platform/asus_laptop/wlan

At this point I can connect to any access point through wicd.

Wifi led stays on despite link is on or off.

---

### Post by ferral-cat on 2009-12-28
@moosesoom:

Thank you very much for your detailed response.  I was concerned that when the WiFi indicator light stays on that the battery will drain very quickly.  

Is this the case with ASUS K50IJ ?

---

### Post by moosesoom on 2009-12-29
> **ferral-cat said:**
> @moosesoom:

Thank you very much for your detailed response.  I was concerned that when the WiFi indicator light stays on that the battery will drain very quickly.  

Is this the case with ASUS K50IJ ?

I've just found how to fix this bug:

in /usr/share/acpi-support/state-funcs file

change line 9 from
if [ -d $DEVICE/wireless ]; then
to 
if [ -d $DEVICE/wireless ] || [ -d $DEVICE/phy80211 ]; then


change line 107 from
test -w /sys/devices/platform/asus-laptop/wlan && echo -n "$action" > /sys/devices/platform/asus-laptop/wlan
to
test -w /sys/devices/platform/asus_laptop/wlan && echo -n "$action" > /sys/devices/platform/asus_laptop/wlan

According to powertop's output it seems there's no such difference in power consumption with led turned on or off.

(anyway I've found a previous remark of this bug at [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/451108](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/451108) )

uh-oh....little problem, it seems the acpi scripts have no write permission on /sys/devices/platform/asus_laptop/wlan, so the automagical led power toggle is not working when invoked by Fn+F2 shortcut.

---

### Post by Szunti on 2010-01-02
> **WestCity said:**
> I installed that package. Still loosing wireless connection with "Transmission BitTorrent Client". After computer restart it works, but again for short time only. Btw., when I use "Firefox" to browse internet - no problems. 
K50IJ + upgraded from Jaunty to Karmic.
Maybe clean install would help?

Edit: I am loosing connection than downloading files with "Firefox"...

So, the problem is not with a program, that is used to download files, but somethere else.

I found another problem with wifi, it disconnected every 2 mins for a couple of seconds, due to Network Manager's background scanning (if I interpreted well from the googling it's some problem with ath9k driver). "wpa_supplicant[1142]: CTRL-EVENT-SCAN-RESULTS" in syslog and daemon.log every 2 mins show this.
installing wicd (I installed the latest stable version using their repo [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)) solved this problem, it doesn't do background scanning.

---

### Post by neoroses on 2010-01-27
rite, turns out what is happening, the main laptop speakers dont go off when i put the head phone jack in? any ideas? i have top mute it at the moment.

thanks )

---

### Post by neoroses on 2010-02-04
well guys, it would a[[ear that this laptop works sweet out of the box with 9.10. just letting you know.

---

### Post by jenaniston on 2010-02-04
> **2541 said:**
> 

. . . Ubuntu is the very first Linux-Distro to bring a single beep out of my notebook...



I will second this . . . Ubuntu 9.04 on a Sharp AL27 laptop . . .

though in my case it is a hopeless Windows XP OS on the hard drive primary partition (with the Windows recovery utility doing*** itself*** in) 
that I am trying to rescue files off, before I do the Linux full install.

---

### Post by masterkorp on 2010-03-05
> **KoKuToru said:**
> 
[FONT=Arial Black][SIZE=4]Sound 2[/SIZE][/FONT]
```

wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
sudo make install

```



I found an error in the **make** command, this is the last lines of the output:
```

ch_cmedia.o
  CC [M]  /home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda/patch_conexant.o
In file included from /home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda/patch_conexant.c:3:
/home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda/../../alsa-kernel/pci/hda/patch_conexant.c: In function ‘cxt5051_init_mic_port’:
/home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda/../../alsa-kernel/pci/hda/patch_conexant.c:1774: error: implicit declaration of function ‘conexant_report_jack’
make[4]: *** [/home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda/patch_conexant.o] Error 1
make[3]: *** [/home/masterkorp/Transferências/sound/alsa-driver-unstable/pci/hda] Error 2
make[2]: *** [/home/masterkorp/Transferências/sound/alsa-driver-unstable/pci] Error 2
make[1]: *** [_module_/home/masterkorp/Transferências/sound/alsa-driver-unstable] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [compile] Error 2

```

Any help? 
I am using ubuntu 9.10

---

### Post by Transmutable on 2010-05-09
Has anyone tried upgrading to Lucid yet? Rather hoping to avoid surprise mystery black screen this time around.

---

### Post by mutrax on 2010-05-13
Running lucid since the beta.. no issues whatsoever now you mention it... Well some software related glitches that got ironed out in the final release.

:)

---

### Post by mykrob on 2010-05-14
Running Lucid on mine as well. I installed a slightly older Atheros wifi card before installing, I keep a couple extra that I know work flawlessly in Linux.

I am having the speaker problem though. When I plug in my headphones, the speakers still play :(

---

### Post by spanky1023 on 2010-05-17
im really wanting to try Lucid, but am a little timid.  has anyone else run into issues yet?  aside from the headphones not working? 

maybe there arent enough of us asus k50ij people out there

---

### Post by Transmutable on 2010-06-10
It's been really good for me so far. Installation was super smooth. Haven't tried headphones, but an annoying sound issue I had with Firefox seems to have cleared up. One of my favorite things about Ubuntu is things generally get better with each release. :)

---

### Post by 2541 on 2010-06-11
> **spanky1023 said:**
> im really wanting to try Lucid, but am a little timid.  has anyone else run into issues yet?  aside from the headphones not working? 

maybe there arent enough of us asus k50ij people out there

With Lucid my screen keeps flickering a little bit.
Everything else works out of the box.

---

### Post by jasonp03 on 2010-07-06
I have the "BestBuy" version of this laptop, and everything works fine except when I plug in headphones, the sound still comes out of the speakers in the laptop too; the speakers don't mute when headphones are plugged in. 

any suggestions?

btw im using Ubuntu 10.04

---

### Post by gordamemson on 2010-09-25
I'm having the same issue's with the screen bugging out and the sound playing through the headphones and the main speakers in 10.4 on my k5oij,  i've been searching for fix's but none of them appear to pertain to this model or version.  If anyone has a link to a relevant thread i would be most pleased.

---

### Post by Pan0ramix on 2010-09-28
one year after this post and still have the cam issue around!
It seems like no patch were added in new Ubuntu releases. I have this problem running ubuntu Lucid. I'm going to try it... we'll see

---

### Post by windsxs on 2010-10-18
have a problam... what to do?
```
root@vygandas-laptop:/bin# flip_webcam 1
bash: /bin/flip_webcam: cannot execute binary file

```

---

### Post by masterkorp on 2011-04-25
> **windsxs said:**
> have a problam... what to do?
```
root@vygandas-laptop:/bin# flip_webcam 1
bash: /bin/flip_webcam: cannot execute binary file

```

You need to give permission to that file to be executable.
```

man chmod      

```
Read this to get all the info

---

