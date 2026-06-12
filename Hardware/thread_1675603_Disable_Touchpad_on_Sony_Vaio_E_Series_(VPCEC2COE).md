---
title: "Disable Touchpad on Sony Vaio E Series (VPCEC2COE)"
date: 2011-01-25
forum: Hardware
---

### Post by d3ngar on 2011-01-25
Hi,

I have a Sony Vaio laptop. Nice machine and works well and fast.

Only problem came up recently: the touchpad wasn't working at all. Then, when I upgraded to 10.10 it started working all of a sudden, but it's not recognised as a touchpad and I can't easily disable it through the preferences.

I keep hitting the damn thing while typing too :(

Is there a way that I can switch it off the hard way?

Here is the ixinput output:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Imperator                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Imperator                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

Any help much appreciated.
I will keep trying and post the output here...

thanks

---

### Post by pi/roman on 2011-01-26
Place this script to toggle your touchpad in a file:

```
# toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "ImPS/2 Generic Wheel Mouse" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 1
else xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 0; fi
```move it to /usr/bin then you can toggle your touchpad by pressing alt/f2 and typing the name of the script.

 you can also go to "gnome-keybinding-properties" and add a new shortcut using the path to the script for the command (/usr/bin/name of script) and make a keyboard shortcut.

To disable automatically you can add this command to startup applications
```
xinput set-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 0
```

---

### Post by d3ngar on 2011-02-01
> **pi/roman said:**
> Place this script to toggle your touchpad in a file:

```
# toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "ImPS/2 Generic Wheel Mouse" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 1
else xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 0; fi
```move it to /usr/bin then you can toggle your touchpad by pressing alt/f2 and typing the name of the script.

 you can also go to "gnome-keybinding-properties" and add a new shortcut using the path to the script for the command (/usr/bin/name of script) and make a keyboard shortcut.

To disable automatically you can add this command to startup applications
```
xinput set-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 0
```
Excellent, this really did the trick right away. I couldn't be happier :)

---

### Post by wchouser3 on 2011-08-06
I too have a sony vaio...and I really really need to disable this damn mousepad....h


how exactly do I place script into the folder you described? I've already bumped into the damn thing eleven times just typing these two sentences. I'm fairly new to ubuntu, and by that virtue...Linux

---

### Post by techtabu on 2011-08-06
I also have the same problem with touchpad. Needed to off sometimes. but don't know how to. I am completely new to Ubuntu, so I don't know much. Can you please let me know how to do turn off and on the touch pad? I mean, can you please give me some more additional details like how to write the script file, how to save it (name and extension) etc. Thanks.

---

### Post by stafford.ritchie on 2011-08-10
> **techtabu said:**
> I also have the same problem with touchpad. Needed to off sometimes. but don't know how to. I am completely new to Ubuntu, so I don't know much. Can you please let me know how to do turn off and on the touch pad? I mean, can you please give me some more additional details like how to write the script file, how to save it (name and extension) etc. Thanks.

This took me a while to figure out, so I hope I can save you some frustration.  The above instructions from pi/roman did not work 'out of the box' on my E Series, so I modified them.  Thank you for the starting point, pi/roman!  Here is how I disable the touchpad:

- Open a terminal: click the ubuntu symbol, then type "terminal" and hit enter.
- Create a file: type "pico /usr/bin/touchpad_toggle.script" then hit enter.
- Paste the following into the file
```
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 1
else xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 0; fi
```- Save the file: type Ctrl-X, type "Y", then hit enter.
- Open Keyboard Shortcuts:  click the ubuntu symbol, then type "Keyboard Shortcuts" and hit enter.
- Add a new shortcut: Click Add, type "Touchpad Toggle" for the name, hit tab, type "/usr/bin/touchpad_toggle.script" for the command, then click Apply.
- Allow the file execute mode: In a terminal, issue the following command
```
chmod +x /usr/bin/touchpad_toggle.script
```
- Assign the shortcut to a key: Scroll to the bottom of the list, click on the Shortcut column of the Toggle Touchpad line, hit the ASSIST button on your keyboard, then click Close.
-Try it out: Hit the ASSIST button on the keyboard.  Your touchpad should now be disabled, and you should be able to type without accidentally clicking.  Hit the ASSIST button again.  Your touchpad should now be enabled.
- Rejoice: Good work!  You've done well.

hth

-Stafford

---

### Post by techtabu on 2011-08-10
Thanks stafford.. I will try it soon..

---

### Post by techtabu on 2011-08-10
I am sorry, Staffort I did not work for me. I forgot to mention that I use HP dv6-3250us. I think if I could give you the xinput out put, it may help you.

 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Microsft Microsoft Wireless Desktop Receiver 3.1	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
    &#8627; Microsoft LifeChat LX-3000              	id=12	[slave  keyboard (3)]
    &#8627; Microsft Microsoft Wireless Desktop Receiver 3.1	id=14	[slave  keyboard (3)]

Honestly, I did not understand the code, so I did not try to correct. But I hope it will be okay if I change the name of the mouse. Am I right?

---

### Post by stafford.ritchie on 2011-08-11
> **techtabu said:**
> 
[...]

SynPS/2 Synaptics TouchPad

[...]

Honestly, I did not understand the code, so I did not try to correct. But I hope it will be okay if I change the name of the mouse. Am I right?

Try replacing all occurences of "PS/2 Mouse" in your script file with "SynPS/2 Synaptics TouchPad" and let me know what happens.  You can use pico or similar from the command line or use the Text Editor from the gdm to edit your existing file.

---

### Post by BeeDee on 2011-08-11
Thanks **pi/roman** and **stafford.ritchie**, my two-week-old HP Pavillion DM1 is now working 99% perfectly. HP's touchpad is a bugger to control, on that all of the reviews (using windoze 7) of this laptop agreed.
Now I just need to get right-click tapping to work and I'll be a happy camper.

HP Pavilion dm1-3101ea (dm1z in USA)
LinuxMint 10 (Julia)
Kernel 2.6.35-22 Generic
Gnome 2.32.0

---

### Post by techtabu on 2011-08-11
Thanks Stafford. This time Ubuntu gives me an error message saying "Error while trying run (/usr/bin/touchpad_toggle.script)
which is linked to the key (<Control><Alt>apostrophe). I have attached the screen shot displaying code and error message.

---

### Post by stafford.ritchie on 2011-08-11
My aplogies, techtabu, I forgot to list the following step.  I've edited my post to include the instruction.

> **stafford.ritchie said:**
> 
- Allow the file execute mode: In a terminal, issue the following command
```
chmod +x /usr/bin/touchpad_toggle.script
```

---

### Post by techtabu on 2011-08-12
Job done.. Brilliant Stafford. Thank you so much and my apologies for giving you so much trouble with every single line of code and procedures..

---

### Post by 10o on 2011-08-25
I also keep on hitting the touchpad when typing! Sony's preassigned shortcut [Fn]+[F1] does not respond, neither can I assign it.
On the new F-series (Sony Vaio VPCF22L1E) the script **does not work**, unfortunately. In terminal it outputs:
```
unable to find device PS/2 Mouse
[: 4: =: unexpected operator
unable to find device PS/2 Mouse

```

---

### Post by stafford.ritchie on 2011-08-25
> **10o said:**
> I also keep on hitting the touchpad when typing! Sony's preassigned shortcut [Fn]+[F1] does not respond, neither can I assign it.
On the new F-series (Sony Vaio VPCF22L1E) the script **does not work**, unfortunately. In terminal it outputs:
```
unable to find device PS/2 Mouse
[: 4: =: unexpected operatort
unable to find device PS/2 Mouse

```

The script I tweaked and provided above will only work if the device named in the script matches verbatim the device listed in your xinput list.  You will need to edit the script according to the name of the appropriate device your machine reports in your ixinput list.

---

### Post by 10o on 2011-08-26
Got it working now!
My thanks to pi/roman and stafford.ritchie.

Found out (with HardInfo) that my device goes by the name of "**SynPS/2 Synaptics TouchPad**".
Thus, on my Vaio F-series VPCF22L1E the script goes like this:

```
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
else xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0; fi
```

Placed this code in the file **/usr/bin/touchpad_toggle.script** and assigned the script to the [ASSIST] button, since [Fn]+[F1] is not "heard" by Natty.

---

### Post by opodaniel on 2011-09-05
Original script works like a charm for me on VpcSA laptop. I can finally type normally.

---

### Post by 10o on 2011-09-12
> **10o said:**
> Got it working now!
My thanks to pi/roman and stafford.ritchie.

Found out (with HardInfo) that my device goes by the name of "**SynPS/2 Synaptics TouchPad**".
Thus, on my Vaio F-series VPCF22L1E the script goes like this:

```
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
else xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0; fi
```

Placed this code in the file **/usr/bin/touchpad_toggle.script** and assigned the script to the [ASSIST] button, since [Fn]+[F1] is not "heard" by Natty.

In Xubuntu 11.04 "SynPS/2 Synaptics TouchPad" appears to be "PS/2 Synaptics TouchPad"...

---

### Post by mr_nice_guy on 2011-10-09
> **stafford.ritchie said:**
> This took me a while to figure out, so I hope I can save you some frustration.  The above instructions from pi/roman did not work 'out of the box' on my E Series, so I modified them.  Thank you for the starting point, pi/roman!  Here is how I disable the touchpad:

- Open a terminal: click the ubuntu symbol, then type "terminal" and hit enter.
- Create a file: type "pico /usr/bin/touchpad_toggle.script" then hit enter.
- Paste the following into the file
```
# toggle synaptic touchpad on/off
MOUSESTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $MOUSESTATE = 0 ]; then xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 1
else xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 0; fi
```- Save the file: type Ctrl-X, type "Y", then hit enter.
- Open Keyboard Shortcuts:  click the ubuntu symbol, then type "Keyboard Shortcuts" and hit enter.
- Add a new shortcut: Click Add, type "Touchpad Toggle" for the name, hit tab, type "/usr/bin/touchpad_toggle.script" for the command, then click Apply.
- Allow the file execute mode: In a terminal, issue the following command
```
chmod +x /usr/bin/touchpad_toggle.script
```
- Assign the shortcut to a key: Scroll to the bottom of the list, click on the Shortcut column of the Toggle Touchpad line, hit the ASSIST button on your keyboard, then click Close.
-Try it out: Hit the ASSIST button on the keyboard.  Your touchpad should now be disabled, and you should be able to type without accidentally clicking.  Hit the ASSIST button again.  Your touchpad should now be enabled.
- Rejoice: Good work!  You've done well.

hth

-Stafford
Awesome.!! Works like a charm. Thank you, Stafford. Been hunting for such a hack for long. 
You could use:
> xinput --list to find out the actual device

My VPCF135 says device is **ImPS/2 Generic Wheel Mouse**

---

### Post by opodaniel on 2011-10-15
I just updated to Oneiric and found that the script wasn't working any more and thanks to mr_nice_guy's command **xinput --list** found that although Ubuntu detected the  _AlpsPS/2 ALPS GlidePoint_  it loaded the PS/2 Mouse  . So here is the output of xinput and the script that works for me.
> **xinput --list**
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                id=11   [slave  pointer  (2)]
&#9116;   &#8627; _PS/2 Mouse_                                id=14   [slave  pointer  (2)]
&#9116;   &#8627; _AlpsPS/2 ALPS GlidePoint_                  id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                            id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; USB2.0 Camera                             id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]


> # toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "PS/2 Mouse" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 1
else xinput set-int-prop "PS/2 Mouse" "Device Enabled" 8 0; fi

Mysterious are the Linus ways ( for us newbies :d )

---

### Post by paradajz on 2011-10-23
Can you explain the code in the script abit? It works flawlessly, but in my case, I've got USB mouse which goes under the name of Logitech USB-PS/2 Optical Mouse.

So when I do xinput list it detects it and when I unplug it it doesn't (what a surprise). I'd like to write a script which would turn off touchpad if my device is plugged (Logitech USB-PS/2 Optical Mouse).

---

### Post by paradajz on 2011-10-23
Nevermind the previous posts, I kinda got it. I'm pretty sure there is a better way to do this but I've installed Linux a week ago. Also this is my first script ever:

```
# toggle synaptic touchpad on/off

logsave /home/igor/testing/test.log xinput list-props "Logitech USB-PS/2 Optical Mouse" &> /dev/null
grep unable /home/igor/testing/test.log &> /dev/null
STATE=$?
rm /home/igor/testing/test.log

if [ $STATE = 1 ]; then xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 0
else xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 1; fi

```

Now, how to launch it at specific times (mouse plugged / mouse unplugged)?

---

### Post by opodaniel on 2011-10-26
You can make a key combination to run the script. I use Ctrl+F1 to launch the **sh /path_to_script/script.sh**. Don't forget to make it executable with **chmod +x script.sh**

---

### Post by 1formatnet on 2011-11-08
Genial. VAIO VPCEJJE:popcorn:

---

### Post by calvertdw on 2011-11-28
Thank you!!

Worked very well for me. Fedora 15 64-bit (VPCF1190X)

commands used (/usr/bin):
yum install xinput
vi touchpad.sh
sh touchpad.sh

---

### Post by youWho on 2012-02-11
In case it helps to say: please note that to create, save or move (command "mv" in terminal for example) anything in /usr/bin you have to be root. On ubuntu that generally means using "sudo". A few searches on the interwebs should turn up plenty of wonderfully informative tutorials on sudo, root and such. The point here is that /usr/bin/ is owned by "root".

Oops, I was reading posts at the top end of this thread and thought to post this remark just because it seemed some people were maybe unsure about how to make use of a shell script; but my little remark got added only here at the end of the thread, where it's not too relevant... well, maybe it's still helpful to say.

---

