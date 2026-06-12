---
title: "Asus A6 series (A6VA)"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by lazy74 on 2006-02-21
Hello,

Here is a quick summary on how I got Ubuntu 5.10 work on my Asus laptop, *thanks* to various posting found on this forum. 

**snd-hda-intel**
After installation the boot process hangs on the usual hotplug problem:
*Starting hotplug subsystem*
Thanks to *Wouterr *for the tip: deactivate the Audio component in the BIOS (menu 'Security', option 'Audio/Modem' -> LOCK).
Next boot in recovery mode. 
Edit the file /etc/hotplug/blacklist and append  'snd-hda-intel' on a new line.
Reboot again and back in the BIOS, 'UNLOCK' the Audio/Modem component.

**Black screen on X11 startup**
The boot process now completed but I finally got a black screen.
As mentioned in many posts, I had to install the ATI drivers.
You need to follow all the steps described in the (great) starter guide:
[http://help.ubuntu.com/starterguide/C/ch04.html#installatidriver]("http://help.ubuntu.com/starterguide/C/ch04.html#installatidriver")
**but** since you cannot execute Synaptic, you need to manually install the driver. Replace step 1. with the following:
[LIST]
[*]Press "Ctrl+Alt+F1" to get to the terminal prompt
[*]Log in with the user defined during installation
[*]Use apt-get to install the driver: ```
sudo apt-get -V install xorg-driver-fglrx
```
[/LIST] 
Now you need to follow the rest of the instructions from the starter guide.
Beware of typos or you'll end up banging your priceless laptop on the wall in frustration.

Hope it helps.
/L.

---

### Post by bruno.vitorino on 2006-02-21
thanks a lot, i was almost desperating... i'll try to follow the steps, and then i'll post my results :D

---

### Post by bruno.vitorino on 2006-02-21
yyeeehhh it worked great!! thanks a lot :D

---

### Post by lazy74 on 2006-02-22
Great!
Actually I later found this great site ! [french]
[http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA]("http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA")

---

### Post by bruno.vitorino on 2006-03-01
hi, i finaly folowed the french tutorial and it works realy good. Now i have the oficial Ati driver and Sound :D
thanks

---

### Post by pstracha on 2006-03-09
Hi,

I want to thank lazy74 for posting this solution. I just purchased an Asus Z83V and experienced the same problem. The solution specified worked perfectly and I'm now up and running with Ubuntu! :D

---

### Post by arkangel on 2006-04-02
the french site was indeed good,

any idea how to  have the video camera  (Asus A6Va bison ...) working ;)

---

### Post by lazy74 on 2006-04-03
Sorry, I don't know either :-( I'm not using it under linux but it would be nice to get it working too!

---

### Post by arkangel on 2006-04-05
Hello people 

for you all that have an Asus A6Va,   after installing  the ati drivers (X700 128 mb)   i notice  something  really weird,  if i log out instead of   seeing  the gdm welcome screen  the screen start to brigth like some kind of flourecence , have you observed  this effect  :S

---

### Post by lazy74 on 2006-04-13
Arkangel,
I have not noticed anything on the screen. 
Regarding the webcam, it seems the related open-source driver project is stalled.

---

### Post by arkangel on 2006-04-14
i have installed the following ati drivers 
8.19.10 
8.21.7
8.22.5
at last   8.23.7
according to  ubuntu , gentoo,  and a french site  wikies

all seems to be ok  , in all cases   no problem to install , no problem to configurate and  to test , 
in another forum i was told (flgrx forum)  that seems to be bios issue  , i update to the last bios i could found in asus web site  (asus support "we do not support linux in our laptops"  so why did  they ask me in the form; which is your OS. Bad support for a Top Laptop ! :mad: )   a guy  with the same report (but in a clevo solved so i followed his steps as well ) i disabled  kernel  agp  i put flgrx in the blacklist, etc ...

always  i get the same effect (see picture ) but at random, my screen is really moody. and always when shutting down or restarting the X server (shutdown  , reboot , logout , ctl+alt+bksp ) so actually i can work with no problem , but it is scary
Also in asus  forum 2 guys report this , but  in windows  and when they started the machine the first time (defective screen ) , i was using these computer for 6 months  from  9 to 7 pm   every day(windows and linux) , and i only have this problem with  the flgrx driver :confused: 

either it is  bug or my screen is defective (i doubt it 90 %) or  a config issue

could you please  post your xorg.conf ?

---

### Post by lazy74 on 2006-04-18
[QUOTE=arkangel]could you please  post your xorg.conf ?[/QUOTE]

my xorg.conf file (attached)

---

### Post by lrovernut on 2006-04-19
thanks for the tip qbout the security setting, it got my install moving again, it'll do untill dapper is released

Eddie

---

### Post by bruno.vitorino on 2006-05-25
hi, i wonder if anyone has been able to set up dual head monitor with horizontal spanning? i've been able to clone the screen but i not to span.

---

### Post by rjcsc on 2006-05-25
any news about have the video camera working?

---

### Post by rjcsc on 2006-05-27
*bump*

---

### Post by Deomanh on 2006-06-05
Greets

To my knowledge there's currently no driver for the builtin camera, however there's this recent project I became aware of that is attempting to make just that at [http://m560x.x3ng.com/](http://m560x.x3ng.com/)
If you want to lend a hand in the development process, just pay them a little visit and check it out.

Other than that, I wonder if anybody has solved the Fn+F2 (wireless) thingy yet? Or actual audio multiplexing? Or even perhaps a Windows-like powersave key functionality, with configurable profiles such as Gaming, Office, Presentation etc.? Hmm.. maybe I'll just make a more comprehensive listing:

- "LCD display error" (or something) with KDE and KMilo (i.e. without needing to shutdown kmilo)

- Infrared? I tried with a palmpilot, but since it's a weird new model I couldn't assert whether or not the problem was with the IR port

- builtin microphone?

- anyone test TVout yet?

- or cardreader?

- or pcmcia?

- what about the modem?

- firewire?

- line in / mic in?

---

### Post by bruno.vitorino on 2006-06-06
Well, the builtin microphone works well and line in / mic in too. As for the other ones i havent tried yet.

---

### Post by an.echte.trilingue on 2006-06-07
I just did a similar thread to this for kubuntu dapper on this system if anyone is interested.

Edit:  [link]("http://www.ubuntuforums.org/showthread.php?t=191655")

---

### Post by walding on 2006-07-08
I have the same laptop.  I have TVOut working (NVidia driver works fine); the card reader works without any probs.

Suggest we post back here if any other solutions are found!

---

### Post by walding on 2006-07-08
I forgot:  KLaptop works well for battery modes.  I'd like to be able to configure the button to switch modes.

---

### Post by Cisto on 2006-07-19
Take a look to this thread:

[http://www.ubuntuforums.org/showthread.php?t=191655&highlight=a6va](http://www.ubuntuforums.org/showthread.php?t=191655&highlight=a6va)

---

