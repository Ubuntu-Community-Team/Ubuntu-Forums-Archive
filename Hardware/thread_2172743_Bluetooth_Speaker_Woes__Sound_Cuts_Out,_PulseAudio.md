---
title: "Bluetooth Speaker Woes:  Sound Cuts Out, PulseAudio Crashes"
date: 2013-09-06
forum: Hardware
---

### Post by buzzingrobot on 2013-09-06
Bought myself a pair of Bluetooth speakers to use with my new ThinkPad. (They pair as headphones.)

In use, after I've switched the sound output setting to use the speakers, the sound is initially OK.  

However, eventually, i.e, in a few minutes, sound begins to rapidly cut in and out, and finally stops altogether. 

At that point, a look at Sound Settings shows the Bluetooth speakers are no longer set as the output device.  They aren't listed, in fact.  The Bluetooth setting panel still shows them as paired.

Often, but not always, this is accompanied by a Pulseaudio crash report from Apport.

I've looked around for workarounds and fixes.  I haven't found any that work here, but i did find many reports of similar problems.

What I want, of course, is a reliable and persistent pairing of the speakers and a reliable and pesisent routing of sound through them, something that survives rebooting.

Can I fix this?  Or should I get the old speakers and plug them in?

Currently on Ubuntu Gnome 13.04, but I've seen the same behavior on other flavors.

---

### Post by tgalati4 on 2013-09-06
What model Thinkpad and what model speakers?  I would review them both on the web and see if others are having the same problem.  It's possible that the Thinkpad's bluetooth chipset is not up for handling a constant music stream--causing the chip to heat up and stop functioning.

Open a terminal and note the following immediately after a crash:

```
dmesg | tail -100
```

If it is simply a software crash, then you would get consistent logs.  But a hardware crash will often leave no trace, or strange error messages that are not consistent.

And, yes, before wireless, we did use wires.

Try other bluetooth devices--keyboard, headset, etc.  Any strange behavior in those devices like dropped keys or voice dropouts would point to the bluetooth hardware.

Since this is a "New" thinkpad, how was it delivered?  Did a brown truck drop it on the front porch?  Many times, new, delivered, hardware needs to be reseated.  Laptops don't ship well.

I had a Dell laptop that was dropping wireless connectivity at random times.  It simply needed cleaning of the contact points on the mini-card using an eraser and reseating.  No more dropouts.  I would locate the bluetooth radio and reseat it if possible.

---

### Post by buzzingrobot on 2013-09-06
Thanks.  It's a new W530 FedEx'd from Shanghai by Lenovo. I'll take a look at the bluetooth card.

Hadn't occurred to me that the chipset might not be up to it.  

The speakers are a cheap set I bought at a big box, thinking to clear some wires off the desk.

---

### Post by tgalati4 on 2013-09-06
If you have a smartphone, can you pair it with the speakers and play music for a long period of time?  You have 4 failure points:

1.  Lenovo bluetooth transmitter is not working.
2.  Jambox receiver is not working.
3.  Lenovo receiver is not working.
4.  Jambox transmitter is not working.

All it takes is one failure and you have no tunes.  Somehow wires don't have this problem.

So search the house for all of your bluetooth devices and mix and match and see if you can narrow it down.

---

### Post by buzzingrobot on 2013-09-06
I was streaming radio to it. The problem was consistent across different streams.

Sold the smartphone because I never used the smart bits that were costing me $1000 per annum. Have an iPad, though.  Looks like rain this weekend, so I'll check things.

---

### Post by SeijiSensei on 2013-09-07
I can play audio from my Samsung Galaxy S3 phone to my little [Oontz speaker]("http://www.amazon.com/Ultra-Portable-Wireless-Bluetooth-Cambridge-SoundWorks/dp/B008JGR9MO") for hours on end without interruption, so I'm guessing it's a hardware issue as well.

---

### Post by buzzingrobot on 2013-09-07
Cleaned and reseated the card.  Same problem.

Streamed from an iPad.  Same problem.

I'm blaming the speakers.  Back to the wires.

I've wondered if it might be something related to streaming radio, versus feeding in local files.  Since I only do the streaming, though, it's a moot point.

