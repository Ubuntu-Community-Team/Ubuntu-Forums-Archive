---
title: "ctrl:nocaps for Jackalope"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by smooshy on 2009-04-25
I've been bashing my head on trying to get the old xorg.conf ctrl:nocaps behaviour working after upgrading to Jackalope.  I updated from Intrepid, and see that my xorg.conf got changed to:

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier    "Generic Keyboard"
#    Driver        "kbd"
#    Option        "CoreKeyboard"
#    Option        "XkbRules"    "xorg"
#    Option        "XkbModel"    "pc105"
#    Option        "XkbLayout"    "gb"
#    Option        "XkbOptions"    "ctrl:nocaps"
#EndSection

I had to poke at HAL in Intrepid to get the touchpad accelleration set.  Searching led me to believe that a keyboard.fdi file in /etc/hal/fdi/policy is the way to go, and the following is what I tried.
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
    <match key="info.capabilities" contains="input.keys">
      <merge key="input.x11_driver" type="string">kbd</merge>
      <merge key="input.x11_options.XkbRules" type="string">xorg</merge>
      <merge key="input.x11_options.XkbModel" type="string">pc105</merge>
      <merge key="input.x11_options.XkbLayout" type="string">gb</merge>
      <merge key="input.x11_options.XkbOptions" type="string">ctrl:nocaps</merge
>
    </match>
 </device>
</deviceinfo>

Unfortunately this left me with an unusable keyboard that appeared to generate random gibberish on key presses. I tried several variants, but either nothing happened, or the results were the same.

So, how do I turn the caplock key into a ctrl key for 9.04?

---

### Post by b100dian on 2009-05-07
Hi, 

I had the same problem. I tried to write an fdi file as said here ([http://blogmal.42.org/tidbits/xorg-hald.story](http://blogmal.42.org/tidbits/xorg-hald.story)) and ended up with this:```
<deviceinfo version-"0.2">
        <device>
                <match key="info.capabilities" contains="input.keyboard">
                        <merge key="input.x11_driver" type="string">kbd</merge>
                        <merge key="input.xkb.Rules" type="string">xorg</merge>
                        <merge key="input.xkb.Options" type="string">ctrl:nocaps</merge>
                </match>
        </device>
</deviceinfo>

```

What I also tried was, from gnome-keyboard-properties, to tick the Caps lock as ctrl option, the "Apply to all users". 

I honestly don't know which one did the trick..

*LATER EDIT: the fdi file was incorrect (version-"2.0") so just running gnome-keyboard-properties fixed it, .. but only for that session:( still searching..*

---

### Post by b100dian on 2009-05-07
Ok, next I tried to copy he fdi file from /usr/share/hal/fdi/policy/10osvendor/10-keymap.fdi and edit it.

Hal wasn't complaining about parsing (grep hal /var/log/syslog) now, but it didn't do anything.

NEeeext.. I saw that my Xorg.0.log kept on saying that it applied grp:alt_shift_toggle to keyboard devices. Which I hadn't set in the .fdi file.

So I grepped my /etc/ for this option and found /etc/defaults/console-setup which contains XKB options too. 

I modified there, and now may Xorg log prints the new settings being applied. BUT THEY DONT WORK. 

Anybody any other idea?:(

---

### Post by b100dian on 2009-05-08
Last update: editing the /etc/default/console-setup actually solved it *if* I disabled XFCE's keyboard applet's "Change layout option". You cannot do this in xfce4-xkb-plugin 0.5.3.2 but you will in 0.5.3.3.(because the blank option will be there in the selector).
Anyway, this is also an xfce xkb 'known issue' :( [http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin) "Bugs and Limitations"

Now.. I have trouble understanding WHO parses /etc/default/console-setup and WHY? dpkg -S doesnt mention any package that installs it, so it must have been generated..? I miss my slackware..

---

### Post by 73ckn797 on 2009-05-08
If you see "Configuration Editor under Applications/System Tools you can find it in there and check caplocks on.

---

### Post by b100dian on 2009-05-08
> **73ckn797 said:**
> If you see "Configuration Editor under Applications/System Tools you can find it in there and check caplocks on.

I suppose that's the gnome menu.. but I'm not sure what application is there, because I don't have a Configuration Editor in Application/System tools. 
Can you at least give the name of the process launched?
Thanks

---

### Post by 73ckn797 on 2009-05-09
> **b100dian said:**
> I suppose that's the gnome menu.. but I'm not sure what application is there, because I don't have a Configuration Editor in Application/System tools. 
Can you at least give the name of the process launched?
Thanks

I do not know the process as in a terminal command but it can be a simple gui procedure.

If you go to System/Preferences/Main Menu you can enable it to show up in the Applications/System Tools section. Once accessible open it. Go to Desktop/gnome/peripherals/keyboard. There you can check off to "remember_numlock_state".

See if that will do the trick for you.

Here is a screen shot attached

---

### Post by b100dian on 2009-05-09
Aaaah but that's gconf-editor:)

I suppose GConf could play a role here to, but not sure if it does if you use XFCE without gnome services.

However I was trying to set up Caps Lock to work as Control with simply Xorg comfogiration. And I think the OP wished the same.

In Gnome it works already.
Thanks though:)

---

### Post by mlnease on 2009-07-26
> **73ckn797 said:**
> I do not know the process as in a terminal command but it can be a simple gui procedure.

If you go to System/Preferences/Main Menu you can enable it to show up in the Applications/System Tools section. Once accessible open it. Go to Desktop/gnome/peripherals/keyboard. There you can check off to "remember_numlock_state".

See if that will do the trick for you.

Here is a screen shot attached

Hello, 73ckn797,

Attached is a screenshot of my Desktop/gnome/peripherals/keyboard settings.  Still no numlockx on login.  I have, of course, installed numlockx and properly edited /etc/gdm/Init/Default.  Still no luck.  I've overcome this particular obstacle in perhaps a dozen Hardy installs but so far no luck in Jaunty.  Any further advice?  Anyone?

Thanks in advance.

mike

---

### Post by 73ckn797 on 2009-07-27
Look under the gnome/peripherals/keyboard sub-menu in Configuration Editor. You may see one selection titled "host-computer name" (that is your computer name). See screen shot attached.

---

### Post by mlnease on 2009-07-27
> **73ckn797 said:**
> Look under the gnome/peripherals/keyboard sub-menu in Configuration Editor. You may see one selection titled "host-computer name" (that is your computer name). See screen shot attached.

Thanks very much for the response, 73ckn797.  I found the setting and it is checked 'on' (screenshot attached).  Still no numlock on login.  Any other suggestions?

Thanks for your patience.

mike

---

### Post by mlnease on 2009-08-06
> **73ckn797 said:**
> Look under the gnome/peripherals/keyboard sub-menu in Configuration Editor. You may see one selection titled "host-computer name" (that is your computer name). See screen shot attached.

Thanks, done (screenshot attached)--still no numlock on login.  Any other thoughts?  Thanks for your patience.

mike

---

