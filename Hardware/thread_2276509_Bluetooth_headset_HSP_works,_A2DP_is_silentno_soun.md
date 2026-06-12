---
title: "Bluetooth headset HSP works, A2DP is silent/no sound"
date: 2015-05-03
forum: Hardware
---

### Post by b00n on 2015-05-03
I have a headset (that is, with microphone) that connects by default as HSP.  When I select [FONT=courier new]System Settings > Sound > Output > Play sound through > [My headset] > Mode: > High Fidelity Playback (A2DP)[/FONT] I get no sound output.  When I go back to HSP, I get sound.

With A2DP selected, when I click [FONT=courier new][My headset] > Test[/FONT], I sometimes get the stereo test pane; sometimes the mono test pane.  With the stereo pane, I never get audio when I click a test button.  With the mono pane I sometimes get audio when I click test, but only sometimes.  This is the only scenario when I get sound with A2DP; it sounds correct (no obvious defects).

I started pavucontrol.  Under HSP, the VU meter shows I have audio.  Under A2DP it also shows audio but at about 1/3 the volume.  Turning up the master volume does not produce any audio in the headphones, though.

I tried
```
dmesg | tail -10
[ 9542.892096] Bluetooth: hci0 SCO packet for unknown connection handle 64511
[ 9542.912150] Bluetooth: hci0 SCO packet for unknown connection handle 0
[ 9542.922147] Bluetooth: hci0 SCO packet for unknown connection handle 65521
[ 9542.932142] Bluetooth: hci0 SCO packet for unknown connection handle 65530
[ 9542.952136] Bluetooth: hci0 SCO packet for unknown connection handle 65521
[ 9542.962078] Bluetooth: hci0 SCO packet for unknown connection handle 65517
[ 9542.982069] Bluetooth: hci0 SCO packet for unknown connection handle 61695
[ 9542.992074] Bluetooth: hci0 SCO packet for unknown connection handle 65523
[ 9543.012076] Bluetooth: hci0 SCO packet for unknown connection handle 65328
[ 9543.022022] Bluetooth: hci0 SCO packet for unknown connection handle 65328
```

However, there is no change (no new lines) when switching between HSP and A2DP.  If I tail -f on /var/tmp/syslog, I see

```
... rtkit-daemon[1364]: Successfully made thread 3559 of process 2038 (n/a) owned by '1000' RT at priority 5.
... rtkit-daemon[1364]: Supervising 5 threads of 1 processes of 1 users.
... rtkit-daemon[1364]: Successfully made thread 3561 of process 2038 (n/a) owned by '1000' RT at priority 5.
... rtkit-daemon[1364]: Supervising 5 threads of 1 processes of 1 users.
```

The first two lines added when I switch to A2DP and the last two when I switch to HSP.  I assume this is normal behavior.

[FONT=courier new]pulseaudio --kill[/FONT] while in A2DP does not cause audio to appear.  It does cause a 2nd headset entry to appear under [FONT=courier new]Play sound through[/FONT].  The 2nd entry goes away after a while (e.g., after I click on various things).

Somebody in another thread about a similar-sounding but to add [FONT=courier new]Enable=Socket[/FONT] to [FONT=courier new]/etc/bluetooth/audio.conf[/FONT] and restart ([FONT=courier new]rfkill block bluetooth && sudo rfkill unblock bluetooth[/FONT]).  No change.

I captured the output of pactl list and attached parts of them as files [FONT=courier new]HSP.txt[/FONT] and [FONT=courier new]A2DP.txt[/FONT] -- "parts of them" as the full file size for each was larger than the Ubuntu Forums upload limit.  I tried to delete only unimportant stuff, but may have chopped something important by mistake.  I am not familiar with the format, so I am not clear if any of the changes are relevant.

Ubuntu 14.04 64-bit, recently updated and rebooted (today).

Any ideas what is the problem, or what I can try/check next?  Thanks.

---

### Post by b00n on 2015-05-03
Somebody in another thread suggested adding [FONT=courier new]Disable=Headset[/FONT] to [FONT=courier new]/etc/bluetooth/audio.conf[/FONT] then restart bluetooth ([FONT=courier new]sudo restart bluetooth[/FONT]).  I did that and tried connecting the headset.  It showed as connected in [FONT=courier new]System Settings > Bluetooth[/FONT] and also appeared in the list under [FONT=courier new]System Settings > Sound > Output > Play sound through[/FONT], but clicking on it never selected it.  I removed the line from [FONT=courier new]audio.conf[/FONT] and did another reset, at which point System Settings crashed (yes, I sent the crash dump).

I'd like to be able to use the headset both ways, but right now I would  like to use the headset for e.g., music, so I am trying to figure out  how to force it to do A2DP only as a workaround for being able to  select.  Suggestions?

---

### Post by tgalati4 on 2015-05-04
It's possible that your bluetooth hardware does not support A2DP.  It's also possible that your headset does not support A2DP.  It's possible that there is a version mismatch between A2DP, since there are some variations in the protocol and how it is implemented.  Sometimes you need to turn off WiFi to get it to work because many bluetooth chipsets use the same antennas or multiplex the bluetooth signal with the WiFi signal.

If this machine is dual-boot, does it work in Windows?

---

