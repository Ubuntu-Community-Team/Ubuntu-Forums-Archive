---
title: "ATI PowerPlay"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by GEnX20 on 2005-10-27
I found this orphan post in the Hoary Laptop forum
I'm also interested in using ATI PowerPlay to lengthen my battery life, but I'm running  Breezy 

Any Ideas?
Thx a lot

[QUOTE=dave1111]Hi,

I got the Acer Aspire 1694 WLMi with the ATI-Mobile x700.
Under Windows with Powerplay enabled and set for maximum battery lifetime I don't hear any fan. Only once in an hour or so it is turned on for a minute or two.
I found a tip on the net that with the Option "DynamicClocks" "on" there could be some of the Powerplay-features enabled with the xorg-radeon-driver. I tried this out but the fan doesn't stop. It is going the whole time I work under Linux.
I don't think it has to do with CPU - powernowd is running (I haven't tried different options for it but in Windows I have to put the Powerplay to max. batt. lifetime to get the fan quiet so I think its the GPU)

Are there other options I can use apart from DynamicClocks? Is there something else misconfigured? Is there hope that ATI will bring Powerplay to their linux drivers?
If the fan doesn't stop it doesn't make sense for me to use this option - maybe battery lifes longer, but the main thing I want is silence.

What else could I try to get the GPU-fan quiet in a safe way?

Thanks,
Dave[/QUOTE]

---

### Post by GEnX20 on 2005-10-30
Bump

---

### Post by Mo.Bang on 2005-11-02
Hi,

take a look at ATI's website.
There's a new driver available that can switch off parts that are not in use.

Maybe this one does the right thing for you.

Ralf

---

### Post by Flandry on 2005-11-02
> Dynamic Clock Gating The Linux 8.18.8 software driver provides dynamic clock gating. This feature allows the supported graphics cards to deactivate components when they are not being used.

 As found [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.18.8.html") ((hmm... https: that link might not work for you). Sounds good, and like something i would like for my Thinkpad, too, but i'm not sure what the ubuntu kernel config looks like and therefore don't know how complicated getting this to work would be.  The current drivers in the repository are 8.16.20.

---

### Post by tawk on 2005-11-14
Good evening,
with the newest fglrx driver installed ATI-Powerplay should work as followed:

Show available power-states:
```
aticonfig --list-powerstates
```
Set your power-state:
```
aticonfig --set-powerstate=NUMBER
```

For me on my Samsung X20 (with X600) it worked only once. Any further tips appreciated!

---

### Post by dave1111 on 2005-11-20
Hi,

for me on Breezy now with the new ATI-Drivers the aticonfig --set-powerstate is working (run as root). My Aspire 1694 WLMi got 3 Modes and it is more quiet. I haven't tested battery-lifetime yet.

Does it work every boot only once or did it work only once at all?

What doesn't work for me is the setting in the xorg.conf which is written by the aticonfig.
Log:
(WW) fglrx(0): Option "PowerState" is not used

But its ok, since I can switch modes after boot manually.

---

### Post by Pheonix on 2005-11-20
Sorry for dumming down a bit, but I've been experimenting with Ubuntu on my Acer Travelmate 3202Xci.

It has a Radeon 9700; but I've got no idea what drivers its using, or how to tell Ubuntu I want to use the ATI Drivers (thus allowing me to use powermanagement).

Any help rendered is appreciated!

---

### Post by Mo.Bang on 2005-11-22
Just download the installer from ati's website and install it as described on the
site or in the Readme.

Ralf

---

### Post by Maverick911 on 2005-11-22
Hi everyone,
I'm trying to work through loading the latest driver from ATI's site (currently 8.19.10). Please excuse me if this is a stupid question, but ATI has this note on their site:
> Note: 	If you are unsure of which version of XFree86/X.org is installed on your system, download and run check.sh from a command line to verify the version. How do I find out what version I'm running?

I don't even know how to run this script from the command line. I tried cutting and pasting it to the command line, but it just stops and I have to Ctr+C to return to the prompt.

I also saw this:
> The display driver requires POSIX shared memory to be enabled on the systemHow do I find this out?
Thanks for any help.

---

### Post by tawk on 2005-11-23
@Maverick911 + Phoenix
Just install the latest fgrlx-driver as described in this nice [HOW-TO from ubuntuforums.org]("http://ubuntuforums.org/showpost.php?p=423584"). This is the fastest and most secure way. By the way: Ubuntu uses X.org.

My only problem was, that "aticonfig --initial" messed up my xorg.conf with double-entries. Having fixed this, it is working on my laptop now very well with 20% less power consumption by "aticonfig --set-powerstate=1". As the powerstate is not recovered after reboot, I added this command to system > properties > sessions > start-programs

But, as I have feared, suspend to ram is not working anymore with the fgrlx-driver. My Samsung X20 does not wake up after being asleep.
Do you have any helpful Hints?

---

### Post by dave1111 on 2005-11-23
On Breezy it should be Xorg 6.8.2 by default.
On Console you can type 
X -version
and/or check in synaptics if Xorg or XFree is installed by searching them


SuspendToRam isn't working for me too, but I have heard someone getting fglrx working with vbetool which can be installed by synaptic. I tried but I didn't manage to get it work.

---

