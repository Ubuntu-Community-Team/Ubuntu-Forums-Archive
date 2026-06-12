---
title: "Wacom settings not working in 11.04"
date: 2011-05-09
forum: Hardware
---

### Post by Dave M G on 2011-05-09
Because of Nvidia driver problems my upgrade failed and I had to do a clean install of Ubuntu 11.04.

Now I have my system restored, but my Wacom tablet is no longer set to the preferences I had before.

The real problem is that the method I used to set it last time under 10.10 does not seem to apply. (Which is par for the course because Wacom settings are **never** the same twice.)

Before, I created this file:

```
/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```

... and then I added the following details:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
    <merge key="input.x11_options.Mode" type="string">Relative</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.Button3" type="string">2</merge>
        <merge key="input.x11_options.Speed" type="string">1.2</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>
```

... but this isn't working.

So what unholy rituals do I need to perform this time to get Wacom running again?

---

### Post by Favux on 2011-05-09
Hi again Dave M G,

I think you mean Karmic (9.10) because with Lucid  (10.04) they ditched HAL/.fdi files in favor of xorg.conf.d/.conf files.  RIP HAL.  So in Natty you now get to configure a wacom.conf file.  But since you now have X server 1.10 with Natty you can actually configure dependent devices again!  Hurrah!

This time I've got some fancy mediawiki pages for you to look at:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

---

### Post by Dave M G on 2011-05-10
Favux,

Thanks for responding. Your constant efforts to deal with Wacom issues for all Ubuntu users is much appreciated.

Turns out I'm an idiot. Or at least very forgetful. I had been down this road before, with your help:
[http://ubuntuforums.org/showthread.php?t=1592422]("http://ubuntuforums.org/showthread.php?t=1592422")

The problem was that I saved the wrong notes on my computer... so I was just repeating old mistakes.

D'oh!

Anyway, it's solved now. I'm using the right configuration file in the right place.

Still hoping for the day when we can use a nice GUI for Wacom configuration.

Anyway, thanks again.

---

