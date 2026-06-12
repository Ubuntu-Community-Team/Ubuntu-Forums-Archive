---
title: "Genius EasyPen i405x graphics tablet in Kubuntu 11.10"
date: 2011-11-24
forum: Hardware
---

### Post by anton_melnikov on 2011-11-24
Hello everybody!

I have a little problem with my new Genius graphics tablet in Kubuntu 11.10. It was recognized correctly without installing "wizardpen" driver (have verified that by lsusb*, *xinput and contents of the /dev/input folder) but behaves pretty strange. I can move mouse pointer with tablet's pen, but can't click on things by touching tablet with it! 

By accident, I have clicked browser's window and guess what? It worked like "back" button! And button on the pen worked like "forward"! That was pretty unexpected, but now I have hope to set it up correctly :) So, do I have to remap buttons or something?

---

### Post by Favux on 2011-11-24
Hi anton_melnikov,

It could be on the wrong driver, say evdev, which is why you are seeing that behavior.  What is the tablet line in the output of:
```
lsusb
```
run in a terminal?  Also what is the output of?
```
xinput list
```

---

### Post by anton_melnikov on 2011-11-24
Thanks for reply, Favux!
```
anton@ubunchu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 005 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 001 Device 004: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
```The last one is the tablet.

```
anton@ubunchu:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; Genius EasyPen i405X                      id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; LITEON Technology USB Multimedia Keyboard id=10   [slave  keyboard (3)]
```

---

### Post by anton_melnikov on 2011-11-24
A little update: I've read article on Ubuntu's wiki about mouse buttons configuration and successfully remapped keys, so now it works as regular mouse. But there is no pressure detection in Mypaint yet.

```
xinput query-state "Genius EasyPen i405X"
```
That command showed me numbers of buttons when I pressed them (8, 9 and 10), than I used this command to remap them:
```
xinput set-button-map "Genius EasyPen i405X" 0 0 0 0 0 0 0 1 2 3 0
```

---

### Post by Favux on 2011-11-24
Hopefully:
```
xinput list-props "Genius EasyPen i405X"
```
will show us which driver it is on.  Again no pressure implies evdev.  Otherwise we'll need to look in /var/log at the Xorg.0.log and see what module is being loaded.

---

### Post by anton_melnikov on 2011-11-24
Yes, you were right, it uses evdev and I presume evdev doesn't have any pressure detection support? Well, that's sad. I've already tried "wizardpen" driver, couldn't get it to work. PPA mentioned in Ubuntu Wiki article doesn't have version for Ubuntu 11.10, so I've manually downloaded and installed the one for 11.04. (xorg config below). I've even created LiveUSB with 11.04 - no luck either.

//Damn, I knew I should've bought Wacom tablet, but they are nearly three times more expensive than Genius' models, and I'm not really a cool artist, just wanted to try it out.

tail -f /var/log/Xorg.0.log (after plugging in the tablet)
```
[    56.120] (II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/event7)
[    56.120] (**) Genius EasyPen i405X: Applying InputClass "evdev pointer catchall"
[    56.120] (**) Genius EasyPen i405X: Applying InputClass "evdev keyboard catchall"
[    56.120] (**) Genius EasyPen i405X: Applying InputClass "evdev tablet catchall"
[    56.120] (II) Using input driver 'evdev' for 'Genius EasyPen i405X'
[    56.120] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    56.120] (**) Genius EasyPen i405X: always reports core events
[    56.120] (**) Genius EasyPen i405X: Device: "/dev/input/event7"
[    56.120] (--) Genius EasyPen i405X: Found 10 mouse buttons
[    56.120] (--) Genius EasyPen i405X: Found scroll wheel(s)
[    56.120] (--) Genius EasyPen i405X: Found relative axes
[    56.120] (--) Genius EasyPen i405X: Found x and y relative axes
[    56.120] (--) Genius EasyPen i405X: Found absolute axes
[    56.120] (II) evdev-grail: failed to open grail, no gesture support
[    56.120] (--) Genius EasyPen i405X: Found x and y absolute axes
[    56.120] (--) Genius EasyPen i405X: Found absolute tablet.
[    56.120] (--) Genius EasyPen i405X: Found keys
[    56.120] (II) Genius EasyPen i405X: Configuring as tablet
[    56.120] (II) Genius EasyPen i405X: Configuring as keyboard
[    56.120] (II) Genius EasyPen i405X: Adding scrollwheel support                                            
[    56.120] (**) Genius EasyPen i405X: YAxisMapping: buttons 4 and 5                                         
[    56.120] (**) Genius EasyPen i405X: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    56.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input7/event7"
[    56.120] (II) XINPUT: Adding extended input device "Genius EasyPen i405X" (type: KEYBOARD)
[    56.120] (**) Option "xkb_rules" "evdev"
[    56.120] (**) Option "xkb_model" "cymotionlinux"
[    56.120] (**) Option "xkb_layout" "us,ru"
[    56.120] (**) Option "xkb_variant" ","
[    56.120] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    56.120] (WW) Genius EasyPen i405X: touchpads, tablets and touchscreens ignore relative axes.
[    56.120] (II) Genius EasyPen i405X: initialized for absolute axes.
[    56.120] (**) Genius EasyPen i405X: (accel) keeping acceleration scheme 1
[    56.120] (**) Genius EasyPen i405X: (accel) acceleration profile 0
[    56.120] (**) Genius EasyPen i405X: (accel) acceleration factor: 2.000
[    56.120] (**) Genius EasyPen i405X: (accel) acceleration threshold: 4
[    56.121] (II) config/udev: Adding input device Genius EasyPen i405X (/dev/input/mouse1)
[    56.121] (II) No input driver/identifier specified (ignoring)

```


/usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

Section "InputClass"
   Identifier "wizardpen"
   MatchDevicePath "/dev/input/by-id/usb-Genius_EasyPen_i405X-event-mouse"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/by-id/usb-Genius_EasyPen_i405X-event-mouse"
   Driver ""
EndSection

```

---

### Post by Favux on 2011-11-24
I think there is a wizardpen driver in the Oneiric repositories that works.  If so that's the one you want to install.  Check in the Software Center or Synaptic Package Manager for a package called something like xserver-xorg-input-wizardpen and install it.  After a reboot see if the tablet is working.  If not check for the wizardpen.conf in /usr/share/X11/xorg.conf.d still probably numbered 70 and post the contents.

As I recall for your model we had to modify the .conf file slightly to get the match.  I'll see if I can find something on that.

Another thing.  Given an interview Peter Hutterer gave about a month ago I think they think evdev now supports WizardPen and Aiptek tablets.  I wonder if what we need is a new .conf to configure it for evdev.  Say GeniusEasyPeni405x-on-evdev.conf.  And in it along with the match to evdev configure the buttons and tell it the z-axis coordinates.  Maybe you're not getting pressure because it isn't auto-detecting the z-axis coordinates.  It seems to be finding the x and y coordinates.

---

### Post by anton_melnikov on 2011-11-25
Wow, so you are involved with driver development? That's cool! I would like to help fix things globally, not just for me. I'm not a programmer, but a least I can test experimental stuff.

I have checked repositories, there are only drivers for Wacom and Aiptek tablets.

Also I have found that interview you mentioned. Unfortunately, there is no certain info about non-Wacom tablets support. 

> I wonder if what we need is a new .conf to configure it for evdev.  Say  GeniusEasyPeni405x-on-evdev.conf.  And in it along with the match to  evdev configure the buttons and tell it the z-axis coordinates.Russian Ubuntu wiki says about configuring HAL policies for getting pressure support. I know, there is no HAL anymore in 11.10, but maybe we can "translate" those rules to evdev config?
```

<?xml version="1.0" encoding="UTF-8" ?> 
<deviceinfo version="0.2"> 
<device>
<!-- &#1048;&#1084;&#1103; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072; (&#1079;&#1076;&#1077;&#1089;&#1100; - &#1076;&#1083;&#1103; Genius G-Pen 450) -->
<match key="info.product" contains="UC-LOGIC Tablet WP5540U"> 
<merge key="input.x11_driver" type="string">wizardpen</merge> 
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>  
<merge key="input.x11_options.TopX" type="string">1</merge> 
<merge key="input.x11_options.TopY" type="string">1</merge> 
<merge key="input.x11_options.BottomX" type="string">32768</merge> 
<merge key="input.x11_options.BottomY" type="string">32768</merge> 
<merge key="input.x11_options.MaxX" type="string">32768</merge> 
<merge key="input.x11_options.MaxY" type="string">32768</merge>  
<!-- &#1063;&#1091;&#1074;&#1089;&#1090;&#1074;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086;&#1089;&#1090;&#1100; &#1082; &#1089;&#1080;&#1083;&#1077; &#1085;&#1072;&#1078;&#1072;&#1090;&#1080;&#1103; &#1087;&#1077;&#1088;&#1072; --> 

<merge key="input.x11_options.TopZ" type="string">1</merge> 
<merge key="input.x11_options.BottomZ" type="string">1023</merge> 
</match> 
</device> 
</deviceinfo>


