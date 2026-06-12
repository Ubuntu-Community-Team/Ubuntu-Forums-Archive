---
title: "Sound not working after kernel upgrade"
date: 2008-09-13
forum: Hardware
---

### Post by smaug42 on 2008-09-13
This is a long standing problem.. and I've yet to figure it out.  The computer is running Kubuntu 8.04 and is fully updated.  No special tweaking to install... basically a default install.

Booted to Kernel 2.6.24-17-server, everything works fine, and the sound modules are loading correctly:

```

lsmod | grep snd
snd_cmipci             38528  4
gameport               16008  1 snd_cmipci
snd_opl3_lib           12928  1 snd_cmipci
snd_mpu401_uart         9728  1 snd_cmipci
snd_seq_dummy           4868  0
snd_usb_audio          83936  1
snd_pcm_oss            42016  0
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq_oss            35456  0
snd_pcm                78596  4 snd_cmipci,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11528  1 snd_pcm
snd_usb_lib            18432  1 snd_usb_audio
snd_seq_midi            9248  0
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            25632  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_hwdep              10500  2 snd_opl3_lib,snd_usb_audio
snd_timer              24836  4 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56868  23 snd_cmipci,snd_opl3_lib,snd_mpu401_uart,snd_seq_dummy,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_usb_lib,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
soundcore               8800  1 snd
usbcore               146028  10 snd_usb_audio,snd_usb_lib,gspca,usbhid,wacom,usb_storage,libusual,ehci_hcd,ohci_hcd

```

If I boot to a newer kernel, for example 2.6.24-21 the sound modules are not loaded, and of course, there is no sound.

Nothing else falls off after a kernel update.. just sound. What can I do to "fix" this so that after a kernel update, sound keeps working?

---

### Post by IntuitiveNipple on 2008-09-13
Can you attach (compressed) copies of /var/log/dmesg, one from the 'good' session and one from when sound fails?

They might give a clue as to what is going on.

---

### Post by smaug42 on 2008-09-15
I've attached the two outputs from dmesg.

One from 2.6.24-17 with working sound, and the other from 2.6.24-21 with no sound.

---

### Post by rizwan1980pat on 2008-09-24
I have installed the following in sequence:



1.Host       : Windows XP Pro SP2 32 bit

2.Middle ware: VMWARE server

3.Guest      : Ubuntu Desktop LTS

4.Tool       : VMWARE tool



All successfully installed, but then I found problem with sound.

---

