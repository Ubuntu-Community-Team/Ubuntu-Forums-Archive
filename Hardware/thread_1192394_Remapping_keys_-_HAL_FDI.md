---
title: "Remapping keys - HAL FDI?"
date: 2009-06-20
forum: Hardware
---

### Post by Edward C on 2009-06-20
I use a couple of keyboards with one PC. I'd like to remap the generic forward and back keys on one keyboard (but not the other), to behave as multimedia skip forward and back keys. I've tried creating a /etc/hal/fdi/policy/10-x11-input.fdi file, but so far can't get it to work. Here's the file:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="@input.originating_device:usb.vendor_id" int="0x045e">
      <match key="@input.originating_device:usb.product_id" int="0x00f9">
        <append key="input.keymap.data" type="strlist">e069:fastforward</append>
        <append key="input.keymap.data" type="strlist">e06a:rewind</append>
      </match>
    </match>
  </device>
</deviceinfo>
```

I'm wondering if it's even possible to redefine mappings that already exist (as opposed to creating mappings for unknown keys) in this manner. Also, it's possible that there could be a problem because the USB device (045e:00f9) is the same for both my keyboard and mouse (it's a wireless desktop combo). I've been able to configure the mouse using this file (though I've removed those options for clarity), but perhaps it doesn't work for the keyboard. Is there another way of matching a specific keyboard device?

Thanks,
Ed.

---

### Post by Edward C on 2009-06-22
Can anyone suggest a better forum for this issue?

---

### Post by mattshow on 2009-07-07
I have been having trouble trying to accomplish the exact same thing. I have a USB remote control that gets picked up as a keyboard. I'd like to change what some of the buttons do, but I've had no luck remapping them this way.

---

### Post by martinbaselier on 2009-08-03
I've been struggling a bit with this myself today. 

You can use xmodmap to remap keys:

xmodmap -e "keycode 163=a"

will assign the letter "a" to the key with keycode 163 (in my case that's my mailbutton)

to get keycodes (and see which key/event is attached to it) : 
xev | grep keycode



this is my hal fdi config which partly works:
```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>

    <!-- These are raw scancodes produced by the atkbd driver -->
    <match key="info.product" contains="key">

        <append key="input.keymap.data" type="strlist">136:a</append> <!-- Fn+F1 Hotkey help -->
        <!-- append key="info.capabilities" type="strlist">input.keymap</append -->

    </match>
  </device>
</deviceinfo>

```
lshal | grep keymap
shows the key is added. 

xev doesn't show any change though. 

if you create a file ~/.Xmodemap you can make the changes permanent.
haven't tried this last part, since I got the stuff I wanted to do working in a different way.

---

