---
title: "HP remote control help"
date: 2008-08-21
forum: General Help
---

### Post by pretobomba on 2008-08-21
So, I have a Hp dv5-1002nr, which has a remote control, but this control doesn't work with Ubuntu (at least in my case) it should work out of the box, but it doesn't. I tried to use keyboard shortcuts for the control settings, but Ubuntu don't even recognizes when a button is pressed on the controller, except for one button (the display one). but even when a command shortcut is assembled to this key (the controller one that works) the command dont work when I press it.The controller is new, and the battery is full, it work normally on windows. How can I make it work on Ubuntu?

---

### Post by Melk79 on 2008-08-22
You didn't mention which version you're running, but my remote worked on 8.04 out of the box.  This [link]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops") also agrees though your specific model isn't included.  I saw other [links]("http://sidrit.wordpress.com/2008/08/09/configuring-windows-media-center-remote-control-for-elisa-on-ubuntu-804/") talking about installing Elisa and lirc, but I have neither installed.  Maybe try that?

---

### Post by Locutus_of_Borg on 2008-08-22
those quickplay remotes are horrible generally, but you are going to need the drivers it uses if you want to use it follow this: [http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html](http://aldeby.org/blog/index.php/en-hp-pavilion-multimedia-buttons-configuration-under-linux-linux-quickplay.html)

of course, some things that are designed to work solely only on windows, and then only on certain models of laptops with windows, and are not designed to work on anything else at all, wont work with linux

---

### Post by Sef on 2008-08-22
Moved to General Help.

---

### Post by pwnprog on 2008-08-22
weird. mine worked right out of the box. how recently was your laptop made?

---

### Post by pretobomba on 2008-08-22
Thank you Melk79, that worked fine.I'm running on Hardy, and my laptop was built this year, its not old.But just one more thing, can I put more than one key for one command (for example when I press the F13 or F14 they do the same thing)?

---

### Post by gokussj4 on 2009-05-02
Hi,
I think ive got a working solution.

My HP model is : HP dv5 1104TU that came with a media remote control.

Now i followed the following steps to get it working on ubuntu 9.04 .

firstly , download lirc, using :
```

sudo apt-get install lirc
```

after that, download the configuration file from lirc's website.
u can find it [here]("http://lirc.sourceforge.net/remotes/hp/DV6331") 

save this file as **lircd.conf** in /etc/lirc/

after that , open up the /etc/lirc/hardware.conf file.
Edit the file so that it should match this :

[HTML]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER="default"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="false"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""[/HTML]

now do :

```
sudo /etc/init.d/lirc start
```

Voila !!
and now your remote should work, you can try it out from Sytem->Preferences->Keyboard Shortcuts

Hope this helps ! :)

---

### Post by brettnak on 2009-05-14
Should something show up in lsusb or lspci about the ir port?  Nothing shows up on mine.

---

### Post by gokussj4 on 2009-05-18
nope ! nothing shows in mine either !

---

### Post by janmyszkier on 2009-05-18
i have tx2500:

in the lirc setup i choose: 
HP IPAQ

then when asked about reciever i choose:
None

I didn't even bothered to download provided file, try on your HP's

Works like a charm :)

---

### Post by corruptor1972 on 2009-05-30
The latest BIOS update, F16A, from HP allowed the remote control for my DV5-1000 to work - as well as enabling the suspend/resume function.

Before the update, xev showed nothing from the remote control.  Now every key generates a response.

---

### Post by jor-ell on 2009-06-25
Hi [janmyszkier]("http://ubuntuforums.org/member.php?u=786191")

Could you post your hardware.conf for see your configuration, cause the solutions mentioned above  does not work for me.

And I can not open the setup wizard To select HP iPAQ.

Regards,

---

### Post by sergiom99 on 2009-08-10
> **janmyszkier said:**
> i have tx2500:

in the lirc setup i choose: 
HP IPAQ

then when asked about reciever i choose:
None

I didn't even bothered to download provided file, try on your HP's

Works like a charm :)

Worked for me... but it needed a reboot after installing lirc, so that the kernel could load up the new module.

Amarok does not recognize my remote, OOB, but was very easy to configure alternative shortcuts in its preferences menu.
Thanks!

---

### Post by Stefano Malinconico on 2010-03-13
Do these instructions work with just a specific media player. which one?

Thnx

---

