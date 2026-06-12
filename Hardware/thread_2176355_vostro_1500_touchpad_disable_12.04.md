---
title: "vostro 1500 touchpad disable 12.04"
date: 2013-09-23
forum: Hardware
---

### Post by chrtylee on 2013-09-23
no i do not have a hardware switch, and if there is a fkey button its not listed. on windows i had to install the driver from synaptics cuz the dell driver is only for xp/2000 and i upgraded to win7, for some reason it didnt show in device manager so i couldnt disable that way either.

---

### Post by varunendra on 2013-09-23
You should edit your original post to elaborate your question on what you have and what you want. So you **want to disable the touchpad when the external mouse is plugged in** (for others - I know from a previous post of the OP).

While others here may be able to suggest a simple and straightforward way to do that, let's just take a look at the drivers that are loaded when the external mouse (USB I assume) is plugged in. So please connect your USB mouse, and post back the outputs of-
```
lsmod
xinput
```

---

### Post by chrtylee on 2013-09-23
```
chris@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
snd_hda_codec_idt      71153  1 
arc4                   12573  2 
snd_hda_intel          44339  5 
b43                   392109  0 
snd_hda_codec         141761  2 snd_hda_codec_idt,snd_hda_intel
i915                  620419  3 
r852                   18241  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_intel,snd_hda_codec
sm_common              16860  1 r852
nand                   59304  2 r852,sm_common
mac80211              630977  1 b43
snd_seq_midi           13324  0 
mtd                    45243  2 sm_common,nand
drm_kms_helper         49597  1 i915
snd_rawmidi            30417  1 snd_seq_midi
drm                   287564  4 i915,drm_kms_helper
nand_ids               12723  1 nand
snd_seq_midi_event     14899  1 snd_seq_midi
bnep                   18258  2 
nand_bch               13147  1 nand
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
gpio_ich               13526  0 
parport_pc             28284  0 
bch                    22063  1 nand_bch
cfg80211              525244  2 b43,mac80211
snd_timer              29989  2 snd_pcm,snd_seq
psmouse                97873  0 
coretemp               13596  0 
r592                   18144  0 
rfcomm                 47864  0 
ppdev                  17113  0 
i2c_algo_bit           13564  1 i915
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ecc               13273  1 nand
memstick               16605  1 r592
bluetooth             247024  10 bnep,rfcomm
lp                     17799  0 
snd                    69533  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17144  0 
serio_raw              13215  0 
dell_wmi               12681  0 
dell_laptop            17425  0 
joydev                 17613  0 
sparse_keymap          13890  1 dell_wmi
soundcore              12680  1 snd
bcma                   41244  1 b43
wmi                    19256  1 dell_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
dcdbas                 14449  1 dell_laptop
mac_hid                13253  0 
video                  19652  1 i915
parport                46562  3 parport_pc,ppdev,lp
microcode              23017  0 
b44                    35967  0 
hid_generic            12540  0 
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
ssb                    57842  2 b43,b44
usbhid                 47346  0 
usb_storage            61749  1 
hid                   105549  2 hid_generic,usbhid
```

```
chris@ubuntu:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice     id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]
```

---

### Post by chrtylee on 2013-09-23
SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]     im guessing i somehow wanna disable this, but i will also need to know how to reenable it just in case, is it possible to create scripts on my desktop? like a shortcut to enable/disable

---

