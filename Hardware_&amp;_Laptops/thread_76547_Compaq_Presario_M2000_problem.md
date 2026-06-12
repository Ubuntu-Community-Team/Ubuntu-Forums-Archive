---
title: "Compaq Presario M2000 problem"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by JuanC on 2005-10-15
Hi ,

I downloaded and install Kubuntu 5.10 , after install the laptop freezes.

I do the trick of this thread :
[http://ubuntuforums.org/showthread.php?t=69367](http://ubuntuforums.org/showthread.php?t=69367)

But i can't watch videos over Kaffeine or VLC , when i try to play a video , my laptop reboot.

I also can't know , how to make volume buttons (+,-,mute) works from laptop?

---

### Post by alvonsius on 2005-10-15
Phew ... I got a compaq M2232AP and after reading your post, i feel a little afraid to install Breezy. But I'll give it a try ... at least when i go freeze just run back to hoary. 

About your problem with the 3 special button, have you ever try using application called hotkeys?It works on my Hoary. I forget where is the link to the app webpage or manual, but you can start from here [http://ubuntuforums.org/archive/index.php/t-6204.html](http://ubuntuforums.org/archive/index.php/t-6204.html)

---

### Post by JuanC on 2005-10-16
Thanks , hotkeys works fine.

Well now ,  if i find a solution for the VLC problem and get my graphic card 3D acceleration , ubuntu makes my so happy.

---

### Post by elemental_silver on 2005-10-16
Thank goodness I'm not the only one with the M2000. I tried an install of the previous version of Ubuntu only to have heartbreak. I'm waiting for the new version to come in, but when it does, I'll try to help fight to good fight with you. It seems that a lot of the problem orients around the video card, cause I couldn't even get past the login screen when I tried installing it. >_<

Good luck and post all findings in here, please! I'm not that experienced with Linux and Ubuntu so every piece of info helps.

---

### Post by alvonsius on 2005-10-17
Hehehe, the same happened to me. I've been trying to find someone with M2000 and now i found them ..

About hoary, if you are using 915GM graphic card, it currently not supporting 915GM graphic card, so you must follow this link [http://www.bram.be/travelmate_4651lci.html](http://www.bram.be/travelmate_4651lci.html) to install new driver so Hoary could recognize it, or if you don't wanna do such thing you can just change the driver of xorg into "vesa" (but of course you won't get 3d accel). Just change this line at /etc/X11/xorg.conf
Section "Device"
...
Driver          "vesa" ==> old value was 'i810'
...

and add this 

Section "Monitor"
...
HorizSync       30.0 - 55.0
VertRefresh     50.0 - 120.0
...


PS: I think the graphic problem was solved on Breezy ...

---

### Post by alvonsius on 2005-10-17
Forgot to ask. JuanC, is there any other problem like touchpad or sound or wireless when you using Breezy ???
And to all who using M2000, when using Hoary is there any problem with the DHCP wireless? Coz i can't connect to any other AP using DHCP. Maybe i made a "stupid mistake i don't know how to fix it now" and if you guys could connect using DHCP then maybe i think to re-install 5.04, coz Breezy seems to much buggy ...

---

### Post by elemental_silver on 2005-10-21
Not that I can tell, but I can't get far enough to even try my wireless. The touchpad and sound works fine, though... but I'm STILL waiting for my CDs to come in, so I haven't tried the new version.

---

### Post by sigma2805 on 2005-10-21
hi,
i have an m2010us and i'm not having any major issues. the only issue i have is that the mute button light doesn't turn on when the volume is muted :)

---

### Post by alvonsius on 2005-10-21
I finally install Breezy on my notebook. Phew, i never thought that breezy was more difficult to handle than hoary. The mp3 issue, dvd playback, adaptation to adept (finally back to kynaptic) and more (somehow it's not notebook specific, it's breezy specific issue, you can find them on another thread) make me feel little bit 'wanna go back to hoary'. But after a few upgrades and read some thread i finally have my breezy on the action. X driver is good, sound good (i must download xine and remove gstreamer to play mp3 smooth), wireless good (altough i havent try the DHCP), and more. One minor problem i still got now is the GL screensaver is not fullscreen. It only fill 1/4 part of my monitor. Hopefully there's update for this in the future.

Humm, i'll better try the DHCP soon ...

---

### Post by elemental_silver on 2005-10-31
Any new reports from the front line about the M2000 problems?

---

### Post by alvonsius on 2005-11-01
[QUOTE=elemental_silver]Any new reports from the front line about the M2000 problems?[/QUOTE]

Uh oh, almost forget to report my DHCP research. Yup, as I expected the DHCP works (hurray, now I can connect from everywhere!!!! :razz: ). There is no other issue about M2000 that majory effect my works (or fun). Humm, forget one thing, don't forget to update your Breezy when you finished your installation. It helps on media recognizion and other else (dunno what but I positively think yes, it affect somehow :D). Last, the card reader still not functioning  :(

PS: I currently write my experience with Kubuntu on my blog, visit it on [http://kuduisolinux.blogspot.com]("http://kuduisolinux.blogspot.com")

---

### Post by sigma2805 on 2005-11-01
Hey everyone,
just as a heads up, make sure you upgrade your wireless drivers from the compaq website. The new drivers i believe support WPA2, a stronger wireless standard. Or, don't upgrade if you aren't planning on using WPA2.

---

### Post by ximosoft on 2005-11-02
I have problems too with my laptop, first with the ati driver ( i changed manually to vesa), then once i got configured everything, my laptop battery die, when i plugged to ac, and start laptop, x-window doesn't start, some trouble with synaptics touchpad?!??.

Anyone had the same problem?, i cannot make it work again. 

PD: Why i cannot login with root user on user screen? ( Says that root logins are not acepted).

Thanks

Edit:
my /dev/input and some more folders are gone, and i cannot reinstall them from pakages because dev package is missing... O_Ou

---

### Post by cokhavim on 2005-11-07
i've gotten Ubuntu Breezy running perfectly on my compaq presario m2105.  sound, wifi, ati stuff, everything! (except for skype).  shouldn't be too different from m2000.  anyway, i typed up my notes for everything i did.  my notes were for myself only, but they should be decipherable.  if you want my notes, give me a PM and i'll send you my 8 pages of fun! :)  

jo

---

### Post by elemental_silver on 2005-11-29
Well, still no sign of my unbuntu CDs any time soon. So, how about a progress check on all those M2000s out there? Running smoothly?

---

### Post by rykel on 2006-04-09
[QUOTE=JuanC]Hi ,

I downloaded and install Kubuntu 5.10 , after install the laptop freezes.

I do the trick of this thread :
[http://ubuntuforums.org/showthread.php?t=69367](http://ubuntuforums.org/showthread.php?t=69367)

But i can't watch videos over Kaffeine or VLC , when i try to play a video , my laptop reboot.

I also can't know , how to make volume buttons (+,-,mute) works from laptop?[/QUOTE]

hi,

i know i am late to this thread, but i installed ubuntu dapper drake flight 4 on this m2000 i am typing at rite now, and the good news is tat the +/-/mute volume buttons at the top of the keyboard works out of the box!

additionally, the battery monitor also works.

i managed to download **fglrx** (ati 3D driver) from synaptic package manager (using both Universe and Multiverse repositories) to run 3D games as well.

[INDENT]remember to do the following after installing fglrx in synaptic:
[B]sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
sudo dpkg-reconfigure xserver-xorg[/B] - choose fglrx as ur video driver
**sudo fglrxconfig**
[/INDENT]

note that currently, the above fglrx instructions may NOT work with flight 6, as i just smart upgraded my system, and fglrxconfig seems to have "disappeared"...

lastly, to watch dvd etc. simply install **totem-xine** using synaptic again, and follow the instructions [here (Ubuntu Official Wiki "Restricted Formats")]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedformats%29") to install the codecs needed to watch some proprietary formats.

---

### Post by vic_ishi on 2006-06-13
Cant install Audio Driver, Ive downloaded driver from [www.hp.com](www.hp.com), but when Intalling it says that Conexant AC-Link Audio Failed. what can I do???:confused:

---

### Post by SuperRyo on 2006-06-17
[QUOTE=vic_ishi]Cant install Audio Driver, Ive downloaded driver from [www.hp.com](www.hp.com), but when Intalling it says that Conexant AC-Link Audio Failed. what can I do???:confused:[/QUOTE]

Hi, I had this problem too at first. Be sure to install the Conexant CX20468-31 AC97 Audio Driver EQ first, next go to Start>Settings>Control Panel>System, click on the Hardware tab, then Device manager.. You should see a bunch of other devices with a yellow question mark. Under that select something that says audio, or unknown audio or something like that and then click on the uninstall icon at the top of the Device manager. Now try running the Conexant CX20468-31 AC97 Audio driver... the actual driver installation from the HP site will indicate that it fails, but the windows hardware detection wizard should come up while you are installing, click next on the wizard and that will install the driver properly. Ignore the failed message as long as the windows hardware wizard installs it okay. To be sure you installed it okay, try playing a sound. Hope this helps

---

### Post by niceguy123 on 2007-09-07
Hi,

Sorry for digging out this ancient thread, I've just started using Ubuntu  on my desktop and would like to install on my loptop as well. I too have  Compaq Presario M2000. I tried (a couple of times) to install with the same disk I used for the desktop up it keeps freezing somewhere after the Ubuntu screen comes up.  Should I be using a different distribution for the laptop? (I'm not sure about AMD, never gave it much thought up to now).

Thanks

---

### Post by niceguy123 on 2007-09-10
I got Kubuntu running on the M200 on a live disk (apparently there was an issue with gnome), but then it gets stuck in the stages of installation (that runs very slow anyway).

---

### Post by zipperback on 2007-09-10
> **niceguy123 said:**
> Should I be using a different distribution for the laptop? (I'm not sure about AMD, never gave it much thought up to now).
Thanks


I have an Acer Aspire 5050-3371 which has an AMD processor and Ubuntu works just fine on it.

Download the current Feisty 7.04 release of Ubuntu and boot the LiveCD to test it out.

Perhaps you could post the output of:  lspci -v

and let us see what we are actually dealing with. This will help us, help you get things working.

- zipperback
:guitar:

---

### Post by niceguy123 on 2007-09-12
I've got Xubuntu running on my Compaq Presario M2000 after a couple of days trying with Ubuntu and Kubuntu.

---

