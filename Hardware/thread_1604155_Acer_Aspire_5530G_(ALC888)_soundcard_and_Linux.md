---
title: "Acer Aspire 5530G (ALC888) soundcard and Linux"
date: 2010-10-23
forum: Hardware
---

### Post by go_linux on 2010-10-23
This post tries to summarize a solution to get sound working on Linux with ALSA, specificaly for the ALC888 sound card present on the Acer Aspire 5530G. However I'll try to make this more useful by describing how I got to this solution.


[LIST]
[*]So for those using an Acer Aspire 5530G and are getting frustrated because it emits no sound at all, you can simply edit the file /etc/modprobe.d/sound.
[/LIST]
[INDENT]All others skip to the next section.
[/INDENT][INDENT]Follow these steps:
  - Edit the file /etc/modprobe.d/sound with superuser privileges, for example:
    sudo joe /etc/modprobe.d/sound
  - You should see something along these lines:
      ```
options snd slots=snd-hda-intel,snd-hda-intel
  #SBx00 Azalia (Intel HDA) 
  alias snd-card-0 snd-hda-intel
  # RS780 Azalia controller
  alias snd-card-1 snd-hda-intel
```  - Change it to:
      ```
options snd slots=snd-hda-intel,snd-hda-intel
  #SBx00 Azalia (Intel HDA) 
  alias snd-card-0 snd-hda-intel
  options snd-hda-intel model="acer-aspire-6530g"
  # RS780 Azalia controller
  alias snd-card-1 snd-hda-intel
```  - Save it and restart the sound service or reboot your machine
     on SuSE you can do:
       ```
rcalsasound restart
```     on Ubuntu you can do:
      ```
sudo service pulseaudio stop
  sudo alsa force-reload
  sudo service pulseaudio start
```  - now from the console run the alsa mixer and unmute the channels
      ```
alsamixer
```  - try to play an audio file, preferably from the command line
[/INDENT]
[LIST]
[*]This post may still be useful even if not using an Acer Aspire 5530G, so read this section.
[/LIST]
[INDENT]Why was the Acer Aspire 5530G producing no sound?
The answer to this is that the sound chip in the Acer 5530G is being correctly detected and driver was being loaded, however this wasn't enough because each sound card model connects the inputs/outputs to different channels, that is, the chip is used differently despite being the same.
Because of this the ALSA sound card model auto detection sometimes has trouble identifying the right configuration to the mixer inputs/outputs for present card and as a result the wrong inputs/outputs are selected, that is, the ones that are not connected, as is in this case, or for other cases, the mixer channels don't match the intended function.

So what can be done?
When the auto detection doesn't wor, there is the possibility for the user to supply the model when loading the snd-hda-intel module into the kernel.
This can be done by doing modprobe snd-hda-intel model="modelname" for a single run
or by editing the /etc/modprobe.d/sound so that it is used everytime the computer is restarted.
In the latter case a line must be inserted to the file, a line that looks like this:
```
options snd-hda-intel model="modelname"
```But how do I find the right model or at least what models can I use?
For this I would suggest downloading the ALSA driver sources that match the version that is installed on the computer.
You can find the version by doing:
 ```
cat /proc/asound/version
```Now download and unzip the alsa-driver zip from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

(I recommend finding the availble models from source code because they always have to match the compiled code, so that you're testing all the models that are available for that version.)

Now change directory to alsa-driver-x.x.xx/alsa-kernel/pci/hda

Find the card that you have on your computer by doing: 
```
 lspci -v
```or hopefuly, by doing 

 ```
head -n1 /proc/asound/card0/codec#0
```Open the file that matches the soundcard manufacturer of your card

For our case we open the patch-realtek.c file and look for something like this:
```
static const char *alc882_models[ALC882_MODEL_LAST] = {
   ...
    [ALC883_ACER]        = "acer",
    [ALC883_ACER_ASPIRE]    = "acer-aspire",
    [ALC888_ACER_ASPIRE_4930G]    = "acer-aspire-4930g",
    [ALC888_ACER_ASPIRE_6530G]    = "acer-aspire-6530g",
    [ALC888_ACER_ASPIRE_8930G]    = "acer-aspire-8930g",
    [ALC888_ACER_ASPIRE_7730G]    = "acer-aspire-7730g",
   ...
```So now it's a matter of trying the models in this set or even all possible values that are listed in this file and that match the ALC888 soundcard model.
From this excerpt we can at least try "acer-aspire", "acert-aspire-4930g","acer-aspire-6530g",...
Luckily the acer-aspire-6530g worked fine on the 5530.
So all that had to be done was to add the line
options snd-hda-intel model="acer-aspire-6530g" to the file /etc/modprobe.d/sound

[/INDENT][B]Hope this helps!
Good Luck![/B]

---

### Post by go_linux on 2010-11-16
**--NOTE--**

On SLED 11 SP1 even when applying the above fix, sometimes no sound can be heard from the Acer Aspire 5530G (ALC888 soundcard).
The SLED 11 SP1 comes with Alsa version 1.0.21.

For the card to produce sound it is required to open the sound mixer and unmute both the IEC958 and IEC958 Default PCM channels followed by a sound system restart.

See previous post to know how restart the sound system.

It is possible that sometimes the computer starts with IEC958 muted and so the procedure will have to be repeated.

---

