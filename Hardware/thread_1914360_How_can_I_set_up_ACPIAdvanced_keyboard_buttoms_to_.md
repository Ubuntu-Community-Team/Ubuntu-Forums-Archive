---
title: "How can I set up ACPI/Advanced keyboard buttoms to work on my thinkpad G40?"
date: 2012-01-24
forum: Hardware
---

### Post by IdanSuper on 2012-01-24
Hello.. I have IBM ThinkPad G40 running Lubuntu 11.10.. and the special buttoms like volume/mute doesn't seems to work.. how do I fix it? thanks for help!

---

### Post by IdanSuper on 2012-01-26
up! help please!.. thanks..

---

### Post by IdanSuper on 2012-01-27
Someone? Please?? don't tell me that I can't do anything with it..

---

### Post by 1dan on 2012-01-27
Actually, you can. The problem must be investigated first.
What happens in logs if you do the following
```
tail -f /var/log/messages
``` in one terminal window
and
```
sudo modprobe thinkpad-acpi
```in another

After that launch both xev and acpi_listen to see if buttons produce any response.

---

### Post by IdanSuper on 2012-01-29
> **1dan said:**
> Actually, you can. The problem must be investigated first.
What happens in logs if you do the following
```
tail -f /var/log/messages
``` in one terminal window
and
```
sudo modprobe thinkpad-acpi
```in another

After that launch both xev and acpi_listen to see if buttons produce any response.

I haven't installed it yet, and I don't know how to install the Thinkpad-acpi..... I would like some help to run it on the newest kernel version (3.0.15). thank you very much for help..!

---

### Post by Mark Phelps on 2012-01-29
Eventually, you will have to run "xev" -- because what it does is display the codes the kernel sees when you press a particular button or key.

And, this is the IMPORTANT part, if you press a button or key and NOTHING is displayed, there is nothing you can do to use that key because it is not being detected.

I used to use Ubuntu on a tablet PC and had to STOP using it because, starting with the kernels in Ubuntu 9.04, they would not detect the bezel buttons anymore -- buttons I absolutely needed to work when in tablet mode.

---

### Post by Favux on 2012-01-31
The thinkwiki.org is usually a good place to start:  [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)  See Special Keys under the HOW TOs.  There are actually a couple HOW TOs dealing with them and/or bezel buttons.

Likely it will be relatively straightforward but it can get involved because you have to figure out where in the chain the problem is.  Are there keycodes there, but higher than 255?  Because right now X won't handle keycode #'s above 255 and they'll have no affect.  If you figure out what the kernel keycode number is for it (X keycode # - 8 ) you should be able to reassign it to another keycode that will be recognised by X.  Say by changing the udev rule for that key mapping.  There is a discussion of this for tablet PC bezel buttons in appendix 2 of the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1"), including a Thinkpad example.  Udev key mapping rules are changed so a bezel button can be switched to another function and a bezel button left non-working by a release upgrade reactivated.

The last place in the chain (or first depending on your perspective) is the BIOS.  If that has changed with a version update then whatever kernel driver/module reads the keys from it, whether thinkpad-acpi.ko or hp-wmi.ko, may need its code modified.  That consists of changing the driver's code button assignments to include the changed scancodes from the BIOS.  There is an example or two of that being done in the N-Trig HOW TO with the hp-wmi.ko (the hp-wmi.c).  This is of course more a developer kind of thing or if you are comfortable playing with C and recompiling kernel modules.

---

### Post by Favux on 2012-02-01
I forgot the link for your model, I'm sure you would have found it anyway, but here it is:  [http://www.thinkwiki.org/wiki/Category:G40](http://www.thinkwiki.org/wiki/Category:G40)

---

### Post by IdanSuper on 2012-02-01
I just want to make any special buttons which operate ... Sound, etc. .. And I do not understand this guide: [http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi) I with kernel 3.0.15 and registered at the two and I do not know how it would work at all .. Maybe someone can explain me thank you! And my bios is the most up to date ..

---

### Post by Favux on 2012-02-01
You just want to verify that the thinkpad_acpi module is loading.  It should do that automatically with a relatively recent linux release with a reasonably new kernel.  If you run the list modules command in a terminal:
```
lsmod
```
you should see it in the list of loaded modules.

