---
title: "HowTo: Acer Aspire 6935 Cinedash and Hotkeys"
date: 2009-03-02
forum: Hardware
---

### Post by K. Hendrik on 2009-03-02
Inspired by [FokkerCharlie's Acer 5920(G) Thread]("http://ubuntuforums.org/showthread.php?t=997860") i tried to get the Cinedash and all Hotkeys to work. Here is the result.



[SIZE="4"]New Keymap File[/SIZE]
First I replaced the standart Acer Keymap File
/usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi
so it now looks like this:
```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <!-- These are raw scancodes produced by the atkbd driver -->
    <match key="@input.originating_device:info.linux.driver" string="atkbd">

      <!-- Acer -->
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Acer">
        <!-- Aspire Series -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" prefix="Aspire">
          <!-- Model 6935 -->
          <match key ="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="6935">
            <!-- CineDash (on the left) -->
            <append key="input.keymap.data" type="strlist">e012:media</append>          <!-- Kid icon, Acer Arcade -->
            <append key="input.keymap.data" type="strlist">e01e:prog1</append>          <!-- Back-Arrow icon (beneath Kid icon) -->
            <append key="input.keymap.data" type="strlist">e003:back</append>           <!-- back -->
            <append key="input.keymap.data" type="strlist">e009:forward</append>        <!-- forward -->

            <!-- Media Keys (on the right) -->
            <append key="input.keymap.data" type="strlist">e074:prog2</append>          <!-- "e icon" key, Acer Empowering Technology -->
            <append key="input.keymap.data" type="strlist">e032:www</append>            <!-- WWW button -->
            <append key="input.keymap.data" type="strlist">e06c:mail</append>           <!-- Mail button -->

            <!-- Fn Key Combinations -->
            <append key="input.keymap.data" type="strlist">e026:setup</append>          <!-- Fn+F2 Acer eSettings for Acer Empowering Technology -->
            <append key="input.keymap.data" type="strlist">e027:battery</append>        <!-- Fn+F3 Acer ePowerManagement for Acer Empowering Technology -->
            <append key="input.keymap.data" type="strlist">e04e:brightnessup</append>   <!-- Brightness up -->
            <append key="input.keymap.data" type="strlist">e06f:brightnessdown</append> <!-- Brightness down -->

            <!-- Euro and Dollar Key -->
            <append key="input.keymap.data" type="strlist">e033:prog3</append>          <!-- Euro symbol -->
            <append key="input.keymap.data" type="strlist">e034:prog4</append>          <!-- Dollar symbol -->

            <append key="info.capabilities" type="strlist">input.keymap</append>
          </match>
        </match>
      </match>

    </match>
  </device>
</deviceinfo>

```
(this file will only work for Acer Aspire 6935)
after rebooting there are still some configurations that need to be made.



[SIZE="4"]Assigning the programmable keys[/SIZE]
After changing the keymap the programmable keys ("Back-Arrow icon", "e icon") need to be assigned. You can do so with xbindkeys, my ".xbinkeysrc" looks like this:
```

# start TV-Browser 	(prog1) (Back-Arrow icon [beneath Kid icon])
"tvbrowser"
	c:156

# start Synaptic	(prog2) (e icon)
"gksu /usr/sbin/synaptic"
	c:157

```
Also the combinations Fn+F1 and Fn+F2 don't have any effect by now, you can change that in "system->preferences->hotkeys" I assigned Fn+F1 to the helpbrowser and Fn+F2 to my homefolder.


[SIZE="4"]Fixing the Euro and Dollar key[/SIZE]
Like in FokkerCharlie's Thread mentioned the Euro and Dollar key couldn't be assigned directly so I asigned them to "prog3" and "prog4"
then i generated a File as FokkerCharlie described with:
```

mkdir .startscripts
cd .startscripts
gedit eurodollar.sh

```
the script itself looks slightly different because i used the "prog3" and "prog4" for assigning the keys in the keymap.
```

#!/bin/sh
echo 'keycode 210 = EuroSign EuroSign EuroSign EuroSign EuroSign' | xmodmap -
echo 'keycode 211 = dollar dollar dollar dollar dollar' | xmodmap -

```
now reboot and every key should work.



[SIZE="4"]What still doesn't work[/SIZE]
Until now I havent figured out how to activate the lights for mute and the volume. So the mute light might be switched on when the laptop is not muted and the volume-scale-display will be incorrect.



Ok that's it i hope it's usefull and thank's too FokkerCharlie and his nice Thread.

---

### Post by the_davenull on 2009-04-05
Hello, I have a question. I have the same laptop, and I cannot get <ctrl>+<enter> to work. I used the fdi file you posted, but I don't know where to start at on getting this to work. Any help would be appreciated.

---

### Post by K. Hendrik on 2009-04-17
Hi, what exactly is the combination supposed to do I never used that before.

Edit: Ok looked it up, firefox address completion with <ctrl> + <enter> works for me

---

### Post by ZeroXtreme on 2009-07-05
Hi, I tried using your customized keymap file, nothing changed. I also tried setting the keyboard layout to "Acer Laptop" under system preferences, but still no luck.

I have the Acer Aspire 4937G, while it does not have the CineDash like yours, it does have Acer MediaTouch, which is fairly similar in terms of touch sensitive keys and all the same functions as your CineDash, however i suspect the hardware mappings are different.

So the following keys dont work now:
1. Web Browser Button (hard key)
2. e-Mail Button (hard key)
3. Empowering Technology Button (hard key)
4. Volume Slider (touch sensitive control)
5. Acer Arcade Deluxe / Windows Media Center Button (touch sensitive key)

The play/pause, stop, next and previous buttons work and so does the mute button, but as you mentioned the mute light does not go on or off.

I'm sort of wondering how you got to map the key addresses of all the buttons since i tried xev and pressing the buttons that dont work do not produce any output in the xev screen. Interesting that the media controls like play/pause work but also do not produce any output in the xev screen.

Any help would be greatly appreciated.

---

### Post by K. Hendrik on 2009-07-05
Hi,
my keymap file needs to be modified to be usable on your system the lines:
```

           <!-- Acer -->
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Acer">
        <!-- Aspire Series -->
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" prefix="Aspire">
          <!-- Model 6935 -->
          <match key ="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="6935">

```
only allow the ussage of the configuration for an Acer Aspire 6935 i did that because i don't know if it will work on any other system, to test it on your system you need to change the Model part to suit your Acer Aspire 4937G.

---

### Post by iasenko on 2009-10-20
I have the same Cinedash problem with my 6035G . Here is what I found but I'm not so advanced Linux user to make it work:
"The cinedash can be configured to behave appropriately by mapping the keycodes (checked using xev) to specific functions, including the touch sensitive volume meter that can be mapped to a sliding volume control."

If anybody can help, it will be great :)

---

