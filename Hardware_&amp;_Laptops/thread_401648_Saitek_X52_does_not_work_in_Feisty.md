---
title: "Saitek X52 does not work in Feisty"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Chris on 2007-04-04
I considered submitting a bug on this and maybe I will but I figured it would be prudent to first see what you guys thought.  I may need to post this on a kernel list or something.

In older releases (eg. Edgy 6.10) the X52 joystick works fine but as of Feisty it has stopped working correctly.  After talking with some other people on the 'Net it seems like this might be a problem with the 2.6.20 kernel but I can't be sure.  The Saitek X52 is (in theory) an USB HID joystick.

I can look at the raw events using the jstest program.  Here is the output in Edgy 6.10 which is using kernel 2.6.17-11-generic:

```

$ jstest --event /dev/input/js0
Driver version is 2.1.0.
Joystick (Saitek Saitek X52 Flight Control System) has 11 axes (X, Y, Z, Rx, Ry, Rz, Throttle, Hat0X, Hat0Y, (null), (null))
and 34 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, BtnX, BtnY, BtnZ, BtnTL, BtnTR, BtnTL2, BtnTR2, BtnSelect, BtnStart, BtnMode, BtnThumbL, BtnThumbR, ?, ?, ?, ?, ?, ?).
Testing ... (interrupt to exit)
Event: type 129, time -58772, number 0, value 0
Event: type 129, time -58768, number 1, value 0
Event: type 129, time -58768, number 2, value 0
Event: type 129, time -58768, number 3, value 0
Event: type 129, time -58768, number 4, value 0
Event: type 129, time -58768, number 5, value 0
Event: type 129, time -58768, number 6, value 0
Event: type 129, time -58768, number 7, value 0
Event: type 129, time -58768, number 8, value 0
Event: type 129, time -58768, number 9, value 0
Event: type 129, time -58768, number 10, value 0
Event: type 129, time -58768, number 11, value 0
Event: type 129, time -58768, number 12, value 0
Event: type 129, time -58768, number 13, value 0
Event: type 129, time -58768, number 14, value 0
Event: type 129, time -58768, number 15, value 0
Event: type 129, time -58768, number 16, value 0
Event: type 129, time -58768, number 17, value 0
Event: type 129, time -58768, number 18, value 0
Event: type 129, time -58768, number 19, value 0
Event: type 129, time -58768, number 20, value 0
Event: type 129, time -58768, number 21, value 0
Event: type 129, time -58768, number 22, value 0
Event: type 129, time -58768, number 23, value 1
Event: type 129, time -58768, number 24, value 0
Event: type 129, time -58768, number 25, value 0
Event: type 129, time -58768, number 26, value 0
Event: type 129, time -58768, number 27, value 0
Event: type 129, time -58768, number 28, value 0
Event: type 129, time -58768, number 29, value 0
Event: type 129, time -58768, number 30, value 0
Event: type 129, time -58768, number 31, value 0
Event: type 129, time -58768, number 32, value 0
Event: type 129, time -58768, number 33, value 0
Event: type 130, time -58768, number 0, value 0
Event: type 130, time -58768, number 1, value 0
Event: type 130, time -58768, number 2, value -1352
Event: type 130, time -58768, number 3, value 0
Event: type 130, time -58768, number 4, value 0
Event: type 130, time -58768, number 5, value 0
Event: type 130, time -58768, number 6, value 32767
Event: type 130, time -58768, number 7, value 0
Event: type 130, time -58768, number 8, value 0
Event: type 130, time -58768, number 9, value 4681
Event: type 130, time -58768, number 10, value 4681
Event: type 2, time -56788, number 2, value -1690
Event: type 2, time -56732, number 2, value -2365
Event: type 2, time -56664, number 2, value -3041
Event: type 2, time -56644, number 2, value -3379
Event: type 2, time -56624, number 2, value -4054
Event: type 2, time -56608, number 2, value -4392
Event: type 2, time -56592, number 2, value -5068
Event: type 2, time -56568, number 2, value -6757
Event: type 2, time -56552, number 2, value -7432
Event: type 2, time -56536, number 2, value -8446
Event: type 2, time -56520, number 2, value -10135
Event: type 2, time -56500, number 2, value -11148
Event: type 2, time -56480, number 2, value -13175
Event: type 2, time -56464, number 2, value -14527
Event: type 2, time -56444, number 2, value -16216
Event: type 2, time -56428, number 2, value -17567
Event: type 2, time -56412, number 2, value -19256
Event: type 2, time -56396, number 2, value -21621
Event: type 2, time -56372, number 2, value -22634
Event: type 2, time -56360, number 2, value -24323
Event: type 2, time -56344, number 2, value -26012
Event: type 2, time -56320, number 2, value -27701
Event: type 2, time -56304, number 2, value -29390
Event: type 2, time -56288, number 2, value -30404
Event: type 2, time -56276, number 2, value -32093
Event: type 2, time -56252, number 2, value -32767
Event: type 2, time -55840, number 2, value -32431
Event: type 2, time -55824, number 2, value -31417
Event: type 2, time -55808, number 2, value -30404
Event: type 2, time -55784, number 2, value -29390
Event: type 2, time -55768, number 2, value -27701
Event: type 2, time -55752, number 2, value -25337
Event: type 2, time -55736, number 2, value -23648
Event: type 2, time -55712, number 2, value -21958
Event: type 2, time -55696, number 2, value -19932
Event: type 2, time -55680, number 2, value -18242
Event: type 2, time -55656, number 2, value -16216
Event: type 2, time -55640, number 2, value -14527
Event: type 2, time -55624, number 2, value -12162
Event: type 2, time -55600, number 2, value -10135
Event: type 2, time -55584, number 2, value -8446
Event: type 2, time -55568, number 2, value -5743
Event: type 2, time -55552, number 2, value -3379
Event: type 2, time -55532, number 2, value -1690
Event: type 2, time -55516, number 2, value 0
Event: type 2, time -55388, number 2, value 1689
Event: type 2, time -55368, number 2, value 3378
Event: type 2, time -55352, number 2, value 4391
Event: type 2, time -55336, number 2, value 5742
Event: type 2, time -55316, number 2, value 6756
Event: type 2, time -55292, number 2, value 7431
Event: type 2, time -55264, number 2, value 7769
Event: type 2, time -55224, number 2, value 7431
Event: type 2, time -55208, number 2, value 6756
Event: type 2, time -55152, number 2, value 6080
Event: type 2, time -55128, number 2, value 5742
Event: type 2, time -55116, number 2, value 4391
Event: type 2, time -55100, number 2, value 4053
Event: type 2, time -55072, number 2, value 3378
Event: type 2, time -55060, number 2, value 3040
Event: type 2, time -55044, number 2, value 1689
Event: type 2, time -55028, number 2, value 0
Event: type 2, time -54864, number 2, value -1690
Event: type 2, time -54836, number 2, value -3379
Event: type 2, time -54824, number 2, value -5743
Event: type 2, time -54808, number 2, value -7770
Event: type 2, time -54792, number 2, value -9459
Event: type 2, time -54768, number 2, value -11148
Event: type 2, time -54752, number 2, value -13175
Event: type 2, time -54736, number 2, value -14864
Event: type 2, time -54712, number 2, value -16553
Event: type 2, time -54700, number 2, value -18242
Event: type 2, time -54676, number 2, value -19256
Event: type 2, time -54652, number 2, value -21621
Event: type 2, time -54620, number 2, value -22634
Event: type 2, time -54596, number 2, value -24323
Event: type 2, time -54576, number 2, value -25337
Event: type 2, time -54540, number 2, value -27026
Event: type 2, time -54520, number 2, value -28715
Event: type 2, time -54504, number 2, value -30404
Event: type 2, time -54488, number 2, value -32093
Event: type 2, time -54464, number 2, value -32767

```

