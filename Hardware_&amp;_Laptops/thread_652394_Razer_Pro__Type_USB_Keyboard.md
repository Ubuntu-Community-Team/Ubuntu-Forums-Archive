---
title: "Razer Pro | Type USB Keyboard"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by denham2010 on 2007-12-28
Hi,

Having received a [_[COLOR="Blue"]Razer Pro | Type USB keyboard[/COLOR]_]("http://www.razerpro.com/index.php?option=com_content&task=view&id=38&Itemid=49") for Christmas, I immediately set about trying to get all the special keys to work in Linux.

As a profile currently does not exist for [[COLOR="Blue"]_Key Touch_[/COLOR]]("http://keytouch.sourceforge.net/") (my personal choice for enabling special keys as I'm not familiar with the Gnome config files that do this), I set about creating a profile.

Currently, I have all the media keys on the right of the keyboard functioning, except the SHUFFLE key, and on  the left side I can only get the SLEEP and WWW buttons working. The Key Touch editor recognises the ZOOM + and ZOOM - buttons, but no matter what function I apply to them, I just can not seem to get them to work.

Reading the Key Touch site, it appears this may be a problem with the current Linux USB input driver, which is being looked at, so hopefully soon we will be able to map these missing keys.

While playing around with the keyboard in Windows, I noticed the 3 keys I was unable to recognise in Key Touch are preset with macros. The ROTATE key generates CTRL+K, 100% key CTRL+A and SHUFFLE key CTRL+H. I tried mapping these keyboard shortcuts in Linux, but it seems these keystrokes are only assigned upon the keyboard driver loading.

The L1-5 and R1-5 buttons (and the PROFILE button) are not able to be read by Key Touch either. Again, this may be to do with the USB input driver. I am also unsure if these keys actually generate a keypress event or if they only function at the keyboard level causing the assigned macro or command to be sent back to the computer.

The commands these keys send are all stored in .conf files in windows, which I believe are loaded into RAM on the keyboard when the driver loads. I did try assigning functions to these keys in Windows, hoping they would be retained and would then work in Linux. Unfortunately it would appear the onboard RAM is deleted when power is removed from the keyboard. The only way I can see these keys working is by finding a way to load the .conf files (they are just simple text files) into the keyboard RAM from within Linux.

I have included my Key Touch profile below for anyone who may want to try it out, and may be able to get the ZOOM keys working.

I am interested in hearing from anyone else who has this keyboard, and the success they may have had, so hopefully, we can eventually have this keyboard fully working with Linux.

Thanks.

Here is the Key Touch profile. It is simply an XML file. Just copy and paste the code into your favourite text editor and save the file as **Pro_Type_(USB).Razer**. Then open Key Touch and import the profile.

```
<keyboard>
  <file-info>
    <syntax-version>1.1</syntax-version>
    <last-change format="%d-%m-%Y">25-12-2007</last-change>
    <author>Denham2010</author>
  </file-info>
  <keyboard-info>
    <keyboard-name>
      <manufacturer>Razer</manufacturer>
      <model>Pro Type (USB)</model>
    </keyboard-name>
  </keyboard-info>
  <key-list>
    <key>
      <name>Mute</name>
      <scancode>0</scancode>
      <keycode>MUTE</keycode>
      <default-action action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Mute</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Volume Down</name>
      <scancode>0</scancode>
      <keycode>VOLUMEDOWN</keycode>
      <default-action action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Volume decrease</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Volume Up</name>
      <scancode>0</scancode>
      <keycode>VOLUMEUP</keycode>
      <default-action action-type="plugin">
        <plugin-name>Amixer</plugin-name>
        <plugin-function>Volume increase</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Next song</name>
      <scancode>0</scancode>
      <keycode>NEXTSONG</keycode>
      <default-action action-type="plugin">
        <plugin-name>XMMS</plugin-name>
        <plugin-function>Next</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Previous song</name>
      <scancode>0</scancode>
      <keycode>PREVIOUSSONG</keycode>
      <default-action action-type="plugin">
        <plugin-name>XMMS</plugin-name>
        <plugin-function>Previous</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Stop CD</name>
      <scancode>0</scancode>
      <keycode>STOPCD</keycode>
      <default-action action-type="plugin">
        <plugin-name>XMMS</plugin-name>
        <plugin-function>Stop</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Play/Pause</name>
      <scancode>0</scancode>
      <keycode>PLAYPAUSE</keycode>
      <default-action action-type="plugin">
        <plugin-name>XMMS</plugin-name>
        <plugin-function>Play/Pause</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Config</name>
      <scancode>0</scancode>
      <keycode>CONFIG</keycode>
      <default-action>kcontrol || gnome-control-center</default-action>
    </key>
    <key>
      <name>Homepage</name>
      <scancode>0</scancode>
      <keycode>HOMEPAGE</keycode>
      <default-action action-type="plugin">
        <plugin-name>WWW Browser</plugin-name>
        <plugin-function>Home</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Sleep</name>
      <scancode>0</scancode>
      <keycode>SLEEP</keycode>
      <default-action action-type="plugin">
        <plugin-name>Lock Screen</plugin-name>
        <plugin-function>Lock Screen</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Zoom +</name>
      <scancode>0</scancode>
      <keycode>SCROLLUP</keycode>
      <default-action action-type="plugin">
        <plugin-name>Zoom</plugin-name>
        <plugin-function>In</plugin-function>
      </default-action>
    </key>
    <key>
      <name>Zoom -</name>
      <scancode>0</scancode>
      <keycode>SCROLLDOWN</keycode>
      <default-action action-type="plugin">
        <plugin-name>Zoom</plugin-name>
        <plugin-function>Out</plugin-function>
      </default-action>
    </key>
  </key-list>
</keyboard>
```

---

