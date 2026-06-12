---
title: "Sound disabled after suspend/resume on Vostro 1510"
date: 2008-07-30
forum: Hardware
---

### Post by Frem on 2008-07-30
Sound does not play in any application after suspending and resuming my Dell Vistro 1510 laptop. It will work after a reboot.

```

$ lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

$ lsmod|grep snd
snd_hda_intel         344728  5 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm_oss            42144  0 
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  19 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

I read [here]("https://bugs.launchpad.net/alsa-driver/+bug/200210/+viewstatus") that unloading and reloading the module works for some people.
```
# rmmod snd_hda_intel
ERROR: Module snd_hda_intel is in use

# rmmod $(lsmod | grep snd | cut -d " " -f 1)
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_hwdep,snd_pcm,snd_timer
ERROR: Module soundcore is in use by snd

# rmmod snd_hwdep
ERROR: Module snd_hwdep is in use by snd_hda_intel

```

Any help on module options which fix this, reloading the module, or reloading the module automatically after resume from suspend would be appreciated.

---

### Post by iamvaz on 2008-08-07
Hi:

I have the same problem I guess the module unload problems are due the fact that we still have apps running which are using sound (maybe even GDM) please let me know if you find a solution or work around

BTW is your ethernet working ?? because mine isn't (just wireless)

---

### Post by Frem on 2008-08-07
iamvaz, This is from my install notes (avalible in my sig)
> Getting the Ethernet card to work
from: [http://www.stupent.at/2008/06/22/ubuntu-linux-on-a-dell-vostro-1510-a-review/](http://www.stupent.at/2008/06/22/ubuntu-linux-on-a-dell-vostro-1510-a-review/)
Giuseppe Says:
July 11th, 2008 at 09:02
Hi there, I&#8217;m currently using ubuntu 8.04. I had serious problems with the Realtek RTL8111/8168B Gigabit Ethernet controller (all packets dropped). The module name is r8169. I would like to report that I was able to fix the issue by passing the pci=nomsi parameter to the kernel at boot time. (edit /boot/grub/menu.lst)
--
Additionally, I had to disable the option in Windows Vista which allowed the hardware to be disabled to conserve power.

GDM is not using the sound card. You can check this with the following command:
sudo fuser -v /dev/snd/*

The only thing I've got using it right now is pulseaudio, which should theoretically be handling all that stuff? Or not? I'm not really sure how it works, though I'll probably end up looking that up if nobody else finds a solution.

---

### Post by Frem on 2008-08-17
This [Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/198218") seems relevant.

Temporary fix!
Running "sudo /sbin/alsa force-reload" will reload the sound drivers!

(...and crash the Gnome volume control applet and Firefox, both of which were probably trying to use sound)

---

### Post by gerard67 on 2008-10-08
> **Frem said:**
> This [Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/198218") seems relevant.

Temporary fix!
Running "sudo /sbin/alsa force-reload" will reload the sound drivers!

(...and crash the Gnome volume control applet and Firefox, both of which were probably trying to use sound)


Thank you !

---

### Post by isparkes on 2008-10-16
Strange... For me, it restores the annoying beep in the terminal, but not the real sound that I want to hear.

Curioser and curioser... 

I'm x64, if that makes andy difference.

---

### Post by Frem on 2008-10-16
Could you post your lspci info? Dell sells laptops with a variety of soundcards, and they might swap them out on the same model occasionally.

---

