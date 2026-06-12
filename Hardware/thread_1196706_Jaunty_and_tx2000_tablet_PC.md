---
title: "Jaunty and tx2000 tablet PC"
date: 2009-06-25
forum: Hardware
---

### Post by trx64 on 2009-06-25
I have a HP tx2115nr tablet PC, wich works perfectly in Jaunty, except by the touch and stylus. I've searched in the forum, but I'm a bit confused :confused:: what is the way to activate my tablet in 9.04?

---

### Post by Favux on 2009-06-25
Hi trx64,

Welcome to Jaunty!

Gali98 has a HOW TO for you.  It will get your TX2000 set up in Jaunty.  Follow this link to Jaunty Users (near the top) and read it:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  You will want to follow the link in 1) to gali98's HOW TO.

Good luck!

---

### Post by trx64 on 2009-06-25
Thanks for the answer, Gali's tutorial really worked. I've readed your tutorial about screen rotate, working too.

The only problem is that only the touch is recognized, not the stylus (it works, but like the touch, without pressure ou right-click). Any idea?

PS.: well, it's a really nice tutorial. I'm from Brazil and I'm thinking about translate your tutorial and Gali's one to Portuguese and post it in the forum (in Brazil). Of course, with credits to you and Gali98. I think it can help a lot of people now, because HP tablets are not so expensive now and there is a lot of that in the stores around here.

---

### Post by Favux on 2009-06-25
Hi trx64,

I think translating the HOW TO's into Portuguese would be great.  I'm sure gali98 wouldn't mind.

I'm going to guess that the stylus is working only you haven't used wacomcpl to calibrate and configure your tablet.  See Section 3 in the HOW TO on the first page first post of the thread with gali98's HOW TO.  If that isn't it let me know.

---

### Post by trx64 on 2009-06-25
Thanks for the answer. The only device in wacomcpl is the touch. There isn't any option for stylus.

---

### Post by Favux on 2009-06-25
Hi trx64,

OK, something is weird.

Let's look at:
```
xsetwacom list
```
and
```
xinput --list
```
I'm hoping it is a problem with how you installed the .fdi.  Can you verify your stylus works in Windows?

---

### Post by trx64 on 2009-06-25
Just touch... I just overwrited my original fdi with Gali's one, what enabled the touch. I think that I will have to add some options to it (end of post). 

Yes, the stylus works in Windows.

All right, exit of *xsetwacom list*:

touch            touch     


Result of *xinput --list*:

"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"touch"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 186
        Max_value is 3947
        Resolution is 397
    Axis 1 :
        Min_value is 185
        Max_value is 3909
        Resolution is 633
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1



My fdi:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
    <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
              <append key="wacom.types" type="strlist">eraser</append>
        <merge key="input.x11_options.BottomY" type="string">16466</merge>
        <merge key="input.x11_options.BottomX" type="string">26271</merge>
        <merge key="input.x11_options.TopY" type="string">183</merge>
        <merge key="input.x11_options.TopX" type="string">397</merge>
    </match>
    </match>
  </device>
  <device>
    <match key="input.originating_device" contains="if1">
    <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">touch</merge>
        <merge key="info.product" type="string">touch</merge>
        <merge key="input.x11_options.BottomY" type="string">3909</merge>
        <merge key="input.x11_options.BottomX" type="string">3947</merge>
        <merge key="input.x11_options.TopY" type="string">185</merge>
        <merge key="input.x11_options.TopX" type="string">186</merge>
    </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
</deviceinfo>

---

### Post by Favux on 2009-06-25
Hi trx64,

Well touch shouldn't be there twice in "xsetwacom list".  No stylus in "xinput --list".  The .fdi looks right.  Did you put in a custom_wacom.fdi in "/etc/hal/fdi/policy/"?  Or do you have any wacom entries in the xorg.conf?

---

### Post by trx64 on 2009-06-25
> **Favux said:**
> Hi trx64,

Well touch shouldn't be there twice in "xsetwacom list".  No stylus in "xinput --list".  The .fdi looks right.  Did you put in a custom_wacom.fdi in "/etc/hal/fdi/policy/"?  Or do you have any wacom entries in the xorg.conf?

No, the only fdi is that. xorg.conf doesn't have any wacom entry, just Nvidia's default + xrandr to rotate screen.

---

### Post by Favux on 2009-06-25
Hi trx64,

Did you compile the 0.8.3.x wacom.ko and copy it into place?  No problems with doing that?

Rather than looking at your lshal output with:
```
lshal>trx64_lshal.txt
```
just now try:
```
lshal | grep 56a_93_noserial_if0
```

