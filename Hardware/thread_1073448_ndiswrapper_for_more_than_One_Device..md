---
title: "ndiswrapper for more than One Device."
date: 2009-02-18
forum: Hardware
---

### Post by zancoste on 2009-02-18
Hello People,

What I am trying to do now is to use the ndiswrapper for more than one Device. 
One my laptop, I have a Broadcom wireless card. I was able to make it run using ndiswrapper and the Windows driver. I also have a usb Zydas wifi device. Once plugged in, it uses the zd1211rw module. Unfortunately, with that module, I can't really get the ad-hoc to work and connecting to a access point yields a very low connection strength. 

So what I decided to do was to use the Windows XP drivers, I used **ndiswrapper**, unload and blacklisted **zd1211rw**, and added in the "ndiswrapper" file located under  **"/etc/modprobe.d/"** the following lines **"alias wlan1 ndiswrapper"**. After reloading the ndiswrapper module, both devices (Broadcom wireless, and Zydas Wifi) were using it, and it worked fine. However, after a while, I started seeing the same instances of the driver being listed under the "gnome network manager"; so it looked as if it was stuck in a recursion or something. 

I tried to restart, but when I Zydas wifi device is plugged in, the start up process hangs. When I later try to plug in the Zydas device when Ubuntu starts up, the computer Froze.

So it seems that my system is having trouble using one module for both devices. How can I go about resolving this issue? Apparently using **ndiswrapper** instead of **zd1211rw** gives better performances.


Also here is the output of "ndiswrapper -l"
```

bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
zd1211bu : driver installed

```

Thanks.

**_Update_:**
After some more digging, I found out that ndiswrapper can indeed be used with more than 1 device. However, there seems to be a bug when trying to use it with USB dongles. On many pages that I have read, they suggest completely removing ndiswrapper and recompiling it from source against the version of the kernel you are running. However this didn't work for me. My system still kept on hanging. So to the first question I asked in the title, the answer is YES. The only thing is, I am a bit out of luck to be trying to make it work with USB dongles. When I fix my system freeze, I will let everyone know.

Thanks to **ajmctaggart** and **lwfinger** for giving me some idea, you guys rule!

---

### Post by ajmctaggart on 2009-02-18
As far as I know...

ndiswrapper can handle multiple XP/Vista/Whatever Drivers installed on your Linux System...But I WOULD THINK the main problem here isn't that...

Are you shutting off your Broadcom Card when using the usb?

The reason I ask is that 2 wifi devices that close to eachother running on the same system, both on, will give you all sorts of errors and issues that really don't have anything to do with ndiswrapper...

If you can shut off the Broadcom or unplug the USB when using the other, for example, I would think you'd get far better results...

Sorry if I am missing the question, but I think that your problem is coming more from that than an ndiswrapper or NetworkManager issue...

---

### Post by zancoste on 2009-02-18
Thank you for you quick answer. 

So let me reiterate the question: I was able to use both devices before,when one of them was using the ndiswrapper module and the other one was using the zd1221rw module. It was working without errors, however, the performance of the usb wifi (the one using the zd1211rw module) was very weak. 

When I made both devices use the ndiswrapper module, at first, it worked the way I wanted it to work. Performance was good. But when I rebooted, this is when I Started having a problem with the system hanging up. So it appears that ndiswrapper is unable to load for both devices.

---

### Post by ajmctaggart on 2009-02-18
Got it...

Can you restart, without usb device plugged in, boot up into Ubuntu, and then plug it in and have it work without problem?

Just trying to see why it would hang, ndiswrapper should be able to handle it from what I've seen on my own systems...

Oh and I think I may have an answer for you after looking at a Fedora thread on multiple instances of wlan...

Since you've got more than one wlan device, wouldn't you need both added to the modprobe file?

---

### Post by zancoste on 2009-02-18
No, once I boot up and I plugin the device, the system hangs and I have to do a hard reset (Holding the power button).

---

### Post by ajmctaggart on 2009-02-18
hmm, what do you think about the other recommendation, can you add both ```
alias wlanx ndiswrapper
``` to the modprobe file?

If not, I think you'll need some help from a ndiswrapper guru...

---

### Post by zancoste on 2009-02-18
What I had in the file was:

```

alias wlan0 ndiswrapper
alias wlan1 ndiswrapper

```

also thanks for the quick replies :D

Edit: I already had the in the the modprobe file, and it was still hanging.

---

### Post by ajmctaggart on 2009-02-18
If you already had that in the file, that should have been good enough...you'll have to get some help from someone with more knowledge than me...

Whoever else helps you will want to know your ndiswrapper output...
from the terminal...

```
ndiswrapper -l
```

that'll show us what we've got so far...

---

### Post by zancoste on 2009-02-18
```
ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
zd1211bu : driver installed

```

---

### Post by ajmctaggart on 2009-02-18
Also

```
iwconfig
```

just curious what the system is showing since there are two cards...but since you can't boot with two cards this may not work...

Okay here's where you should start to see if this is even possible to get working...

remove the usb device from ndiswrapper...remove the line from your modprobe and perform an ```
ndiswrapper -e 
``` of your usb's driver...

reboot

If your Broadcom card allows you to boot up w/o problem, then we definitely know it all started with the usb device...

shut off the Broadcom card completely and reboot again with your usb attached

go on to attempt to ```
ndiswrapper -i
```with your XP drivers for that usb device...im sure you'll have to use ndiswrapper's modprobe setting ```
ndiswrapper -m
```or manually add these devices to the modprobe...

