---
title: "Kinesis foot pedal delayed input"
date: 2009-08-04
forum: Hardware
---

### Post by drbusch on 2009-08-04
I just got a 'Savant Elite USB' 3 button foot pedal to decrease my finger strain with shift, alt, and cmnd keys.  

I programed the device in windows, per instructions, then plugged it into my dell dimension 670 running ubuntu 9.04.  For all the keys, I seem to get a 1 key stroke delay in implimenting the modification, i.e. for the shift key, I get 
tHe
when I type
[shift] t h [off shift] e

Any ideas?  I played around with the keyboard delays in the control panel, without effect.  

lsusb output is below.
root@LRM411-7:~# lsusb -v -s 007:003

Bus 007 Device 003: ID 05f3:030c PI Engineering, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05f3 PI Engineering, Inc.
  idProduct          0x030c 
  bcdDevice            1.00
  iManufacturer           1 Kinesis 
  iProduct                2 Footpedal
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               96mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

---

### Post by exilio3000 on 2009-08-05
Hi Drbusch,

I've been wanting to get foot pedals (or pedal) as well. I was scared off by the products' disclaimers. Although I can't help you with your current hardware, there is at least one documented success story on the web - the author simply "repurposed" an existing keyboard to be a three button switch. Details are at the website. It's a hack but it might work if you can't get your present pedals working, probably wouldn't be too hard to make your own pedal switch. Either way I wish you success.

Here's the link:
[http://www.uchobby.com/index.php/2007/02/26/custom-function-key-box/]("http://www.uchobby.com/index.php/2007/02/26/custom-function-key-box/")

---

### Post by drbusch on 2009-08-05
Thanks- I was hoping for something with better engineering then I can manage by myself in a reasonable amount of time.  I'm writing a thesis at the moment and finding I use the control, alt, and shift keys a bit much.

Something like this hack is the fall back plan.

---

### Post by mrhat2743 on 2009-09-13
Hello Drbusch,

I have a similar setup (Savant Elite USB 3 button foot pedal, Ubuntu 9.04) and I also experience a similar 1 keystroke delay before modifier keys take effect.  Here are my additional comments:

The foot pedal works correctly at the command prompt, so it seems to be something in Gnome or X that is causing the problem.

Here is a capture of part of xev output when I press and hold the "Ctrl" modifier on the foot pedal while then pressing the "a" key:

```

>>> Depress foot pedal 
KeyPress event, serial 100, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 2112978, (616,144), root:(2221,368),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

>>> Depress "a"
MappingNotify event, serial 102, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 102, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

KeyPress event, serial 102, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 2114386, (616,144), root:(2221,368),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

>>> Release "a"
KeyRelease event, serial 104, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 2114578, (616,144), root:(2221,368),
    state 0x4, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (01) ""
    XFilterEvent returns: False

>>> Release footpedal
MappingNotify event, serial 104, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 104, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

KeyRelease event, serial 104, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 2115666, (616,144), root:(2221,368),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```Of note, the depression of "a" is interpreted incorrectly (state = 0, should be 4 i believe), but the release of "a" is interpreted correctly.  My guess is that perhaps the remapping that happens immediately after the depression of "a" occurs too close in time to the handling of the keystroke itself to take effect.  Should this remapping be linked to the depression of the foot pedal rather than the depression of "a"?  After all, the release of the foot pedal triggers the reverse remapping events.

Any help is much appreciated.

Thanks,
Matt

---

### Post by deadguy on 2009-10-02
I have this same problem with my Fragpedal 2, which is similarly configured with control, alt, shift, and windows modifiers on the pedal.  I've used it before with 9.04 and it worked fine.  So I think it's safe to say the problem is not with the device[s].  Interestingly, the windows modifier does not have this problem, only ctrl, alt, and shift.

I'm seeing this problem on a fresh install of 9.04.  I upgraded to 9.10 Alpha 6, and still no luck :(.

Could it be the MappingNotify events?  Only the first "a" is dropped, and only the first "a" generates MappingNotifies.

The windows key could be a special case, since XMonad is eating the "a" event before xev even sees it.  It's still generating the MappingNotifies for the first though.

I'll take it home this weekend and see what it does with my other machines, which I think were working before.

---

### Post by deadguy on 2009-10-02
I tried it in a virtual terminal (Ctrl + Alt + F1), and it worked fine.  So it's definitely not hardware or driver related. 

Then I backedup my .xsession, created a new one:

#! /bin/bash
xterm

and ran "startx -- :1" from the virtual terminal.  Problem was still there.  So looks like a bug in X.

---

### Post by deadguy on 2009-10-04
Confirmed the problem with my laptop and a second usb keyboard, so it looks like a general bug catching modifier keys across input devices.  Behavior is the same whether the modifier key is from the usb keyboard and the modified is from the laptop keyboard or vice versa.

---

### Post by deadguy on 2009-10-04
Filed as a question: [https://answers.launchpad.net/ubuntu/+question/84762](https://answers.launchpad.net/ubuntu/+question/84762)

Please add any info I may have missed.

---

### Post by deadguy on 2009-10-16
Fixed!  Apparently the next release of xinput fixes this problem.  I upgraded xorg using [the xorg-xi2 ppa]("https://launchpad.net/~thjaeger/+archive/xorg-xi2"), and I'm back in business.  One caveat: make sure the ppa includes your video driver before you install (if you ask nicely, the ppa maintainer may be able to add it), and have ppa-purge ready in case you hit trouble.

---

