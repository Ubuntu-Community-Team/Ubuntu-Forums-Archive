---
title: "Older Fujitsu Lifebook w/ Stylus, Would Like To Also Be Able to use Trackpad"
date: 2013-05-11
forum: Hardware
---

### Post by emanpuedam on 2013-05-11
I recently installed Ubuntu 12.04 onto a Fujitsu Lifebook T4220.  I am about to return to college and have just changed my major from Mathematics to Mathematics & Computer Science.

I purchased the Lifepad so that I could have an inexpensive laptop to haul to and from campus to serve as a workhorse for programming assignments.  I selected the Lifebook because its touchscreen that flips and folds (turning the netbook into a bulky tablet) can double as a digital notebook, which drastically reduces the bulk and weight of my day-bag by consolidating all of my notebooks into a single, digital system.  I installed "Xournal" and have been exremely happy with the results.

The touchscreen & stylus are responsive and accurate.  However, when I am using the computer as a laptop instead of a tablet, holding the stylus makes typing with two hands impossible.  The standard trackpad offers the most ergonomic interface.  Unfortunatly, I have been unable to get the trackpad to work.  The left and right buttons function.  However, I cannot move the cursor with the pad.

I have attached a USB mouse which works fine, in tandem with the stylus.  So I don't think the issue is related to multiple pointing devices.  I used the xinput command with the following results:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1166                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled Touchscreen stylus    id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled Touchscreen eraser    id=15    [slave  pointer  (2)]

deactivating the Synaptic device at id=13 deactivates the left and right buttons.  However, nothing I have tried enables the trackpad.

I am beginning to wonder if this is a software issue at all.  Could it be a defective Trackpad?  This computer was a recent eBay purchase and if there is a hardware issue, I would like to bring it to the sellers attention ASAP.

Can any of the guru's out there provide me with some direction as to what the cause of my problem might be.  Is this a software issue or have I been sold a partially busted device.  I _really_ like this computer, so I am hoping that this issue can be corrected.  A functional trackpad would make this the ideal device.

Please let me know what additional information I can provide to shed light on this.  Are there tests that I should perform.  I am fairly new to Linux, but wouldn't consider myself a complete nood (I am working my way through a number of books on Ubuntu and Linux), but detailed instructions would be appreciated.  Thanks.  I have found answers to many other Linux issues on this site from reading responses to other members questions.  If I am lucky enough to get a similar level of support, I have no doubt that I can resolve this quickly.

---

