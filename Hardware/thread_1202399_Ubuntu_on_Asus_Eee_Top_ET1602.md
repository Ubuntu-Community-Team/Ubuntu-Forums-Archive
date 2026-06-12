---
title: "Ubuntu on Asus Eee Top ET1602?"
date: 2009-07-02
forum: Hardware
---

### Post by ben72 on 2009-07-02
What works and what not on Asus Eee Top ET1602 using Ubuntu?

Which version of Ubuntu works best? Desktop or Netbook remix?

I'm specially interested to know if the the touch screen works or what can be done to make it work.

I'm thinking of buying one but I need to know if it works reasonably good first..


Thanks for any hints!

Ben

---

### Post by kat_ams on 2009-08-10
Ubuntu Netbook Remixed works fine on the ASUS EeeTop ET1602, installing is not out of the box though. It takes some special configuration.

Everything works, Touchscreen, Keyboard, Mouse, Sound, Video once configured.

You need the file attached to this post in order to get the Display and Touchscreen to work I don't know how to cross post so I attached them here as well. Search for my post SOLVED! ASUS EeeTop ET1602 for the full installation instructions.
The 1st file is xorg.conf which needs to be placed in /etc/X11/xorg.conf
the 2nd file is 69.touchscreen.rules which needs to be placed in /etc/udev/rules.d/69-touchscreen.rules
Again see my other post for full installation instructions.

Also it is advisable to upgrade the internal RAM to 2GB. I will post a separate post to describe how.

---

### Post by kat_ams on 2009-08-10
Here is how to Upgrade the RAM on an ASUS EeeTop 1602 to 2GB to make Ubuntu go faster.

[LIST]
[*]Buy a 2GB DDR2 SO-DIMM (667mhz or faster)
[*]Unplug your EeeTop and Remove all connected cables (mouse, keyboard, speakers, network, usb...)
[*]put down a soft towel on the table
[*]lay the EeeTop on it's front side down on the soft towel
[*]carefully remove the rubber stoppers from each of the four corners of the back of the screen
[*]carefully remove the four rubber stoppers in the middle of the screen (one is above the middle of the metal stand 3 are below it)
[*]Remove the four screws from each of the corners
[*]remove the four screws from the middle of the screen
[*]lift the EeeTop with the clear acrylic base upwards so you can see the underside of the middle of the metal stand
[*]remove only the 4 bigger screws in the middle of the stand
[*]the stand will come loose and you have a metal piece sticking out the back
[*]put the EeeTop display down on the soft towel
[*]gently press downwards with your palm on the metal base piece of stand that sticks up while gently lifting one of the corners of the backplate
[*]Gently press downwards on the metal piece while lifting each corner until the backing comes off
[*]near the middle right hand side you see the SO-DIMM
[*]gently push the tiny metal latches to each side at the same time using your thumbs
[*]the SO-DIMM will pop up at an angle
[*]remove it by holding it by its sides
[*]insert your new SO-DIMM at the same angle the old one came out
[*]press it down gently until it locks in place
[*]place the backplate back on the EeeTop making sure you start with the side that has the USB ports sticking out the side
[*]click the backplate on
[*]before closing everything test to make sure your memory upgrade worked
[*]Plug in the Power, Keyboard and Mouse
[*]Start your EeeTop with the power button and tap the F2 key until the BIOS screen comes up
[*]On the first screen of the BIOS you see how much memory is installed. It should say 2048 MB (==2GB)
[*]If this does move exit without saving and let Ubuntu boot fully.
[*]Then go to the ubuntu menu Admin... System Monitor... the tab "system"
[*]this should say Memory 2GB
[*]when everything is satisfactory you can remove the power, mouse and  keyboard cables and put everything back together again.
[*]place the metal stand with the long foot facing down towards the clear acrylic foot
[*]screw the 4 screws to the foot (these are slightly longer screws than the ones that go in the backplate)
[*]screw the 4 middle screws and the 4 screws on each corner back in
[*]place the rubber stoppers back in the 8 holes
[*]enjoy your new faster EeeTop ET1602
[/LIST]

Word of caution, not all memory modules work with the EeeTop.
I am using an A-Data 800mhz DDR2 SO-DIMM which works perfectly
Kingston has a memory module in their memory configurator that they recommend. Pick what works for you and fits your budget.

---

### Post by ben72 on 2009-08-11
Thanks a lot for the information!

I also got an answer on launchpad/questions that works for Ubuntu 9.04.

[https://answers.launchpad.net/ubuntu/+question/76895](https://answers.launchpad.net/ubuntu/+question/76895)

I'm now running Ubuntu 9.04 on my Asus Eee Top. Do you think there's a good reason to change to UNR?

---

### Post by guywithcable on 2010-07-06
Here's a method to get the touchscreen working in 10.04 Lucid:

[http://ubuntuforums.org/showthread.php?p=9554927](http://ubuntuforums.org/showthread.php?p=9554927)

---

