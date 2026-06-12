---
title: "Webcam problem (hardy)"
date: 2009-10-29
forum: Hardware
---

### Post by _exn_ on 2009-10-29
Hi everybody!

  I have a problem with a "hercules deluxe optical glass" webcam on ubuntu 8.04.3 
  
 Of course it does not support webcams, but I'm tried to compile a v4l modules for this webcam then got a problem.

```

903.174428] gspca: probing 06f8:3008
[  903.184911] sonixj: Sonix chip id: 11
[  903.190952] gspca: probe ok
[  903.190968] usbcore: registered new interface driver sonixj
[  903.190971] sonixj: registered
[  936.259390] gspca: usb_submit_urb alt 8 err -28
[  936.283474] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a370 (#81) state 2
[  944.526739] gspca: usb_submit_urb alt 8 err -28
[  944.550831] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a3c0 (#81) state 2
[  960.120511] gspca: usb_submit_urb alt 8 err -28
[  960.144601] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a410 (#81) state 2
[ 1119.186950] gspca: usb_submit_urb alt 8 err -28
[ 1119.211033] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a460 (#81) state 2
[ 1464.460793] gspca: usb_submit_urb alt 8 err -28
[ 1464.483882] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a4b0 (#81) state 2
[ 1503.846718] gspca: usb_submit_urb alt 8 err -28
[ 1503.870812] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a500 (#81) state 2
[ 1524.680075] gspca: usb_submit_urb alt 8 err -28
[ 1524.704160] ohci_hcd 0000:00:02.0: leak ed ffff81007ba5a550 (#81) state 2

```

 device video0 are present

 of course nothing works.. empty screen or crashes of the programs which attempts to work with it. 

 any suggestions ?

---

