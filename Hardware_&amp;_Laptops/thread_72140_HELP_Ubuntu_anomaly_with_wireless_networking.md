---
title: "HELP: Ubuntu anomaly with wireless networking"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by The_Saint on 2005-10-05
Ladies and gentlemen,
I have a serious issue with Ubuntu 5.04 and so far I haven't found a solution to my problem.
So.
I have a laptop, it's an Estonian-made Ordi CL56PD, but that could also be irrelevant. It has Intel Centrino Mobile Technology in it and the wireless card is Intel Pro Wireless 2200, if I am not mistaken. 
The problem starts with this - at home I use wifi, but at work I connect to the internet by cable.
At home, I start the computer, everything works, the light on the computer panel that proves that wifi-card works, is on (it's supposedly a software based light, although there is a switch too, which is permanently on all the time for me). I close the computer and go to work, stick the cable in and start the machine - and the wifi light is gone. I.e. the card has been switched off by something in software.
So, as I don't need wifi at work, I don't worry there, but when I get home and restart the computer, the light is still off. The *only* way to get the card working again is to log in to Windows - Win is smart enough to restart the card again. So, restart and back to Ubuntu and everything works again.
So, I was thinking that perhaps the issue is that the wifi card is being turned off by the fact that i connect the cable. But no. Today in the morning I started the machine without sticking in the network cable, and the light of wifi card was still off. When i start the computer at home, it is on.
So, my conclusion was that if the computer does not notice a familiar wireless network at the very moment of booting, then it won't load the wifi card. Because, at my work place there are wifi networks, I just don't have access to them. So, it could supposedly at least find some of them. What if I go to a cafe where's free wifi and I wanna log into it? What if I go to a different place where I know the key to get in a restricted net?
At the same time, it's incredibly weird, because the computer cannot possibly know if there is or is not a wifi coverage until the OS has loaded.
I wouldn't basically mind if it turned out the wifi card when I am at work, but I do mind that i have to mess with it when I get back home.
When I open the networking section in Ubuntu, both eth0 (LAN) and eth1 (wifi) are active. But there is no difference in the issue I described if I deactivate wifi before sticking in the network cable or not. Also, there is no difference with wifi if I deactivate eth0 or not. And there is no difference if I deactivate eth1 and activate it again in order to make the wifi card work - it won't help. The only possibility to get the card working again after it has been turned off by this anomaly is logging into WIndows and let it turn on the card.
I would really very much appreciate if someone could come up with a solution to this problem that would be easier than logging into Windows. Because I am planning to get rid of Windows and what happens then? I could be pretty fubar then.
Maybe the UFOs or some incredible conspiracy is the one that turns off my wifi card. But I would like to beat those UFOs and/or conspiracy. With your help - I would be more than thankful.
Sincerely,
The_Saint

---

### Post by mlomker on 2005-10-05
> 
I have a laptop, it's an Estonian-made Ordi CL56PD, but that could also be irrelevant. It has Intel Centrino Mobile Technology in it and the wireless card is Intel Pro Wireless 2200, if I am not mistaken.

Usually the hotkey can turn the card on or off.  Does the hotkey have no effect?  Are you getting an error about the radio being turned off in dmesg?

Are you using ndiswrapper or native drivers for the wireless?  Is it the latest version?

```

dmesg | grep eth1

```

There is a [software switch project]("http://rfswitch.sourceforge.net/") but I'm not sure if it'll help you.  Every laptop is a bit different.

---

### Post by The_Saint on 2005-10-05
[QUOTE=mlomker]Usually the hotkey can turn the card on or off.  Does the hotkey have no effect?  Are you getting an error about the radio being turned off in dmesg?
Are you using ndiswrapper or native drivers for the wireless?  Is it the latest version?
```

dmesg | grep eth1

```
There is a [software switch project]("http://rfswitch.sourceforge.net/") but I'm not sure if it'll help you.  Every laptop is a bit different.[/QUOTE] I am quite new to Linux, i.e. I have been using some distros before now and then, but this is my first that close encounter with it, so I might be asking stupid questions or saying stupid things :) I hope I can be forgiven.

