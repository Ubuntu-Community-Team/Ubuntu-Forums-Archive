---
title: "NO SOUND! Linux Newbie Here."
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by Masahiro on 2005-06-18
Hello,

I am a newbie to Linux and I'm trying to get away from windoze.

Anyway, I managed to tri boot XP, my recovery partition, and Ubuntu "Hoary Hedgehog" with no problems.

But, in Ubuntu, there is absoutley no sound, from programmes like CD Player.

When I attempt to open Volume Control, I get the following error:
No volume control elements and/or devices found.
And Volume Monitor gives this error:
Cannot connect to sound daemon.
Please run 'esd' at a command prompt.

I have tried the command 'esd' at the terminal window but it's still not fixed.

Please can somebody help me?
Many Thanks.
Also, sorry if I have posted in the wrong forum, If I have, please move this and PM me the new forum
THANKS!

---

### Post by Xian on 2005-06-18
Try this for a quick attempt at a fix. 
Open a terminal and issue this command:
```
$ gst-register-0.8
```

---

### Post by Masahiro on 2005-06-18
Nope!

Unfortunatley, I still have the same problem! :(

Thanks for the quick response though.

---

### Post by Masahiro on 2005-06-19
Someone told me on IRC to try these commands and post what came up, so I have:
ashley@computer:~$ modprobe snd-ac97-codec
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Operation not permitted


ashley@computer:~$ sudo tail /var/log/messages
Password:
Jun 19 09:05:52 localhost kernel: usb 3-1: USB disconnect, address 2
Jun 19 09:05:52 localhost kernel: drivers/usb/class/usblp.c: usblp0: removed
Jun 19 09:05:54 localhost kernel: usb 3-1: new full speed USB device using uhci_hcd and address 3
Jun 19 09:05:54 localhost kernel: drivers/usb/class/usblp.c: Disabling reads from problem bidirectional printer on usblp0
Jun 19 09:05:54 localhost kernel: drivers/usb/class/usblp.c: usblp0: USB Unidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0604
Jun 19 09:05:54 localhost usb.agent[10706]:      usblp: already loaded
Jun 19 09:11:43 localhost gconfd (root-10850): starting (version 2.10.0), pid 10850 user 'root'
Jun 19 09:11:43 localhost gconfd (root-10850): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 19 09:11:43 localhost gconfd (root-10850): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 19 09:11:43 localhost gconfd (root-10850): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
ashley@computer:~$

I don't understand those, but would somebody else?
Thanks.

---

### Post by MuLLeR on 2005-06-19
[QUOTE=Masahiro]Nope!

Unfortunatley, I still have the same problem! :(

Thanks for the quick response though.[/QUOTE]
 Do you hear startup sound, when Ubuntu load?

---

### Post by Arktis on 2005-06-19
Not like I can help or anything, but it might be good to list what card you have. Or if your sound is onboard, what chipset you have.

> ashley@computer:~$ modprobe snd-ac97-codec
Looks like you have onboard.  Why didn't you use sudo?

---

### Post by FalcTH on 2005-06-19
[QUOTE=Masahiro]Someone told me on IRC to try these commands and post what came up, so I have:
ashley@computer:~$ modprobe snd-ac97-codec
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_ac97_codec (/lib/modules/2.6.10-5-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Operation not permitted
[/QUOTE]

Try doing this in a terminal:
sudo modprobe snd-ac97-codec
<Enter your password and hit enter>

if theres any output paste it here, then do: sudo tail /var/log/messages.
If THAT doesn't help you should go into an audio player and use eSound (I'm gonna be using XMMS for this example):
Press  CTRL + P
Select "eSound Output Plugin 1.2.10 [libesdout.so]" in the Output Plugin header.
click Apply and then OK, play a song in XMMS and see if it works, if it does: tell us.
If it don't: Tell us what error message you get.

Good luck.

---

### Post by Masahiro on 2005-06-19
[QUOTE=FalcTH]Try doing this in a terminal:
sudo modprobe snd-ac97-codec
<Enter your password and hit enter>

if theres any output paste it here, then do: sudo tail /var/log/messages.
If THAT doesn't help you should go into an audio player and use eSound (I'm gonna be using XMMS for this example):
Press  CTRL + P
Select "eSound Output Plugin 1.2.10 [libesdout.so]" in the Output Plugin header.
click Apply and then OK, play a song in XMMS and see if it works, if it does: tell us.
If it don't: Tell us what error message you get.

Good luck.[/QUOTE]
 Nope, still no sound.

And I can't find eSound.

---

### Post by JediPottsy on 2005-06-19
I have the same problem with
ATI IXP150 AC97 onboard sound

someone said do

pci=noapci

whats that?

---

### Post by Masahiro on 2005-06-19
[QUOTE=JediPottsy]I have the same problem with
ATI IXP150 AC97 onboard sound

someone said do

pci=noapci

whats that?[/QUOTE]
 @JediPottsy : Same here, somebody told me how to add that, but still not fixed.

If you do happen to get it fixed, be sure to post so that I and others in the future can solve this annoying problem quicker.

---

### Post by JediPottsy on 2005-06-19
hi, how do i add pci=noapic and also how do i

"disable the detection of the ATIIXP modem driver detected by alsa"
?

i now have volume monitor working, via this, i think i just need to diable my modem or modem drivers.

[http://ubuntuforums.org/showthread.php?t=26567&highlight=sound+hoary](http://ubuntuforums.org/showthread.php?t=26567&highlight=sound+hoary)

---

### Post by FalcTH on 2005-06-19
You would just have to make the sound card use alsa, but not disable the moem completely. Doing that would be inefficient.

How you do that is beyond me, though. :/

---

### Post by JediPottsy on 2005-06-19
[QUOTE=FalcTH]You would just have to make the sound card use alsa, but not disable the moem completely. Doing that would be inefficient.

How you do that is beyond me, though. :/[/QUOTE]
 i dont care about the modem

---

### Post by JediPottsy on 2005-06-19
got sound to work via this:

for ATI IXP with ATI IXPmodem - the modem is taking over, so follow this

```

sudo apt-get install build-essential
sudo apt-get install kernel-headers-$(uname -r)
sudo apt-get install alsa-source

sudo dpkg-reconfigure alsa-source
 ## choose "no" to PnP, "Yes" to debug, and then scroll down to choose ATIIXP - do not choose ATIIXP-MODEM


cd /usr/src
sudo tar xfj alsa-driver.tar.bz2
cd modules/alsa-driver
sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r) KVERS=$(uname -r)

ls ../*.deb
## something like modules-(kernel version)_1.0.8-4ubuntu_i386.deb should appear - this is gud

dpkg -i ../*.deb
cat /proc/asound/modules
## up should pop

## 0 snd_atiixp
## 1 snd_atiixp_modem

[CHOICE 1]
alsamixergui
##in this make sure everything is unmuted and then make all volumes max

[CHOICE 2]
go to applications> sound & video> volume control, make sure that both devices have all things enabled - ie "edit > preferecnes" make sure all things are selected, and then unmute and max all controls.

http://ubuntuguide.org/#configuresoundproperly


```

now ctrl+alt+backspace and sound should work :D

---

### Post by Jonax on 2005-07-05
^ Just registered to say a very grateful Thank You to JediPottsy - This does indeed work on Ubuntu (not sure on Kubuntu) for a Toshiba Satellite A60 :D

Few points though:
- Some of the backports in the sources.list file will have to be uncommented if not already.  The alsa-source (and probably the other alsa packages) had to be gotten from the Universe repositories (GB for me) because the others didn't seem to have that module
- Get the relevant linux_headers package before you start the binary_modules command.  Otherwise, you're just going to get an error message telling you to get them anyway.
- Not sure on referring to the Unofficial Ubuntu Guide at the end.  asound.conf wasn't in /etc/ so I grabbed the sample and put that in just in case.  Likewise, Step 10 can be ignored as there is no libesd.so.0 in /usr/lib/ to begin with.  

However, the end result is that for the first time in four distros & countless weeks of patience all that's standing between me & ditching WinXP is getting Cedega to work :D

---

