---
title: "Help with nvidia drivers"
date: 2011-12-16
forum: Hardware
---

### Post by z3uSS on 2011-12-16
hy guys

i got an asus k53s series laptop with one nvidia gt 520MX on it and can't use the driver for it on my fresh desktop 11.10 install

i'be installed the driver (cause the app on menu did nothing) with the folowing:

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

this went well, now it looked i had an driver installed (and according to ubuntu was in use) so i went to nvidia x server settings and opened it. there i got this message : "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." ... i said ok ... let's do that ... so i went in  an terminal and typed "sudo nvidia-xonfig" ... all went well .. the system said that i have an new /etc/X11/xorg.conf file updated to the driver. after this all hell broke lose :) i restarted the laptop and ... surprise ... no boot ... it just got stuck to different positions ... so i intrerupted the boot and tried to start X alone ... the message i got was "Fattal error : no screens detected".

so i just rm the /etc/X11/xorg.conf file and here i am ... someone can help me here ? pls ... i reall need the driver ...

---

### Post by z3uSS on 2011-12-17
update : i've tried the IgnoreAbi line in xorg.conf but no luck ... still same issue.

anyone has any ideas ?

---

### Post by xyzzyman on 2011-12-17
If you delete that xorg file it made, you'll go back to it working previously. Do that, and then in a terminal window type 'lsmod' to see if the nvidia driver is loading or if nouveau is still loading.

---

### Post by z3uSS on 2011-12-17
ok .. with xorg.conf deleted i did in an terminal "lsmode" and here is the output:
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
rts5139               351143  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
i915                  566827  2 
iwlagn                314213  0 
asus_nb_wmi            12517  0 
mac80211              462092  1 iwlagn
asus_wmi               20035  1 asus_nb_wmi
joydev                 17693  0 
sparse_keymap          13890  1 asus_wmi
mxm_wmi                12979  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
psmouse                73882  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
mei                    41480  0 
v4l2_compat_ioctl32    17083  1 videodev
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
nvidia              12128043  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              199587  2 iwlagn,mac80211
video                  19412  1 i915
wmi                    19256  2 asus_wmi,mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
ahci                   26002  2 
r8169                  52788  0 
xhci_hcd               82820  0 
libahci                26861  1 ahci

nvidia is present but not in use ... atm i'm in graphic mode but not with nvidia. the funny part is that at the repository driver app it apears i have in use that driver

---

### Post by z3uSS on 2011-12-17
and here is the output of glxinfo:

name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

any ideas ?

---

### Post by xyzzyman on 2011-12-17
Ah, your system has nVidia Optimus. [http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus) Right now you're running with the integrated intel i915 graphics card. I haven't had any experience with that, but if you look up on here and on google I know there are guides on making it work out there. How stable or easy to use IDK. Unfortunately I think it's still quite early as far as linux support goes.

---

### Post by z3uSS on 2011-12-18
> **xyzzyman said:**
> Ah, your system has nVidia Optimus. [http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus) Right now you're running with the integrated intel i915 graphics card. I haven't had any experience with that, but if you look up on here and on google I know there are guides on making it work out there. How stable or easy to use IDK. Unfortunately I think it's still quite early as far as linux support goes.

yep .. did some research 2 this days and found that too. it seems there are 2 ways of dealing with this problem. asus-switcheroo and bumblebee. 
for asus-switcheroo i installed ubuntu 10.10 cause suposaly it had it already installed but wass to unstable and buggy .. so i came back to ubuntu 11.10 and i will try with bumblebee. 

ps: best solution would be if asus makes an bios update for my MB an give me an intrerupt button there ... for the onboard card :)

i'll keep my progress updated here ... maybe some other guys have the same problem.

---

### Post by z3uSS on 2011-12-19
ok ... now with bumblebee :

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee

and after this ... sudo usermod -a -G bumblebee root
i used root because my user account is not integrated in bumblebee.

but bumped in a problem ...
when i optirun something i have lot's of errors

for example at "optirun firefox &" i get "ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored."

still have to do some research ... anyone has some ideas ?

---