IF FOR WHATEVER REASON IT HANGS, YOU'LL HAVE TO COMMENT OUT WHATEVER CARD IN YOUR MODPROBE THAT YOU ARE NOT TESTING DURING ALL THIS

If the same symptoms happen again, I'm afraid that you may be out of luck with ndiswrapper running 2 cards at once...hopefully somebody will have a definite Yes/No to this question shortly...

Sorry I wasn't of more assistance...I cannot find this exact question, but other people trying to use 2 actual networks at the same time on different devices have not had luck either...

I guess it's worth a shot while you wait for a better answer...

---

### Post by ajmctaggart on 2009-02-18
And I know you've already said this before, but with both drivers installed, and with the Broadcom present like it is in the output you just posted, when you plug in the usb device, the system crashes?

---

### Post by zancoste on 2009-02-18
yes with the settings I just posted, when I plug in the usb device, the system crashes.

---

### Post by ajmctaggart on 2009-02-18
Can you startup as usual, Broadcom not USB, and then shutoff the Broadcom and THEN plug in USB without a crash happening?

I think that just points to the answer being "no," ndiswrapper cant run 2 devices simultaneously, just support both devices individually on the same system in different instances...

what about the iwconfig output?

---

### Post by zancoste on 2009-02-18
When I shutoff the Broadcom and started the usb, I still got a crash. 
The way I disabled the Broadcom was using the "Fn" key... I don't know if this has to do anything with it.

Is there another wrapper class you know of that I could use?

---

### Post by ajmctaggart on 2009-02-18
Post your output of 

```
iwconfig
```

Well, there are other wifi helpers out there...

MadWifi for instance...[http://madwifi.net/]("http://madwifi.org/")

You can install from Ubuntu Repos I believe, but it will still be a pain to get these working simultaneously, but I believe it can be done.

If you have a Windows Install on this machine, boot into Windows and make sure BOTH devices are turned on, and see if you are getting signals with both.

Also, I have reason to believe you may be using the wrong drivers for that usb device FOR NDISWRAPPER PERHAPS...If its crashing without the Broadcom present, something is definitely wrong...


For Example, Even if they work in XP, are you running 64 bit Intrepid with a 32 bit driver, anything strange like that?

Finally, You could post something to ndiswrapper on sourceforge's site and see if you get any help...

I'm really sorry I couldn't be of more service, I was really hoping we could get that working for you, but maybe someone will come along with a little more experience in this area...

EDIT: MAKE SURE YOU'VE LISTED YOUR LAPTOP MODEL IN THE FIRST POST O, AND MAYBE ADD IT TO THE TITLE...

---

### Post by zancoste on 2009-02-18
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"UMBC Visitor"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:26:2A:C5:82   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"UMBC Visitor"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:26:2A:C5:82   
          Bit Rate=6 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=47/100  Signal level:20/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

But I reverted back to zd1211rw, driver.
And yes both devices work simultaneously under Windows XP. And I used copied the device drivers from the Windows partition.

The weird thing is that when I installed the Zydas drivers with ndiswrapper, both devices, it **WORKED**, but when I rebooted, problems started happening.

---

### Post by ajmctaggart on 2009-02-18
I bet if you could figure out how to turn the wlan1 device to "G" only you could get better service...

Again, Sorry :(

---

### Post by zancoste on 2009-02-18
Don't be sorry, you have done a lot :)
Thanks for your assistance. I will investigate and let you know what I came up with

---

### Post by ajmctaggart on 2009-02-18
I asked a guy I know that works on Opensuse, see if he knows if it's possible, I'll let you know if I get a response.

---

### Post by lwfinger on 2009-02-18
I think that I'm the openSUSE guy mentioned above. First of all, I am not an ndiswrapper expert.

If your problem is due to trying to run two drivers under ndiswrapper at the same time, there is one workaround. Your BCM4318 will work just fine using the b43 driver if the appropriate firmware is installed. I does not need to use ndiswrapper.

---

### Post by zancoste on 2009-02-19
Hello lwfinger, 
Thanks for helping :)

I had to look around and see how to make b43 work. So after doing that, I was able, as you said, to use Broadcom without ndiswrapper. 

The bad news is even with that, the system freezes, when I plug in the USB device and try to load ndiswrapper; I don't know how I can get an error message given because I always have to hard reboot. 

At first I thought maybe it had to do with the version of ndiswrapper I was using and how it was compiled, so I downloaded the source and compiled it against my kernel, then reinstall Windows XP driver, but still no luck. 

Just to show you that all "seems" to be done correctly, here is the output of "ndiswrapper -l"
```

zd1211bu : driver installed
	device (0ACE:1215) present (alternate driver: zd1211rw)

```
When I ran that command, I was using zd1211rw module and unloaded ndiswrapper...

also running ndiwrapper -v:
```

zana@zana-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-11-generic/misc/ndiswrapper.ko
version:        1.54
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586

```

uname -r
```

 uname -r
2.6.27-11-generic

```

It really throws me off, because I know ndiswrapper worked once with my usb device ... 

Thanks again for helping me.

---

### Post by ajmctaggart on 2009-02-20
Zancoste,

Sorry it's still not working...

One question, Have you tried the "alternate driver" that ndiswrapper is showing you on a "ndiswrapper -l?" 

Just curious...

---

### Post by zancoste on 2009-02-20
Yes I have tried (zd1211rw); it works, but not as well as the first time ndiswrapper was working. 
For example, it won't do ad-hoc and won't give strong signal (I mean ndiswrapper -- the only first time it worked -- was giving very very good results).

---

### Post by stchman on 2009-02-20
I don't see a problem, I would use ndisgtk.

---

