---
title: "Sony VGN-FZ11M - (almost) Everything works!"
date: 2008-05-06
forum: Hardware
---

### Post by Contsa on 2008-05-06
Hi all,

My intentions here: 
1) Sum up info spread in many other threads for FZ11M laptop.
2) Spread the word on how Suspend / Hibernate functions keys and Brightness worked for me.

After upgrading to kubuntu 8.04. Had to:
a) For the Sound card: edit /etc/modprobe.d/alsa-base and append this line "options snd-hda-intel model=vaio". After a reboot the mixer go "enhanced" and the speakers get muted when I plug headphones.
b) For the Webcam:  svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) r5u870 to fetch the patched module; make, make install as root and modprobe r5u870 to load the module. To have the module load on boot edit the /etc/modules  and append the line "r5u870".
c) For the NVIDIA drivers I manually installed the 169.12 driver downloaded from the NVIDIA's site, but restricted drivers should be just fine for everyone. (I hope).

d) For suspend/hibernate (my main contribution): After reading [https://help.ubuntu.com/community/SuspendHowto]("https://help.ubuntu.com/community/SuspendHowto") and [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") I made some minor changes in the /etc/default/acpi-support and /etc/X11/xorg.conf . Both files are in the attachment. (in xorg.conf I only added 'Option "NvAGP" "1"' under Device). After a reboot suspend and hibernate worked!
Note that to have suspend and hibernate to work you should first resolve the problem with the webcam. 

e) For Brightness: I have found only one solution that makes use of the nvidia-sttings utility. I change the color-brightness and not the lamp brightness. I am attaching a bash script (dimmer.sh) which takes a single argument: "--inc" to increase the brightness "--dec" to decrease it and "--reset" to reset brightness to the defaults.
   So... unzip it: "gzip -d dimmer.sh.gz"
   copy it to your path: "sudo cp  dimmer.sh /usr/bin/"
   and make sure it is executable: "sudo chmod +x /usr/bin/dimmer.sh"
   and you are ready to go!: dimmer.sh --inc

   The first time you will run this script (and only in case you have never launched nvidia-settings) you will get the nvidia-settings window in order to create the ~/.nvidia-settings-rc file.
   Note that this script will also work if you run it as root. It will guess the user owning the display and act accordingly. It is a patched version of a script I found somewhere in the forums.

f) For Function keys: Most of the function keys function (!?!?). When you do a "acpi_listen" and you play with the function keys you notice that the keypresses are traped by the acpi daemon. So lets fix the brightness keys to execute the dimmer.sh script:
   Edit the acpi event file "sudo pico /etc/acpi/events/sony-brightness-up" or whatever is your favourite editor (vim, kate ...) 
   Replace the content with  
         "event=sony/hotkey SNC 00000001 00000011"
         "action=/usr/bin/dimmer.sh --inc"
The  "SNC 00000001 00000011" is the keypress code you get with acpi_listen. Do some thing with the "sony-brightness-down" file 
and this "SNC 00000001 00000010" key code
   All done! save it and you are ready! 
   Finally restart the acpi daemon "sudo /etc/init.d/acpid restart" 

Hope these work for you too!

Cheers,
KT

NOTE: Step b) (and c if you install nVidia drivers yourself) install kernel modules so they should be repeated each time a new kernel is available.

---

### Post by onejr on 2008-05-11
thx soo much friend :)

---

### Post by thechemist1 on 2008-05-11
just one question 
how do you append to the alsa-base file??
i try to append and save the file and it wont allow me to

thanks in advance

thechemist

---

### Post by Contsa on 2008-05-12
You have to be root to add the extra line "options snd-hda-intel model=vaio".

So you should do something like
"sudo pico /etc/modprobe.d/alsa-base"   or whatever other editor you like (vim, kate ...).

---

### Post by mickymouse on 2008-05-14
i added the line in the alsa-base file, rebooted the x server but nothing changed. should i do i complete reboot?

---

### Post by Contsa on 2008-05-15
> **mickymouse said:**
> i added the line in the alsa-base file, rebooted the x server but nothing changed. should i do i complete reboot?

Probably yes... perhapse you could skip the reboot by unloading some modules or just restart some service... but I am not sure....

---

### Post by mickymouse on 2008-05-16
this is what the alsa-base file contains. Please tell me if i should add or remove some lines ```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=vaio

```
Thanks for your help

---

### Post by Contsa on 2008-05-17
Hi,

I see you have added the line I was proposing but when I run a diff between your alsa-base and mine I get 
"
29,30c29,30
< options snd-bt87x index=-2
< options cx88-alsa index=-2
---
> options bt87x index=-2
> options cx88_alsa index=-2
"

What is the problem you are facing? You dont get sound?

KT

---

### Post by hihihi on 2008-05-20
thanks for your how to,
hybernate/suspend works thanks to your posted link.
cool,
but about brightness:
i dont want to mess the party, but this way we control the color-brightness and not the tl-lamp brightness, which is what we all want and need.
but thanks anyway

---

### Post by Contsa on 2008-05-20
Xm... ok I have updated my initial post

---

### Post by mickymouse on 2008-05-21
> **Contsa said:**
> Hi,

I see you have added the line I was proposing but when I run a diff between your alsa-base and mine I get 
"
29,30c29,30
< options snd-bt87x index=-2
< options cx88-alsa index=-2
---
> options bt87x index=-2
> options cx88_alsa index=-2
"

What is the problem you are facing? You dont get sound?

KT
I get sound but when i plug in the speakers mini-jack the built-in speakers  don't shutdown. they continue to work.
I will change the lines and post back with the results

---

### Post by mickymouse on 2008-05-21
no nothing happend i will do an update to the 8.04 and see what will happen. Thanks for your help though

---

### Post by andr3ib on 2008-05-21
Hello ... do you know something about the compatibility with Sony Vaio VGN-FE890N ?

Please.

---

### Post by Contsa on 2008-05-21
> **mickymouse said:**
> no nothing happend i will do an update to the 8.04 and see what will happen. Thanks for your help though

Sorry, I did not understand that you were using 7.10. The instructions I have posted are for 8.04. I knew the sound problem is unsolved in 7.10 unless you upgrade the alsa server(or something like that) manually. 

KT

---

### Post by tempaznx on 2008-06-10
I tried changing the acpi file, but it says "permission denied."  How do I go around this?

---

### Post by Contsa on 2008-06-11
> **tempaznx said:**
> I tried changing the acpi file, but it says "permission denied."  How do I go around this?

You should be root user. Try from a consol "sudo gedit <your file to edit>"... Or any other editor (kate, kwrite ...)

See  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dadedvd on 2008-07-10
When I run dimmer.sh i recive this error  : mad:

/usr/bin/dimmer.sh: 94: patch: not found


if i run it with sudo i recive a loop with


stdin: is not a tty


Ubuntu 8.04 on Sony Vaio FZ31E

---

### Post by loxan on 2008-10-21
The brightness has been fixed : [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/95444)

---

### Post by Contsa on 2011-09-05
I finally did it!

After three years I updated my Kubuntu 8.04 to 11.04. In my Sony Vaio FZ11M kubuntu 11.04 was unbearable ubuntu was better but it was getting too hot and did not feel "sharp", xubuntu is immature (forgets configurations, wm randomly decides not to start etc).

Anyway.... my biggest problem was the webcam. The r5u870 was not maintained. I had to port it to the new kernel. Quick, dirty, just works for me...

---

