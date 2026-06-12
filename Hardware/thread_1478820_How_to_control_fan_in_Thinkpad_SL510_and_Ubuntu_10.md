---
title: "How to control fan in Thinkpad SL510 and Ubuntu 10.04?"
date: 2010-05-10
forum: Hardware
---

### Post by vickoxy on 2010-05-10
Hi,
i read many forums but i still can not figure is there any way to adjust fun speed in thinkpad SL510 and ubuntu 10.04 64 bit?

I bought today SL510 and just installing updates for ubuntu 10.04 and fan is always working although the chase is cold. The fan noise is not annoying but, i just want to make it quite as possible.

I read that in win there is one fan control program: TPFancontrol ([http://www.thinkpad-forum.de/forum-community/kaufentscheidung/91099-thinkpad-edge-13-oder-thinkpad-sl510/](http://www.thinkpad-forum.de/forum-community/kaufentscheidung/91099-thinkpad-edge-13-oder-thinkpad-sl510/)).
Is there something like that for Ubuntu/Linux? Or, could i install this programm with wine under Ubuntu (or would that be to risky)?


Hope to find some help here. 

SL510 Specs:

• Core 2 Duo T6570 2x 2.10GHz
• 2048MB • 250GB • DVD+/-RW DL
• Intel GMA X4500HD (IGP) max.384MB shared memory
• 4x USB 2.0/Gb LAN/WLAN 802.11abgn/Bluetooth/eSATA
• HDMI
• ExpressCard/54 Slot
• 7in1 Card Reader
• Webcam (2.0 Megapixel)
• 15.6" WXGA non-glare LED TFT ( 1366x768 )

---

### Post by vickoxy on 2010-05-10
I tried to install tpfan control but nothing. Any clue on this?

[http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)

---

### Post by vickoxy on 2010-05-11
Bump!

I remember-few years ago i had Asus EEE Pc 701 and i just run little sh script as someone posted me on some forum. But i can not find it any more.

Is there some easy way to adjust fan speed in ubuntu?

---

### Post by vickoxy on 2010-05-11
Bump!

---

### Post by vickoxy on 2010-05-11
I tried to use this method here to control my fan:
[http://wiki.ubuntuusers.de/Lüftersteuerung](http://wiki.ubuntuusers.de/Lüftersteuerung)

But, i can not start this comand:

```
sudo pwmconfig
```

I become his:

```
thinkpad@thinkpad:~$ sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

Any idea?

---

### Post by Yellow Pasque on 2010-05-11
I don't think it's supported :( [http://dev.iksaif.net/issues/27](http://dev.iksaif.net/issues/27)

---

### Post by vickoxy on 2010-05-11
> **Temüjin said:**
> I don't think it's supported :( [http://dev.iksaif.net/issues/27](http://dev.iksaif.net/issues/27)

I thought that tpfancontrol isn´t to work on sl510, but toher methods should work?

Or am i wrong?

---

### Post by Method X on 2010-05-11
Hi there, laptop brother :)

try this one: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control")

Another model of laptop, but work for every IBM Thinkpad.

---

### Post by vickoxy on 2010-05-11
> **Method X said:**
> Hi there, laptop brother :)

try this one: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control")

Another model of laptop, but work for every IBM Thinkpad.

Well i tried that-but it doesn´t run on sl510....

---

### Post by Method X on 2010-05-11
Oh...sorry man.
What does it saying?
maybe we can try to get it work?

---

### Post by vickoxy on 2010-05-11
I described problem also here:
[http://forum.ubuntuusers.de/topic/tp-fancontrol-lueftersteuerung-fuer-thinkpad-/](http://forum.ubuntuusers.de/topic/tp-fancontrol-lueftersteuerung-fuer-thinkpad-/)

```
thinkpad@thinkpad:~$ sudo apt-get install tpfand tpfandprofiles tpfan-adminPaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Paket tpfand ist nicht verfügbar, wird aber von einem anderen Paket
referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket tpfand hat keinen Installationskandidaten
thinkpad@thinkpad:~$ 
```

It seems that thinkpad_acpi is not supported in sl510...

---

### Post by Method X on 2010-05-11
Very strange...

---

### Post by vickoxy on 2010-05-11
So, is there any easy/simple way to adjust my fan?

---

### Post by Method X on 2010-05-11
[http://sysphere.org/~anrxc/j/articles/thinkpad/index.html]("http://sysphere.org/~anrxc/j/articles/thinkpad/index.html")

> Install cpufrequtils first, then load the acpi-cpufreq module. Run cpufreq-info next to see what are your options. I chose not to use the cpufreq daemon or any utility other than laptop-mode-tools. I configured its cpufreq module to use the conservative governor (load cpufreq_conservative module) while on battery, with max and min frequencies identical to what cpufreq-info reported as max/min. Otherwise when on AC I decided to always use the performance governor (default, no modules to load).

---

### Post by vickoxy on 2010-05-11
> **Method X said:**
> [http://sysphere.org/~anrxc/j/articles/thinkpad/index.html]("http://sysphere.org/~anrxc/j/articles/thinkpad/index.html")

But i can not see how can i control fan there: 

```
Until then our hardware will work without it, but with some limitations: several hotkeys are completely invisible to the kernel (hibernate, screen zoom and lock, microphone/wifi/bluetooth/touchpad toggle, battery status and the ThinkVantage button), fan control is missing and backlight has quirks as mentioned previously (but fixable in X11).
```

Thanks

---

### Post by Method X on 2010-05-11
Looks like i'm out of ideas. Sorry.
:(

---

### Post by vickoxy on 2010-05-12
So, i found solution that i used in acer aspire one:

[http://jorge.fbarr.net/2008/08/06/acer-aspire-one-tips-and-tricks/#Managingthefanspeed](http://jorge.fbarr.net/2008/08/06/acer-aspire-one-tips-and-tricks/#Managingthefanspeed)

Hoping there is some simple solution also for thinkpad sl series...

---

### Post by vickoxy on 2010-05-12
Have one more question. Would it be possible to install tpfancontrol for windows (that works with sl510) with wine? Would that version adjust fan speed (i doubt it...)?

I found on another forum that this is not possible.

---

### Post by vickoxy on 2010-05-13
Bump!

So, any of Linux gurus has some suggestion how to adjust and control FanSpeed on SL510? I am not programer and i think it is very hard to acomplish something like this, but still...

---

### Post by vickoxy on 2010-05-13
Bump!

Really no way to control my fan in sl510?

Should here be some way to change factory values, or to make some script that would control the fan?

Just asking....

---

### Post by Yellow Pasque on 2010-05-13
The best thing you can do is file a bug on kernel.org

---

### Post by vickoxy on 2010-05-13
> **Temüjin said:**
> The best thing you can do is file a bug on kernel.org

Well, but what to write? I would like to have some fan control? Maybe is this more lenovo thing...

Unfortunately, i don´t even know how does it have to function? Is this Software problem or Hardware issue. Is it possible to achieve any control here...

---

### Post by vickoxy on 2010-05-14
Bump

---

### Post by vickoxy on 2010-05-14
Still, can someone tell me why i can´t run /usr/sbin/pwmconfig? I followed instructions here ([http://wiki.archlinux.org/index.php/Fan_Speed_Control](http://wiki.archlinux.org/index.php/Fan_Speed_Control)), but have no clue how to run it. It seems that other notebooks are controling fan speed with this program very well...

Found something here: [http://nil-techno.blogspot.com/search?q=rc.fancontrol](http://nil-techno.blogspot.com/search?q=rc.fancontrol). It seems that SL510 has some 3pin cooler fan, and pwmconfig recognizes 4pin (have no idea what does this mean). But i have in my /etc/init.d/fancontrol app. If i run it:
> thinkpad@thinkpad:~$ /etc/init.d/fancontrol start
 * Not starting fancontrol, outdated configuration file; please re-run pwmconfig.


have this message. Can i avoid pwmconfig and try to connect fancontrol and this fancontrol config script in /etc/?

So, to run fancontrol whitout pwmconfig?

---

### Post by vickoxy on 2010-05-14
Well i run ```
sensor-detect
```.
After that i made one /etc/fancontrol file

```
INTERVAL=5
FCTEMPS=hwmon0/device/pwm4=hwmon0/device/temp2_input
FCFANS= hwmon0/device/pwm4=hwmon0/device/fan5_input
MINTEMP=hwmon0/device/pwm4=65
MAXTEMP=hwmon0/device/pwm4=75
MINSTART=hwmon0/device/pwm4=30
MINSTOP=hwmon0/device/pwm4=100
```

After that i run in terminal fancontrol and get this message:


```
thinkpad@thinkpad:~$ gksudo nautilus
thinkpad@thinkpad:~$ sudo fancontrol &
[1] 2434
thinkpad@thinkpad:~$ Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=5

Settings for hwmon0/device/pwm4:
  Depends on hwmon0/device/temp2_input
  Controls hwmon0/device/fan5_input
  MINTEMP=65
  MAXTEMP=75
  MINSTART=30
  MINSTOP=100
  MINPWM=0
  MAXPWM=255

Configuration is too old, please run pwmconfig again

```

Is tehre any way to make this scipt working without pwmconfig? Or does anyone know what should i add there?

---

### Post by ian dobson on 2010-05-15
Hi,

Just use an old version of fancontrol. The new version in 10.04 seems to look for extra information in the configuration file about what chip is used.

I've attached an older perl based verion of th fancontrol script that I'm using on my server.

Regards
Ian Dobson

---

### Post by vickoxy on 2010-05-15
> **ian dobson said:**
> Hi,

Just use an old version of fancontrol. The new version in 10.04 seems to look for extra information in the configuration file about what chip is used.

I've attached an older perl based verion of th fancontrol script that I'm using on my server.

Regards
Ian Dobson

Thanks for answer. Could you tell me where to put this script and how to activate it? And where to find older version of fancontrol?

Still, i doubt that it would work. If i type **sensors** (before that i made sensors-detect) i have no fan found:


```
thinkpad@thinkpad:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +45.0°C  (crit = +105.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +105.0°C, crit = +105.0°C)  

thinkpad@thinkpad:~$ 
```

Or should i try t anyway?

Thanks

---

### Post by SiegHard on 2010-05-18
Hey dude maybe it's problem not in ubuntu :) Try to update your bios, cuz in somekind version of bios fan works like wacuum cleaner :D

---

### Post by vickoxy on 2010-05-18
> **SiegHard said:**
> Hey dude maybe it's problem not in ubuntu :) Try to update your bios, cuz in somekind version of bios fan works like wacuum cleaner :D

Well, i have the newest version already. Thanks

---

### Post by SiegHard on 2010-05-19
> **vickoxy said:**
> Well, i have the newest version already. Thanks

Hmm and u tried any other OS?

---

### Post by vickoxy on 2010-05-22
Does anyone knows if fancontrol or tpfancontrol works under karmic?

---

### Post by vickoxy on 2010-05-23
Or-does anyone knows if one kernel-downgrade would make fancontrol to work?

---

### Post by Blümchen Blau on 2010-05-29
Have you ever thought of upgrading the kernel from the [Mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")? Maybe the problem is solved in one of the "future" kernels (2.6.33 or 2.6.34)!

---

### Post by vickoxy on 2010-05-29
I posted lots of posts at thinkpad-forum.de at other linux sites-it seems that here will be no support for acpi (including fan control) to thinkpad sl series.
I downgraded few days ago kernel, but still couldn´t make fan control running.

---

### Post by Blümchen Blau on 2010-05-29
So I still assume, it's a problem of 64-bit. I have no need for fan-control on my 32-bit Lucid! Maybe you make the test with a SD- or USB-Stick-installation?

---

### Post by vickoxy on 2010-05-29
maybe i should try to install 32bit. what hardware do you have? same as i?

---

### Post by Blümchen Blau on 2010-05-30
Lenovo SL510, Type 2847-7MG (with only upgrade to 3GB RAM)

---

### Post by visual_decoy on 2010-06-04
I'm very surprised that you can't run tpfan. I have it running on a Thinkpad T400 with Ubuntu 10.04 64 bit.

> **vickoxy said:**
> 
```
thinkpad@thinkpad:~$ sudo apt-get install tpfand tpfandprofiles tpfan-adminPaketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
Paket tpfand ist nicht verfügbar, wird aber von einem anderen Paket
referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket tpfand hat keinen Installationskandidaten
thinkpad@thinkpad:~$ 
```



I can't read German, but does this mean that you weren't able to download the tpfand, tpfan-admin, and tpfand-profiles packages?

---

### Post by Phocean on 2010-06-04
I gave a try to tpfan but didn't like it, because it was constantly flapping from a level to another.

tpfan-admin ([http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)) is not only the easiest way to configure fan control as you like, but it has settings to avoid flapping (defaults ones are probably good enough).

---

### Post by vickoxy on 2010-06-04
> **Phocean said:**
> I gave a try to tpfan but didn't like it, because it was constantly flapping from a level to another.

tpfan-admin ([http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control)) is not only the easiest way to configure fan control as you like, but it has settings to avoid flapping (defaults ones are probably good enough).

Well, SL series supports no acpi-so actually under linux is no fancontrol possible. I would be happy if i am wrong, but i think i am not.

T400 is just "real" thinkpad, and all drivers/modules/apps are working there...

---

### Post by Phocean on 2010-06-04
Oh that's a shame :(

(a happy user of an old good T61)

---

### Post by Arsic on 2010-08-04
> **Method X said:**
> Hi there, laptop brother :)

try this one: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_(Lucid_Lynx)_on_a_ThinkPad_Z61m#Setup_Fan_Control")

Another model of laptop, but work for every IBM Thinkpad.

This is beautiful. Thank you. This works on my T61p. I just set everything to full and my temperatures go down.

---

### Post by coady on 2010-08-06
> **vickoxy said:**
> maybe i should try to install 32bit. what hardware do you have? same as i?

Has anyone tried this with the 32 bit version, and if so, how did it go with fan control?

Thanks...

---

### Post by vickoxy on 2010-08-06
SL510 does not support, and probably will not support under Linux any fancontrol application.... Sorry... i tried everything but no hope...

---

### Post by coady on 2010-08-06
> **vickoxy said:**
> SL510 does not support, and probably will not support under Linux any fancontrol application.... Sorry... i tried everything but no hope...

So what's your situation. Does the fan run full speed constantly, or is it just that you would rather be able to have full control over fan speed?

Cheers...

---

### Post by vickoxy on 2010-08-06
> **coady said:**
> So what's your situation. Does the fan run full speed constantly, or is it just that you would rather be able to have full control over fan speed?

Cheers...

Well, i sold my SL510 and bought R500 ;)...

The fan wasn´t working constantly at full speed, but it was to loud. I wanted to control the speed because the computer temp. was low-but, as said, sl510 doesn´t have acpi full support as other thinkpads. And that is why you can not control fan speed under linux...

---

### Post by nulldozer on 2010-08-07
**pwmconfig** won't work if you haven't detected any temperature sensors yet. 

In the terminal, run: ```
sensors-detect
```It will walk you through detecting sensors. Then you can go ahead and run **pwmconfig**.

EDIT: Whoops, sorry for repeating this. Didn't read previous posts first.

---

### Post by coady on 2010-08-08
> **nulldozer said:**
> edit: Whoops, sorry for repeating this. Didn't read previous posts first.
... ;)

---

### Post by words1 on 2012-01-21
My understanding is that the firmware in the SL510 is actually Ideapad, not Thinkpad firmware. It's not really a Thinkpad, in other words. Which really sucks. Maybe there's an Ideapad fan control program.

---

