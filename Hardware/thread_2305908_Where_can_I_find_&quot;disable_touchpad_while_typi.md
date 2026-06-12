---
title: "Where can I find &quot;disable touchpad while typing&quot;?"
date: 2015-12-10
forum: Hardware
---

### Post by jander on 2015-12-10
Hey

This can be a really silly question, but here I go...

I'm using UbuntuGnome 15.10 Wily Warewolf and in Settings -> Mouse and touchpad there is no option to disable touchpad while typing. Where is it?

I tried googling for it, but apparently I am the only one missing the feature. Also no luck in Ubuntu Forums.

This is what I have:

[IMG]https://www.dropbox.com/s/2qxi3yph9k34qsj/Captura%20de%20tela%20de%202015-12-10%2011-11-08.png?dl=1[/IMG].

The screenshot is in Portuguese and under "touchpad" you can see "pointer speed", "tap to click", "two finger scrolling" and "natural scrolling".

Thanks!

Jander

---

### Post by sudodus on 2015-12-10
Maybe these terminal window commands can help you. (I often use Lubuntu in laptops, and then I turn off the touchpad and use only a mouse.)

```

       Option "TouchpadOff" "integer"
              Switch off the touchpad.  Valid values are:

              0   Touchpad is enabled
              1   Touchpad is switched off
              2   Only tapping and scrolling is switched off
              Property: "Synaptics Off"

```

This means that

```
synclient touchpadoff=1
```
will turn off the touchpad completely and
```
synclient touchpadoff=2
```
will turn off only tapping and scrolling.

See ```
man synaptics
``` for more details.

You can also start syndaemon in the background, which disables the touchpad while typing

```
syndaemon -d
```

See ```
man syndaemon
``` for more details.

I know that this works in Lubuntu and Xubuntu, but I'm not sure about Ubuntu Gnome. There might be a GUI program, that overrides this simple command line method. In that case I hope you get help from someone who is familiar with Ubuntu Gnome's program menu.

---

