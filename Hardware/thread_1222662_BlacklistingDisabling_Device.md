---
title: "Blacklisting/Disabling Device?"
date: 2009-07-25
forum: Hardware
---

### Post by Petro on 2009-07-25
I've got problem with my touchsmart tx2 touchscreen and i would like to disable it, but after hours and hours of googling i haven't found a working solution!
In Windows of course disabling device is point click disable but how on earth do i do it on Linux?
I've found out that blacklisting something might help but after few tests i just gave up on it. I also tried deleting it from /dev/input/ but it magically popped back there.

I took screenshot of the gnome-device-manager with the problem device info in there, if it helps :)
[http://petro.darkstars.co.uk/work/Kuvakaappaus.png]("http://petro.darkstars.co.uk/work/Kuvakaappaus.png")

---

### Post by Favux on 2009-07-25
Hi Petro,

Why do you want to disable it?

You don't say what version of Ubuntu you are using.  It looks like it's configuring the digitizer through the n-trig subsection of the 10-wacom.fdi.  So you would just comment that out.  Unless you also have n-trig entries in your xorg.conf.

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

Why do you want to disable it?

You don't say what version of Ubuntu you are using.  It looks like it's configuring the digitizer through the n-trig subsection of the 10-wacom.fdi.  So you would just comment that out.  Unless you also have n-trig entries in your xorg.conf.

Version of Ubuntu is Jaunty. I want to disable it because the pen doesn't work that well when touchscreen is on (the pen doesn't disable touchscreen like it does in windows). xorg.conf doesn't have anything about n-trig right now.

I will see if editing /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi helps :) thanks for help i'll post results soon.

---

### Post by Favux on 2009-07-25
Hi Petro,

OK.  That will knock everything out.

Ayuthia has figured out how to get stylus and touch working for Jaunty using Rafi Rubin's patches.  You use the xorg.conf though.  See Appendix 2 near the bottom here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

You do need to comment out the n-trig subsection in the 10-wacom.fdi for his kernel deb.s and the xorg.conf to work right.  If you need any help with that let me know.

---

### Post by Petro on 2009-07-25
Hmm... seems like that touchscreen is not in 10-wacom.fdi only stylus functions are there. Touchscreen info.parent contains "if1" and stylus has "if0". So touchscreen is not configured there if i understand correctly.

<match key="info.product" contains="HID 1b96:0001">
 <match key="info.parent" contains="if0">
  <merge key="input.x11_driver" type="string">wacom</merge>
  <merge key="input.x11_options.Type" type="string">stylus</merge>
 </match>
</match>

Is there a way to configure touchscreen so that it's disabled in 10-wacom.fdi? with of changing the matching key to "if1" in this case?

---

### Post by Favux on 2009-07-25
Hi Petro,

No.  The stylus and touch screen are both on the same usb by-path (if0) with the n-trig.  The if1 isn't the touchscreen, we haven't figured out what it is.  If you look at lshal there's an if2 also.

The only way to knock out just touch is through the xorg.conf as far as I know.

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

OK.  That will knock everything out.

Ayuthia has figured out how to get stylus and touch working for Jaunty using Rafi Rubin's patches.  You use the xorg.conf though.  See Appendix 2 near the bottom here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

You do need to comment out the n-trig subsection in the 10-wacom.fdi for his kernel deb.s and the xorg.conf to work right.  If you need any help with that let me know.

Hi Favux,
I have read all the ways to get touchscreen and stylus working at the same time but it usually brings just more problems. Does inking with stylus now work while your hand is touching touchscreen? If this is problem is fixed i can try Ayuthia's way .

---

### Post by Favux on 2009-07-25
Hi Petro,

I'm not sure.  I know that angel120 had some problems with Xournal but we could knock touch out for him while preserving the stylus using the xorg.conf (Ayuthia's way).  And most folks are able to use a xsetwacom command to turn touch on and off.  Not sure why that didn't work for angel120, he may not have installed wacom-tools.

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

No.  The stylus and touch screen are both on the same usb by-path (if0) with the n-trig.  The if1 isn't the touchscreen, we haven't figured out what it is.  If you look at lshal there's an if2 also.

The only way to knock out just touch is through the xorg.conf as far as I know.

Hi Favux,
That clears things up a bit. Even tho it makes me wonder what "if1" is cause it's HID 1b96:0001 too. To me it looked like that HID 1b96:0001 with "if0" is stylus and HID 1b96:0001 with "if1" is touchscreen.
I would like to try disabling HID 1b96:0001 "if1" in 10-wacom.fdi do you know how that can be done?

---

### Post by Favux on 2009-07-25
Hi Petro,

No I don't know how to do it.  Ayuthia and I tried to get a working .fdi, but couldn't.  You can look at our efforts starting in post #169 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=17](http://ubuntuforums.org/showthread.php?t=1038898&page=17)

Maybe you'll figure out what we missed.

---

### Post by Favux on 2009-07-25
Hi Petro,

I wonder if adding to the n-trig part of the .fdi:
```
<merge key="input.x11_options.Touch" type="string">off</merge>
```
after
```
<merge key="input.x11_options.Type" type="string">stylus</merge>
```
would do what you want?

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

