---
title: "PlayStation controllers not working in Feisty"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by &#12465;&#12452;&#12488; on 2007-05-05
After upgrading to 7.04 yesterday, my girlfriend got problems using her PlayStation dance pad with Ubuntu. It's connected with a cheap adapter I bought at eBay, [StepMania's wiki](http://www.stepmania.com/wiki/USB_Adapters) says it's called a Dilong pu203 adapter, but it'd been working like a charm straigth out of the box in 6.10.

The pad was too sensitive, and buttons didn't work like they had been mapped to function. I checked what dmesg had to say after plugging in the dance pad, and it had recognised the pad as an Xbox controller! No wonder it wasn't working the way it was supposed to.

I'm running Debian lenny/sid on my computer, and it's working perfectly here. dmesg says the following after plugging in the pad:

input: Twin USB Joystick as /class/input/input8
input: USB HID v1.10 Joystick [Twin USB Joystick] on usb-0000:00:1d.1-1

This is what Ubuntu was recognising it as earlier, a "Twin USB Joystick". How can I make Ubuntu load the right module/driver?

She's threatning me to break up if I don't fix this ASAP, so please help me!

---

### Post by Fizile on 2007-05-07
Fiesty 7.04, updated

I am having a problem with my playstation controller and feisty, but it does not involve DDR.

I am using a non-dualshock psx controller in collaboration with a "Super Box4" psx to usb adapter.  The controller is readily recognized and all buttons *work*.  However the manner in which they work is odd.

After installing a Joystick Calibration tool from synaptic package manager I go to calibrate my controller.  When pressing any of the buttons on the controller, the calibration tool recognizes that the button was pressed.  While a button (or a direction on the dpad) is held down the calibration tool shows that the button is being pressed repeatedly (and rapidly).

This results in very choppy and annoying movement and function with the joystick. (zsnes)

Anyone have normal function with their psx to usb adapters, or know of a fix/definate unresolved issue for me?

---

### Post by mmxbass on 2007-05-11
> **Fizile said:**
>  When pressing any of the buttons on the controller, the calibration tool recognizes that the button was pressed.  While a button (or a direction on the dpad) is held down the calibration tool shows that the button is being pressed repeatedly (and rapidly).I have the exact same problem with a controller that IS dualshock. Not only does mine register a button being held down ad super-rapid repeated presses. The 2 analog joysticks keep alternating between their actual values and the maximum possible value (also super rapidly).

---

### Post by Fizile on 2007-05-11
although my psx controller has no analog sticks, the jscalibrator shows.. as stated above.. the axis going to its max repeatedly and rapidly.

Anyone got a fix? seems like this issue is common.

---

### Post by mmxbass on 2007-05-11
Also. I forgot to mention. My converter is the EMS model that converts 2 playstation gamepads to a single USB connection. It only shows up as ONE joystick in /dev/input/ but I only have one gamepad so that has never been a problem.

This didn't used to happen in Edgy.

---

### Post by mmxbass on 2007-05-11
I fixed it.........

Try plugging another controller into the 'empty' one of the 2 controller ports, even if you only plan to just use one of gamepad. Something actually being plugged into the 2nd port seems to make it operate correctly. The controller in the 2nd port happens to be non-functional so I don't know how or why this happens though I can bet dollars to donuts that it has something to do with the fact that the device only registers as ONE joystick when it is in fact a converter for TWO gamepads.

---

### Post by mmxbass on 2007-05-11
EEK! Perhaps I spoke too soon. The input now seems to be a COMBINATION of the broken gamepad and the one I actually want to use! Yikes! Some driver-writer screwed up big time!

---

### Post by yibble on 2007-06-06
Hi,

  I hope you're still monitoring this thread. I had the same issue with the EMS USB II under Feisty. Worked perfectly fine in Edgy. I've done some digging, and have now resolved the issue. I've detailed the steps I followed in a blog post, so sorry for blog-spam: [http://blog.yibble.org/2007/06/06/feisty-usb-joystick-issue-resolved/](http://blog.yibble.org/2007/06/06/feisty-usb-joystick-issue-resolved/)

  I hope that helps.

---

### Post by mmxbass on 2007-06-06
These hackish solutions wouldn't be necessary if Ubuntu moved to the latest 2.6.21 kernel which is known to have the issue permanently resolved.

---

### Post by rossperk on 2007-09-22
> **hexnet said:**
> These hackish solutions wouldn't be necessary if Ubuntu moved to the latest 2.6.21 kernel which is known to have the issue permanently resolved.

Can we upgrade to that kernel version ourselves? How difficult is it (and would it kill my binary video drivers that I just got working, which is required for StepMania)? Or would the hackish solution be easier in the long run?

---

### Post by SZF2001 on 2007-09-26
^Try this:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