---

### Post by tgalati4 on 2013-09-07
You can test local files versus streaming.  Some wireless cards have the bluetooth radio as well, so streaming wireless creates bluetooth interference--dumb design.  You can check via:


tgalati4@tpad-Gloria7 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 021: ID 0a5c:201e Broadcom Corp. IBM Integrated Bluetooth IV
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tgalati4@tpad-Gloria7 ~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

The bluetooth radio hangs off of USB and the Wireless is connected to the PCI bus, so they are separate radios.  This is for a Thinkpad T43p.  

I'm not sure of the iPad's radio.  You can search one of the teardown websites to expose the internals.  

But definitely check a local mp3 file versus streamed internet radio and see if there is a difference in behavior.  Otherwise back to the Big Box store for recycling.

---

### Post by rthewitt.devel on 2013-12-13
I have this exact problem, with a Lenovo Thinkpad w520, Broadcom BCM2045B.  Running Bluez 4.101-0ubuntu8b1 with Pulseaudio 4.0 on [currently] ubuntu 13.10 atop 3.11.0-14-generic.  (Sending locally stored audio over A2DP)

Syslog errors were often things like:

```
kernel: [269196.845263] Bluetooth: hci0 link tx timeout
kernel: [269196.845275] Bluetooth: hci0 killing stalled connection 94:ce:2c:fa:be:25
```

and

```
bluetoothd[1106]: Audio connection got disconnected
```

and

```
kernel: [263639.422364] Bluetooth: hci0 SCO packet for unknown connection handle 6
```

With the last showing up in dmesg as well.

I tried several things including updating Pulseaudio and Bluez.  I switched to a mainline kernel when I was using 13.04 and eventually upgraded entirely to 13.10 due to unrelated instabilities.

The problem does not appear to originate with Pulseaudio as I temporarily purged it from my machine in favor of alsa, as shown in: [http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/)
 ... and saw the same underlying errors.  I have since returned to pulseaudio when I upgraded to Ubuntu 13.10.


Strong evidence that this is a *hardware* issue is as follows:


[LIST]
[*]I too can stream indefinitely to the JBL Flip speaker from my Galaxy S3.
[*]I have been able to reproduce the problem regardless of underlying audio server
[*]I have been able to reproduce the problem on my dual boot Windows 7 OS. [symptoms only, I don't know where to find error logs]
[*]I have been able to reproduce the problem with my Sony SBH20 Headset
[/LIST]

I do not understand the underlying protocol/hardware.  However as a software developer I would be interested to see if there was any additional information that can be gleaned through tracing the code.  I would need some guidance for this if anyone is interested.  I'm a JVM/Python/Web developer with some sysadmin experience and a working knowledge of C/C++ as a language.

The process for manual connection is as follows for those who need it.  Use Blueman bluetooth manager. (built-in does not work on 13.10 for me)


[LIST=1]
[*]Search while in pairing mode.
[*]Add device
[*]Pair to device
[*]Connect as Headset
[*]Open sound settings.
[*]If headset is present and responsive skip to step #10.
[*]issue ```
pactl load-module module-bluetooth-discover
``` to trigger a refresh.
[*]If it does not appear issue ```
pulseaudio -k
``` and wait a second
[*]If pulseaudio has previously crashed the process may be rogue, so kill it manually via ```
kill -9 <*PID*>
```
[*]Select the headset on sound settings and change the profile to A2DP.  (Blueman is unable to switch profiles for me without this step)
[*]Connect to Audio sink on Blueman
[*]Switch back to Sound settings, click another device (such as laptop speakers), then switch back.
[*]The profile will have reverted again to HFP/HSP, so select A2DP a second time.
[*]Adjust volume - you're good until it breaks again.
[/LIST]


**Odd behavior with streaming video:**
The error appears to be more frequent when streaming video from YouTube. Even when the failure is silent, it will affect Youtube playback for me in Chrome.  The video will often freeze or become choppy until I kill pulseaudio.  I have no explanation for this behavior.  Perhaps the A2DP protocol more closely resembles TCP than UDP.  I would have expected a dumb broadcast with no feedback.

---

