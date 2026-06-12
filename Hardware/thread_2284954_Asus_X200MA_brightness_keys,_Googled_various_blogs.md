---
title: "Asus X200MA brightness keys, Googled various blogs and threads, still stuck"
date: 2015-07-02
forum: Hardware
---

### Post by nic_de_vera on 2015-07-02
Installed Ubuntu 14, the fn + F5, F6 brightness keys don't work, locked on max brightness. [This blog post]("http://sajan.io/blog/asus-x200m-perfect-linux-ubuntu-xubunu-utility-laptop") said add GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=" to the grub file, did that, now I can decrease brightness by one click and that's as far as it will go.
[COLOR=white][FONT=Consolas]GRUB_CMDLINE_LINIUX_DEF[/FONT][/COLOR]

---

### Post by NoWayWin8 on 2015-07-02
Does it work if you change it to this: GRUB_CMDLINE_LINUX_DEAULT="quiet splash acpi_backlight=vendor"  Remember to run **sudo update-grub** after editing etc/default/grub or the changes aren't applied.

---

### Post by vq1 on 2015-07-02
I have a HP elitebook 2730 and I also tried those grub edits with no success. 

Instead I got xbacklight and xbindkeys 

and choose the hotkeys I wanted to dim and brighten the screen. 

If that sounds like something that would solve your problem but you have trouble getting it to work I can look for the specific tutorial I followed. 

good luck

---

### Post by nic_de_vera on 2015-07-02
Been on this all night, I can sudo gedit /etc/default/grub and sudo update-grub in my sleep. Still doesn't work. Tried stuff from [this thread]("http://askubuntu.com/questions/266046/brightness-function-keys-not-working?rq=1") so so far I've done:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=vendor acpi_backlight=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux acpi_backlight=vendor"

and nothing works, the function keys do nothing, Settings, Brightness doesnt work either. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=" is the closest to working, I get some response from the function keys and I can bring it down to about 80% brightness. xrandr works for dimming but isn't persistent, it's right back at max brightness after restart. Tried Brightness Control in the Software Center, I get an error "Package dependencies cannot be resolved brightness-controller: Depends: python (>= 2.7.1-0ubuntu2) but 2.7.5-5ubuntu3 is to be installed
                       Depends: python-wxgtk2.8 but it is not going to be installed

I've seen bug threads that say this is fixed, maybe if I update to Ubuntu 15? I'd like to make this Asus my main machine, but the brightness is hard on the eyeballs.

---

### Post by NoWayWin8 on 2015-07-02
Does the brightness slider work? (its on "Brightness & Lock" in System Settings)  For the grub file, have you tried just GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

---

### Post by nic_de_vera on 2015-07-03
Sys Settings, Brightness & Lock, I can move the slider around but it does nothing. When I'm on [COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi=" and I press fn+F5, the indicator shows on the upper right, brightness goes down to 80% and doesn't go down any further, and the slider in Brightness & Lock follows.[/COLOR]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Ok that works the same, can bring it down one click.
Looking into xbacklight

---

### Post by NoWayWin8 on 2015-07-03
What shows up under sys/class/backlight ? ```
ls /sys/class/backlight
```

---

### Post by nic_de_vera on 2015-07-04
ls /sys/class/backlight
outputs "acpi_video0 intel_backlight"

Saw some Youtube stuff on this, I can setup a xorg config file, seems complicated.
Yesterday I tried xbacklight and pretty much gave up, did xbacklight -dec 50 then xbacklight -get, the number wouldn't even change. Figured that's it, game over, this sucker's just really locked into max bright, less tha ideal but hell, I can live with it.

Today I do xbacklight -dec 50, check with xbacklight -get, the number goes down but the screen doesn't look different. Will try restarting. God I've missed Ubuntu yakshaving. Not.

---

### Post by NoWayWin8 on 2015-07-04
> **nic_de_vera said:**
> ls /sys/class/backlight outputs "acpi_video0 intel_backlight"  Ok try GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=intel_backlight" in /etc/default/grub.  By the by, does this computer also have an Nvidia graphics card in addition to Intel?

---

### Post by nic_de_vera on 2015-07-04
"quiet splash acpi_backlight=intel_backlight" does nothing, no applet in the corner. There are several confusing versions of the Asus X200MA, looking at online specs at the same low pricepoint, this may have Nvidia. So "quiet splash acpi_backlight=nvidia_backlight"?

To clarify, I don't really need functioning brightness keys, any hack that would just have this permanently fixed at, say, 10% brightness would be great, I would thank the software gods and burn an offering in thanksgiving.

---

### Post by NoWayWin8 on 2015-07-04
It's definitely Intel that controls backlighting, at least for the built-in monitor. You can see your graphics devices with **sudo lspci | grep VGA**