```

---

### Post by Favux on 2011-11-25
Cripes, you're right.  I was thinking of Natty.  There is nothing in the Oneiric repository for WizardPen nor on the PPA.  Ouch.

So let's try by starting with the "evdev tablet catchall" snippet in 10-evdev.conf.  Since that's the one matching your tablet in Xorg.0.log.

We'll create a 52-wizardpen-on-evdev.conf in /etc/X11/xorg.conf.d:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wizardpen-on-evdev.conf
```
Unfortunately *man evdev* doesn't provide too much guidance.  This assumes you have 1024 levels of pressure and we'll set a threshold of 1.
```
Section "InputClass"
        Identifier "wizardpen-on-evdev class"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "TopZ" "1"
        Option "BottomZ" "1023"
EndSection
```
Hopefully evdev accepts these Options.  If this works then we can try mapping the buttons through it too.
> Wow, so you are involved with driver development?
No, I'm no developer.  I'm just talking about helping someone else set up the same tablet in Natty or maybe it was Maverick.

---

### Post by Mnemoth on 2011-12-28
Hi anton_melnikov and favux

I bought my son a Genius i405X tablet for Christmas. I am having trouble to get it working in Ubuntu 11.10. 

I have followed you advices in this thread but do not seem to make to any change. 

The device is seen when plugged in. The is no pressure. The cursor track on the screen and the buttons are funny. 

If I enter the 'xinput set-button-map "Genius EasyPen i405X" 0 0 0 0 0 0 0 1 3 2' command I can the buttons working. at this point it seems to work just like a mouse. 

We wish to have the pressure as my son want it for Photo and Picture editing in GIMP, Inkscape. 

I have tried your suggestion regarding the 'xorg.conf.d'. I do not have a '/etc/xorg.conf.d'. If I put the file in '/usr/share/X11/xorg.conf.d/' I see no change in behaviour. and the buttons settings are lost at every connection. 

I have the .conf file and the outputs from udevadm monitor for further advice. 


Regards,
Marc

---

### Post by Favux on 2011-12-28
Hi Marc,

Welcome to the Ubuntu forums!

Pressure seems to be a big problem.  We're trying to figure things out on this thread too:  [http://ubuntuforums.org/showthread.php?t=1899225](http://ubuntuforums.org/showthread.php?t=1899225)
> I do not have a '/etc/xorg.conf.d'.
The directory path should be:
```
/etc/X11/xorg.conf.d
```
I think it is there in the default Oneiric install.

---

### Post by Favux on 2012-01-02
From the thread I linked to above, post #[http://ubuntuforums.org/showpost.php?p=11572948&postcount=17](http://ubuntuforums.org/showpost.php?p=11572948&postcount=17)  **I'll basically quote it.**

Alright, from what I am being told the evdev driver has indeed replaced the WizardPen driver in Oneiric.  Nick (Nikolai Kondrashov) says:
> It should just work for the models supported by the kernel.

See compatibility table [1]. The latest git of the patchset has untested support for one more model, see latest compatibility table [2]. If you need other models supported, I would be happy to add support for them to the kernel, provided there is anyone having the device and willing to help with diagnostics and testing.
In other words there is no need for a xorg.conf.d .conf file.  The problem being if you look in the 3.0 or later kernel the /drivers/hid/hid-kye.c is empty, no tablet entries at all.  And there isn't a hid-acecad.c at all.  Only the hid-uclogic.c has tablets entered.  It isn't clear to me whether some of the UC-LOGIC tablets and KYE tablets might be the same tablet, just with a different Vendor and Product ID.  In which case there might be something we could do.

Peter Hutterer further confirms there is no need for a .conf file because:
> evdev doesn't really treat any axes as a special one, it just forwards them. pressure is supposed to come from ABS_PRESSURE from the kernel and should just be forwarded as-is. Might be worth just running evtest against it to get the details. ABS_Z is for d devices that have a true z-axis.

there are no options specific to other axes than x and y though.
So no way to change Z axis settings.  This is a problem since it means evdev is feature incomplete for the tablets.  You should be able to change at least the pressure threshold (something like *Option "TopZ" "?"*).

In the compatibility table it doesn't matter if you are seeing a similar name to your tablet's e.g. *Genius MousePen*.  What counts is that your:
Vendor ID = 0458 = KYE Systems
Product ID = 5010
And there is no Vendor ID 0458 in Nick's compatibility table that I see much less a 5010 product model.  I only see UC-LOGIC (5543) and Waltop (172f) tablets in the table.  This appears to explain why the following tablets are not exhibiting pressure:
```
lsusb:
Bus 001 Device 004: ID 0458:5010 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius EasyPen i405X                      id=11   [slave  pointer  (2)]
```
```
lsusb:
Bus 002 Device 003: ID 0458:5011 KYE Systems Corp. (Mouse Systems)
xinput list:
&#9116;   &#8627; Genius MousePen i608X                     id=9    [slave  pointer  (2)]
```
There're probably more but I'd have to go back and look for them.