Anyway, i don't know what is ndiswrapper. I know that I am using drivers that come with Ubuntu CD, because I did not install any additional drivers for the wireless card. It worked just fine after the install.

The hotkey (I presume it's the key on the computer that is used for turning the wifi card on and off) does not have any effect. Turning it off and on again when the wifi card has been mysteriously switched off does not have any effect. 

dmesg | grep eth1 - that tells me a lot of things. Like: ```
eth1: duplicate address detected!
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)
```

That doesn't tell me anything.

---

### Post by mlomker on 2005-10-05
> 
eth1: duplicate address detected!
eth1: decryption failed (SA=00:02:b3:86:cf:e6) res=-2
eth1: WEP decryption failed ICV mismatch (key 0)


You using Hoary or Breezy?  

This tells me that you may have a static address that conflicts with another machine on the network and that your WEP key is misconfigured.  Judging from this output I would say that your card is working fine right now.

The first two tell you the access point name and IP address.  The third one is the configuration.

```

iwconfig eth1
ifconfig eth1
cat /etc/network/interfaces

```

---

### Post by The_Saint on 2005-10-05
I am using Hoary.

And right now it is working fine - I am on wifi. Card is working fine and wep is not misconfigured - i am on the network :)

I would like to know what should I do when I tomorrow get back from work and have to boot to Win again in order to get the wifi card working again :)

---

### Post by mlomker on 2005-10-05
> I would like to know what should I do when I tomorrow get back from work and have to boot to Win again in order to get the wifi card working again :)

I'd try [installing the latest drivers]("http://www.ubuntuforums.org/showthread.php?t=26623"), as a place to start, but I don't know if it'll solve your issue.  

I have the same card but my wireless stays on between reboots.  Every laptop is a bit different.  You've already looked through the BIOS settings for things related to wireless?  Perhaps there's an 'always-on' option.

---

### Post by The_Saint on 2005-10-05
Nothing in BIOS regarding wireless, sadly.

My wireless stays in between reboots as well, as long as I stay at home in my own wifi coverage area. When i shut it down at home and start it again at work, it won't work any more... sounds like a conspiracy, ha :)

About the latest drivers you suggested - it says there that upgrading firmware is also needed... in past I've had bad experiences with updating wifi card firmware, are you sure it's safe, if I do everything as described there?

Or, if I don't need wpa support, can I leave the firmware untouched?

---

### Post by mlomker on 2005-10-05
> In past I've had bad experiences with updating wifi card firmware, are you sure it's safe, if I do everything as described there?


The firmware has to match the driver version, so you'd have to update it.  It's nothing more than a few files copied to the proper directory.  I installed the latest drivers first thing because mine wouldn't work at all with Hoary's version.

---

### Post by The_Saint on 2005-10-05
So, now I did all that - upgraded drivers, firmware and all... and I succeeded :) Damn I'm good :)

Anyway, I will tell you tomorrow evening then if it helped with my issue or not. I sure hope it did, but if not, I'll let you know.

Thank you very much for your time and teachings :)

---

### Post by The_Saint on 2005-10-06
Hello again,

Didn't work at all :P

I am at work, when I turned the computer on here today, the wireless light was off again. So I presume everything continues as it was before upgrading drivers... 

Any other suggestions? :)

---

### Post by The_Saint on 2005-10-06
And hello again,

I am now back home from work and that anomaly is still here.

So, I did what was suggested in previous posts and the result is here:

```
kala@hankewitz:~$ dmesg | grep eth1
eth1: no IPv6 routers present
kala@hankewitz:~$ iwconfig eth1
eth1      radio off  ESSID:"Stennu"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kala@hankewitz:~$ ifconfig eth1
eth1      kapseldus:Ethernet  HWaddr 00:0E:35:C9:DB:39
          inet6 aadr: fe80::20e:35ff:fec9:db39/64 skoop:&#252;hendus
          UP BROADCAST MULTICAST  MTU:1500 meetrika:1
          RX pakette:0 vigu:0 &#228;ra visatud:0 &#252;let&#228;it:0 kaadri vigu:0
          TX pakette:0 vigu:0 &#228;ra visatud:0 &#252;let&#228;it:0 carrier:0
          kollisioone:0 txqueuelen:1000
          RX baite:0 (0.0 b)  TX baite:0 (0.0 b)
          katkestus:10 baasaadress:0xc000 m&#228;lu:d0000000-d0000fff

kala@hankewitz:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet dhcp
wireless-essid Stennu
wireless-key 38204553267d7e522c4365374e



iface eth0 inet dhcp





auto eth1

auto eth0
kala@hankewitz:~$
``` From what I see from here I conclude that radio in fact is off. But that I knew before already :)