I wonder if adding to the n-trig part of the .fdi:
```
<merge key="input.x11_options.Touch" type="string">off</merge>
```
after
```
<merge key="input.x11_options.Type" type="string">stylus</merge>
```
would do what you want?

Hi Favux,
That would do what i wan't if it would work. I also tried to put just the touchscreen working .fdi with no success. I'm starting to believe that problem is elsewhere. Also now i'm sure that "if1" is not touchscreen.
I have fiddled with .fdi enough and i'm ready to give up.

now .fdi looks like this.
<match key="info.product" contains="HID 1b96:0001">
        <match key="info.subsystem" contains="input">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <merge key="input.x11_options.Touch" type="string">off</merge>
          <merge key="input.x11_options.Button2" type="string">3</merge>
        </match>
      </match>

---

### Post by Favux on 2009-07-25
Hi Petro,

Sounds like you're saying touch off in the .fdi isn't working.  The .fdi I came up with looks like:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="info.product" type="string">stylus</merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>
    </match>
```
with the info.product stylus line to try and get:
```
xinput --list
```
to call it stylus.  The only other thing I can think of is to add an USB on line and see if that does anything.  Doubtful.

---

### Post by Favux on 2009-07-25
OK, here's everything including the kitchen sink:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="info.product" type="string">stylus</merge>
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Mode" type="string">absolute</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>
    </match>
```

---

### Post by Petro on 2009-07-25
> **Favux said:**
> OK, here's everything including the kitchen sink:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="info.product" type="string">stylus</merge>
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Mode" type="string">absolute</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>
    </match>
```
Hi Favux,
my touchscreen still works after that, unfortunately. It's odd that touching the screen works as mouse scroll but that probably is common symptom.

---

### Post by Favux on 2009-07-25
Hi Petro,

Not surprising.  The only added line that I know works is the stylus button line.  The problem is we don't know what Timo did to get basic stylus function for n-trig.  It's clear he didn't do all the n-trig patches to linuxwacom.

The only way I know to get things "working" is to apply Rafi Rubin's patches either to linuxwacom for Intrepid or the kernel patches (or newer kerenels that have them) and then the n-trig.patch for Jaunty.  And Ayuthia's done that.  His deb.s plus the xorg.conf should get you what you want.

Edit:  This thread talks about setting things up:  [http://ubuntuforums.org/showthread.php?t=1206355&page=9](http://ubuntuforums.org/showthread.php?t=1206355&page=9)  Just remember the by-path changes depending on whether you have Vista or Win7 firmware.

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

Not surprising.  The only added line that I know works is the stylus button line.  The problem is we don't know what Timo did to get basic stylus function for n-trig.  It's clear he didn't do all the n-trig patches to linuxwacom.

The only way I know to get things "working" is to apply Rafi Rubin's patches either to linuxwacom for Intrepid or the kernel patches (or newer kerenels that have them) and then the n-trig.patch for Jaunty.  And Ayuthia's done that.  His deb.s plus the xorg.conf should get you what you want.

Edit:  This thread talks about setting things up:  [http://ubuntuforums.org/showthread.php?t=1206355&page=9](http://ubuntuforums.org/showthread.php?t=1206355&page=9)  Just remember the by-path changes depending on whether you have Vista or Win7 firmware.
Hi Favux,
yep i give up on .fdi, but thanks for help! Ayuthia's deb's here i come.

---

### Post by Petro on 2009-07-25
Hi Favux,
i installed .deb's and magically touchscreen doesn't work! I still have all the n-trig stuff in .fdi and nothing in xorg.conf. Works perfectly now.

---

### Post by Favux on 2009-07-25
Hi Petro,

Awesome!  What does the .fdi look like?

---

### Post by Petro on 2009-07-25
> **Favux said:**
> Hi Petro,

Awesome!  What does the .fdi look like?
Hi Favux,
.fdi looks like this. It's the one you gave. Probably doesn't even need "Touch off" there, cause it probably does nothing anyway.

<!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
       <merge key="info.product" type="string">stylus</merge>
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Mode" type="string">absolute</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
       <merge key="input.x11_options.Button2" type="string">3</merge>
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>
    </match>

---

### Post by Favux on 2009-07-25
Hi Petro,

You're probably right.  You could try removing the lines one at a time and see if it makes a difference.
```
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Mode" type="string">absolute</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>

```
I'd go from the bottom up and remove the touch off line last:
```
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>

```

---

### Post by Petro on 2009-07-26
> **Favux said:**
> Hi Petro,

You're probably right.  You could try removing the lines one at a time and see if it makes a difference.
```
       <merge key="input.x11_options.USB" type="string">on</merge>
       <merge key="input.x11_options.Mode" type="string">absolute</merge>
       <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>

```
I'd go from the bottom up and remove the touch off line last:
```
       <merge key="input.x11_options.Touch" type="string">off</merge>
      </match>

```

Hi Favux,
As suspected removing those lines did nothing touchscreen still disabled. But now i tried setting touch settings for HID 1b96:0001 "if1" device, and of course nothing worked.

---

### Post by Favux on 2009-07-26
Hi Petro,

Right.  That's the perspective Ayuthia and myself were coming at it from.  We wanted to get stylus and touch both working.  Couldn't do it with a .fdi.

---