### Post by varunendra on 2013-09-23
I think I just found a solution at least better than dealing with the drivers. It is based on the detected IDs of your two pointing devices (although I'm not sure if it remains the same across next boot) -
> **chrtylee said:**
> 
chris@ubuntu:~$ xinput
&#9121; Virtual core pointer                        **id=2 **   [**master** pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; **reserved Dynex Watermelon Wireless Mice     [COLOR="#006400"]id=9[/COLOR]**    [slave  pointer  (2)]
&#9116;   &#8627; **SynPS/2 Synaptics TouchPad                  [COLOR="#FF0000"]id=11[/COLOR]**    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
....
Please try -
```
xinput --float 11
```
It should disable your touchpad without messing with the driver (which is often too touchy in case of wireless devices).

To re-enable it -
```
xinput --reattach 11 2
```

If this works as expected, reboot and see if the IDs (2, 9, 11) remain the same for same devices (Virtual core, wireless mouse, touchpad). If not, change the IDs to whatever they become on next boot. I'd love to make this as easy as a single click on something, but don't think I'm upto it right now ;)

Let me know how it works.

**PS:**
Please always use 'Code' box to post commands and outputs. It preserves the formatting and makes the post look clean, compact and more readable. Please follow the "Using Code Tags" link in my signature to see how. You may wish to edit your above post afterwards to do that. It looks 'scary' in its current form :P

**PPS:**
Just noticed your next post. I'd love to do the scripting adventure. Just let me know if the IDs remain the same across different boots. Even if it doesn't, I think we can still conjure a "double-click" script, only it'll become a bit longer :)

---

### Post by chrtylee on 2013-09-26
you disbaled my keyboard, thankfully i have one for my destop. the "Renable" command gave me this error

```
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  43 ()
  Device id in failed request: 0x17
  Serial number of failed request:  18
  Current serial number in output stream:  19
```


```
xinput --float 11
``` does not maintain across reboots, keyboard works again

---

### Post by varunendra on 2013-09-26
> **chrtylee said:**
> you disbaled my keyboard, thankfully i have one for my destop.
Oops ! Sorry for that. Although I knew it is a temporary change, I should have warned you in advance, you can slap me on the butt for my ignorance.. 8-[

I somehow had an idea that these IDs get changed across reboots (probably a "who's detected first" case), but wasn't sure. Fortunately, there is an option to use the full names of the devices instead of their XIDs. This option has no chance of mistakes as happened in the ID confusion above, because the name string can go wrong only if the device is not present at all, in which case, the command will simply do nothing.

So please try this (across several boots, and I'm confident this time) -
```
xinput --float "SynPS/2 Synaptics TouchPad"
xinput --reattach "SynPS/2 Synaptics TouchPad" "Virtual core pointer"
```

If it works as expected, and I'm confident it always will, we can create a script and place it on your desktop. To go even further, we can even try to create a launcher button (if you are using Unity) or a launcher icon so as to be able to do this with a single click (or double in case of a launcher icon). Not sure if the 'launcher button' idea is too ambitious though. :P

But please first post back if you are satisfied with the solution above. If yes, post back the output of -
```
xinput
```
again from the state when the touchpad is disabled. We can then create a single script to handle both the enable and disable operations.

---

### Post by chrtylee on 2013-09-28
enabled ```
Vostro-1500:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice     id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]


```

disabled

```
 Vostro-1500:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; reserved Dynex Watermelon Wireless Mice     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]
&#8764; SynPS/2 Synaptics TouchPad                  id=11    [floating slave]

```


this was done after clean boot,  clean install too. the disable script obv works, i also tested the enable script which also worked (:

---

### Post by chrtylee on 2013-09-28
my daughter likes to press the power button while i do stuff, could i same thing with ```
xinput --float "Power Button"
```

---

### Post by varunendra on 2013-09-28
> **chrtylee said:**
> this was done after clean boot,  clean install too. the disable script obv works, i also tested the enable script which also worked (:
Great !! Would you like to share your script with us here? I'd like to see if it is already better than I can think of. :)

> **chrtylee said:**
> my daughter likes to press the power button while i do stuff, could i same thing with ```
xinput --float "Power Button"
```

Sure you can, but I think the one you see in the output of xinput is for the power button on the keyboards, probably not the main power button that sends direct (or through operating system's acpi controls) signal to the motherboard.

If you try that, you'll have to "--reattach" it with "Virtual core keyboard".

If you consider it solved, please mark the thread as such (using "Thread Tools" link above the top post), or post back your script and wait while I can conjure mine (if I could :P).

---

### Post by chrtylee on 2013-09-28
i just assumed it was the laptops power button, but i didnt write a script for the desktop like i was asking you for, by script i just meant the commands you gave me...idk the first thing about writing a script like that. would i just put the code in a notepad and save with .sh file extension?

---

### Post by varunendra on 2013-09-29
> **chrtylee said:**
> would i just put the code in a notepad and save with .sh file extension?
Yeah, something like that.

Usually a script starts with the line #!/bin/bash *(or sh or whatever shell interpreter you prefer)*. The next lines are your commands, and optionally - comments (the lines that start with '#'). So basically it is nothing but a list of commands, only it makes use of variables and complex routines much more easier.

Assuming you are using the default Ubuntu with Unity desktop, you can do the following to make it all easy and fun (Point A is the main script, Points B and C are just ways to make it also usable via Unity GUI.) -

[COLOR="#800000"][SIZE=3]**A. _Creating a script to Enable/Disable the touchpad_ :**[/SIZE][/COLOR]

**1)** Open Gedit and copy-paste the following in it -
```
#!/bin/bash
# Script to Enable/Disable the touchpad

# If you wish to use this same script on another laptop, you only
# need to change the value of 'TARGET' in the Definition below to
# its touchpad name, which you can find with "xinput" command

MASTER="Virtual core pointer"
TARGET="SynPS/2 Synaptics TouchPad"
STATUS=`xinput | grep "$TARGET" | grep -c floating`

# Function to enable/disable the touchpad

if [ $STATUS -eq 0 ]; then
	xinput --float "$TARGET"
else
	xinput --reattach "$TARGET" "$MASTER"
fi

```

**2)** Save this script in your Home folder with a name that is simple and unique. For this example, we save this file as "**ToggleTP.sh**"

**3)** Make this script executable. Either do it via gui (right-click > Properties > Permissions tab > Allow executing the file....) or in a terminal -
```
chmod +x ./ToggleTP.sh
```

**4)** Now let's create a symlink with name "**ctp**" (**C**razy **T**ouch**p**ad, hence the name ;)) so that you can enable/disable it by just typing "ctp" in the terminal -
```
sudo ln -sT /home/$USER/ToggleTP.sh /usr/sbin/ctp
```

Now your script is ready to work. To test it, just type **ctp** in terminal and press Enter. If it is enabled, it will get disabled. To enable it again, just type and enter **ctp** again.


[COLOR="#800000"][SIZE=3]**B. _Creating a Launcher with an Icon to be able to run it from Unity Dash_ :**[/SIZE][/COLOR]

**1)** Open Gedit and copy-paste the following :
```
[Desktop Entry]
Name=Crazy Touchpad
Exec=/usr/sbin/ctp
Icon=/usr/share/icons/Humanity/devices/48/input-mouse.svg
Type=Application
```
Things to remember in above -
[LIST]
[*]The first and last line must be same.
[*]The name "**Crazy Touchpad**" can be changed to whatever name you like. It will appear with the same name in Unity launcher (regardless of what is the name of the .desktop file).
[*]This launcher won't work if the symlink we created above is deleted or renamed ('/usr/sbin/**ctp**'). To make it work, either change this value to the new symlink you created, or directly point it to your script file (for example: **/home/chris/ToggleTP.sh**).
[*]Similarly, the value of '**Icon**' can be changed to point to some other icon you like. Make sure it satisfies the properties of an icon.
[/LIST]

