---
title: "No sound, Toshiba Dynabook TX/65D, Sound card: Intel 82801G (ICH7 Family)"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by uuser_ms on 2007-10-26
Hi
I have big problems to get sound on my new [COLOR="Red"]Toshiba Dynabook TX/65D Laptop[/COLOR]. I installed [COLOR="Red"]Ubuntu 7.10[/COLOR] already few times with different settings. Kubuntu 7.10 too. Nothing helps. There is [COLOR="Red"]no sound[/COLOR] when trying to play anything. Volumes in alsamixer and all other mixer applications are [COLOR="Red"]100%[/COLOR] and there is definitely [COLOR="Red"]no mute setting[/COLOR] turned on. Still no sound.

lspci output :
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

cat /proc/asound/cards output;
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 21

lsmod | grep snd:
snd_rtctimer            4384  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

Ive been struggling with it for few weeks already and I cant get any sound. I would be gratefull for any help.
Ubuntu User

---

### Post by sw_ on 2007-10-26
you have a toshiba with intel HDA and gutsy - possibly the worst combination ever...

in 7.04 i somehow managed to get the sound working with the DSDT hack, but it dosen'T work with 7.10 - and the developers don't seem to care...

i've been struggeling since the dey gutsy came out to fix the sound but i also didn'T have any luck.

seens the problem is the toshiba BIOS - at boot i always  get the "can't allocate device bla bla"

and the adress seems to match my sound card

so good luck to you...

---

### Post by uuser_ms on 2007-10-26
You are probably right. It can be tough to make it work but I really have to. I deinstalled windows and I really dont want to install it again. Ubuntu is perfect if it werent for that sound card problem.
Please, does anybody have a solution ?
Ubuntu User

---

### Post by xphelanx on 2007-10-26
I'm having the same issue with a Toshiba U305-S5077. I've tried everything I've found on the forums and it just doesn't seem to do it. The last thing I tried makes it so my volume controls tells me there's no sound card there even though it still shows up in Hardware Information. *sigh* Well, Hopefully we'll be seeing a solution to this soon.

---

### Post by uuser_ms on 2007-11-09
No replies ?

---

### Post by kazik1616 on 2007-11-20
The same problem with this laptop. Any ideas?

> **xphelanx said:**
> I'm having the same issue with a Toshiba U305-S5077. I've tried everything I've found on the forums and it just doesn't seem to do it. The last thing I tried makes it so my volume controls tells me there's no sound card there even though it still shows up in Hardware Information. *sigh* Well, Hopefully we'll be seeing a solution to this soon.

---

### Post by Renfield on 2007-11-21
I seem to be having the same problem with my Toshiba equium A100-549.
sorry, i have no solution yet.

---

### Post by kavatzoulas on 2007-11-21
hello
i have the same problem with my Toshiba satellite P100-437 .
in 7.04 i found the solution with shuting down the acpi,in 7.10 i haven t found yet a solution but i tried another distro (open suse 10.3) and the sound WORKS FINE so i think that somebody that is a guru can make something to works the sound with UBUNTU that would be nice.

---

### Post by nicbell10 on 2007-11-21
I have the Same problem, Toshiba Tecra A7... the same with both Kubuntu and Ubuntu...

---

### Post by kavatzoulas on 2007-11-21
> **nicbell10 said:**
> I have the Same problem, Toshiba Tecra A7... the same with both Kubuntu and Ubuntu...

i was an owner of a7-248

try this one

**sudo nano /boot/grub/menu.lst**

find the option **# defoptions** and changed it to **# defoptions=acpi=off**
if its written **# defoptions=quiet splash** changed it to **# defoptions=quiet splash acpi=off** or if its written 
**acpi=off apm=on apm=power-off**

press** CTRL+X** then press** Y**and **ENTER**

**sudo update-grub**

its all done

i hope i helped you

---

