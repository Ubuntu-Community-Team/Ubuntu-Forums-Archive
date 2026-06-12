---
title: "Sound problem after a BIOS update."
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by Mustard on 2006-04-14
I bit the bullet today and finally upgraded my BIOS to the latest version.  The update went smoothly, except for one issue.  Upon updating the BIOS, it was necessary to reload the 'Optimal defaults' after rebooting (or so the instructions said).  My carefully crafted BIOS settings, which I spent many hours fine tuning are now lost. So I boot up and when I get to GDM, my sound card starts looping, playing the drum beat over and over again.  If I react immediately, I can get to tty1 and shut down aplay with a killall aplay command, and from there I can muck around in terminal.  If I hesitate to the system locks up completely.  I can also use recovery mode.  After fiddling with bios setting for a while and looking through cryptic looking log outputs, I eventually decided it would be easier to just pull the sound card out and avoid the problem, so I could actually log in.

(I'd add that I threw in a Kanotix Live CD and it had the same sound looping problem at startup, which is what eventually led me to thinking this is a hardware issue).

I've got Soltek SL-KT400-A4 motherboard (cpu = AMD Athlon(tm) XP 2200+)

The sound card is a pretty standard Creative Sound Blaster that worked out of the box (prior to the BIOS upgrade and resetting BIOS to optimal defaults).

From the error messages it seems to be saying that there is a problem with the IRQ's.

Any advice on this issue would be helpful. :)

Some information that might be helpful for me is how do I find out which devices are using what IRQ's on my system atm.  Where can I look to find this out?

---

### Post by dermotti on 2006-04-14
You sure you don't have an onboard audio controller also? I would look through your bios and disable it.

---

### Post by Mustard on 2006-04-14
[QUOTE=dermotti]You sure you don't have an onboard audio controller also? I would look through your bios and disable it.[/QUOTE]

I do have AC97 onboard sound, which was disabled at the time I still had my Sound Blaster in the PCI slot.  That was one of the first things I changed when I loaded the optimal defaults and then rebooted.  After rebooting from the optimal defaults I turned of the onboard sound, disabled most of the power management settings, disabled parallel port and second serial port, game controller.  All the pci slot settings are set for 'auto' atm.  I could manually set the IRQ's for each PCI slot, but I'm trying to avoid that at the moment.  It could be that when I reseat the card in the slot that it might decide to work again.  I havent done that yet, as I've just logged in after fiddling around with it for a couple of hours.  My main goal atm is to find any advice that people might have and then give it another go later on this evening.

---

### Post by dermotti on 2006-04-14
The easiest thing to try is jsut moving that card to a differnt pci slot.

---

### Post by Mustard on 2006-04-14
[QUOTE=dermotti]The easiest thing to try is jsut moving that card to a differnt pci slot.[/QUOTE]

Yeah, I'll give that a go.  I was just pondering that as an option.  The sound card has always been very particular about which slot it was in.  I usually put it as far away from the graphics card as possible.  It was sitting under the tv tuner card before in the bottom slot, and I was concerned that the tv card was going to make contact with it (because of a bulky tuner thing sitting on the tv tuner card).  I'll try shuffling it up a few pci slots and see how I go.

Thanks for the input too.  I can see there aren't a lot of options really other then tinkering around with the hardware and BIOS settings until the system decides to work.  Initially I had some concerns about what changes I might need to make on the operating system side of things.  After it failed on kanotix though, I figured that no amount of playing with the OS was going to change much (other than some boot options for the kernel maybe?)

---

### Post by Mustard on 2006-04-14
Well, I got tired of browsing through the forums reading random posts, so I decided to shut down and try changing the PCI slot.  I plugged the sound card into the slot above the TV tuner card, then powered up, and had a quick look through BIOS before booting up again.

The GDM login came up and I had no sound loop. :)  Then I realised that I had forgotten to disable the AC97 onboard sound while I was in BIOS, so now it doesnt seem to want to recognise my TV tuner.

/me slaps himself in the head....

It's good that sound is back and I don't have a lockup situation at GDM anymore.  I'll tackle the issue of getting the TV card to work another time.  I'm currently getting this error report in kern.log, which I assume is to do with the TV card (I'm only guessing though)...

```
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Using ACPI for IRQ routing
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 1 of device 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 2 of device 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 3 of device 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 4 of device 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 5 of device 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 1 of device 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 2 of device 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 3 of device 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 4 of device 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.402000] PCI: Cannot allocate resource region 5 of device 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.403000] PCI: Device 0000:00:0b.0 not found by BIOS
Apr 14 15:58:11 localhost kernel: [4294671.403000] PCI: Device 0000:00:0b.1 not found by BIOS
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #1:80000000@0 for 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #2:80000000@0 for 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #3:80000000@0 for 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #4:80000000@0 for 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #5:80000000@0 for 0000:00:0b.0
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #1:80000000@0 for 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.404000] PCI: Failed to allocate mem resource #2:80000000@0 for 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.405000] PCI: Failed to allocate mem resource #3:80000000@0 for 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.405000] PCI: Failed to allocate mem resource #4:80000000@0 for 0000:00:0b.1
Apr 14 15:58:11 localhost kernel: [4294671.405000] PCI: Failed to allocate mem resource #5:80000000@0 for 0000:00:0b.1
```

Everything seems present on the sound card side of things, including the unwanted AC97 onboard sound. :)

```
mustard@slave:/var/log$ lsmod | grep snd
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
```

The search for TV card modules loading brings sadness. :)
```

mustard@slave:/var/log$ lsmod | grep tv
mustard@slave:/var/log$

```

Thanks for the suggestions too, Dermotti. :)

---

### Post by Mustard on 2006-04-27
This has become a bit of an ongoing saga for me, so i'll update my progress.  I've had the sound card and tv tuner running after adding irqpoll to the kernel boot options in grub.  Things were going ok after that, and I actually got my TV tuner to work in overlay mode for the frst time ever.

Lately I installed Dapper on another partition, and I was getting problems with nvidia-glx drivers.  It started locking up on the nvidia splash screen.  My system is being particularly difficult with regards to which slot I can put the cards into.  The best solution is the worse fit unfortunately.  With the sound card in the bottom slot and TV tuner in the slot above, the case of the tuner on the tv card is nearly making contact with the bottom of the sound card.  I suspected that this might be causing some lockups I was experiencing on occasion, so I've been juggling around the card locations and using irqpoll to get around the IRQ complaints when I use any other slots than the ones where they don't fit well together.

---

