---
title: "Special Hotkeys not Generating any ACPI events or keypresses in 18.xx"
date: 2018-10-19
forum: Hardware
---

### Post by kenneth-fechter on 2018-10-19
I installed 18.10 on a Lenovo Legion Y530 (i7-8750H, GTX 1050Ti, 16GB ram). Everything runs well except for some of the special hot keys. 

Specifically Airplane Mode, Microphone Mute, Camera Privacy, and the Screen Record button. 

I tried assigning them in Keyboard shortcuts and tried seeing if they generate any events in acpi_listen, but neither of those yielded any results. 

the screen record button generates an event in evtest, but none of the other buttons do. 

Event: time 1539923835.799043, type 4 (EV_MSC), code 4 (MSC_SCAN), value 6d
Event: time 1539923835.799043, -------------- SYN_REPORT ------------
Event: time 1539923835.859878, type 4 (EV_MSC), code 4 (MSC_SCAN), value 6d
Event: time 1539923835.859878, -------------- SYN_REPORT ------------
Event: time 1539923836.489912, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1d
Event: time 1539923836.489912, type 1 (EV_KEY), code 29 (KEY_LEFTCTRL), value 1
Event: time 1539923836.489912, -------------- SYN_REPORT ------------
Event: time 1539923836.492229, type 4 (EV_MSC), code 4 (MSC_SCAN), value 2a
Event: time 1539923836.492229, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1539923836.492229, -------------- SYN_REPORT ------------
Event: time 1539923836.493270, type 4 (EV_MSC), code 4 (MSC_SCAN), value 6d
Event: time 1539923836.493270, -------------- SYN_REPORT ------------
Event: time 1539923836.789563, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1d
Event: time 1539923836.789563, type 1 (EV_KEY), code 29 (KEY_LEFTCTRL), value 0
Event: time 1539923836.789563, -------------- SYN_REPORT ------------
Event: time 1539923836.794150, type 4 (EV_MSC), code 4 (MSC_SCAN), value 2a
Event: time 1539923836.794150, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1539923836.794150, -------------- SYN_REPORT ------------
Event: time 1539923836.795585, type 4 (EV_MSC), code 4 (MSC_SCAN), value 6d
Event: time 1539923836.795585, -------------- SYN_REPORT ------------



the above is what evtest prints when the screen record button is pressed.

---

