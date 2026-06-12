---
title: "Slimblade Trackball mouse configuration problem"
date: 2009-11-13
forum: Hardware
---

### Post by mfearby on 2009-11-13
I recently bought a Kensington Slimblade Trackball mouse and would like to configure the rear buttons to act as back/forward. Reading [this]("http://www.theinquirer.net/inquirer/review/1557167/kensington-slimblade") review's comment by "Spike" I get the impression that it just worked, thanks to a new kernel. 

So, I upgraded from Jaunty to Karmic the other day. Xev does actually now show stuff when I click the rear buttons, but they don't exactly do as I would have hoped. The right-rear button actually sends the "back" command to Firefox and the left-rear button closes the current tab if it is simply clicked on the current tab title (not the little "x"; quite bizarre).

I haven't had any luck with the various mice configuration howto articles out there, but I can see that my system thinks I have two mice: a Kensington and one which is a Macintosh-emulated mouse. Don't know where it gets that idea. Here's the mouse-related output from "cat /proc/bus/input/devices":

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=047d Product=2041 Version=0110
N: Name="Kensington Kensington Slimblade Trackball"
P: Phys=usb-0000:00:1a.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=17
B: KEY=f0000 0 0 0 0
B: REL=103

It looks to me like Linux is actually detecting this mouse as two mice. Does anybody know how to get Linux to recognise this as just the Kensington Slimblade Trackball AND to get the rear buttons configured as back/forward?

Thanks.

---

### Post by mfearby on 2009-11-14
OK, according to xev the four buttons are as follows:

south-west: button 1 (left-click)
south-east: button 3 (right-click)
north-west: button 2 (closes firefox tab for some reason)
north-east: button 8 (back)

Checking the default button assignment shows the following:

xinput get-button-map "Kensington Kensington Slimblade Trackball"
1 2 3 4 5 6 7 8 9 10 11 12

After a quite few attempts, I managed to get my north-west button to be "back" and my north-east to be "forward" by running the following command

xinput set-button-map "Kensington Kensington Slimblade Trackball" 1 8 3 4 5 6 7 9 2 10 11 12

I'm not sure I truly understand how this works because I can't find any docs on the number ordering, but all I know is that the rear buttons now behave as back and forward properly. Next step will be to add this to my GNOME session startup or something so that it stays that way. Why this isn't the default I will never know. Hopefully this might save somebody some time if they find this posting one day.

Maybe it works because the 2nd button is now sending an 8 and the button that was formerly in the 8th spot is now sending a 9. In any case, xev is now registering an 8 for the north-west and a 9 for the north-east button, so I guess that's it then. Would be nice to see some docs that actually spell this out rather than leaving it to the imagination.

---

