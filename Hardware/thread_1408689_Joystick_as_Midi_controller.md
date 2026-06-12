---
title: "Joystick as Midi controller"
date: 2010-02-16
forum: Hardware
---

### Post by AxelMan0 on 2010-02-16
I have a Saitek X45 flight controller and I have been doing a lot of messing around with softsynths. The controller has several wheels and buttons that would make it a very nice makeshift midi controller since I don't actually own any real hardware of the sort. Is there a way to make a udev rule that will trick ubuntu into thinking it is a midi device, or at the very least let me hook it up as a midi controller through qjackctl?

---

### Post by Borbor on 2010-02-16
Awesome idea, I wanna see if that works, wish I could help

---

### Post by AxelMan0 on 2010-02-16
I've looked into PureData, but I have no idea how that program works. The manpages and --help were no help at all. I read something about telling PureData to use it as a [hid] but it seems like I should be able to do it straight from Ubuntu...

---

### Post by AxelMan0 on 2010-02-18
bump?

---

### Post by brandjamie on 2010-03-12
Ok,  I think I've got this figured now. 
You need to install pd-extended to use the 'hid' object. 

It's not available in the Karmic repositories so follow these instructions here:

[http://kijjaz.exteen.com/20091005/installing-pd-extended-on-ubuntu-9-10-beta](http://kijjaz.exteen.com/20091005/installing-pd-extended-on-ubuntu-9-10-beta)

once that's done you can follow the instructions here to set up your controllers.

[http://en.flossmanuals.net/PureData/GameControllers](http://en.flossmanuals.net/PureData/GameControllers)

the above shows how to get the data from the controller. you'll need to adjust the range of the output. for instance my joypad has a range of 0-255 so I divided the controller output by 255 and multiplied it by 127. 

then you create a 'ctlout' object and assign a midi cc number to it. 

you should then be able to use patchage to send the controller data to whatever you want to control. 

i don't think i've explained this well so i've attached a pd file mapping the x-axis of my joystick to controller 68 (Which just happens to be the 'drive' parameter on Rakkarack!).
It will only work in pd-extended. 

Switch from Edit mode (in the edit menu). 

Click the bang (the circle in a box) on the right of the patch. That will send a list of your controllers to the pd-extended main window. 

My joystick is device no 10. Find the device number for your joystick in the main window and change the 'open 10' to 'open /yournumber/' (you'll need to temporarily switch back to edit mode to do this). 

click the toggle (looks like the 'bang' on the left hand side) so it is on and you should be able to see a range of numbers in the the number boxes.

the maximum number you see in the number box under 'route abs_x' is your range. change '/ 255' to '/ /range/'.
 
to use pd to send midi out you may need to select ALSA midi, from the 'media' menu of pd. that will give you a midi out you can connect with patchage.

hope this helps:)

---

### Post by maghoxfr on 2010-05-28
have anyone tried this? I'm thinking on building a foot midi controller from an old usb joystick for rakarrak or similars and even though I've only soldered remotes and guitar cables I'm going to give it a try. 

I'd like to know if this method to convert joystick to midi works.

---

### Post by AxelMan0 on 2010-11-22
oops double posted

---

### Post by AxelMan0 on 2010-11-22
I just recently checked this again it's been awhile, thanks for your help! I too investigated puredata and [hid] and, it works wonderfully. I use the throttle to control a lpf, buttons for octave switches, rX and rY for other things...the possibilities are endless.

I also set up a foot controller to use with Rakarrack, it's great to use my DDR pad as a stompbox :D.

A tip for those who want to do this though, I have a problem with certain buttons sending all their messages twice, which can screw up your otherwise well-working patch. I have put my stompbox patch in the attachments, and you can open that to see a simple fix to this problem.

You will need the 'joyconfig' patch (also attached) for the stompbox patch to work. I use the joyconfig patch for all patches involving creative controllers, so you may find it very useful. It routes axis, button, and ff messages in that order. The fourth outlet is for anything other kind of message that I may have missed.

(lame, I can't upload .pd files, well I'll put a screenshot up instead. The send objects are sending the signals to the column of bangs on the bottom, which then bang the message which goes to [ctlout])

---

### Post by AxelMan0 on 2010-11-22
.

---