---

### Post by IdanSuper on 2012-02-01
Okay .. That's what I get from the start .. This link:[http://paste.ubuntu.com/825207/]("http://paste.ubuntu.com/825207/")
Please help me and show me how to enable this option.. thanks!

---

### Post by Favux on 2012-02-01
Alright, it is loading.  Have you tested the buttons with xev yet?

Make a list of the buttons then type *xev* in a terminal.  A box opens, press one of the keys, close the box.  Your looking for a keycode that pressing one of the buttons on the list emits.  You want the keycode for each button.

---

### Post by IdanSuper on 2012-02-01
What do you mean when you say to make a list of the buttons? thanks!

---

### Post by Favux on 2012-02-01
A list of the special keys that aren't working.  How many are there and what are they suppose to do?  Then find the keycode associated with each key/button.

---

### Post by IdanSuper on 2012-02-01
Okay I tried the key of the mute in xev as you said and it doesn't give me any response .. Thank you!

---

### Post by Favux on 2012-02-01
How about with the volume key?  That's the other one that isn't working correct?

I don't see either of those in the G series special keys by the way:  [http://www.thinkwiki.org/wiki/Default_meanings_of_special_keys#G_Series](http://www.thinkwiki.org/wiki/Default_meanings_of_special_keys#G_Series)  What is it suppose to mute?  The music player or the microphone?  I do see a microphone mute for another Thinkpad model.

With an older version of Keyboard Shortcuts (Maverick) I see that:
```

Volume mute     XF86AudioMute
Volume down     XF86AudioLowerVolume
Volume up       XF86AudioRaiseVolume

```
Have you looked in Keyboard in the Shortcuts tab and tried editing the settings?  You click on the action desired and press the button that is suppose to perform it?

---

### Post by IdanSuper on 2012-02-01
I have special keys to them without FN .. Only them .. That's why .. And then what can I do?

---

### Post by Favux on 2012-02-01
OK, so you have a Volume and a Mute key that don't work and emit no keycode in xev.

The Shortcuts did nothing?

Then you're going to have to work through the kind of stuff described in appendix 2 in the Rotation HOW TO I linked you to earlier.  My guess is your udev keymaps are using the wrong keycodes or aren't using the correct XF86 sym keys I showed you above, i.e. XF86AudioMute etc.  So you may need to find the lenovo equivalent of the hewlett-packard udev keymap etc. in /lib/udev/keymaps, look them over and fix the problem.

Since I don't have a Thinkpad I can't do that for you.

---

### Post by SaintDanBert on 2012-02-01
> **Favux said:**
> I forgot the link for your model, I'm sure you would have found it anyway, but here it is:  [http://www.thinkwiki.org/wiki/Category:G40](http://www.thinkwiki.org/wiki/Category:G40)

I heard that there is some boot-time bit to set that enables more
"special keys" and related ACPI parts. To date I have not found the
details on which bit and how to set it.

In my case, I get nothing running either **xev** or **acpi_listen** and I have no way to know what if anything gets thrown and discarded or lost in the mixmaster.  

(hiding behind thick armor) Does anyone know if something win-dose will reveal keys or codes because bezel buttons all work under win-dose v7?

Favux, do you know how one obtains the thinkpad_acpi.txt file from the build tree as described on the ThinkWiki pages?

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2012-02-01
> **Favux said:**
> 
...
Since I don't have a Thinkpad I can't do that for you.

I'm having similar ACPI issues and want to help sort this out.

I have two (well, 3 actually) Thinkpads -- X61t and X220t.
(Two X61t -- one touch, one not)
The are currently setup as follows:
[list]
[*]X220t touch ..... Linux Mint-12 [aka, Ubuntu v11.10]
[*]X61t no-touch ..... Ubuntu Lucid (v10.04 LTS)
[*]X61t touch ..... Linux Mint-11 [aka, Ubuntu v11.04)
[/list]

I'll run any experiment you tell me how to do ... (grinning) within reason.

Eager to help,
~~~ 0;-Dan

PS/  I use Karl Hegbloom's **tablet-screen-rotation-support** package instead of "magic rotate".  All of the rotate display works fine. However, the mouse orientation never changes. Sigh. Fine for stylus though.