At the start is some initialization events then all the "type 2" events at the end are of me moving the throttle. Also pushing and holding a button down generates exactly one event until it is released. This is normal output.

Now look at the output on Feisty using kernel 2.6.20-13-generic:

```

$ jstest --event /dev/input/js0
Driver version is 2.1.0.
Joystick (Saitek Saitek X52 Flight Control System) has 11 axes (X, Y, Z, Rx, Ry, Rz, Throttle, Hat0X, Hat0Y, (null), (null))
and 16 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC).
Testing ... (interrupt to exit)
Event: type 129, time 288989924, number 0, value 0
Event: type 129, time 288989924, number 1, value 0
Event: type 129, time 288989924, number 2, value 0
Event: type 129, time 288989924, number 3, value 0
Event: type 129, time 288989924, number 4, value 0
Event: type 129, time 288989924, number 5, value 0
Event: type 129, time 288989924, number 6, value 0
Event: type 129, time 288989924, number 7, value 1
Event: type 129, time 288989924, number 8, value 0
Event: type 129, time 288989924, number 9, value 0
Event: type 129, time 288989924, number 10, value 0
Event: type 129, time 288989924, number 11, value 0
Event: type 129, time 288989924, number 12, value 0
Event: type 129, time 288989924, number 13, value 0
Event: type 129, time 288989924, number 14, value 0
Event: type 129, time 288989924, number 15, value 0
Event: type 130, time 288989924, number 0, value 0
Event: type 130, time 288989924, number 1, value 0
Event: type 130, time 288989924, number 2, value 18917
Event: type 130, time 288989924, number 3, value 0
Event: type 130, time 288989924, number 4, value 0
Event: type 130, time 288989924, number 5, value 0
Event: type 130, time 288989924, number 6, value 32767
Event: type 130, time 288989924, number 7, value 0
Event: type 130, time 288989924, number 8, value 0
Event: type 130, time 288989924, number 9, value 4681
Event: type 130, time 288989924, number 10, value 4681
Event: type 2, time 288991844, number 2, value 19255
Event: type 1, time 288991844, number 7, value 0
Event: type 1, time 288991844, number 7, value 1
Event: type 2, time 288991932, number 2, value 19931
Event: type 1, time 288991932, number 7, value 0
Event: type 1, time 288991932, number 7, value 1
Event: type 2, time 288991972, number 2, value 20268
Event: type 1, time 288991972, number 7, value 0
Event: type 1, time 288991972, number 7, value 1
Event: type 2, time 288992044, number 2, value 20944
Event: type 1, time 288992044, number 7, value 0
Event: type 1, time 288992044, number 7, value 1
Event: type 2, time 288992084, number 2, value 21282
Event: type 1, time 288992084, number 7, value 0
Event: type 1, time 288992084, number 7, value 1
Event: type 2, time 288992116, number 2, value 21620
Event: type 1, time 288992116, number 7, value 0
Event: type 1, time 288992116, number 7, value 1
Event: type 2, time 288992156, number 2, value 22295
Event: type 1, time 288992156, number 7, value 0
Event: type 1, time 288992156, number 7, value 1
Event: type 2, time 288992196, number 2, value 22633
Event: type 1, time 288992196, number 7, value 0
Event: type 1, time 288992196, number 7, value 1
Event: type 2, time 288992212, number 2, value 22971
Event: type 1, time 288992212, number 7, value 0
Event: type 1, time 288992212, number 7, value 1
Event: type 2, time 288992228, number 2, value 23984
Event: type 1, time 288992228, number 7, value 0
Event: type 1, time 288992228, number 7, value 1
Event: type 2, time 288992252, number 2, value 24660
Event: type 1, time 288992252, number 7, value 0
Event: type 1, time 288992252, number 7, value 1
Event: type 2, time 288992284, number 2, value 24998
Event: type 1, time 288992284, number 7, value 0
Event: type 1, time 288992284, number 7, value 1
Event: type 2, time 288992324, number 2, value 25336
Event: type 1, time 288992324, number 7, value 0
Event: type 1, time 288992324, number 7, value 1
Event: type 2, time 288992380, number 2, value 26011
Event: type 1, time 288992380, number 7, value 0
Event: type 1, time 288992380, number 7, value 1
Event: type 2, time 288992452, number 2, value 26349
Event: type 1, time 288992452, number 7, value 0
Event: type 1, time 288992452, number 7, value 1
Event: type 2, time 288992508, number 2, value 26687
Event: type 1, time 288992508, number 7, value 0
Event: type 1, time 288992508, number 7, value 1
Event: type 2, time 288992524, number 2, value 27700
Event: type 1, time 288992524, number 7, value 0
Event: type 1, time 288992524, number 7, value 1
Event: type 2, time 288992548, number 2, value 29052
Event: type 1, time 288992548, number 7, value 0
Event: type 1, time 288992548, number 7, value 1
Event: type 2, time 288992564, number 2, value 30065
Event: type 1, time 288992564, number 7, value 0
Event: type 1, time 288992564, number 7, value 1
Event: type 2, time 288992580, number 2, value 31078
Event: type 1, time 288992580, number 7, value 0
Event: type 1, time 288992580, number 7, value 1
Event: type 2, time 288992604, number 2, value 32430
Event: type 1, time 288992604, number 7, value 0
Event: type 1, time 288992604, number 7, value 1
Event: type 2, time 288992620, number 2, value 32767
Event: type 1, time 288992620, number 7, value 0
Event: type 1, time 288992620, number 7, value 1
Event: type 1, time 288992636, number 7, value 0
Event: type 1, time 288992636, number 7, value 1
Event: type 1, time 288992660, number 7, value 0
Event: type 1, time 288992660, number 7, value 1
Event: type 1, time 288992676, number 7, value 0
Event: type 1, time 288992676, number 7, value 1
Event: type 1, time 288992692, number 7, value 0
Event: type 1, time 288992692, number 7, value 1
Event: type 1, time 288992980, number 7, value 0
Event: type 1, time 288992980, number 7, value 1
Event: type 1, time 288992996, number 7, value 0
Event: type 1, time 288992996, number 7, value 1
Event: type 1, time 288993012, number 7, value 0
Event: type 1, time 288993012, number 7, value 1
Event: type 1, time 288993036, number 7, value 0
Event: type 1, time 288993036, number 7, value 1
Event: type 1, time 288993052, number 7, value 0
Event: type 1, time 288993052, number 7, value 1
Event: type 1, time 288993068, number 7, value 0
Event: type 1, time 288993068, number 7, value 1
Event: type 1, time 288993092, number 7, value 0
Event: type 1, time 288993092, number 7, value 1
Event: type 2, time 288993108, number 2, value 32430
Event: type 1, time 288993108, number 7, value 0
Event: type 1, time 288993108, number 7, value 1
Event: type 2, time 288993124, number 2, value 31416
Event: type 1, time 288993124, number 7, value 0
Event: type 1, time 288993124, number 7, value 1
Event: type 2, time 288993148, number 2, value 30065
Event: type 1, time 288993148, number 7, value 0
Event: type 1, time 288993148, number 7, value 1
Event: type 2, time 288993164, number 2, value 28376
Event: type 1, time 288993164, number 7, value 0
Event: type 1, time 288993164, number 7, value 1
Event: type 2, time 288993180, number 2, value 26687
Event: type 1, time 288993180, number 7, value 0
Event: type 1, time 288993180, number 7, value 1
Event: type 2, time 288993196, number 2, value 26011
Event: type 1, time 288993196, number 7, value 0
Event: type 1, time 288993196, number 7, value 1
Event: type 2, time 288993220, number 2, value 24660
Event: type 1, time 288993220, number 7, value 0
Event: type 1, time 288993220, number 7, value 1
Event: type 2, time 288993236, number 2, value 22633
Event: type 1, time 288993236, number 7, value 0
Event: type 1, time 288993236, number 7, value 1
Event: type 2, time 288993252, number 2, value 21282
Event: type 1, time 288993252, number 7, value 0
Event: type 1, time 288993252, number 7, value 1
Event: type 2, time 288993276, number 2, value 19931
Event: type 1, time 288993276, number 7, value 0
Event: type 1, time 288993276, number 7, value 1
Event: type 2, time 288993292, number 2, value 18579
Event: type 1, time 288993292, number 7, value 0
Event: type 1, time 288993292, number 7, value 1
Event: type 2, time 288993308, number 2, value 16552
Event: type 1, time 288993308, number 7, value 0
Event: type 1, time 288993308, number 7, value 1
Event: type 2, time 288993332, number 2, value 15539
Event: type 1, time 288993332, number 7, value 0
Event: type 1, time 288993332, number 7, value 1
Event: type 2, time 288993348, number 2, value 14863
Event: type 1, time 288993348, number 7, value 0
Event: type 1, time 288993348, number 7, value 1
Event: type 2, time 288993364, number 2, value 13174
Event: type 1, time 288993364, number 7, value 0
Event: type 1, time 288993364, number 7, value 1
Event: type 2, time 288993388, number 2, value 12499
Event: type 1, time 288993388, number 7, value 0
Event: type 1, time 288993388, number 7, value 1
Event: type 2, time 288993404, number 2, value 11823
Event: type 1, time 288993404, number 7, value 0
Event: type 1, time 288993404, number 7, value 1
Event: type 2, time 288993420, number 2, value 10472
Event: type 1, time 288993420, number 7, value 0
Event: type 1, time 288993420, number 7, value 1
Event: type 2, time 288993444, number 2, value 9458
Event: type 1, time 288993444, number 7, value 0
Event: type 1, time 288993444, number 7, value 1
Event: type 2, time 288993460, number 2, value 8107
Event: type 1, time 288993460, number 7, value 0
Event: type 1, time 288993460, number 7, value 1
Event: type 2, time 288993476, number 2, value 7431
Event: type 1, time 288993476, number 7, value 0
Event: type 1, time 288993476, number 7, value 1
Event: type 2, time 288993492, number 2, value 6418
Event: type 1, time 288993492, number 7, value 0
Event: type 1, time 288993492, number 7, value 1
Event: type 2, time 288993516, number 2, value 5742
Event: type 1, time 288993516, number 7, value 0
Event: type 1, time 288993516, number 7, value 1
Event: type 2, time 288993532, number 2, value 5405
Event: type 1, time 288993532, number 7, value 0
Event: type 1, time 288993532, number 7, value 1
Event: type 2, time 288993644, number 2, value 5742
Event: type 1, time 288993644, number 7, value 0
Event: type 1, time 288993644, number 7, value 1

```