A [suggestion](https://wiki.ubuntu.com/Kernel/Debugging/Backlight) in the Ubuntu Wiki is to explicitly tell xorg by creating a file...
```
sudo nano /usr/share/X11/xorg.conf.d/80-backlight.conf
```
And put this text in the file:
```
Section "Device"
    Identifier  "Intel Graphics"
    Driver      "intel"
    Option      "AccelMethod"     "sna"
    Option      "Backlight"       "intel_backlight"
    BusID       "PCI:0:2:0"
EndSection
```
Then save and exit (ctrl-o, enter, ctrl-x) then reboot.

---

### Post by NoWayWin8 on 2015-07-05
Incidentally, the "acpi_osi=" parameter from grub might interfere with hardware switches (like power button or wifi button if you have one). You may want to change it back to the default "quiet splash".

---

### Post by nic_de_vera on 2015-07-07
Put it back on quiet splash, xorg conf done, setup xbacklight in keyboard shortcuts, and ok, now I can drop the brightness down to 20% or even zero. Good thing too, max bright burns through the battery in 3 hours. Wish it was persistent, 20% brightness at bootup, but I'll tackle that some other time. Thanks NoWayWin8 and vq1.

---

### Post by vq1 on 2015-07-08
> **nic_de_vera said:**
> Put it back on quiet splash, xorg conf done, setup xbacklight in keyboard shortcuts, and ok, now I can drop the brightness down to 20% or even zero. Good thing too, max bright burns through the battery in 3 hours. Wish it was persistent, 20% brightness at bootup, but I'll tackle that some other time. Thanks NoWayWin8 and vq1.

happy it worked for you. cheers

---

### Post by nordbergsam on 2015-09-01
I tried this method, (NoWayWin8's method as shown in [http://ubuntuforums.org/showthread.php?t=2284954&p=13315287#post13315287](http://ubuntuforums.org/showthread.php?t=2284954&p=13315287#post13315287) ) in addition to all combinations of the previously mentioned acpi_ options, but nothing works for me at all. I have utterly no control over the backlight in my Asus X200M (Lubuntu 14.04 here). 
The best I ever get is the presence of the on-screen slider when hitting Fn-F5/F6 when using the "acpi_osi=" option, but of course the actual brightness never changes. I'm really at a loss here. The screen when in use is at 100% brightness which kills my eyes and my battery. I didn't have any luck with xbacklight either. Would love to hear any other suggestions; this is really driving me mad.

---

### Post by nic_de_vera on 2015-09-01
I dunno, but I remember it took a while before xbacklight started working for me. Maybe it's a Lubuntu compatibility thing? As I understand it a lot of functionality's sacrificed to keep the lightweight desktop zipping along.

---

### Post by nordbergsam on 2015-09-02
Hmm well after installing acpi_support, xbacklight has begun working for me, though I did mess around quite a bit so they may be unrelated. 
Just for future reference, I had also tried adding the ***video.use_native_backlight=1*** tag to the GRUB boot menu as suggested on other threads. Had no luck there either. 
I guess for now, I'll rely on xbacklight. I do also notice that core temperature monitoring doesn't work on the X200MA for me either. Seems like more than one ACPI issue here. I might do the nuclear option and go back to Windows :-P

---

### Post by nic_de_vera on 2015-09-02
Oh and low bright at startup's easy, search for Startup Applications, setup 

xbacklight -set 5

and bam, you've got a dim screen right after bootup without any fn key combos

---

### Post by Muthiullah on 2016-04-18
> **NoWayWin8 said:**
> Incidentally, the "acpi_osi=" parameter from grub might interfere with hardware switches (like power button or wifi button if you have one). You may want to change it back to the default "quiet splash". Thx a lot, this is very helpful, so, do you mind if i ask another question?, okay however, this is my condition, sometimes I write stuff on libre office and I need to set the light low and in another time I prefer to watch videos with more light, so if there is a way to activate the hotkey with fn key and f5 or f6 to set the backlight, that'll be great....!!

---

### Post by nic_de_vera on 2016-04-20
> **Muthiullah said:**
> Thx a lot, this is very helpful, so, do you mind if i ask another question?, okay however, this is my condition, sometimes I write stuff on libre office and I need to set the light low and in another time I prefer to watch videos with more light, so if there is a way to activate the hotkey with fn key and f5 or f6 to set the backlight, that'll be great....!!

I can't get it to work with the fn key for some reason, but in Keyboard settings, Custom Shortcuts, I setup Ctrl+F5 = xbacklight -5 and Ctrl+F6 = xbacklight +5. Have to remember a diff finger combo but otherwise works fine.

---