### Post by b00n on 2015-05-04
> **tgalati4 said:**
> It's possible that your bluetooth hardware does not support A2DP.  It's also possible that your headset does not support A2DP.  It's possible that there is a version mismatch between A2DP, since there are some variations in the protocol and how it is implemented.  Sometimes you need to turn off WiFi to get it to work because many bluetooth chipsets use the same antennas or multiplex the bluetooth signal with the WiFi signal.

If this machine is dual-boot, does it work in Windows?

Thanks, and some notes:

[LIST]
[*]The headset is a Sony MW600.  I do not see it on Sony's site, but another site from 2010 says it uses A2DP v1.0 -- I do not know if there were sub-models with other A2DP versions, so I might have something different. 
[*]The Bluetooth adapter is an Aircable XR3 [http://www.aircable.net/products/host-xr3.php](http://www.aircable.net/products/host-xr3.php) -- it does not actually say "A2DP" but does say stereo, and see below.  I'll contact them about the A2DP version, but see also below. 
[*]I connected using an Antec BXR-100, and it lets me switch to and play A2DP -- I do not see the BXR-100 on Antec's site, but the "Gain" looks the same and is listed as A2DP v1.2 and another site says the BXR-100 uses v1.2 as well. 
[*]The USB dongle is Bluetooth-only, but that said this computer has WiFi off (in System Settings > Network > Wireless). 
[*]This is a Linux-only machine so I cannot reboot it to try the headset with another OS. 
[/LIST]

I expect since it works with v1.2 (Antec BXR-100) it would also work with v1.0 (Sony MW600).

Any other suggestions/ideas?

---

### Post by b00n on 2015-05-04
I checked with the AIRcable folks; they wrote back (quickly!) to say A2DP is not related to the adapter's firmware but runs on the Linux.  They also suggest a lot of debug is available via BlueZ and in particular from various profiles.  I spent some time browsing online for more, but I have not figured out what to do to extract useful debug info from BlueZ's A2DP.

I should also clarify, when I wrote "I expect since it works with v1.2 it would also work with v1.0" -- that is "expect" as in "stuff I have seen suggests it is backwards-compatible."

---

### Post by tgalati4 on 2015-05-04
I have the same Sony bluetooth headset and I have similar problems.  So it works with old Sony phones, but not with my thinkpad's bluetooth or several random usb-bluetooth adapters that I have tried.  I was never able to figure it out.  Sometimes it would work for a few seconds and then drop out.  Other times it would not switch at all.  Works fine with headset (low-fidelity) profile.  So I assume that it is a bluetooth bandwidth issue.  

My research at the time (a few years ago) seemed to indicate trouble with wifi and bluetooth being used at the same time.  Don't know if V1.2 is backwards compatible with V1.0.  If it doesn't work out-of-the-box, then that is a technology fail.

Try to find other laptops or bluetooth adapters or Sony mp3 players and phones and test with that.  I find that Sony products tend to work with each other, but not necessarily with anything else.  So much for standards.

I got the $70 Sony headset for $10 at a Sony outlet store.  So that should be indicative.

---

### Post by b00n on 2015-05-05
> **tgalati4 said:**
> I have the same Sony bluetooth headset and I have similar problems.  So it works with old Sony phones, but not with my thinkpad's bluetooth or several random usb-bluetooth adapters that I have tried. [...]   

 I find that Sony products tend to work with each other, but not necessarily with anything else.  So much for standards.

Ah, silly me -- it did not occur to me Sony would get wrong something basic.

> Sometimes it would work for a few seconds and then drop out.  Other  times it would not switch at all.  Works fine with headset  (low-fidelity) profile.  So I assume that it is a bluetooth bandwidth issue.

I have a good strong signal; as far as I know there's nothing suspect about the Bluetooth adapter; and I have a fairly fast Linux system (Intel Haswell 2-core/4-thread, 16 GiB RAM, SSD).  Even after a fresh reboot when everything is pretty much idle and empty, I still cannot connect A2DP on the Sony.  But I can use A2DP on the Antec with no problems.  So I'm guessing it has nothing to do with bandwidth and everything to do with Somebody not following the standards (as you say above).

> My research at the time (a few years ago) seemed to indicate trouble with wifi and bluetooth being used at the same time.

I have WiFi off and am using a separate Bluetooth dongle anyway, so I don't think that's the problem in my case :-o

 > Don't know if V1.2 is backwards compatible with V1.0.  If it doesn't work out-of-the-box, then that is a technology fail.

Something like this [https://developer.bluetooth.org/TechnologyOverview/Documents/A2DP_SPEC.pdf](https://developer.bluetooth.org/TechnologyOverview/Documents/A2DP_SPEC.pdf) seems like about the right place to look, but I only see notes on v1.2 to v1.3 and nothing about compatibility.  I think I have seen compatibility discussed elsewhere, and the above is a set of rules that probably ensures compatibility, but I don't see that stated explicitly.

> Try to find other laptops or bluetooth adapters or Sony mp3 players and phones and test with that. 

I got the $70 Sony headset for $10 at a Sony outlet store.  So that should be indicative.

Okay, will do.  I'm not sure what I'll learn, though -- you say you already went through it with essentially the same thing.

---

### Post by tgalati4 on 2015-05-05
All I learned is that my $10 Sony bluetooth headset works ok with older Sony mp3 players and Sony cell phones.  Could not get it to work with any Linux machine (laptop or desktop).  My impression is that it was an early 1.0 implementation of A2DP and that it was buggy.  Later implementations V1.3 and beyond and newer bluetooth headsets work as expected.

---