You can see that for every normal "type 2" event there are two "type 1" events (which is a button 7 press then release).  I'm not pushing any buttons.  Holding a button down generates a stream of press/release events.  This is abnormal behavior and doesn't work in most software that uses a joystick.  It sort of works but not well because there are too many extraneous events flying around.

Anyone have any ideas?  I'm pretty sure this is related to a kernel change but I'm not ready to go digging in kernel code just yet.

---

### Post by Zedark on 2007-04-29
Same behavior with my 'Dual PSX-USB Adaptor' since migration to Feisty:

holding a button down generates a stream of on/off events.


Driver version is 2.1.0.
Joystick (Dual PSX-USB Adaptor  Dual PSX-USB Adaptor ) has 4 axes (X, Y, Z, Rz)
and 16 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDe
ad, BtnA, BtnB, BtnC).
Testing ... (interrupt to exit)

---

### Post by Chris on 2007-04-29
A while ago I did a test with the 2.6.21-rc5 kernel and it seemed to be fixed.  I'm not sure if it works in the final 2.6.21 kernel.

Unfortunately I'm not sure what the exact fix is.  I would like to simply patch the stock Fiesty 2.6.20 kernel so I can continue to easily run the stock kernel.

---

### Post by vmistl on 2007-04-30
Same problem for me with the USB Saitek X52 Joystick.
Was working fine in Edgy... until I installed Feisty (2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux). Now axes are working fine but buttons of the main joystick do not work...

---