---

### Post by Favux on 2012-02-01
[QUOTE=SaintDanBert]Favux, do you know how one obtains the thinkpad_acpi.txt file from the build tree as described on the ThinkWiki pages?[/QUOTE]
I asssume you are talking about the source code for the thinkpad_acpi?

Download the kernel source code:
```
apt-get source linux-image-`uname -r`
```
Then thinkpad_acpic.c will be in /drivers/platform/x86.  Looks like some of the relevant code (for IdanSuper at least) is this:
```
/* HKEY events */
enum tpacpi_hkey_event_t {
	/* Hotkey-related */
	TP_HKEY_EV_HOTKEY_BASE		= 0x1001, /* first hotkey (FN+F1) */
	TP_HKEY_EV_BRGHT_UP		= 0x1010, /* Brightness up */
	TP_HKEY_EV_BRGHT_DOWN		= 0x1011, /* Brightness down */
	TP_HKEY_EV_VOL_UP		= 0x1015, /* Volume up or unmute */
	TP_HKEY_EV_VOL_DOWN		= 0x1016, /* Volume down or unmute */
	TP_HKEY_EV_VOL_MUTE		= 0x1017, /* Mixer output mute */

```

---

### Post by IdanSuper on 2012-02-02
Well I didn't understand anything .. There are a big mess .. Can anyone explain step by step noobs like me what to do .. Thank you!

---