**2)** Proofread to make sure the Name, path and filenames are correct, then save the file as "**CrazyTouchpad.desktop**" in the **.local/share/applications** folder in you home. *(Create the folder beforehand if it does not exist. Since **.local** is a hidden folder, you may have to enable "View > Show Hidden files" (or **Ctrl-H**) in the file-manager)*. Make sure there is no blank space in the file name.

Now open dash, and type "Crazy", the launcher icon should jump out in front of you. Click it and see if it works (it will, if everything is correct above). In some systems, it may take a log-off, re-login to make it appear if Unity is too laggy.

[COLOR="#800000"][SIZE=3]**C. _Locking The Icon to Unity Launcher_ :**[/SIZE][/COLOR]

**1)** Open '**dconf Editor**' from dash *(in 12.04, you may have to install it first with "sudo apt-get install dconf-tools")*

**2)** Navigate to "desktop > unity > launcher"

**3)** Click on the Value of **favourites** to edit it. It should look something like -
```
['nautilus-home.desktop', 'firefox.desktop', 'libreoffice-writer.desktop',......]
```

**4)** To add the launcher, say below firefox icon, add **'CrazyTouchpad.desktop'** after it, so that it now looks like -
```
['nautilus-home.desktop', 'firefox.desktop', **'CrazyTouchpad.desktop',** 'libreoffice-writer.desktop',......]
```
Press 'Enter' to save the change, and its icon should immediately jump up in the Unity Launcher below Firefox icon.

Click and enjoy.. :popcorn:
And don't forget to post back how good or bad it works.. :P

---

### Post by chrtylee on 2013-09-29
ill just go with the ctp command, i cant create files or folders in the local folder

---

### Post by varunendra on 2013-09-30
> **chrtylee said:**
> ill just go with the ctp command, i cant create files or folders in the local folder

Can't or won't? If you don't want to create those files/folders, no problem, although it doesn't cause 'any' side effect at all, except that you'll have one more item in Unity dash menu.

But if you mean you're unable to do that, may be you tried in wrong place *(outside of your Home folder)*, or didn't enable hidden file view *(did you notice the '**dot**' (**.**) in the folder name "**.local**"? That dot is what makes files and folders hidden in linux)*. If that's what you mean, here's an easy way to create it -
```
mkdir -p ~/.local/share/applications
```
It will create all the parent directories (.local, share) as well if they don't already exist (and won't harm if they already exist). If you use software like "wine", it must already be there.

Then, you can create the .desktop file and save it on desktop (if having trouble finding the .local hidden folder). To move it from desktop to the correct location -
[code]mv ~/Desktop/CrazyTouchpad.desktop ~/.local/share/applications/[code]
..and done.

Not compelling you, just putting up an optional way to do it in case you had problems.

But glad it's working for you, I learned something new in the process too!

---

### Post by chrtylee on 2013-09-30
on my laptop it wouldnt let me do anything in that folder, unless theres more than one local/share? i went to file system, the usr/local/share and there was no applications folder but i couldnt create it. but the ctp command in terminal is fine with me

---

### Post by varunendra on 2013-09-30
> **chrtylee said:**
> i went to file system, the usr/local/share
Exactly what I suspected. :)

It is not the **/usr/local** *(note that there is no dot (**.**) in this "local", and it is in **/usr** folder)*, but the one in your Home folder -- **/home/<your user name>/.local** --note the dot (**.**) here which makes it 'hidden', and it is within your Home folder, where you have full permission to do anything you want.

Normal way to see these hidden files/folders :

Open your Home folder > press **Ctrl+H** to make hidden folders visible.

You will now see a number of folders and files with their names beginning with a dot (.). See if the **.local** folder is among them. If not, you can either manually create it (don't forget the dot in its name) or with a single "**mkdir -p**" command as I posted previously.

---

