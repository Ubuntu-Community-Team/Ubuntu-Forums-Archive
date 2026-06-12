---
title: "Tablet PC [Motion Computing LE1600] Issues"
date: 2009-02-06
forum: Hardware
---

### Post by DrGNU on 2009-02-06
**Ubuntu 8.10 - LE1600 (Motion Computing Tablet PC)**

**Wikipedia Stump**
[http://en.wikipedia.org/wiki/Motion_computing](http://en.wikipedia.org/wiki/Motion_computing)

**Images**
[http://images.google.com/images?client=opera&rls=en&q=le1600&sourceid=opera&oe=utf-8&um=1&ie=UTF-8&sa=N&hl=en&tab=wi](http://images.google.com/images?client=opera&rls=en&q=le1600&sourceid=opera&oe=utf-8&um=1&ie=UTF-8&sa=N&hl=en&tab=wi)

**ISSUES**
1. [[COLOR="Red"]working*[/COLOR]] **PEN/STYLUS**  
>  - other posts address the XORG configuration and wacom drivers
 - Pressure/Sensitivity is working well and no need to calibrate.

2. [[COLOR="#ff0000"]working[/COLOR]] **ROTATION** 
>  - other posts address the randr and scripts for rotating orientation of the screen, stylus and eraser


NOTE HAL not XORG controls this in Jaunty 9.04 SEE BELOW (work in progess)
3. [[COLOR="#ff0000"]working[/COLOR]] **HANDWRITING RECOGNITION** 
>  - I recommend CELLWRITER (onscreen keyboard and cell-based character recognition)
 - I recommend EASYSTROKE gesture recognition (can customize any gesture and link to command, button, etc)
 - I haven't customized this fully yet

4. [[COLOR="#ff0000"]UNRESOLVED[/COLOR]] **LOGIN/PASSWORD KEYBOARD**
 - Seen suggestions to do "automatic login" 
    -- this is unacceptable and NOT a solution
>  - I did see something about enabling GROK? or some keyboard as an accessibility solution, also I have not tried making EASYSTROKE available to the LOGIN process (I probably need to read more about how to do that)

5. [[COLOR="#ff0000"]UNRESOLVED[/COLOR]] **HARDWARE BUTTONS**
 - I have tried "xev" and none of the buttons on the machine do anything
>    -- 4-way pad (PAGE-UP/DOWN/LEFT/RIGHT SCROLL?) with a central button (ENTER?) 
   -- Four buttons (2 on each side of the "scroll/enter" pad) 
   -- Wi-fi on/off button
   -- Fingerprint reader
   -- Button for reset (CTRL-ALT-DEL?] next to Fingerprint reader

6. [[COLOR="#ff0000"]UNRESOLVED[/COLOR]] **FINGERPRINT READER**
>   - I have not tried to work on the Fingerprint reader yet
    -- Saw information about another TabletPC recommending a couple software solutions and mentioning that they didn't work on all reader models
    -- Hardware model for the LE1600 Fingerprint Reader:
$ lusb
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor

This looks promising:
[http://ubuntuforums.org/showthread.php?t=503928](http://ubuntuforums.org/showthread.php?t=503928)

7. [[COLOR="#ff0000"]UNRESOLVED[/COLOR]] **SOUND/MICROPHONE**
>    -- Sound is currently broken this is lower priority for me at the moment
   -- Microphone - unchecked due to broken sound
   -- Will need to find links to finding out the hardware and fixes for these two items at some point

8. [[COLOR="#ff0000"]WORKS W/ JAUNTY 9.04 [/COLOR]] **WI-FI**
>  - I am more interested in getting my SPRINT EVDO PCMIA CARD working instead as a mobile connectivity solution.

9. [[COLOR="#ff0000"]UNRESOLVED?[/COLOR]] **EVDO PCMIA CARD**
>  - I have a SPRINT EVDO Card that I use for internet access via an old laptop that runs WINDOWS XP.  I've had success in the past on that old laptop that can dual boot to Ubuntu Studio (7.04?) but don't know how to share that internet connection and it is slower in Ubuntu compared to with WINDOWS XP.  It worked by using KPPP.
 - A while back I found a SPRINT .PDF file that describes how to get the EVDO working with Ubuntu and KPPP I don't have the link but can post it to my server if there is an interest in this.
 - I must have done something wrong with my EVDO card with the LE1600 because it found the card but wouldn't test properly or connect to the internet.
 - This will need some more work/experimentation.
   -- I have poor reception in my apartment so that may be a complicating factor. 

I have searched the forums and can not find how to get dead hardware keys to be found and working.  There is no information on the LE1600 from what I have searched.  There are some links on the internet to a Gentoo Linux site for this model but apparently that site lost its database so they don't find any information.
AS OF 7/26/09 STILL BROKEN

> I hope others with the LE1600 or similar LE1700 will find this thread useful and will add in their fixes and links to information that will help others.

-DrGNU (Steve FSF Member#:6887)

---

### Post by Favux on 2009-02-07
Hi DrGNU,

re 4. :  There are several posts at the HP TC1100 thread on using CellWriter to log in with.  You may have looked at this.
[http://ubuntuforums.org/showthread.php?t=563736&highlight=tablet]("http://ubuntuforums.org/showthread.php?t=563736&highlight=tablet")

re 5. :  Check in Synaptics Package Manager that you have hotkey-setup installed.  Search hotkey.  Some bezel buttons, the ones that return no keycode with xev, we haven't figured out how to detect.  Apparently they use a proprietary driver?

re 6. :  Not many have succeeded in configuring fprint for log in.  My impression is that those who have, except for a few models of readers, still have problems with it.  It seems that most fingerprint reader manufacturers haven't released enough useful information on their hardware.

---

### Post by DrGNU on 2009-05-14
> **Favux said:**
> Hi DrGNU,
re 4. :  There are several posts at the HP TC1100 thread on using CellWriter to log in with.  You may have looked at this.
[http://ubuntuforums.org/showthread.php?t=563736&highlight=tablet]("http://ubuntuforums.org/showthread.php?t=563736&highlight=tablet")

I basically got rid of the authentication on logon but when I get some time to hack around again then I'll follow this link. Thank you!

> re 5. :  Check in Synaptics Package Manager that you have hotkey-setup installed.  Search hotkey.  Some bezel buttons, the ones that return no keycode with xev, we haven't figured out how to detect.  Apparently they use a proprietary driver?


This is frustrating to me.  A perfectly wonderful machine with hardware buttons that don't do anything!  Motion Computing should be ashamed of themselves.  It is a nice machine but definitely NOT worth the sticker price!  They make even more money selling add-ons like the keyboard/cover.

I wonder if the keyboard (if/when I get one) will ALSO have issues!

I'll check out hotkey.  Thank you!

> re 6. :  Not many have succeeded in configuring fprint for log in.  My impression is that those who have, except for a few models of readers, still have problems with it.  It seems that most fingerprint reader manufacturers haven't released enough useful information on their hardware.

Again, the manufacturers should be outed and boycotted by our community.  Not releasing the information is completely unsatisfactory.  I was amazed the hardware even worked!

I look foward to seeing the community make a work-around.
In the meantime it is another ANTI-MOTION COMPUTING advertisement to everyone whom I show the gorgeous machine.
I use such opportunities to plug FREE SOFTWARE and to inform them about companies such as Motion Computing who are BAD. Instead of Motion helping someone like me and others in the GNU/LINUX and FREE SOFTWARE community innovate uses for their nice looking and over-priced machine on OUR OWN TERMS they have chosen to force us to use restrictive operating systems and hardware such as WINDOWS and their UNSUPPORTED HARDWARE BUTTONS to do things on someone else's terms and on our dimes!

Then to top it all off Motion Computing has the nerve to e-mail me trying to sell me more attachments for this computer.

---

### Post by Favux on 2009-05-14
Hi DrGNU,

I propose an experiment.
> -- 4-way pad (PAGE-UP/DOWN/LEFT/RIGHT SCROLL?) with a central button (ENTER?)
-- Four buttons (2 on each side of the "scroll/enter" pad) 
This sounds almost like the "pad" on Wacom external graphics tablets.  Why not try adding "pad" to your xorg.conf and see if there is any response from them.
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
# Option        "Device"        "/dev/input/wacom"    
  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
# Option        "USB"           "on"                  # USB ONLY
EndSection

```
and to "ServerLayout" under the last Wacom entry:
```
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets

```

---

### Post by DrGNU on 2009-05-14
Favux,

Thank you.

I'll have to give that a try sounds like a good experiment to me.
I'll also post my xorg.conf file.

I want to believe that at one time I did try this pad setting but I'll try again with what you have there and report back. So I keep track of such things and so others in a similar predicament can follow along.

My apologies - right now I'm a little distracted with some issues with another computer.
[http://ubuntuforums.org/showthread.php?t=1155157](http://ubuntuforums.org/showthread.php?t=1155157)

Favux, are you using a Tablet?

---

### Post by Favux on 2009-05-14
Hi DrGNU,

No.  I have a HP TX2000 usb tablet pc.

---

### Post by DrGNU on 2009-05-14
> **Favux said:**
> Hi DrGNU,

No.  I have a HP TX2000 usb tablet pc.

Hi Favux,
I am not familiar with that model.
Google images shows me this:
[http://2tu.us/f75](http://2tu.us/f75)

Pretty nice looking machine.
Does it use a Wacom active digitizer pen also?

I'm missing using a keyboard, eventually I'll spring for the convertible cover/keyboard combo for the slate.
Lately, I've been using my Asus EeePC with gNewSense installed on it and since I'm rapidly becoming a big EMACS fan I'm missing NOT having a keyboard for the slate.  I also need to get an extra battery for the LE1600 because it doesn't last more than a couple hours running full bore with wifi on etc on battery alone.
It does charge up wickedly fast though.

---

### Post by Favux on 2009-05-14
Hi DrGNU,

I gave a lot of thought to getting a Motion because they look so handy.  But getting all the accessories did drive the price up.

The HP TX series started with the TX1000 which just had a touch screen, no digitizer.  Then the TX2000 and TX2500 which have both a wacom digitizer and touch screen.  The new TX2z has the N-trig digitizer which combines the digitizer and touch screen in one and supports multi-touch.  Unfortunately multi-touch isn't yet supported in linux and the way to get it to work is to patch linuxwacom to support it.  Without, as yet, official linuxwacom support.

---

### Post by DrGNU on 2009-05-14
> **Favux said:**
> Unfortunately multi-touch isn't yet supported in linux and the way to get it to work is to patch linuxwacom to support it.  Without, as yet, official linuxwacom support.

Truly a frustrating situation to be in - and not because of any weakness with **GNU/LINUX** but purely due to the manufacturers!

I am refusing to support restrictive manufacturers and restrictive software.  When I saw the **Motion LE1600** being sold cheap (used) I couldn't resist... since before I went to Free Software I was constantly watching their products wanting to splurge on one. I'm glad I erased XP without even trying it out on it because I refuse to use XP or any Microsoft operating system any longer.

That decision has given me some frustrations, but I have learned a great deal and have only been even more impressed by the Free Software community and their tools/help as result.  I think the only thing I put on the machine that is not Free Software is one copy of the Opera Browser - which I hardly use because I use **GNUzilla IceCat**.  Since I put Ubuntu on it however there may be some other proprietary blobs of code here or there.  I wanted to get it up and running but probably could have been just as successful with **gNewSense** (100% Free Software built off of gnome/debian/Ubuntu).

**In the future** - if I ever buy hardware that can not handle a 100% Free GNU/Linux then it's getting returned for a full refund of my money.

---

### Post by richardjbrown on 2009-07-23
Hi there, wondering if you have any more luck on the LE1600. I have just install ubuntu 9.04 on a LE1600 and most things work out of the box. screen, wifi, sd card, pen. what i dont have working is

On board buttons. none of them i can get working and have really tried too much

Fingerprint scanner.i have had a go at the [think wiki]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader#Installing_and_configuring_the_driver") but have had some troubles and have not got it running.

Audio. i have had a go at the[ ALSA project]("http://www.alsa-project.org") but again still no win.

if you have got any of these working i would love to know more info on it.

cheers.

---

### Post by DrGNU on 2009-07-23
> **richardjbrown said:**
> Hi there, wondering if you have any more luck on the LE1600. I have just install ubuntu 9.04 on a LE1600 and most things work out of the box. screen, wifi, sd card, pen. what i dont have working is

On board buttons. none of them i can get working and have really tried too much

Fingerprint scanner.i have had a go at the [think wiki]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader#Installing_and_configuring_the_driver") but have had some troubles and have not got it running.

Audio. i have had a go at the[ ALSA project]("http://www.alsa-project.org") but again still no win.

if you have got any of these working i would love to know more info on it.

cheers.

Actually, I just happened to have upgraded the LE1600 to Ubuntu 9.04.  Unfortunately, that messed up my pen's button making it not work properly.  I did not get the hardware buttons to work and they do not work with the upgrade.  Wifi appears to work for me but I was upgrading to see if I could get my Sprint Pantech 500 EVDO card to work since it wasn't before.  I'll probably be working on it more later during the week.

---

### Post by DrGNU on 2009-07-23
> **DrGNU said:**
> Actually, I just happened to have upgraded the LE1600 to Ubuntu 9.04.  Unfortunately, that messed up my pen's button making it not work properly.  I did not get the hardware buttons to work and they do not work with the upgrade.  Wifi appears to work for me but I was upgrading to see if I could get my Sprint Pantech 500 EVDO card to work since it wasn't before.  I'll probably be working on it more later during the week.

I did notice (before the upgrade) that the audio ports appeared to be reversed but never got them to work satisfactorily.  I don't think the LE1600 has built-in speakers, so I was using desktop speakers plugged into the jacks.  Messing around with software settings and plugging in different ports caused me to discover things don't match the software settings clearly and the audio output was lower volume than it should be (from the wrong port).

I didn't mess around with the fingerprint reader much aside from the demo I believe I wrote about earlier.  It seemed that software was still in development at that time - things may have progressed since then.  I think I have links to what I was reading at that time at [http://delicious.com/drgnu](http://delicious.com/drgnu)

I need to rediscover the links I used to rewrite my xorg.conf file (and where to find it again - /etc?).  Well I've been working nights and am pretty tired right now.  Will write an update later if and when I make any progress.

Good luck.

-Steve

---

### Post by Favux on 2009-07-25
Hi DrGNU,

In Jaunty you are suppose to use HAL/.fdi instead of the xorg.conf.  You can add this line to the serial subsection of the 10-wacom.fdi to get the stylus button back:
```
<merge key="input.x11_options.Button2" type="string">3</merge>
```
Or you can configure it with wacomcpl.  Unfortunately the .fdi doesn't parse the device names correctly into linuxwacom names.  To see this enter in a terminal:
```
xswetwacom list
```
It should return (if wacom-tools is installed) stylus, and eraser.  To see what HAL is calling things:
```
xinput --list
```

---

### Post by DrGNU on 2009-07-25
> **Favux said:**
> Hi DrGNU,

In Jaunty you are suppose to use HAL/.fdi instead of the xorg.conf.  You can add this line to the serial subsection of the 10-wacom.fdi to get the stylus button back:
```
<merge key="input.x11_options.Button2" type="string">3</merge>
```
Or you can configure it with wacomcpl.  Unfortunately the .fdi doesn't parse the device names correctly into linuxwacom names.  To see this enter in a terminal:
```
xswetwacom list
```
It should return (if wacom-tools is installed) stylus, and eraser.  To see what HAL is calling things:
```
xinput --list
```

Thank you!
Got pen button working.
Eraser not working (ex. xournal treats like a pen)
Tried "xsetwacom list" but that gave no output...

My "xinput --list" output:
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Video Bus"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
```

For "giggles" added:
```
<merge key="input.x11_options.Button3" type="string">4</merge>
```
To my "10-wacom.fdi" file - I'll see what that breaks... :-)

---

### Post by DrGNU on 2009-07-25
Well nothing broke and eraser still not working.

---

### Post by Favux on 2009-07-25
Hi DrGNU,

So according to HAL:

stylus =  "Wacom Serial Tablet PC Pen Tablet/Digitizer"
eraser =  "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

To get wacomcpl to work so you can configure the stylus button you can either rename things or use rec's script.  See Jaunty Users 3 and 3a near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Are you adding the button stuff to the serial subsection of the 10-wacom.fdi?  And remember in Xournal the eraser is the stylus button.

---

### Post by DrGNU on 2009-07-25
> **Favux said:**
> Hi DrGNU,

So according to HAL:

stylus =  "Wacom Serial Tablet PC Pen Tablet/Digitizer"
eraser =  "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

To get wacomcpl to work so you can configure the stylus button you can either rename things or use rec's script.  See Jaunty Users 3 and 3a near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Are you adding the button stuff to the serial subsection of the 10-wacom.fdi?  And remember in Xournal the eraser is the stylus button.

I truly appreciate your continued help.
Changed the names as per your provided link.
Xournal should treat my eraser as a highlighter, yes the button is the eraser there, I mean when I turn my pen over (I do not use/have a touch screen device).

My 10-wacom.fdi file (no serils section):
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
	<merge key="input.x11_options.Button2" type="string">3</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>

</deviceinfo>
```

Gimp also mishandles the pen and doesn't let me use the buttton as a tool.
wacompl shows no device.

Thank you for helping me.
-Steve

---

### Post by Favux on 2009-07-25
Hi Steve,

No problem.

Your "Button2 3" line is in the serial subsection and in the right place.  So it should work (configuring the stylus button as a right mouse click), it's not in the USB subsection above it.

Wacomcpl should work.  If "xsetwacom list" is still empty something isn't right.  What did you do to change the names?  What does "xinput --list" look like now?

---

### Post by DrGNU on 2009-07-26
> **Favux said:**
> Hi Steve,

No problem.

Your "Button2 3" line is in the serial subsection and in the right place.  So it should work (configuring the stylus button as a right mouse click), it's not in the USB subsection above it.

Wacomcpl should work.  If "xsetwacom list" is still empty something isn't right.  What did you do to change the names?  What does "xinput --list" look like now?

My "xinput --list" [same]
```
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24576
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18432
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Video Bus"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
```

I changed the names via "gksudo gedit .xinitrc"
Did find for "stylus" and "eraser" replace with ... oh maybe this was too much?

My ".xinitrc" now:
```
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser Button1 "Button 3"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser bottomy "18543"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser bottomx "24565"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser topy "76"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser topx "33"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer bottomy "18543"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer bottomx "24565"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer topy "76"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer topx "33"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer TPCButton "off"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer Button3 "DisplayToggle 1"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer Button2 "Button 3"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer Button1 "Button 1"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer Suppress "2"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer RawSample "8"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer ClickForce "2"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer PressCurve "25 0 100 75"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser Suppress "2"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser RawSample "4"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser ClickForce "2"
xsetwacom set Wacom Serial Tablet PC Pen Tablet/Digitizer eraser PressCurve "0 0 100 100"
# run the primary system script
. /etc/X11/xinit/xinitrc
```
Maybe these should be in quotes?

---

### Post by Favux on 2009-07-26
Correct, they should be in quotes.

---

### Post by DrGNU on 2009-07-26
> **DrGNU said:**
> 
My ".xinitrc" now:
Maybe these should be in quotes?

Adding quotes didn't fix it.
```
$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/lib ]"
```
Gives no devices...

---

### Post by Favux on 2009-07-26
Check in Synaptic Package Manager that you have wacom-tools installed.

---

### Post by DrGNU on 2009-07-26
> **Favux said:**
> Check in Synaptic Package Manager that you have wacom-tools installed.

Yes it's installed.
So is X.Org X server -- Wacom input driver

---

### Post by Favux on 2009-07-26
Hi Steve,

I'm not sure what's wrong.  I guess you could try reinstalling wacom-tools and rebooting.  Otherwise you might want to try rec's script.

---

### Post by richardjbrown on 2009-08-23
I have got my fingerprint scanner working i ended up trying many different ways so not 100% sure what my process was on it all but in the end this did it for me

Fingerprint GUI
[http://www.pdfserver.net/fingerprint/](http://www.pdfserver.net/fingerprint/)

it is a lovely little app that lets you record you bioscan and then save it to a file. Then editing your PRAM to lookup that file as a means for autho.

It works VERY well. only thing is it might work alittle too well. There is a setting to turn up the "markers" on your bioscan so that your fingerprint can be check faster and better. but i did not change this. so 25% of the time my fingerprint scan fails and i simply have to rescan.


Prior to that i tried and failed to install from
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader#Installing_and_configuring_the_driver](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader#Installing_and_configuring_the_driver)

but didnt have much luck with it.

but could be something you will need to look at if the Fingerprint GUI doesnt work.


I did a full install and removal and reinstall of the ALSA drivers and tried many different mods to get it to work but so far no luck at all. 

So if anyone has any idea's on the sound card that would be wonderful. 

I have it setup as a dual boot with windows (for a Yamaha studio monitor software) and the sound works fine in there once the drivers are installed so i know the hardware works fine.

cheers

---

### Post by Nichod on 2009-08-26
I came across this useful post on getting the sound to work in the LE1600. Could someone check it out and see if it works for them?

> The sound driver is installed correctly on Ubuntu 8.10+, though the ports are not mapped on the LE1600 as other computers, therefore we need to make the following changes:

Where to make these changes: ALT+F2 and type “alsamixer”, or from the Volume icon at the system tray

Click on Preferences Button and un-hide the following:
- enable Master, PCM, and Mic for Playback
- enable only MicBoost and External Amplifier for Switches
- enable ALL Options

The most important change is the “External Amplifier” Switch, this needs to be DISABLED, sound should be coming out of the MIC jack (plug in a set of headphones), check out my screenshots in the following link to enable only whats needed in the Volume Control panel:

Note, we only need to worry about the
“Intel ICH6 ALSA (Alsa Mixer)”

[http://s28.photobucket.com/albums/c206/designjam/le1600/](http://s28.photobucket.com/albums/c206/designjam/le1600/)


---

### Post by Nichod on 2009-08-26
Anyone get the Bluetooth to work?

---

### Post by richardjbrown on 2009-08-26
> **Nichod said:**
> I came across this useful post on getting the sound to work in the LE1600. Could someone check it out and see if it works for them?


WORKS LIKE A CHARM
it works perfectly took me all of 2min to fix and remap. Thanks Heaps as for bluetooth not something i have looked at yet but i have done before with another system. So i will give it a look at.

---

### Post by Nichod on 2009-08-27
I actually think I'd be more interested in getting those hardware buttons working.

---

### Post by Davaris on 2009-09-04
What's weird is the hardware buttons always work at the very start, so I can choose operating system - only if I shut Ubuntu down fully, rather than suspend or hibernate.

EDIT:
I found some interesting things in the inf files. I don't know if it will help the technical people, but oem2.inf looks like it might have some IDs for the buttons.

I put the files here
[http://www.megaupload.com/?d=DDSUNO5R](http://www.megaupload.com/?d=DDSUNO5R)

---

### Post by iconnor on 2009-11-11
BUMP

I have been unable to get the wacom to work under jaunty or karmic.  Does wacdump work for anyone else?  Mine appears to be on ttyS1 but wacdump won't talk to it.

---

### Post by Favux on 2009-11-11
Hi iconnor,

Welcome to Ubuntu Forums!

Wacdump won't work when X starts.  With X started wacom_drv.so grabs the input and wacdump won't see it.  So you have to run wacdump before starting X.  You should be able to use xidump, as in "xidump stylus" with X running.

---

### Post by iconnor on 2009-11-12
Hey Favux, thanks for that tip, although I don't think it's the issue.

xidump stylus
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'stylus'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'stylus'
Unable to find input device 'stylus'

Also there is nothing in Xorg.0.log about wacom.  Also lshal doesn't list any wacom devices.

With no X running I use 
wacdump -c serial -f tpc /dev/ttyS1

And get no changes whenever I use the pen or click buttons, etc.

Is everyone else's on ttyS1?  I am currently on karmic, but will go back to Jaunty for more testing.

---

### Post by Favux on 2009-11-13
Hi iconnor,

I thought I should mention, in case you're on 64-bit Karmic, that people have been having trouble with it.  Their stylus may act strangely/slow or not appear at all.  There's a couple bug reports on that.  Karmic 32-bit seems to work alright for serial tablet pc's.

---

### Post by iconnor on 2009-11-18
This isn't 64bit.  This is an old CeleronM.

---

### Post by reverend1313 on 2010-06-27
Anyone get the sound to work for 10.4? They removed a ton of the options by default from the sound menu in 10.4. I messed around a little trying to see if I could get the sound to work from the speaker or with headphone but no luck. Funny thing is the MIC works ;).

---

### Post by TacoTaco! on 2010-07-26
> **reverend1313 said:**
> Anyone get the sound to work for 10.4? They removed a ton of the options by default from the sound menu in 10.4. I messed around a little trying to see if I could get the sound to work from the speaker or with headphone but no luck. Funny thing is the MIC works ;).

LE1600, 10.04 gnome [Mint 9, 32bit]: Only sound comes from mic-jack, not speakers.  :(

---

### Post by h38thsc0tt on 2010-11-15
I was able to get sound working by using alsamixer in the terminal. this exposes the options that were needed in previous releases.

---

### Post by h38thsc0tt on 2010-11-15
Has anyone had any luck with the hardware buttons or bluetooth?

---

### Post by h38thsc0tt on 2010-11-16
> **Davaris said:**
> What's weird is the hardware buttons always work at the very start, so I can choose operating system - only if I shut Ubuntu down fully, rather than suspend or hibernate.
 
EDIT:
I found some interesting things in the inf files. I don't know if it will help the technical people, but oem2.inf looks like it might have some IDs for the buttons.
 
I put the files here
[http://www.megaupload.com/?d=DDSUNO5R](http://www.megaupload.com/?d=DDSUNO5R)
 
[COLOR=black][FONT=Verdana]Thanks for the file I don't have a windows partition anymore so this helps.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I found that the Buttons correspond to a device in the /PROC files it is MCO0101 number 00:09.  Does any one know how to attach this device as a keyboard or what I need to do to install a driver for this? Thanks[/FONT][/COLOR]

---

### Post by h38thsc0tt on 2011-01-21
Still looking for help on enableing Bluetooth and the hardware keys. Anybody?

---

### Post by taesoobear on 2011-06-11
> **h38thsc0tt said:**
> [COLOR=black][FONT=Verdana]Thanks for the file I don't have a windows partition anymore so this helps.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I found that the Buttons correspond to a device in the /PROC files it is MCO0101 number 00:09.  Does any one know how to attach this device as a keyboard or what I need to do to install a driver for this? Thanks[/FONT][/COLOR]

On my LE1600, there is no /proc/MCO0101 file. I would like to know how you found out the proc files. If I can find such file, I might be able to write a daemon program to send message.

---

### Post by netipot on 2012-05-30
I hope there are still some interest in the LE1600. I just got a 1600 tablet PC & I installed bodhi OS on it. It's very fast & since it is based on ubuntu 10.04 using enlightenment I was hoping that I could use most of what people in this topic tried. The stylus works very well & I have cellwriter & easystroke. My main proplem is getting the sound to work.


Where to make these changes: ALT+F2 and type “alsamixer”, or from the Volume icon at the system tray

Click on Preferences Button and un-hide the following:
- enable Master, PCM, and Mic for Playback
- enable only MicBoost and External Amplifier for Switches
- enable ALL Options

The most important change is the “External Amplifier” Switch, this needs to be DISABLED, sound should be coming out of the MIC jack (plug in a set of headphones), check out my screenshots in the following link to enable only whats needed in the Volume Control panel:

Note, we only need to worry about the
“Intel ICH6 ALSA (Alsa Mixer)”

[http://s28.photobuck....ignjam/le1600/](http://s28.photobuck....ignjam/le1600/)

However alsamixer has changed significantly since 2009. I put alsamixer in terminal & fooled around but could not see anything like this fix. Any thoughts.

---

### Post by iconnor on 2012-06-08
I am still interested.  I have several.  Would love to put them to use.

I still can't get the digitizer working.  

I was able to get the sound to work through alsamixer, I basically just went through every option until suddenly sound came out. I'm on ubuntu precise, so don't give up!

Havn't tried buttons or bluetooth.

---

### Post by Favux on 2012-06-08
Hi iconner,

Since you are in Precise and not Lucid like netipot your problem could well be the input-attach rule.

Did you try my suggestion of following the instructions in:  [http://ubuntuforums.org/showpost.php?p=11807798&postcount=354](http://ubuntuforums.org/showpost.php?p=11807798&postcount=354)  and see if that gets your digitizer working?

---

### Post by iconnor on 2012-06-09
I did, to no effect.  

I've tried manually configuring xorg.conf... which actually causes X to crash.  

There is something different about these tablets and the wacom is not seen. Back in the day I used to try to use wacdump, etc to detect it and never got anything.  Would love some help, and I can actually send someone one of them.  They have been replaced by ipads now, so this is just a pet project.

Isaac

---

### Post by Favux on 2012-06-09
> I can actually send someone one of them.
To keep?  lol I'll take one!  :)

Alright let's try some diagnostics on the thing.  What do you see with the following command in a terminal?
```
xinput list
```
Post the output.  And also:
```
sudo dmesg | grep ttyS
```

---

### Post by iconnor on 2012-06-09
Yes to keep.  I have... 5 of them in various states of repair (some are damaged, but still work).  Their HD's generally all have bad sectors too.  I'm looking to use mine with nfsroot though..

If you want to PM me an address, I'll lookup shipping... if it's not exorbitant, I'll send you one.

Anyways

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Optical Mouse by Starck    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

iconnor@tablet3:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.843221] tty tty11: hash matches

---

### Post by Favux on 2012-06-09
That'd be fun!

The empty **xinput list** tells us X doesn't see anything.

Provided the inputattach rule was commented out this suggests:
> ~$ dmesg | grep tty
[ 0.000000] console [tty0] enabled
[ 1.843221] tty tty11: hash matches 
the internal serial connection from the digitizer to the motherboard is missing.  We could try using **xxd** to see if there is a signal on one of the ports.  Or we could try udevadm info.  We would like to know the PnP ID and other udev info anyway so let's try that first:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
Run it and if nothing try systematically changing the port, i.e. ttyS1 then ttyS2 etc.  Your choices used to be 0 to 4.  There were a few on port 5 and one I recall on 6, which meant you had to add them special.  But now, I think due to Upstart, Ubuntu has 32 ports available (0-31).  I don't think you need to go through all of them.  Since some have shifted by 4, i.e. were on ttyS0 and now on ttyS5, I think you "only" need to go to 10 (6 + 4).

I gather opening one of these things up is a pain?  So not easy to check for a loose connection?

---

### Post by iconnor on 2012-06-09
> **Favux said:**
> That'd be fun!

The empty **xinput list** tells us X doesn't see anything.

Provided the inputattach rule was commented out this suggests:

the internal serial connection from the digitizer to the motherboard is missing.  We could try using **xxd** to see if there is a signal on one of the ports.  Or we could try udevadm info.  We would like to know the PnP ID and other udev info anyway so let's try that first:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```Run it and if nothing try systematically changing the port, i.e. ttyS1 then ttyS2 etc.  Your choices used to be 0 to 4.  There were a few on port 5 and one I recall on 6, which meant you had to add them special.  But now, I think due to Upstart, Ubuntu has 32 ports available (0-31).  I don't think you need to go through all of them.  Since some have shifted by 4, i.e. were on ttyS0 and now on ttyS5, I think you "only" need to go to 10 (6 + 4).

I gather opening one of these things up is a pain?  So not easy to check for a loose connection?

This is all about the fun.  And I hate to see perfectly good hardware go to waste. 
Definitely Linux does not see the hardware.  your udevadm line gives:

  looking at device '/devices/platform/serial8250/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/platform/serial8250':
    KERNELS=="serial8250"
    SUBSYSTEMS=="platform"
    DRIVERS=="serial8250"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""

for all values of ttyS up to 31.

Linux just isn't seeing the device.  I have one of these all opened up.  The fact is that windows sees it just fine.  I think it's like the bluetooth where some bit hasn't been set and it isn't viewable whereas on the later models it just works.  I think this may require some windows debugging/reverse engineering.

---

### Post by Favux on 2012-06-10
So no incoming data stream at all on any port it looks like.

But the hardware is good and not a loose connection.  Which is very helpful to know.

I think these leaves something else claiming the port or setserial.  While I do recall some very early tablet PC's were actually Wacom serial digitizers like the old Wacom graphics tablets.  However there were very few like that, maybe a ViewSonic for example.  They were almost immediately replaced with the Wacom ISDV4 serial digitizers.   So I don't think it is worthwhile to pursue that but for comleteness sake:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV)
Almost for sure:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=ISDV4_Protocol](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=ISDV4_Protocol)

The PnP for an ISDV4 should begin with **WACf**, which was one of the things we were trying to find with udevadm info.  The only thing I can think of claiming the port would be the inputattach rule.

That seems to leave setserial and or some line discipline problem.  Maybe the automatic setserial configuration doesn't work for the 1600 for some reason.  We can probably find an example of the old setserial configuration line.  Then change the auto setserial config file, if I can remember where it is now.

I might have the PnP and configuration line in my notes somewhere.

Sorry I'm slow, right now I'm distracted coding for my little python applet.  Hopefully I'll finish that up in a day or so.  Need to test the new code.  Sure hope it works.

---

### Post by iconnor on 2012-06-12
So now I feel like a bit of an idiot...

I went looking for the serial port, and re-reading old forums.  I used seterial on /dev/ttyS0 like so:

setserial /dev/ttyS0 port 0x0238 irq 5 autoconfig

and now xxd shows events on ttyS0 when I pen around!  I swear this never worked before.  However it does now!  So on to the next step!  

Unfortunately X still crashes when I manually configure it to use wacom devices on ttyS0, but maybe if I go back to square 1 on that, I can get it going too.

---

### Post by iconnor on 2012-06-12
Still nothing found in udev lists, xinput lists, etc.  I rebooted and xxd wasn't showing input, so I retraced my steps.

After I run X with a manual wacom config in xorg.conf, X crashes, but thereafter I get events on /dev/ttyS0.  So X does something to turn on the digitizer before it crashes.  

Interesting.

---

### Post by iconnor on 2012-06-18
Looks like it's actually a TouchKO digitizer, which were bought out by wacom.  It's identifier is TKO00001, not WACf

---

### Post by Favux on 2012-06-19
Really?

Since you say it is on ttyS0
```
sudo dmesg | grep ttyS
```
then let's run a little udevadm info on it and pull up more details:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```

---

### Post by iconnor on 2012-06-21
[    1.830821] tty ttyS12: hash matches
[  319.056980] serio: Serial port ttyS0
[  321.356299] input: Wacom Serial Touchscreen as /devices/platform/serial8250/tty/ttyS0/serio5/input/input6
[  328.642697] serio: Serial port ttyS0
[  330.900298] input: Wacom Serial Touchscreen as /devices/platform/serial8250/tty/ttyS0/serio6/input/input7
[  355.425369] serio: Serial port ttyS0
[  357.688315] input: Wacom Serial Touchscreen as /devices/platform/serial8250/tty/ttyS0/serio7/input/input8


  looking at device '/devices/platform/serial8250/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/platform/serial8250':
    KERNELS=="serial8250"
    SUBSYSTEMS=="platform"
    DRIVERS=="serial8250"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by Favux on 2012-06-21
Hmm.  I'm thinking some serio driver is claiming it and that's why you're seeing:
```
[ 319.056980] serio: Serial port ttyS0
[ 321.356299] input: Wacom Serial Touchscreen as /devices/platform/serial8250/tty/ttyS0/serio5/input/input6
```
There shouldn't be anything identifying as a Wacom Serial Touchscreen grabbing it.  I'm trying to think if the wacom_w8001.ko serio driver calls itself a touchscreen.  I think it does.  That suggests it is that driver combined with inputattach claiming your digitizer.  Do you see **wacom_w8001** or **inputattach** in ***lsmod***?

Actually the Wacom serio driver should work with your tablet also.  It's just not currently necessary.  What's happening is it is probably using the wrong baudrate.  Have to check it out but I bet it's trying 38,400 because despite your udevadmin info your PnP is a WACf*.  But maybe your baudrate is suppose to be 19,200.  Or it could be the other way around I suppose.

---

### Post by iconnor on 2012-06-22
Nothing happens automatically. On fresh boot, there are no wacom related modules loaded. Here is what happens as I manually try to input attach various things. 

fresh boot: xxd /dev/ttyS0 returns no events

/lib/udev/inputattach --daemon --baud 19200 --wacom_iv /dev/ttyS0

returns no output on first attempt. Nothing in Xorg.0.log.  wacom_serial.ko is loaded. xxd /dev/ttyS0 now says Device or resource busy.

removing wacom_serial causes lots of 
[   80.552398] serio: Serial port ttyS0
[   81.572044] input (null): Timed out waiting for tablet to respond with model and version.
[   81.572071] wacom_serial: probe of serio5 failed with error -5

any further use of wacom_iv results in inputattach: device initialization failed


/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/ttyS0

returns no errors. dmesg shows
input: Wacom Serial Touchscreen as /devices/platform/serial8250/tty/ttyS0/serio207/input/input6

[   284.897] (II) config/udev: Adding input device Wacom Serial Touchscreen (/dev/input/event6)
[   284.897] (**) Wacom Serial Touchscreen: Applying InputClass "Wacom class"
[   284.897] (**) Wacom Serial Touchscreen: Applying InputClass "Wacom class"
[   284.897] (II) LoadModule: "wacom"
[   284.905] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   284.907] (II) Module wacom: vendor="X.Org Foundation"
[   284.907]    compiled for 1.11.3, module version = 0.14.0
[   284.907]    Module class: X.Org XInput Driver
[   284.907]    ABI class: X.Org XInput driver, version 16.0
[   284.908] (II) Using input driver 'wacom' for 'Wacom Serial Touchscreen'
[   284.908] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   284.908] (**) Wacom Serial Touchscreen: always reports core events
[   284.908] (**) Option "Device" "/dev/input/event6"
[   284.908] (EE) Wacom Serial Touchscreen: Invalid type 'stylus' for this device.
[   284.908] (EE) Wacom Serial Touchscreen: Invalid type 'eraser' for this device.
[   284.908] (EE) Wacom Serial Touchscreen: Invalid type 'cursor' for this device.
[   284.908] (EE) Wacom Serial Touchscreen: Invalid type 'touch' for this device.
[   284.908] (EE) Wacom Serial Touchscreen: Invalid type 'pad' for this device.
[   284.908] (EE) Wacom Serial Touchscreen: No type specified
[   284.908] (EE) PreInit returned 8 for "Wacom Serial Touchscreen"
[   284.908] (II) UnloadModule: "wacom"
[   284.908] (II) Unloading wacom

I can't seem to get udev to automatically do anything.  I've added some lines to the rules  as follows:

In /lib/udev/rules.d/40-inputattach.rules I commented out everything and added 
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="TKO0001", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --wacom_iv /dev/%k"

In /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules I added two lines
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="TKO0001", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="TKO0001", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

---

### Post by Favux on 2012-06-23
Hi iconnor,

This is bizarre.  I have always been under the impression that Motion Computing was using Wacom digitizers.  Apparently you are correct and that is not true for the LE 1600.  It is a TouchKO touchscreen with a PnP of "TKO0001".
[http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg05584.html](http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg05584.html)
[http://www.yourpcdrivers.com/driver_detail.php?id=42342&md5=dca2f5b7924a29161410592ecf8b607a&driver=touchko-resistive-touch-digitizer](http://www.yourpcdrivers.com/driver_detail.php?id=42342&md5=dca2f5b7924a29161410592ecf8b607a&driver=touchko-resistive-touch-digitizer)

I need time to digest this news.

So what, it was just luck that the linuxwacom X driver happened to support them through it's serial driver?  Then with the rewrite of the ISDV4 code that has happened since the xf86-input-wacom fork the accidental support for the TKO0001 touchscreen driver has been eliminated.  And that's why you are seeing the?
```
input (null): Timed out waiting for tablet to respond with model and version.
```
Not being Wacom ISDV4 protocol compliant it is not responding correctly to the queries?

So what the serio driver we are seeing is serial8250?  It now has the TKO0001 ID in it?  So then raw serial data is being sent to X and you have nothing to interpret it with.  Sounding like you need a serio kernel driver to massage the input so maybe the evdev X driver could handle it.  Or write a serial X driver.  This is not so good.

---

### Post by Favux on 2012-06-23
Hmm.  I'm looking at the 3.2 kernel's 8250_pnp.c (drivers/tty/serial) and I do not see the TKO0001 in it, just as in the link above.
```
	/* Wacom tablets */
	{	"WACFXXX",		0	},
	/* Compaq touchscreen */
	{       "FPI2002",              0 },
.....
	/* Fujitsu Wacom Tablet PC device */
	{	"FUJ02E5",		0	},
	/* Fujitsu P-series tablet PC device */
	{	"FUJ02E6",		0	},
	/* Fujitsu Wacom 2FGT Tablet PC device */
	{	"FUJ02E7",		0	},
	/* Fujitsu Wacom 1FGT Tablet PC device */
	{	"FUJ02E9",		0	},
```

---

### Post by Favux on 2012-06-23
From:  [http://www.gentoo-wiki.info/Motion_Computing_LE1600](http://www.gentoo-wiki.info/Motion_Computing_LE1600)
> I call setserial /dev/ttyS0 port 0x0238 irq 5 autoconfig (If this does not work, try /dev/ttyS3 instead of /dev/ttyS0 or irq5 instead of irq 5.)
It appears we don't have to mess with setserial, but just so we have that.

He goes on to show his xorg.conf.  It is the linuxwacom driver it is working on.  I suspect another key thing is he uses:
```
Option      "ForceDevice" "ISDV4"
```
which was dropped from xf86-input-wacom's wcmISDV4.c a while ago.

So the serial protocol must be close enough to ISDV4 to work expecially when the driver was told it was.

I don't know for sure if it was ISDV4 or the old serial driver that was picking up the LE1600, but my guess is ISDV4.  So using one of the legacy serio drivers:
```
/lib/udev/inputattach --daemon --baud 19200 --wacom_iv /dev/ttyS0

```
probably isn't going to get us anywhere at either baud rate.  So this udev rule is unlikely to be helpful:
```
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="TKO0001", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --wacom_iv /dev/%k"
```
It seems like you made the most progress with the wacom_w8001 serio driver:
```
/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/ttyS0
```
At least it was talking to the X driver then according to dmesg.

I don't think we need to use the wacom_w8001.ko since the problem appears to be with the X driver.  Althoug if we were I'd add it to rc.local and use:
```
inputattach --wacom /dev/ttyS0 
or
inputattach --baud 38400 --wacom /dev/ttyS0
```
depending on which baud rate was right.  I think we should just eliminate any possibly extra layers of stuff and try to get as direct as possible.  Unless we want to try it and try to let the tablet fall through to evdev and see if its tablet catchall snippet picks the LE1600 up.

So what would happen if we mess with wcmISDV4.c?  Try something like changing at about line #931:
```
static ISDV4ModelDesc isdv4_models[] = {
	{ "WACf%x", WACOM_VENDOR_ID, set_keybits_wacom },
	{ "FUJ%x", 0 /* FIXME: */, set_keybits_fujitsu },
	{ NULL, 0 }
};

```
to
```
static ISDV4ModelDesc isdv4_models[] = {
	{ "WACf%x", WACOM_VENDOR_ID, set_keybits_wacom },
	{ "FUJ%x", 0 /* FIXME: */, set_keybits_fujitsu },
	{ "TKO0001", 0, set_keybits_wacom },
	{ NULL, 0 }
};

```
Then if that doesn't work try set_keybits_fujitsu.  See if that gets us anywhere.

---

### Post by iconnor on 2012-06-23
Where do we find wcmlSDV4? is it in xorg?

I should mention that I also have an LE1600 that works just fine, but it has an A appended to the model.  The TouchKO was bought by wacom at pretty much exactly when these tablets were purchased.  Most people probably have the later model which is a proper wacom.

---

### Post by iconnor on 2012-06-23
Never mind, found it, building now.

---

### Post by iconnor on 2012-06-23
So I did as you suggested, X is still not auto-detecting it. 

I played with isd4-serial-debugger, which seems to report good stuff.  For example, this is the output after  a quick swipe of the pen:
TABLET: version: 13760
TABLET: x max: 56731 y max 65449
TABLET: tilt_x max: 127 tilt_y max 102
TABLET: pressure max: 960
TOUCH version: 7616
TOUCH x max: 21741 y max 33130
TOUCH panel resolution: 120
TOUCH capacity resolution: 49
TOUCH sensor id: 2

My input attach doesn't have wacom as a valid mode.  It has w8001, wacom_iv, wacom_5

---

### Post by iconnor on 2012-06-23
I'm mostly confused at this point about why X isn't seeing it.  I've added TKO0001 to the 50-wacom.conf in /etc/X11/xorg.conf.d/ and in /usr/share/X11/xorg.conf.d

---

### Post by Favux on 2012-06-23
That looks like some progress!
> I should mention that I also have an LE1600 that works just fine, but it has an A appended to the model. 
That's interesting.  You said Wacom bought them?  Do you have a link to that?  Maybe knowing some more details like when might give us a better fix on things.
> I played with isd4-serial-debugger, which seems to report good stuff.
That looks excellent.  That's with it on w80001 and inputattach?  Although the
> TABLET: pressure max: 960
bothers me.  I'd think 256 would be more likely.
> My input attach doesn't have wacom as a valid mode. It has w8001, wacom_iv, wacom_5 
I was looking at the README in input-wacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)  Are you using the one from the Linux Console Project?  Whichever one gets us the w80001 serio driver.
> I've added TKO0001 to the 50-wacom.conf in /etc/X11/xorg.conf.d/ and in /usr/share/X11/xorg.conf.d 
Can you show me those?
> I'm mostly confused at this point about why X isn't seeing it.
Let's concentrate on that then for a moment.  Post to follow.

---

### Post by Favux on 2012-06-23
We want to remove the stuff from 69-wacom.rules in /lib/udev/rules.d/.  Then make our own file called say 72-touchko-touchscreen.rules and stick it in /etc/udev/rules.d/.

Then we want to base the rule on the "new" ISDV4 rules here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)

So something like:
```
ACTION!="add|change", GOTO="wacom_end"

SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="TKO0001", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

LABEL="wacom_end"
```
or
```
ACTION=="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="TKO0001", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
```

What I'm uncertain of is what kernel driver is picking it up since it doesn't appear to be in 8250_pnp.c.  As long as it is working I suppose we don't have to worry about that for now.  But at some point we should figure that out.

---

### Post by iconnor on 2012-06-23
> **Favux said:**
> That looks like some progress!

That's interesting.  You said Wacom bought them?  Do you have a link to that?  Maybe knowing some more details like when might give us a better fix on things.



[http://www.prnewswire.com/news-releases/wacom-acquires-touchko-to-expand-human-interface-solutions-58174707.html](http://www.prnewswire.com/news-releases/wacom-acquires-touchko-to-expand-human-interface-solutions-58174707.html)

> **Favux said:**
> 
That looks excellent.  That's with it on w80001 and inputattach?  Although the

bothers me.  I'd think 256 would be more likely.


That's with nothing loaded.  isdv4-serial-debugger talks straight to the serial port.

> **Favux said:**
> 
I was looking at the README in input-wacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)  Are you using the one from the Linux Console Project?  Whichever one gets us the w80001 serio driver.


It's from the wacom_serial and wacom_serial5 projects.  I also have the stock ubuntu precise inputattach, which also doesn't support wacom as a mode.

> **Favux said:**
> 

Can you show me those?


Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9|TKO0001"
        Option "Device" "/dev/ttyS0"
        Driver "wacom"
EndSection

---

### Post by Favux on 2012-06-23
The xorg.conf.d .conf file looks good.  Either of those serial snippets might match.  Probably doesn't hurt to add the ttyS0 match.  I was worried when you said you had two, one in /etc.

As near as I can tell the buy out of TouchKO happened in 2007 or early 2008.  Hmm.  Looks like the LE1600 was released July '05.  So can't make the timing work.

---

### Post by iconnor on 2012-07-15
Regardless of When or why, this tablet has a touchKO digitizer. 

I don't understand why none of the udev or X rules to detect it are working.

---

### Post by marcaroni on 2012-10-17
anybody ever get bluetooth working on LE1600 or LE1700 models?

---

