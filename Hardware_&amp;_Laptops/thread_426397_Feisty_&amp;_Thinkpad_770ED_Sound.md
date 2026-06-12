---
title: "Feisty &amp; Thinkpad 770ED Sound"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by haylocki on 2007-04-28
Yet another thread about sound on thinkpad 600/700 series laptops


Finally got the sound to work on my Thinkpad 770ED whilst running Ubuntu Feisty.

This is How I did it :

[LIST=1]
[*] Upgraded the bios to the latest version on the[ www.lenovo.com]( www.lenovo.com) website.
     (This may not be neccessary, and can break your laptop, so you may want skip  this step.) 


[*] Press and hold <F1> whilst switching on the laptop

you should now be in the bios setup.

click on configuration
then click on initialize. (This should set your bios to the default settings.)
now click on quick boot, and select disable.
next exit and restart the laptop


[*] edit the grub menu.lst file :

```
sudo gedit /boot/grub/menu.lst
```

search for a line starting with :

# kopt=root=

and add the following to the end of the line if not already present :

ro acpi=force pci=noacpi pnpbios=off pci=usepirqmask

now save and close gedit.


[*] edit the modules blacklist

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the following lines :

blacklist snd-cs46xx
blacklist cs46xx
blacklist snd-cs4231
blacklist snd-cs4232

now save and close gedit.


[*]  edit the alsa-base file

```
sudo gedit /etc/modprobe.d/alsa-base
```

and change it to the following :

```
# Alsa 0.9.X kernel modules' configuration file.

# ALSA portion
alias char-major-116 snd
# OSS/Free portion
alias char-major-14 soundcore

##
## IMPORTANT:
## You need to customise this section for your specific sound card(s)
## and then run `update-modules' command.
## Read alsa-driver's INSTALL file in /usr/share/doc for more info.
##
## ALSA portion
#alias snd-card-0 snd-cs4232
alias snd-card-0 snd-cs4236
# You have to specify every damm paramter to get it working:
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
## OSS/Free portion
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
##

# OSS/Free portion - card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

# Set this to the correct number of cards.
options snd cards_limit=1
```

now save and close gedit


[*]  ```
sudo update-modules
```


[*]  ```
sudo modprobe snd-cs4236
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss
```


[*]  edit the modules file :

```
sudo gedit /etc/modules
```

and add the following lines :

```
snd-cs4236
snd-pcm-oss
snd-mixer-oss
snd-seq-oss
```


[*]  make sure you have the universe repositories enabled, then install the following :

```
sudo apt-get install alsa-utils gnome-alsamixer
```


[*]  Run gnome-alsamixer :

     Applications -> Sound & video -> Gnome-alsamixer

Now raise the sliders to your desired settings.


[*]  That's it ! You should now have working sound.
       To test this :
                               System -> Preferences -> Sound

     Click on the test buttons, and you should here a tone.
[/LIST]
These instructions have mainly been taken from this guide :

[http://mepislovers.org/forums/archive/index.php/t-2247.html](http://mepislovers.org/forums/archive/index.php/t-2247.html)

with a few alterations for Ubuntu

Cheers, Ian

---

### Post by Muckubuntino on 2007-05-06
Hi Ian!

Thank you for this "how to".....it works perfectly for me.

I have a Thinkpad 600E with Xubuntu Feisty Fawn...and FINALLY I the sound working! :)

Tanks!

//Muckubuntino

---