So to get your tablet working you have to do what Nick requests above and on his site:  [http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)  Send in the  usbhid-dump output he requests and then help him test kernel patches so he can submit them to the kernel.


Viktoria.s has sent in the information on the i608X so you can see examples of what's needed on the other thread.  Nick may need the information on the i405X too, not sure.  Nick is also looking for Windows usb data on these model tablets in order to learn how to "switch" them to tablet mode.

---

### Post by Favux on 2012-01-27
[SIZE="3"]**FYI Update**[/SIZE]:

Nikolai Kondrashov with the help of viktoria.s has "discovered the way to make the KYE tablets report all the data, including pressure. This was tested with EasyPen i405X, EasyPen M610X and MousePen i608X in userspace with modified usbhid-dump."

Nick is now working on the kernel driver for the KYE tablets.  He's gone to the extent of ordering an EasyPen i405X from Amazon UK to be delivered to him in Finland!  So with a little luck support should be available shortly.  :)

---

### Post by Favux on 2012-02-15
**[SIZE="3"]FYI Update:[/SIZE]**

Viktoria.s has posted Nick's new kernel support (with instructions) for the Kye Systems new tablets, the EasyPen i405X, EasyPen M610X, MousePen i608 on post #28 here:  [http://ubuntuforums.org/showthread.php?t=1899225&page=3](http://ubuntuforums.org/showthread.php?t=1899225&page=3)  Once the patched kernel driver is in place the evdev X driver should pick up the tablets automatically and you will not have to configure them in a xorg.conf.d .conf file.

The instructions are for Oneiric as is the pre-compiled patched 64-bit kernel.  I am not sure if the Natty evdev driver will work for these tablets like the Oneiric evdev driver does.

---

### Post by Favux on 2012-03-14
**[SIZE="4"]FYI everyone:[/SIZE]**   **[SIZE="3"]The DIGI*mend* project's [mediawiki]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend") is live![/SIZE]**  It already has a lot of information on these tablets and how to get them working in linux using the new method, i.e. the **evdev** driver for **Oneiric** and later.  Please take a look.

---

### Post by DwalerXIII on 2012-03-18
A few years ago I bought a Genius Easypen i405. This works very good on all versions of Ubuntu.
Last month I bought the same tablet for my kids. It looks comletely the same but I din't notice the X, it seems to be a i405X.

I can move the arrow, click an account on the login screen and can click in the notification area. 
But not on the desktop or in any window or button. It cannot draw in any drawing application.
In Mypaint another pencil can be chosen but no colour.

Hope their is a solution soon.

---

### Post by Favux on 2012-03-18
Hi DwalerXIII,

Yep, the re-branding tripped you up.  The Genius Easypen i405 was manufactured by UC-Logic while the Genius Easypen i405X is manufactured by KYE Systems.  Genius is a brand owned by KYE Systems so they went from re-branding to selling their own tablet.
> Hope their is a solution soon. 
There is.  Nikolai got the 3 new KYE tablets working about a month ago and his kernel patch was accepted by the kernel team.  It will be in the 3.4 kernel.  So the release after Precise, i.e. October of this year.

In the meantime viktoria and I are seeing if we can apply the 3.3 kernel patch to Oneiric's (and hopefully Precise's) kernel.  I already tested it and the 3.3 patch does apply to Oneiric's 3.0.  So I posted instructions here:  [http://ubuntuforums.org/showpost.php?p=11762830&postcount=45](http://ubuntuforums.org/showpost.php?p=11762830&postcount=45)  I'm waiting for viktoria to test and see if it works for her.  You're welcomed to join in.


**[SIZE="3"]FYI everyone[/SIZE]**:  I've created a new [**HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu**]("http://ubuntuforums.org/showthread.php?t=1946486") which includes the KYE tablet support instructions linked to above for Oneiric and Precise.

---

### Post by janailson on 2012-03-30
Hello, everyone. Nick created a Kernel for me. Now my Genius tablet Esypen i405x working in Ubuntu 11.10! LOL
If you want to download the kernel, just access my blog: [http://janailsonleite.blogspot.com.b...em-ubuntu.html](http://janailsonleite.blogspot.com.b...em-ubuntu.html)

Remember that it only works with: Ubuntu 11.10 oneiric Ocelot, 32bit system, Genius i405x.

---