### Post by SaintDanBert on 2012-02-02
There is a kernel document [_Thinkpad ACPI Details_](http://www.mjmwired.net/kernel/Documentation/laptops/thinkpad-acpi.txt) that reads, in part:
```

The driver will generate events over the input layer for hot keys and
radio switches, and over the ACPI netlink layer for other events. The
input layer support accepts the standard IOCTLs to remap the keycodes assigned to each hot key.

The hot key bit mask allows some control over which hot keys generate
events.  If a key is "masked" (bit set to 0 in the mask), the firmware will handle it.  If it is "unmasked", it signals the firmware that thinkpad-acpi would prefer to handle it, if the firmware would be so kind to allow it (and it often doesn't!).

Not all bits in the mask can be modified.  Not all bits that can be
modified do anything.  Not all hot keys can be individually controlled by the mask.  Some models do not support the mask at all.  The behaviour of the mask is, therefore, highly dependent on the ThinkPad model.

The driver will filter out any unmasked hotkeys, so even if the firmware doesn't allow disabling an specific hotkey, the driver will not report events for unmasked hotkeys.

Note that unmasking some keys prevents their default behavior.  For
example, if Fn+F5 is unmasked, that key will no longer enable/disable
Bluetooth by itself in firmware.

Note also that not all Fn key combinations are supported through ACPI
depending on the ThinkPad model and firmware version.  On those
ThinkPads, it is still possible to support some extra hotkeys by
polling the "CMOS NVRAM" at least 10 times per second.  The driver
attempts to enables this functionality automatically when required.

```

I'll keep reading and report back once I discover the setting, clearing, masking, details. Hopefully, they will be in the rest of the document.

~~~ 8d;-/ Dan

---

### Post by SaintDanBert on 2012-02-02
I found this page [_ThinkWiki ACPI Discussion_](http://www.thinkwiki.org/wiki/Thinkpad-acpi) that reads, in part:
```

**_Hotkeys_**

To view which hotkeys are active you can use "acpi_listen", but that is deprecated. A better way is to use "lsinput" and "input-events" commands to look at the output of the thinkpad-acpi input device(s).
One important difference from ibm-acpi for those who wish to enable all possible hot keys, is that thinkpad-acpi automatically enables them. One should not need to do anything to get the best possible thinkpad-acpi configuration for his ThinkPad (as long as he is using the latest thinkpad-acpi).

[color=orange]In particular, old documentation that tells you to "echo enable,0xffffffff >/proc/acpi/ibm/hotkey", or to give thinkpad-acpi any hotkey= module parameters to enable hot keys by default, is likely incorrect.[/color]

The thinkpad-acpi driver has detailed documentation, which is shipped inside the Linux kernel sources, as "Documentation/thinkpad-acpi.txt" or as "Documentation/laptops/thinkpad-acpi.txt". If you feel a need to change the hot key mask manually, it is probably best to look at that documentation first to understand the full side effects of any changes.

```
I added the emphasis.
Notice that things are supposed to be enabled by default. That said, I suspect that, as pointed out in the previous posting, *enabled* sometimes blocks the desired behavior.
My Thinkpad X220t reports the following:
```

prompt$ ls /sys/devices/platform/thinkpad_acpi/

bluetooth_enable     hotkey_poll_freq         modalias
cmos_command         hotkey_radio_sw          power
driver               hotkey_recommended_mask  rfkill
hotkey_all_mask      hotkey_report_mode       sound
hotkey_bios_enabled  hotkey_source_mask       subsystem
hotkey_bios_mask     hotkey_tablet_mode       uevent
hotkey_enable        input                    wakeup_hotunplug_complete
hotkey_mask          leds                     wakeup_reason

```
and
```

prompt $ ls /sys/devices/platform/thinkpad_hwmon/

driver  fan1_input  hwmon  modalias  name  power  pwm1  
pwm1_enable  subsystem  uevent

```

Cheers,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2012-02-02
My previous post contained:
> 
To view which hotkeys are active you can use "acpi_listen", but that is deprecated. A better way is to [highlight]use "lsinput" and "input-events" commands[/highlight] to look at the output of the thinkpad-acpi input device(s).
 (emphasis added)
In my case, **lsinput** was not installed and required that I add the package 'input-utils' from the repositories. That done, I get the following:
```

prompt $  sudo lsinput

...
/dev/input/event6
   bustype : BUS_HOST
   vendor  : 0x17aa
   product : 0x5054
   version : 16641
   name    : "ThinkPad Extra Buttons"
   phys    : "thinkpad_acpi/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_SW
...

```

I got no response at all (other than "timeout") to:
```

prompt$ sudo input-event 6  #notice -- just the number not the name

```
when I tried any of the buttons on the bezel.

REMINDER (spoken from behind a thick wall) Win-dose obeys these buttons.

"What next?" he asks plaintivly,
~~~ 0;-/ Dan
[color=#00FF00]
**_Edit: Follow-up_**
The driver will report HKEY events in the following format:

	ibm/hotkey HKEY 00000080 0000xxxx

Here are codes for some Thinkpad Events:

Events that are not propagated by the driver, except for legacy
compatibility purposes when hotkey_report_mode is set to 1:

0x5001		Lid closed
0x5002		Lid opened
**0x5009		Tablet swivel: switched to tablet mode**
**0x500A		Tablet swivel: switched to normal mode**
0x7000		Radio Switch may have changed state

Events that are propagated by the driver to userspace:

0x2313		ALARM: System is waking up from suspend
                because the battery is nearly empty
0x2413		ALARM: System is waking up from hibernation
                because the battery is nearly empty
0x3003		Bay ejection (see 0x2x05) complete, can sleep again
0x3006		Bay hotplug request (hint to power up SATA link when
		the optical drive tray is ejected)
0x4003		Undocked (see 0x2x04), can sleep again
0x4010		Docked into hotplug port replicator (non-ACPI dock)
0x4011		Undocked from hotplug port replicator (non-ACPI dock)
**0x500B		Tablet pen inserted into its storage bay**
**0x500C		Tablet pen removed from its storage bay**
0x6011		ALARM: battery is too hot
0x6012		ALARM: battery is extremely hot
0x6021		ALARM: a sensor is too hot
0x6022		ALARM: a sensor is extremely hot
0x6030		System thermal table changed
0x6040		Nvidia Optimus/AC adapter related (TO BE VERIFIED)

So far, I have not found an event for the bezel "orientation" button listed in recent Thinkpad documentation.
[/color]

---

### Post by Favux on 2012-02-02
Since you know that the buttons should report through "ThinkPad Extra Buttons" which is on event6 you should also be able to test button/key function with:
```
sudo evtest /dev/input/event6 
```
Then press the button/key you are interested in.  You may have to install evtest, I forget.

---

### Post by SaintDanBert on 2012-02-02
I get the following:
```

prompt$  sudo  evtest  /dev/input/event6

Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"

Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 142 (Sleep)
    Event code 148 (Prog1)
    Event code 152 (Screen Lock)
    Event code 191 (F21)
    Event code 194 (F24)
    Event code 205 (Suspend)
    Event code 212 (Camera)
    Event code 224 (Brightness down)
    Event code 225 (Brightness up)
    Event code 227 (Switch Video Mode)
    Event code 228 (Kbd Illum Toggle)
    Event code 236 (Battery)
    Event code 238 (WLAN)
    Event code 240 (Unknown)
    Event code 372 (Zoom)
    Event code 466 (Fn F1)
    Event code 475 (Fn F10)
    Event code 476 (Fn F11)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 5 (Switch)
    Event code 1 (Tablet Mode)
    Event code 3 (RFKILL)
Testing ... (interrupt to exit)

```
I notice the types #0, #1, #4, and #5 are reported while #6 is not.
Either they are not available or are otherwise not yet turned on.

What next,
~~~ 0;-Dan

---

### Post by Favux on 2012-02-02
Just to be sure, since you aren't reporting anything after:
```
Testing ... (interrupt to exit)
```
I am assuming none of the buttons you are interested in gave a response when tested i.e. pressed?

I don't think you've enumerated which tablet PC buttons and their functions aren't working for each of your tablet PCs.  I believe we know at least for the X61t's all of the buttons were working at one point from the Thinkwiki.org.

---

### Post by IdanSuper on 2012-02-03
all the FN works fine for me...... only the volume/mute keys aren't. they was worked on XP without needs to click the FN key.. and now on Lubuntu 11.10 they aren't work.. and it doesn't matter even if I click on FN.. what I need to do? thanks.. and again my Thinkpad model is:IBM G40..

---

### Post by IdanSuper on 2012-02-03
You think I have to update my bios? Now is the version 1.20 and I saw that 1.21 .. And change is in Function update .. I never updated version of the BIOS and I even a little scared to do it .. Do you think it will solve my problem? Should I try to update .. It has no ramifications? Thank you!

---

### Post by Favux on 2012-02-03
Hi IdanSuper,

Normally you want the latest BIOS because it may have bug fixes or even more capabilities.  Unfortunately though sometimes a new BIOS will break things in linux and it takes a while for the linux drivers to catch up to the changes.  BIOS updates are usually very safe in Windows as long as you use proper care.

That might be what you are dealing with now, we don't know yet.  SaintDanBert is investigating his problems.  Maybe we'll get lucky and if he solves them the solutions will apply to you to.

---

### Post by SaintDanBert on 2012-02-04
> **Favux said:**
> Just to be sure, since you aren't reporting anything after:
```
Testing ... (interrupt to exit)
```
I am assuming none of the buttons you are interested in gave a response when tested i.e. pressed?


You are correct, none of the things that I pressed caused any report.

> **Favux said:**
> I don't think you've enumerated which tablet PC buttons and their functions aren't working for each of your tablet PCs.  I believe we know at least for the X61t's all of the buttons were working at one point from the Thinkwiki.org.

The X220t has the following that interest me:
[list]
[*]two non-power buttons on the bezel
[list]
[*]change orientation "toggle": right(portrait)-->inverted(landscape)-->left(portrait)-->normal(landscape)
[*]"refresh" -- redraw the current screen
[/list]
[*]two stylus events
[list]
[*]stylus removed from its parking slot
[*]stylus returned to its parting slot
[/list]
[*]undock Ultrabase from the laptop
[*]undock Ultra-bay device from Ultrabase
[/list]
NOTE -- I say "has" because win-dose notices these things so there must be something that is software readable.

Cheers,
 ~~~ 0;-Dan

---

### Post by Favux on 2012-02-04
Thanks, that helps me understand the context.

I do suggest you post on the "Natty Narwhal on Lenovo ThinkPad X220T" thread:
> The X220t has the following that interest me:

    two non-power buttons on the bezel
        change orientation "toggle": right(portrait)-->inverted(landscape)-->left(portrait)-->normal(landscape)
        "refresh" -- redraw the current screen
    two stylus events
        stylus removed from its parking slot
        stylus returned to its parting slot
    undock Ultrabase from the laptop
    undock Ultra-bay device from Ultrabase

so unclepedro and the rest know that's what you are trying to get working.  (Sorry, couldn't copy your formatting.)

So what are the kernel scancodes and keycodes you're getting for those in console?

---

### Post by Favux on 2012-02-04
Sorry, duplicate.

---

### Post by SaintDanBert on 2012-02-04
> **Favux said:**
> Thanks, that helps me understand the context.

I do suggest you post on the "Natty Narwhal on Lenovo ThinkPad X220T" thread:

I did a search of this forum and got zilch for X220t.  That blanked operator nut must be loose again.
> **Favux said:**
> 
so unclepedro and the rest know that's what you are trying to get working.  (Sorry, couldn't copy your formatting.)

I used the "list" tag nested within another "list" tag.
> **Favux said:**
> 
So what are the kernel scancodes and keycodes you're getting for those in console?
I started here [Console Keycodes and Scancodes](http://www.comptechdoc.org/os/linux/usersguide/linux_ugterminal.html). Is there
something better?
[color=#00FF00]
**Follow-up**
On the Thinkpad X61t, I get the following:
```

acpi_listen:
   stylus remove ..... HKEY  0080  500c
   stylus park ....... HKEY  0080  500b
   orientation ....... echo'd control+@
   lock .............. echo'd control+@
Keycodes:
   orientation ..... 191 (both press and release)
   lock ............ 152 (both press and release)
Scancodes:
   orientation ..... 0x74 (press)  0xf4 (release)
   lock ............ 0xe0 0x12 (press)  0xe0 0x92 (release)

```
This workstation produced reports from an ALT+Fnnn console.
[/color]
[color=#0000FF]
**Follow-up**
On the Thinkpad X220t, I get the following:
```

acpi_listen:
   stylus remove ..... HKEY  0080  500c
   stylus park ....... HKEY  0080  500b
   orientation ....... no report
   refresh ........... no report
Keycodes:
   orientation ..... no keycode
   refresh ......... no keycode
Scancodes:
   orientation ..... no scancode
   refresh ......... no scancode

```
This workstation produced reports from an ALT+Fnnn console.
[/color]
[highlight]Since these features behave as expected in the win-dose world, there must be something that is available to software. We either need to learn how to enable it for existing linux software to process, or it requires some approach outside of what our software expects.[/highlight]
[s]As I recall, I get nothing at this level unless I boot single-user. Otherwise, things are somehow "owned" by the running X11 and other desktop parts. Also, there were some issues with single-user and the tablet.  (blush) ... and I forget how to one-time-boot "single-user" under GRUB2+BURG.
[indent][i]
[CENTER]SIDE-BAR[/CENTER]
I'd like to have a single-user boot option that doesn't get stomped when a kernel update or other **update-grub** process happens.
[/i][/indent][/s]

Cheers,
~~~ 0;-Dan

---

### Post by Favux on 2012-02-04
> I did a search of this forum and got zilch for X220t.
I'm referring to a thread you have already posted on:  [http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)  That pretty much is the Ubunut forums X220t thread.

For the kernel keycodes I was hoping you were going through appendix 2 (near the bottom) of the Rotation HOW TO:  [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)  To quote the first step:
> **a) kernel codes** The first step is to find the bezel button's kernel scan codes.  Enter a console with <ctrl-alt-F1>; to get back to X enter <ctrl-alt-F7>.  Then enter ***showkey -s*** in the console and press the bezel buttons.  Only the scan code from the Q key (none of the other 3 do anything) appears:  0xe0 0x6d 0xe0 0xed.  Next find the kernel keycodes by entering ***showkey -k*** and press the buttons which shows (the two bottom buttons do nothing):  DVD button = 389 and Q button = 226.  So the bezel button assignments from the kernel are:
```

DVD button         scan code = ???                   keycode = 389
Q   button         scan code = 0xe0 0x6d 0xe0 0xed   keycode = 226
Rotation button    N/A
Brightness button  N/A

```
The keys and their corresponding key codes are defined in **input.h** at **/usr/include/linux**.
You use the console so you aren't in X and can get the kernel stuff.

Thanks for that reference, although it does appeared to be focused on mapping keys for the console.

---

### Post by IdanSuper on 2012-02-05
Something resolved here? For me it still looks like gibberish. There is a solution to do with me?
And why I shut the computer is just off the screen and I went to sleep automatically?

---

### Post by IdanSuper on 2012-02-06
Somebody? I really need to do something with it.. thanks..

---

### Post by Favux on 2012-02-06
Hi IdanSuper,

Are you able to do any of the diagnostics I have been suggesting?  In post #36 for example?  Without some input from you I don't know how far we can go.

Here is a concrete example for fixing the X220's hotkeys Zoom and MicMute:  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_11.04_%28Natty_Narwhal%29_on_a_ThinkPad_X220#Fix_for_hotkey_shortcomings](http://www.thinkwiki.org/wiki/Installing_Ubuntu_11.04_%28Natty_Narwhal%29_on_a_ThinkPad_X220#Fix_for_hotkey_shortcomings)  The basic issue is something I've already mentioned, the key codes end up being above the X 255 number limitation.  So they don't do anything.  The fix is to remap them through udev so they end up with a keycode below 255 which makes them usable.

Have you looked at the G series stuff on the thinkwiki.org site?  If there isn't anything useful there, and you can't do any of the diagnostics, you'll have to google and see if you can find out if someone has already figured out your G40 issues and if you can follow their instructions.

---

### Post by IdanSuper on 2012-02-06
But how can I fix the problem that when you close the computer is not going to sleep as well?
And I plowed through the internet on this model and saw nothing but trouble since 2004 that I could not understand them nothing: (

---

### Post by IdanSuper on 2012-02-07
Can you tell me step by step what tests to do? has a little mess here ..

---

### Post by Favux on 2012-02-07
Sure.

First you want to check if the keys are emitting a keycode.  So the two diagnostic test commands that have been shown are *xev* and *evtest*.  Let's use xev.  In a terminal type:
```
xev
```
and hit enter.  A little box pops up.  Press one of the keys in question and then close the box.  The terminal will fill with output.  You are looking for keywords like **KeyPress**, **keycode**, and **keysym**.  You can copy and paste the output into gedit and then do a find for them.  You are looking for the keycode number and the little sections of output that contain it.  There should be two, one for the KeyPress event and one for the KeyRelease event.  Then repeat for the next key.  If there are keycodes post them (and the sections).  Remember the keycodes you get from xev are the X keycodes (hence the x in the name, xev = X event).

Now if there is no X keycode that is another situation and there are two possibilities.
1)  Something is going wrong with the chain:  kernel scancode > kernel keycode > udev key mapping > keysym assignment in udev mapping > X keycode.  That is what the appendix 2 I've been talking about provides, a step by step guide to diagnose the chain.
2)  The BIOS has changed key assignments and the kernel driver code that is reading the key assignment needs to be changed to reflect that.  That was what the examples about the hp-wmi.c code changes on the N-trig HOW TO was about.  In your case it would be the thinkpad-acpi.c code presumably.  The compiled versions of that code are the hp-wmi.ko and thinkpad-acpi.ko (ko = kernel object i.e module/driver) you see in /lib/modules/yourcurrentkernel/kernel/drivers/platform/x86.

---

### Post by cddt on 2012-02-07
I'm not sure if my post is going to be helpful or not. I have an IBM T42 thinkpad which I think is similar to the G40. Also running Lubuntu. 

My volume and mute keys do not give any response in *xev*. However they do increase, decrease and mute volume without changing the volume control on the desktop. 

Not sure if that helps!

---

### Post by Favux on 2012-02-07
Hi cddt,

Thanks for chiming in.  Could you check if for those keys you see in the xev output **XF86**-something or other?

---

### Post by IdanSuper on 2012-02-07
Yes, Only the volume keys are'nt do anything on my Xev.. and they are'nt do anything with thinkpad_acpi.. But I got an idea and I need your helps on it, I get Acpid and I configure FN+F3 and it works, so I need a script for decrease/incerase the volume for acpid, and the key was showing on the command:listen_acpi . so I can to make it work through that.. thank you!

---

### Post by Favux on 2012-02-07
Well we've got the alsa mixer key binding script command for microphone mute from:  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_11.04_%28Natty_Narwhal%29_on_a_ThinkPad_X220#Fix_for_hotkey_shortcomings](http://www.thinkwiki.org/wiki/Installing_Ubuntu_11.04_%28Natty_Narwhal%29_on_a_ThinkPad_X220#Fix_for_hotkey_shortcomings)
```
sh -c "if amixer get Capture,0 | grep -q '\[on\]' ; then amixer -q set Capture,0 nocap ; else amixer -q set Capture,0 cap; fi"
```

Here's a more full blown alsa mixer volume script:  [http://www.linuxjournal.com/content/change-volume-bash-script](http://www.linuxjournal.com/content/change-volume-bash-script)

Between them that might serve you as a starting point for modification.

---

### Post by cddt on 2012-02-12
> **Favux said:**
> Hi cddt,

Thanks for chiming in.  Could you check if for those keys you see in the xev output **XF86**-something or other?

I don't actually see anything in the xev output for the volume and mute keys. Pressing them gives no response in xev. But they still work to control the volume. 

However I do see XF86Launch1 when I press the "Access IBM" button.

---

### Post by SaintDanBert on 2012-02-12
> **Favux said:**
> 
...
Now if there is no X keycode that is another situation and there are two possibilities.
1)  Something is going wrong with the chain:  kernel scancode > kernel keycode > udev key mapping > keysym assignment in udev mapping > X keycode.  That is what the appendix 2 I've been talking about provides, a step by step guide to diagnose the chain.
2)  The BIOS has changed key assignments and the kernel driver code that is reading the key assignment needs to be changed to reflect that.  
...