The main thing is, considering everything I wrote above, how on earth to get it back on again without first booting to Windows and letting it turn it on again...

---

### Post by mlomker on 2005-10-06
> The main thing is, considering everything I wrote above, how on earth to get it back on again without first booting to Windows and letting it turn it on again...

Have you seen this [document?]("http://ipw2200.sourceforge.net/README.ipw2200")  Search for the part about rf_kill.

Here's my file, but your directory name might be different because it's the PCI address.  A zero in that file means that the radio is enabled.  What is yours saying?

```

root@mlomkernote:/sys/bus/pci/drivers/ipw2200/0000:00:0b.0 # cat rf_kill
0

```

EDIT: After Googling around that information isn't very useful because changing the number in the file won't fix it--it's just an indication that the hardware button is on or off.

---

### Post by The_Saint on 2005-10-06
[QUOTE=mlomker]Have you seen this [document?]("http://ipw2200.sourceforge.net/README.ipw2200")  Search for the part about rf_kill.

Here's my file, but your directory name might be different because it's the PCI address.  A zero in that file means that the radio is enabled.  What is yours saying?

```

root@mlomkernote:/sys/bus/pci/drivers/ipw2200/0000:00:0b.0 # cat rf_kill
0

```

EDIT: After Googling around that information isn't very useful because changing the number in the file won't fix it--it's just an indication that the hardware button is on or off.[/QUOTE]

Well, right now it's on, because I already activated it from Windows.

```
kala@hankewitz:/sys/bus/pci/drivers/ipw2200/0000:02:02.0$ cat rf_kill
0

```

---

### Post by The_Saint on 2005-10-07
Hey,

Being at the dead point...

Right now I am at work again and rf_kill says: ```
kala@hankewitz:/sys/bus/pci/drivers/ipw2200/0000:02:02.0$ cat rf_kill
2
```

So, it means that HW based RF kill active (radio off).

Today I began thinking, what if it is related to the fact if the computer is running on battery or cable... Because, from what I see - when i shut it down in the morning at home, it's on the cable (which means that power management is off, I think at least), but when I turn the machine on at work about half an hour after turning it off at home, I run the machine on the battery...

Do I make any sense? When the wifi-card has been off for some reason, when I shut the computer down, during shutdown it does display some kind of problems in power management.

So, what do you think?

I'll test it again later in the evening at home, maybe it's really related to this issue...

---

### Post by The_Saint on 2005-10-07
And hello again,

I am so happy. I managed :) turns out that all it needed was a driver for the hotkey.

So, those sites helped me and I am very grateful to them:
[http://mercury.walagata.com/w/epb613/cl56_guide.html](http://mercury.walagata.com/w/epb613/cl56_guide.html)
[http://heim.ifi.uio.no/~krisvh/linux/cl56.html](http://heim.ifi.uio.no/~krisvh/linux/cl56.html)
[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

So, you may close this subject down, it seems, because I managed to make it work finally :)

I presume it wouldn't hurt if someone made this thread a sticky - maybe there are people who are having similar issues.

Thank you people for trying to help me :)

---

### Post by mlomker on 2005-10-07
> I am so happy. I managed :) turns out that all it needed was a driver for the hotkey.


I had given you a link to those switch project sites in my first post.  Which one ended up working for you?

---

### Post by The_Saint on 2005-10-07
Yes, so you did :)

Acer Hotkey driver worked out for me.

All it came down to the issue that today morning I found out from my personal hacker that my laptop is based on Compal CL56. Or the fact that *is* Compal, only bears a different name. And that I didn't know.

If I had known it before I would have managed, because Google was very helpful already when I searched for just 'Compal'.

:)

But thank you anyway. I really appreciate your help.

---

