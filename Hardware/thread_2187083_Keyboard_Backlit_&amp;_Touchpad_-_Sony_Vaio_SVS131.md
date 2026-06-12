---
title: "Keyboard Backlit &amp; Touchpad - Sony Vaio SVS13117GAB"
date: 2013-11-10
forum: Hardware
---

### Post by mahiyabz on 2013-11-10
Greetings,

i have just installed Ubuntu 12.04 on my Sony SVS13117GAB  ([http://www.sony-asia.com/product/svs13117ga](http://www.sony-asia.com/product/svs13117ga))

1st my Backlit keyboard is not working.
2nd due to large touchpad, its extremely sensitive (even i brought the senstivity down from Mouse / TouchPad settings) which annoys a lot when typing.

any hints how can i fix both issues ?

thanks

---

### Post by Remten on 2013-11-11
I'm new to linux, so definitely not the best person to answer. But since nobody else has answered at all, maybe this will help a little.

For the touchpad problem:
Which desktop environment are you using?

In **XFCE**, there is an option in[INDENT]Settings -->  Mouse & Touchpad --> Devices[/INDENT]
[INDENT]for Device, choose the Touchpad option[/INDENT]
[INDENT]click the Touchpad tab[/INDENT]
[INDENT]you can now adjust Sensitivity* (under the Buttons & Feedback tab) and
[/INDENT]
[INDENT]click "Disable touchpad while typing"  (under the Touchpad tab)
[/INDENT]
 
In Ubuntu, according to this community help manual page:
> **Basic Configuration with a Graphical Interface**

 **Ubuntu** provides configuration of the most common touchpad options in **System > Preferences > Mouse**, under the Touchpad tab. If you cannot find this tab, see the Troubleshooting section at the end of this page. 
Try the touchpad after unchecking the **Enable mouse clicks with touchpad** check box. 
Check operation after **Enable horizontal scrolling** is checked. This may not have been the default setting. 
 
**Disabling Touchpad while Typing**

 Go  to System > Preferences > Mouse > Touchpad and uncheck 'Disable  touchpad while typing' and 'Enable mouse clicks with touchpad'
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

**LXDE** (eg lubuntu) doesn't seem to offer a similar way to set touchpad settings from the settings menu, as far as I have been able to tell. A workaround might be to use the [COLOR=#0000cd]syndaemon[/COLOR] command in a terminal, as mentioned here:
[http://ubuntuforums.org/showthread.php?t=2097515&p=12418981#post12418981](http://ubuntuforums.org/showthread.php?t=2097515&p=12418981#post12418981)

*edit:  I just noticed after I posted this that you already mentioned you had adjusted the sensitivity that way

---

### Post by mahiyabz on 2013-11-11
Thanks Remten,

but unfortunately am not able to control both. touchpad and backlit (or ambient light sensor) nothing is working.

---

