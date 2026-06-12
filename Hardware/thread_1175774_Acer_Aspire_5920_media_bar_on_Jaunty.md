---
title: "Acer Aspire 5920 media bar on Jaunty"
date: 2009-06-01
forum: Hardware
---

### Post by spinstartshere on 2009-06-01
Is anyone able to point in the direction of any instructions for how to get the media bar on this computer working with Jaunty?  Thanks in advance.

---

### Post by master.of.the.lock on 2009-07-27
I have an Acer 5920G-833G25MI. The instructions below helped me.

To get your Acer Media Keys (panel on the right) working do the following:
1) create the file "/usr/share/hal/fdi/policy/20thirdparty/12-x11-acer-media-keys.fdi" and copy this text into it:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Acer">
            <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" string="Aspire 5920G">
                <match key="info.udi" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port_logicaldev_input">
                    <merge key="info.product" type="string">Acer Media Keys</merge>
                    <merge key="input.product" type="string">Acer Media Keys</merge>
                </match>
            </match>
        </match>
    </match>
  </device>
</deviceinfo>

```
2) install xbindkeys and xvkbd:
sudo apt-get install xbindkeys xvkbd
3) Go to System -> Preferences -> Startup Applications, and add these two entries:
  Name: Acer Media Keys
  Command: xinput set-button-map "Acer Media Keys" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
and
  Name: XBindKeys
  Command: xbindkeys
4) create the file ".xbindkeysrc" in your home directory and put the following text into the file:
```

"xvkbd -text "\[XF86AudioPlay]""
  b:17
"xvkbd -text "\[XF86AudioStop]""
  b:18:
"xvkbd -text "\[XF86AudioPrev]""
  b:19
"xvkbd -text "\[XF86AudioNext]""
  b:20

```
BTW, instead of "xvkbd ..." command you can use any command you want to be executed when you press a media key. For example, if you want your media keys to control only rhythmbox the following code is appropriate:
```

"rhythmbox-client --play-pause"
b:17
"rhythmbox-client --no-start --pause"
b:18
"rhythmbox-client --no-start --previous"
b:19
"rhythmbox-client --no-start --next"
b:20

```
5) restart your session.

To get your euro and dollar keys working follow the instruction:
1) create the file "/usr/share/hal/fdi/information/10freedesktop/31-keymap-acer-euro-dollar.fdi" and copy this text into the file:
```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <!-- These are raw scancodes produced by the atkbd driver -->
    <match key="@input.originating_device:info.linux.driver" string="atkbd">
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Acer">
        <append key="input.keymap.data" type="strlist">e033:f23</append> <!-- Euro symbol -->
        <append key="input.keymap.data" type="strlist">e034:f24</append> <!-- Dollar symbol -->
      </match>
    </match>
  </device>
</deviceinfo>

```
2) open a terminal and type "sudo /etc/init.d/hal restart".
3) type "xbindkeys -mk" in your X11 terminal and press your euro and dollar keys and then q to quit. You will get something like this:
```

Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.

--- Press "q" to stop. ---
"(Scheme function)"
    m:0x0 + c:201
    NoSymbol
"(Scheme function)"
    m:0x0 + c:202
    NoSymbol
"(Scheme function)"
    m:0x0 + c:24
    q

```
Remember keycodes for euro and dollar keys. In the output above they are 201 and 202.
4) create the file ".xmodmaprc" in your home directory and copy the following text into the file:
```

keycode 201 = EuroSign
keycode 202 = dollar

```
Where 201 and 202 should be replaced with keycodes from the step 3.
5) restart your session and in the dialog appeared on the startup load your .xmodmaprc file.

---