---

### Post by trx64 on 2009-06-25
I didn't compiled a new wacom driver, I've used Jaunty's one. It's necessary to compile the driver to get the stylus?

Ok:

udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_93_noserial_if0'  (string)

---

### Post by Favux on 2009-06-25
Hi trx64,

OK, the 'if0' headers seem to be from the stylus sections of your lshal, so it is there.

No not all the linuxwacom drivers.  You keep the Jaunty 0.8.2-2 linuwacom drivers except the wacom.ko.  It's the usb kernel module.  So that is probably the problem.  That's why it's in gali98's HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Where you got the new TX2000 10-wacom.fdi.

---

### Post by trx64 on 2009-06-25
Ok, I understand, it's just to compile and get that individual module. I'll follow that part and post the results. Thanks.

EDIT:

I got this error in make (I've installed the dev packages in the tutorial):

    Building linuxwacom drivers for 2.6 kernel. ***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built make -C /lib/modules/2.6.28-13-generic/build M=/home/leotorok/Área de Trabalho/linuxwacom-0.8.3-4/src/2.6.28 make[3]: Entrando no diretório `/usr/src/linux-headers-2.6.28-13-generic' make[3]: *** Sem regra para processar o alvo `de'.  Pare. make[3]: Saindo do diretório `/usr/src/linux-headers-2.6.28-13-generic' make[2]: ** [all] Erro 2 make[2]: Saindo do diretório `/home/leotorok/Área de Trabalho/linuxwacom-0.8.3-4/src/2.6.28' make[1]: ** [all-recursive] Erro 1 make[1]: Saindo do diretório `/home/leotorok/Área de Trabalho/linuxwacom-0.8.3-4/src' make: ** [all-recursive] Erro 1

---

### Post by Favux on 2009-06-25
Hi trx64,

New error to me.  Did the wacom.ko "make"?

If not start over being sure to do every step.  And copy and paste the entire line.

---

### Post by trx64 on 2009-06-25
> **Favux said:**
> Hi trx64,

New error to me.  Did the wacom.ko "make"?

If not start over being sure to do every step.  And copy and paste the entire line.

No, wacom.ko didn't "make". Tryed again, line by line, same problem. 

Another thing: does the default fdi that I used is OK?

---

### Post by Favux on 2009-06-25
Hi trx64,

The .fdi looked OK to me.  If it's the same one as in gali98's post #104 then it is the right one.

You are the second person with a problem compiling with the new Jaunty kernel 2.6.28-13.  I am starting to wonder if it isn't a problem with the new kernel.

---

### Post by trx64 on 2009-06-25
No problem, it's fine like this. Rotating desktop cube with the fingers it's pretty cool. The fact that I will have to recompile the driver after kernel updates is not atractive... I prefer to wait for Karmic.

I've used Hardy, intrepid an Jaunty, the best! Simply great. But i think that Karmic will be even better (100 bugs campaign is incredible).

Thanks for the help, now I finnaly hava touchscreen working (the stylus stays for Karmic).

I could try it again after another kernel update, and post the results.

---

### Post by Favux on 2009-06-25
Hi trx64,

I asked gali98 to take a look and see if he can help us.

You could try using the kernel before the current one.

Or you could start over with the current kernel by following post #270 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=27](http://ubuntuforums.org/showthread.php?t=1038949&page=27)

---

### Post by trx64 on 2009-06-26
I'll take a look at that. Anyway, touch is good for me (no right-click on stylus, but is ok), Karmic will solve this, with the new wacom driver.

Well, you used the tablet for a time. I'm using Xournal and Onboard. Do you know any other program to tablet users?

Thanks for the help, I was waiting for the touchscreen since Hardy. :P

---

### Post by Favux on 2009-06-27
Hi trx64,

I think you'll find CellWriter is superior to Onboard, because it has character recognition.  Give it a try.

---

### Post by trx64 on 2009-06-27
Thanks! It's really better. I've used a similar software on Vista, but it was simply horrible. This one is great very funcional. Thanks for everithing!

---

### Post by gali98 on 2009-06-27
Okay, I successfully compiled 0.8.3-5, and everything works. So what I need you to do is redownload 0.8.3-5 and extract it to your desktop then open a brand new terminal, and run each of the following commands:

```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev wacom-tools xserver-xorg-input-wacom

sudo apt-get upgrade

***Now cd into the linuxwacom directory**

./configure --enable-wacom 

make
```

And then I need you to post the ENTIRE output. Do not leave anything out.
Since it will be quite large, I suggest putting it in a text file and uploading it.
Kory

---