Sir,
     Could you please explain how and where you learned this level of detail?  Did you read the driver(s) and kernel code or is there some other source for that level of detailed information?  I don't find this "Appendix 2" that you mention, so I suspect I'm not looking in the right places for things to read.

Thanks,
~~~ 0;-/ Dan

---

### Post by Favux on 2012-02-12
It towards the bottom of the Rotation HOW TO post (How to Rotate the Screen for a TX2000 Tablet PC TX2500, TX2z, TM2t & other Tablet PCs):  [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)  I do not understand how you have not found appendix 2 yet.

Appendix 2 is me synthesizing sources I read.  I found information in the Ubuntu, Arch, etc. wikis.  Information from googling.  You can also find stuff in the installed documents (/usr/share/doc) and manuals (i.e. man <whatever's name> in a terminal).  I reference to one or two such as /usr/share/doc/udev/README.keymap.txt.  Tough to wade through and find them and many like README.keymap.txt are compressed so you have to first extract them to read, adding to the difficulty.  I don't claim it is complete and there are still holes in my understanding.  But I think it is a reasonably complete and reasonably correct overview.

---

### Post by SaintDanBert on 2012-02-13
There are numerous "documentation packages" -- many of which do not install by default -- that offer more extensive explanations after package installation.

Most of the kernel and gritty documentation (like "thinkpad-acpi.txt") require that one install the "build-a-kernel" packages.

I'm working from a laptop most of the time so I don't have beaucoup packaged installed to save space.

Thanks, Favux, for your patience,
~~~ 8d;-/ Dan

---

### Post by IdanSuper on 2012-02-13
Ok.. I wait for some help.. nothing work. Many FN keys aren't work the only FN key who works is the brightness switcher.. what with the other? I wait for any help with it.. thanks in advance! there isn't any simple fix with package that I need only to install to reboot and that's it? And after I reboot my computer it starts up with black screen.. how to fix it? thanks..
edit: you think if I will update my bios it will solve all my problems?
I'm really afraid to do it now and I'd to ask if it will work under lubuntu because in Lenovo they said that I need to do it under windows

---

### Post by IdanSuper on 2012-02-15
somebody?

---

### Post by IdanSuper on 2012-02-16
I have many problem with it after I resume my computer from sleep/hibernate it makes problem with ndiswrapper.. I can't use wifi and it isn't matter if I make the command: modprobe ndiswrapper as root.. so what can I do? and I have blackscreen after restart and when I resume my computer from sleep or hibernate it makes beep beep every time I click the volume keys.. and They're not work anytime....... How can I fix all my problems? thanks..

---

### Post by IdanSuper on 2012-02-18
somebody?

---

### Post by IdanSuper on 2012-02-19
Please?

---

